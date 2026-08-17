# Tema 24 — Casos Prácticos

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos recorren la aplicación de referencia **avisos ciudadanos** (ver tema-24-contenido.md, «Convenciones»): el **Caso 1** trabaja la **elección de enfoque tecnológico**; el **Caso 2**, el **ciclo de vida, la persistencia local y la sincronización**; y el **Caso 3**, la **accesibilidad, los permisos, la seguridad y la publicación**.

---

## Caso 1 — Elección de enfoque para la app de avisos ciudadanos

### Enunciado

El Área de Obras y Equipamientos quiere una **aplicación móvil de avisos ciudadanos**: el vecino comunica una incidencia en la vía pública (farola apagada, socavón, contenedor dañado) adjuntando **una fotografía y su ubicación**, consulta el estado de sus avisos y recibe una **notificación** cuando se resuelven. Debe estar disponible en **Android y iOS**, el presupuesto es ajustado, el plazo es de seis meses y el Ayuntamiento dispone de un equipo con experiencia en desarrollo web pero no en Kotlin ni en Swift.

### Cuestiones

**Cuestión 1 — Enfoques posibles (3 puntos).** Enumere las cuatro estrategias de desarrollo móvil disponibles e indique, para cada una, **cómo se dibuja la interfaz**.

**Cuestión 2 — Descarte razonado de la PWA (2 puntos).** El proveedor propone resolverlo con una PWA para ahorrar costes. Indique **dos motivos técnicos** por los que esta propuesta es arriesgada para este supuesto concreto.

**Cuestión 3 — Elección y justificación (3 puntos).** Elija el enfoque que recomendaría y justifíquelo con **tres criterios** aplicados a los datos del enunciado.

**Cuestión 4 — Riesgo de la decisión (2 puntos).** Señale el principal **riesgo a medio plazo** del enfoque elegido y una medida para mitigarlo.

### Solución orientativa

- **C1**: (§1.2)

| Estrategia | Cómo se dibuja la interfaz |
|---|---|
| Nativa | Componentes nativos del sistema (Kotlin/Swift) |
| Híbrida de contenedor web | WebView embebido que renderiza HTML/CSS/JS |
| Multiplataforma compilada | Componentes nativos manejados desde JavaScript (React Native) o motor gráfico propio que dibuja cada píxel (Flutter) |
| PWA | Navegador del sistema |

- **C2**: (§1.2.3) Dos motivos suficientes: (a) las **notificaciones push** en iOS han tenido históricamente soporte tardío y limitado en la web, y son un requisito funcional explícito del enunciado; (b) la PWA **no se distribuye por las tiendas**, lo que resta visibilidad a una app dirigida a toda la ciudadanía, y su acceso a cámara y ubicación en segundo plano es más limitado y desigual entre plataformas. También sería válido señalar la dificultad de garantizar el trabajo offline con adjuntos pesados dentro de las cuotas de almacenamiento del navegador.

- **C3**: (§5.2) **Multiplataforma compilado** (React Native o Flutter). Criterios: (a) **presupuesto y plazo ajustados** con necesidad de dos plataformas → una sola base de código y un solo equipo; (b) las capacidades necesarias —cámara, ubicación, notificaciones push, almacenamiento local— están **cubiertas por bibliotecas maduras**, no son API exóticas ni de última hora; (c) el **perfil del equipo** es web, por lo que React Native reaprovecha directamente su conocimiento de JavaScript y del modelo de componentes de React. Un híbrido de contenedor web sería defendible por el perfil del equipo, pero penalizaría el rendimiento con listas de avisos y fotografías; el nativo, siendo la opción de mayor calidad, no encaja con el presupuesto ni con el perfil disponible.

- **C4**: (§5.2) Riesgo principal: **dependencia de un tercero**: si el framework tarda en soportar una versión nueva de Android o de iOS, o si una biblioteca clave queda sin mantenimiento, el proyecto queda expuesto. Mitigación: elegir un framework con respaldo corporativo y comunidad amplia, **limitar el número de dependencias de terceros**, exigir contractualmente el mantenimiento evolutivo y verificar que existe la posibilidad de escribir módulos nativos propios para las funcionalidades críticas.

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Las cuatro estrategias correctamente enumeradas, con el mecanismo de renderizado de cada una | 3 |
| Dos motivos técnicos válidos para descartar la PWA en este supuesto | 2 |
| Elección coherente con el enunciado y justificada con tres criterios aplicados a sus datos | 3 |
| Riesgo a medio plazo correctamente identificado, con una medida de mitigación | 2 |

---

## Caso 2 — Ciclo de vida, trabajo sin conexión y sincronización

### Enunciado

Durante las pruebas de la app de avisos aparecen tres incidencias reportadas por los usuarios:

1. Un vecino redacta un aviso largo, **gira el móvil** para ver mejor el mapa y **el texto escrito desaparece**.
2. Otro vecino envía un aviso desde un aparcamiento subterráneo **sin cobertura**; la app muestra un error y le obliga a repetirlo todo al salir a la calle.
3. Un tercero, con mala cobertura, pulsa «Enviar» y el aviso aparece **duplicado** en la sede.

### Cuestiones

**Cuestión 1 — Diagnóstico del giro de pantalla (2 puntos).** Explique la causa técnica de la primera incidencia en Android e indique los dos mecanismos que la resuelven.

**Cuestión 2 — Diseño offline (3 puntos).** Describa las tres piezas del patrón *offline-first* que resuelven la segunda incidencia.

**Cuestión 3 — Duplicados (3 puntos).** Explique por qué se produce la tercera incidencia y proponga la corrección, indicando qué hace el cliente y qué hace el servidor.

**Cuestión 4 — Hilo principal (2 puntos).** El envío del aviso se implementó llamando a la API directamente desde el manejador del botón. Indique qué problema provoca y cómo se corrige en Kotlin y en Swift.

### Solución orientativa

- **C1**: (§2.1.1) Girar el dispositivo es un **cambio de configuración** que, por defecto, **destruye y recrea la Activity**; el estado no persistido se pierde. Se resuelve guardando el estado transitorio en `onSaveInstanceState()` mediante un `Bundle` y restaurándolo en `onCreate()`, y/o conservando el estado en un **`ViewModel`**, que sobrevive a la recreación.

- **C2**: (§2.3.2) Tres piezas: (a) un **repositorio local** (SQLite vía Room o Core Data) que es la **única fuente de verdad** de la interfaz, de modo que la pantalla nunca espera a la red; (b) una **cola de operaciones pendientes**, con los registros marcados como `sincronizado = false`; (c) un **planificador de trabajo diferido** del sistema (`WorkManager` en Android, `BGTaskScheduler` en iOS) que envía lo pendiente cuando hay red, batería y el sistema lo permite.

```kotlin
@Entity(tableName = "avisos")
data class Aviso(
    @PrimaryKey val id: String,      // UUID generado en el cliente
    val descripcion: String,
    val latitud: Double,
    val longitud: Double,
    val sincronizado: Boolean = false
)
```

- **C3**: (§2.3.2) El `POST` sí llegó al servidor, pero la **respuesta se perdió** por el corte de red; el cliente lo interpretó como fallo y reintentó, creando un segundo aviso. Corrección en dos partes: el **cliente** genera un **identificador único de operación (UUID)** al crear el aviso y lo envía **idéntico en todos los reintentos**; el **servidor** trata ese identificador como **clave de idempotencia** y, si ya existe, devuelve el aviso previamente creado en lugar de crear otro. Con ello reintentar deja de ser peligroso, que es la condición para que el modo offline sea viable.

- **C4**: (§2.3.1) Llamar a la API desde el manejador del botón ejecuta la **petición de red en el hilo principal**, que queda bloqueado: en Android provoca el diálogo **ANR** y en iOS congela la interfaz, con riesgo de cierre por el *watchdog*. Se corrige lanzando el trabajo en un hilo secundario y devolviendo solo el resultado a la interfaz:

```kotlin
suspend fun enviarAviso(aviso: Aviso) = withContext(Dispatchers.IO) { api.crearAviso(aviso) }
```

```swift
Task { let resultado = await servicio.enviarAviso(aviso); actualizarInterfaz(resultado) }
```

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Causa del giro de pantalla correctamente explicada, con los dos mecanismos de solución | 2 |
| Las tres piezas del patrón offline-first, con el papel de cada una | 3 |
| Causa del duplicado bien razonada y corrección repartida entre cliente (UUID) y servidor (idempotencia) | 3 |
| Problema del hilo principal identificado (ANR/congelación) y corregido en ambas plataformas | 2 |

---

## Caso 3 — Accesibilidad, permisos, seguridad y publicación

### Enunciado

La app de avisos está terminada y va a publicarse. Antes de subirla a las tiendas, la Dirección General de Transparencia y Atención a la Ciudadanía solicita una revisión de **accesibilidad, permisos, seguridad y despliegue**, dado que se trata de una aplicación del sector público dirigida a toda la ciudadanía.

### Cuestiones

**Cuestión 1 — Obligación de accesibilidad (2 puntos).** Indique la norma que obliga a esta aplicación a ser accesible y **dos medidas concretas** que deban comprobarse en la interfaz.

**Cuestión 2 — Permisos (2 puntos).** La app solicita cámara y ubicación. Indique cómo debe gestionarse cada permiso en Android y qué elemento adicional exige iOS, y qué debe hacer la aplicación si el usuario **deniega** el permiso de ubicación.

**Cuestión 3 — Seguridad (3 puntos).** El proveedor entrega el código con: el *token* de sesión guardado en `SharedPreferences`, la clave de la API de mapas incrustada en una constante del código y la validación de que el aviso pertenece al ciudadano hecha en la aplicación. Corrija los **tres** defectos.

**Cuestión 4 — Publicación (3 puntos).** Describa el procedimiento de publicación en ambas tiendas, señalando dos diferencias relevantes, y proponga una estrategia de despliegue prudente.

### Solución orientativa

- **C1**: (§2.2.1) Obliga el **Real Decreto 1112/2018**, que extiende la accesibilidad del sector público a las **aplicaciones para dispositivos móviles**, con la norma **EN 301 549** (que incorpora las WCAG en nivel AA) como referencia técnica; incluye publicar una **declaración de accesibilidad** y un mecanismo de reclamación. Dos medidas concretas (bastan dos): etiquetar los iconos sin texto con `contentDescription` (Android) o `accessibilityLabel` (iOS) para TalkBack y VoiceOver; **medir el texto en sp** y respetar el tamaño de fuente del sistema sin que el diseño se rompa; garantizar un **contraste** mínimo de 4,5:1; y áreas táctiles de al menos **48×48 dp** (Android) o **44×44 puntos** (iOS).

- **C2**: (§1.1.1, §3.1.2, §3.2.2) Cámara y ubicación son **permisos peligrosos**: se declaran en el `AndroidManifest.xml` y se **solicitan en tiempo de ejecución**, comprobando antes si ya están concedidos; el usuario puede concederlos de forma permanente, solo mientras usa la app o solo una vez, y revocarlos después. En **iOS** se exige además la **cadena de descripción de uso** en `Info.plist` (`NSCameraUsageDescription`, `NSLocationWhenInUseUsageDescription`), que se muestra literalmente al usuario y cuya ausencia es motivo de rechazo en la revisión. Si el usuario **deniega** la ubicación, la app **no debe fallar**: debe degradarse ofreciendo la introducción manual de la dirección y explicando para qué serviría el permiso, sin bloquear el envío del aviso.

- **C3**: (§2.1.2, §5.1) Tres correcciones:

| Defecto | Corrección |
|---|---|
| Token de sesión en `SharedPreferences` | Trasladarlo al **Keystore** de Android (o al **Keychain** en iOS); las preferencias no son almacenamiento seguro (OWASP Mobile: almacenamiento inseguro) |
| Clave de API incrustada en el código | Todo secreto embarcado en la app **debe considerarse público**: se elimina del cliente y las llamadas se enrutan por el **servidor municipal**, que custodia la clave; si la API exige clave en cliente, restringirla por aplicación firmada y dominio, y rotarla |
| Validación de propiedad del aviso en el cliente | La comprobación de **autorización se hace siempre en el servidor**: el cliente es manipulable. En caso contrario existe una vulnerabilidad de referencia directa insegura a objetos (IDOR) |

- **C4**: (§5.3) **Google Play**: subir un **AAB** (obligatorio para apps nuevas desde agosto de 2021) firmado, con **Play App Signing**, declarar la sección de seguridad de los datos y publicar por canales (interno, cerrado, abierto, producción). **App Store**: generar el **IPA** desde Xcode y enviarlo a App Store Connect con el **certificado y el perfil de aprovisionamiento** del Apple Developer Program, cumplimentar las **etiquetas de privacidad** y pasar la revisión. Dos diferencias relevantes (bastan dos): la cuota es de **pago único** en Google Play frente a **cuota anual** en Apple; la revisión es **mayoritariamente automatizada** en Google Play frente a **revisión humana siempre** en la App Store; y el formato es **AAB** frente a **IPA**. Estrategia prudente: canal **interno** y **TestFlight** para el equipo → **beta cerrada** con vecinos voluntarios → **publicación por fases** al 5 %, 20 % y 100 % vigilando la tasa de fallos, con capacidad de detener el despliegue; reservar días de margen en el calendario para la revisión humana de Apple y **versionar la API** del servidor, porque muchos usuarios tardarán semanas en actualizar.

### Criterios de evaluación

| Criterio | Puntos |
|---|---|
| Norma de accesibilidad correcta (RD 1112/2018, EN 301 549) y dos medidas concretas de interfaz | 2 |
| Gestión correcta de permisos peligrosos en ambas plataformas y degradación adecuada ante la denegación | 2 |
| Los tres defectos de seguridad corregidos: almacén seguro, secreto fuera del cliente y autorización en el servidor | 3 |
| Procedimiento de publicación en ambas tiendas, dos diferencias y estrategia de despliegue por fases | 3 |
