# Tema 24 — Test de Autoevaluación

> **Título**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-17
> **Fuentes**: ver tema-24-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Introducción y estrategias (P1-P10), Arquitectura y fundamentos (P11-P24), Desarrollo nativo (P25-P40), Desarrollo híbrido (P41-P52), Comparativa y publicación (P53-P60).

---

### Pregunta 1

**¿Qué define a una aplicación móvil nativa?**

A) Se desarrolla con el SDK oficial de cada plataforma y se compila a código ejecutable por ella
B) Se escribe en HTML, CSS y JavaScript y se ejecuta dentro de un WebView empaquetado
C) Se distribuye exclusivamente fuera de las tiendas de aplicaciones

<details><summary>Respuesta</summary>

**Correcta: A) Se desarrolla con el SDK oficial de cada plataforma y se compila a código ejecutable por ella** Nativo significa Kotlin o Java con Android Studio para Android, y Swift u Objective-C con Xcode para iOS, usando los componentes de interfaz del propio sistema.

*Referencia: §1.2.1 [ANDROID-DEV]*
</details>

---

### Pregunta 2

**¿Cuál es el rasgo técnico distintivo de una aplicación híbrida de contenedor web?**

A) Compila el código fuente a lenguaje máquina de cada plataforma
B) La interfaz se renderiza dentro de un WebView embebido en una app nativa mínima
C) Utiliza componentes nativos del sistema controlados desde JavaScript

<details><summary>Respuesta</summary>

**Correcta: B) La interfaz se renderiza dentro de un WebView embebido en una app nativa mínima** Cordova, Ionic y Capacitor empaquetan la aplicación web dentro de un contenedor nativo cuya única pantalla es un WebView a pantalla completa.

*Referencia: §1.2.2 [CORDOVA-DOC]*
</details>

---

### Pregunta 3

**¿Qué dos piezas convierten una aplicación web en una PWA?**

A) El fichero de manifiesto de Android y el fichero Info.plist
B) Un plugin de Cordova y un puente asíncrono
C) El Service Worker y el Web App Manifest

<details><summary>Respuesta</summary>

**Correcta: C) El Service Worker y el Web App Manifest** El Service Worker actúa como proxy de red y permite funcionar sin conexión; el manifiesto aporta los metadatos de instalación en la pantalla de inicio. Ambos exigen HTTPS.

*Referencia: §1.2.3 [SERVICE-WORKERS] [WEB-APP-MANIFEST]*
</details>

---

### Pregunta 4

**La fragmentación es una característica típicamente asociada a:**

A) iOS, por la variedad de versiones de Swift
B) Android, por la diversidad de fabricantes, tamaños de pantalla, densidades y versiones del sistema
C) Las PWA, por la diversidad de servidores web

<details><summary>Respuesta</summary>

**Correcta: B) Android, por la diversidad de fabricantes, tamaños de pantalla, densidades y versiones del sistema** Al ser un sistema abierto adaptado por múltiples fabricantes, Android obliga al desarrollador a absorber esa diversidad con recursos alternativos y bibliotecas de compatibilidad.

*Referencia: §1.1 [ANDROID-DEV]*
</details>

---

### Pregunta 5

**Respecto a los permisos sensibles (cámara, localización, micrófono) en las versiones modernas de Android e iOS:**

A) Se conceden en tiempo de ejecución y el usuario puede revocarlos en cualquier momento
B) Se conceden de forma definitiva durante la instalación de la aplicación
C) Los concede automáticamente la tienda tras revisar la aplicación

<details><summary>Respuesta</summary>

**Correcta: A) Se conceden en tiempo de ejecución y el usuario puede revocarlos en cualquier momento** Desde Android 6.0 (API 23) y en iOS moderno, la app debe pedirlos al usarlos y funcionar de forma degradada si se deniegan, sin fallar.

*Referencia: §1.1.1 [ANDROID-DEV] [APPLE-DEV]*
</details>

---

### Pregunta 6

**¿Cuáles son los elementos que más batería consumen en un dispositivo móvil?**

A) El sistema de ficheros y la caché de la aplicación
B) El almacén seguro de credenciales y el cifrado en reposo
C) La pantalla, la radio de comunicaciones y el GPS

<details><summary>Respuesta</summary>

**Correcta: C) La pantalla, la radio de comunicaciones y el GPS** De ahí las técnicas de agrupación de transferencias y de diferimiento del trabajo no urgente: activar la radio tiene un coste fijo elevado que penaliza muchos envíos pequeños y dispersos.

*Referencia: §1.1.2 [ANDROID-DEV]*
</details>

---

### Pregunta 7

**¿Qué consecuencia directa tiene para el programador la limitación de memoria de un dispositivo móvil?**

A) Que no se pueden usar bases de datos relacionales en el dispositivo
B) Que la aplicación debe cifrar toda la información que guarde en disco
C) Que el sistema puede terminar la aplicación en segundo plano y esta debe poder restaurar su estado

<details><summary>Respuesta</summary>

**Correcta: C) Que el sistema puede terminar la aplicación en segundo plano y esta debe poder restaurar su estado** El sistema sacrifica procesos para liberar memoria, por lo que el estado debe guardarse al perder el primer plano y no confiarse a un evento de cierre.

*Referencia: §1.1.2 [ANDROID-DEV] [APPLE-DEV]*
</details>

---

### Pregunta 8

**El diálogo ANR (*Application Not Responding*) de Android aparece cuando:**

A) El hilo principal permanece bloqueado durante varios segundos
B) La aplicación solicita un permiso que el usuario ha denegado
C) La firma digital del paquete no coincide con la registrada

<details><summary>Respuesta</summary>

**Correcta: A) El hilo principal permanece bloqueado durante varios segundos** Toda operación de red o de entrada/salida debe ejecutarse fuera del hilo principal. En iOS el equivalente es la congelación de la interfaz y el posible cierre por el watchdog del sistema.

*Referencia: §2.1.1 [ANDROID-DEV]*
</details>

---

### Pregunta 9

**¿Qué requisito impone el uso de Service Workers en una PWA?**

A) Estar publicada previamente en Google Play o en la App Store
B) Servir la aplicación mediante HTTPS, es decir, en un contexto seguro
C) Disponer de un certificado de firma emitido por Apple

<details><summary>Respuesta</summary>

**Correcta: B) Servir la aplicación mediante HTTPS, es decir, en un contexto seguro** Los navegadores solo registran Service Workers en contextos seguros, precisamente porque interceptan todas las peticiones de red de la aplicación.

*Referencia: §1.2.3 [SERVICE-WORKERS]*
</details>

---

### Pregunta 10

**Señale la afirmación correcta sobre las PWA frente a las aplicaciones de tienda:**

A) No pasan por revisión ni por las tiendas, pero su acceso al hardware es limitado y desigual entre plataformas
B) Ofrecen el mismo acceso al hardware que una aplicación nativa en cualquier plataforma
C) Deben firmarse con la clave de desarrollador antes de instalarse desde el navegador

<details><summary>Respuesta</summary>

**Correcta: A) No pasan por revisión ni por las tiendas, pero su acceso al hardware es limitado y desigual entre plataformas** Se instalan desde el navegador, lo que agiliza la distribución, pero pierden visibilidad en el catálogo de las tiendas y capacidades del dispositivo, con más restricciones históricas en iOS.

*Referencia: §1.2.3 [MDN-PWA]*
</details>

---

### Pregunta 11

**En una aplicación móvil, ¿quién decide cuándo se detiene o se destruye la aplicación?**

A) La propia aplicación, mediante su método principal de finalización
B) La tienda de aplicaciones, según la política de la plataforma
C) El sistema operativo; el programador solo reacciona implementando los métodos de ciclo de vida

<details><summary>Respuesta</summary>

**Correcta: C) El sistema operativo; el programador solo reacciona implementando los métodos de ciclo de vida** Es la diferencia estructural más importante frente al desarrollo de escritorio: la aplicación no es dueña de su propia ejecución.

*Referencia: §2.1 [ANDROID-LIFECYCLE] [APPLE-DEV]*
</details>

---

### Pregunta 12

**¿Qué ocurre por defecto en Android al girar el dispositivo?**

A) La Activity conserva íntegramente su estado sin intervención del programador
B) La Activity se destruye y se recrea, por lo que el estado debe guardarse expresamente
C) El sistema suspende la Activity hasta que el usuario devuelve el dispositivo a su orientación anterior

<details><summary>Respuesta</summary>

**Correcta: B) La Activity se destruye y se recrea, por lo que el estado debe guardarse expresamente** Los cambios de configuración recrean la Activity. El estado transitorio se conserva con onSaveInstanceState() y el estado más amplio, en un ViewModel.

*Referencia: §2.1.1 [ANDROID-LIFECYCLE] [JETPACK]*
</details>

---

### Pregunta 13

**¿En qué callback de una Activity de Android conviene liberar recursos exclusivos como la cámara o el GPS?**

A) En onPause(), porque es el primer aviso de que se ha perdido el foco
B) En onCreate(), antes de inflar el diseño
C) En onDestroy(), porque es el único punto garantizado

<details><summary>Respuesta</summary>

**Correcta: A) En onPause(), porque es el primer aviso de que se ha perdido el foco** Además, onPause() debe ser muy breve. onDestroy() no está garantizado: si el sistema mata el proceso, puede no llegar a ejecutarse.

*Referencia: §2.1.1 [ANDROID-LIFECYCLE]*
</details>

---

### Pregunta 14

**El estado *Suspended* de una aplicación iOS significa que:**

A) La aplicación ha sido desinstalada y debe volver a descargarse de la App Store
B) La aplicación está en primer plano pero no recibe eventos táctiles
C) La aplicación permanece en memoria pero no ejecuta código, y el sistema puede terminarla sin aviso

<details><summary>Respuesta</summary>

**Correcta: C) La aplicación permanece en memoria pero no ejecuta código, y el sistema puede terminarla sin aviso** Por eso el estado debe persistirse al pasar a segundo plano. El estado en primer plano sin recibir eventos es *Inactive*.

*Referencia: §2.1.1 [APPLE-DEV]*
</details>

---

### Pregunta 15

**¿Qué motor de base de datos embebido sustenta la persistencia estructurada local tanto en Android como en iOS?**

A) PostgreSQL en modo cliente ligero
B) SQLite, sin proceso servidor y con la base de datos en un único fichero
C) MongoDB Mobile, sobre documentos JSON

<details><summary>Respuesta</summary>

**Correcta: B) SQLite, sin proceso servidor y con la base de datos en un único fichero** Room en Android y Core Data o SwiftData en iOS se apoyan en SQLite, añadiendo una capa de mapeo objeto-relacional.

*Referencia: §2.1.2 [SQLITE] [JETPACK] [COREDATA]*
</details>

---

### Pregunta 16

**¿Dónde deben almacenarse las credenciales y los tokens de sesión de una aplicación móvil?**

A) En el Keystore de Android o en el Keychain de iOS
B) En SharedPreferences o UserDefaults, cifrando el nombre de la clave
C) En un fichero de texto dentro del almacenamiento externo compartido

<details><summary>Respuesta</summary>

**Correcta: A) En el Keystore de Android o en el Keychain de iOS** El almacenamiento inseguro de datos es uno de los riesgos clásicos del OWASP Mobile Top 10. Las preferencias y los ficheros en claro nunca son sitio para secretos.

*Referencia: §2.1.2 [OWASP-MOBILE] [OWASP-MASVS]*
</details>

---

### Pregunta 17

**El *sandbox* de una aplicación móvil es:**

A) Un entorno de pruebas de la tienda donde se validan las aplicaciones antes de publicarse
B) Un espacio de almacenamiento y ejecución privado y aislado, inaccesible para otras aplicaciones
C) Un servicio en la nube donde se replican automáticamente los datos de la aplicación

<details><summary>Respuesta</summary>

**Correcta: B) Un espacio de almacenamiento y ejecución privado y aislado, inaccesible para otras aplicaciones** Se elimina al desinstalar la app. En Android se apoya en que cada aplicación es un usuario distinto del kernel Linux.

*Referencia: §2.1.2 [ANDROID-ARCH] [APPLE-ARCH]*
</details>

---

### Pregunta 18

**¿Qué diferencia hay entre las unidades dp y sp en Android?**

A) Ninguna: son sinónimos y se usan indistintamente
B) dp se usa para el texto y sp para los márgenes y los iconos
C) sp es como dp pero además se escala con el tamaño de fuente elegido por el usuario, por lo que se usa para el texto

<details><summary>Respuesta</summary>

**Correcta: C) sp es como dp pero además se escala con el tamaño de fuente elegido por el usuario, por lo que se usa para el texto** Medir el texto en dp impediría que la persona que amplía la letra del sistema pueda leer la aplicación: es un defecto de accesibilidad.

*Referencia: §2.2.1 [ANDROID-UI]*
</details>

---

### Pregunta 19

**Una aplicación móvil del Ayuntamiento de Madrid está obligada a cumplir requisitos de accesibilidad en virtud de:**

A) El Real Decreto 1112/2018, que extiende la accesibilidad del sector público a las aplicaciones para dispositivos móviles
B) El Reglamento General de Protección de Datos, en su capítulo de accesibilidad universal
C) El Esquema Nacional de Interoperabilidad, en su norma técnica de digitalización

<details><summary>Respuesta</summary>

**Correcta: A) El Real Decreto 1112/2018, que extiende la accesibilidad del sector público a las aplicaciones para dispositivos móviles** Transpone la Directiva (UE) 2016/2102 y toma como referencia técnica la norma EN 301 549, que incorpora las WCAG en nivel AA.

*Referencia: §2.2.1 [RD1112-2018] [EN301549]*
</details>

---

### Pregunta 20

**¿Qué atributo permite que un lector de pantalla anuncie el propósito de un icono sin texto visible en Android?**

A) El atributo placeholder del elemento
B) El atributo contentDescription
C) El atributo accessibilityLabel

<details><summary>Respuesta</summary>

**Correcta: B) El atributo contentDescription** Es el equivalente de Android para TalkBack. El atributo accessibilityLabel es el propio de iOS para VoiceOver: ambos cumplen la misma función en su plataforma.

*Referencia: §2.2.1 [ANDROID-A11Y] [APPLE-DEV]*
</details>

---

### Pregunta 21

**¿Qué componentes reutilizan las celdas que salen de pantalla para recorrer listas largas con memoria constante?**

A) ConstraintLayout en Android y Auto Layout en iOS
B) Intent en Android y segue en iOS
C) RecyclerView en Android y UITableView o UICollectionView en iOS

<details><summary>Respuesta</summary>

**Correcta: C) RecyclerView en Android y UITableView o UICollectionView en iOS** El reciclado de vistas evita crear un objeto por elemento, que es lo que permite desplazarse por miles de registros sin agotar la memoria.

*Referencia: §2.2.2 [ANDROID-UI] [APPLE-DEV]*
</details>

---

### Pregunta 22

**Jetpack Compose y SwiftUI son:**

A) Los frameworks declarativos de interfaz de Android y de iOS respectivamente, ambos de desarrollo nativo
B) Dos frameworks multiplataforma que permiten compilar la misma interfaz para Android y para iOS
C) Dos motores de renderizado gráfico basados en Skia

<details><summary>Respuesta</summary>

**Correcta: A) Los frameworks declarativos de interfaz de Android y de iOS respectivamente, ambos de desarrollo nativo** Sustituyen a los diseños XML con View y a UIKit con storyboards, pero cada uno sigue siendo específico de su plataforma.

*Referencia: §2.2.2 [ANDROID-UI] [SWIFTUI-DOC]*
</details>

---

### Pregunta 23

**Al consumir una API REST desde una aplicación móvil, ¿qué situación debe tratarse como habitual y no como excepcional?**

A) Que el servidor devuelva un código de estado 200
B) Que el usuario revoque el permiso de cámara durante la petición
C) Que no haya red o se agote el tiempo de espera

<details><summary>Respuesta</summary>

**Correcta: C) Que no haya red o se agote el tiempo de espera** La conectividad móvil es intermitente por naturaleza: la ausencia de red es un caso normal de funcionamiento, no un error puntual, y la interfaz debe contemplarlo.

*Referencia: §2.3.1 [RFC9110]*
</details>

---

### Pregunta 24

**Según la RFC 8252 (*OAuth 2.0 for Native Apps*), la forma correcta de autenticar al usuario en una aplicación móvil es:**

A) Mostrar un formulario propio dentro de la app que envíe usuario y contraseña al servidor
B) Usar el navegador del sistema con el flujo de código de autorización y PKCE
C) Incrustar un WebView con la página de acceso del proveedor de identidad

<details><summary>Respuesta</summary>

**Correcta: B) Usar el navegador del sistema con el flujo de código de autorización y PKCE** Un WebView embebido permitiría a la aplicación leer las credenciales del usuario y rompe el aislamiento de sesión, por lo que está expresamente desaconsejado.

*Referencia: §2.3.1 [RFC8252] [RFC7636]*
</details>

---

### Pregunta 25

**En una notificación push, ¿quién entrega el mensaje al dispositivo?**

A) El servicio de la plataforma (FCM en Android o APNs en iOS), usando el token de registro
B) El servidor de la aplicación, abriendo una conexión directa con el dispositivo
C) La tienda de aplicaciones, tras verificar la firma del mensaje

<details><summary>Respuesta</summary>

**Correcta: A) El servicio de la plataforma (FCM en Android o APNs en iOS), usando el token de registro** El servidor de la aplicación envía el mensaje al servicio de la plataforma indicando el token; es ese servicio, con su conexión persistente, quien lo entrega al dispositivo.

*Referencia: §2.3.2 [FCM] [APNS]*
</details>

---

### Pregunta 26

**¿Qué caracteriza a una notificación local frente a una notificación push?**

A) Solo puede mostrarse cuando la aplicación está en primer plano
B) La programa la propia aplicación en el dispositivo, sin servidor ni conexión de red
C) Requiere un token de registro emitido por APNs o por FCM

<details><summary>Respuesta</summary>

**Correcta: B) La programa la propia aplicación en el dispositivo, sin servidor ni conexión de red** Es la adecuada para recordatorios y alarmas. Al usuario le llega igual que una push, pero su origen y sus requisitos técnicos son distintos.

*Referencia: §2.3.2 [FCM] [APNS]*
</details>

---

### Pregunta 27

**En el patrón *offline-first*, ¿cuál es la única fuente de verdad para la interfaz?**

A) La respuesta más reciente del servidor, almacenada en memoria
B) La caché HTTP del sistema operativo
C) El repositorio local del dispositivo, que la interfaz lee y escribe siempre

<details><summary>Respuesta</summary>

**Correcta: C) El repositorio local del dispositivo, que la interfaz lee y escribe siempre** La pantalla nunca espera a la red: pinta lo que hay en local y un planificador de trabajo diferido sincroniza con el servidor cuando se dan las condiciones.

*Referencia: §2.3.2 [JETPACK]*
</details>

---

### Pregunta 28

**Para evitar que un reintento tras un corte de red duplique un registro en el servidor, la solución correcta es:**

A) Enviar un identificador único de operación que el servidor trate como clave de idempotencia
B) Impedir que el usuario pulse el botón de envío más de una vez
C) Sustituir el método POST por GET en la petición de creación

<details><summary>Respuesta</summary>

**Correcta: A) Enviar un identificador único de operación que el servidor trate como clave de idempotencia** Si el identificador ya existe, el servidor devuelve el registro creado en lugar de crear otro. Solo entonces reintentar deja de ser peligroso, que es la condición del modo offline.

*Referencia: §2.3.2 [RFC9110]*
</details>

---

### Pregunta 29

**¿Qué planificadores permiten ejecutar trabajo diferido respetando las restricciones de batería del sistema?**

A) Broadcast Receiver en Android y segue en iOS
B) WorkManager en Android y BGTaskScheduler en iOS
C) Content Provider en Android y Core Data en iOS

<details><summary>Respuesta</summary>

**Correcta: B) WorkManager en Android y BGTaskScheduler en iOS** Ambos delegan en el sistema la decisión de cuándo ejecutar la tarea, atendiendo a la red disponible, la batería y las políticas de ahorro de energía.

*Referencia: §2.3.2 [JETPACK] [APPLE-DEV]*
</details>

---

### Pregunta 30

**Ordene de abajo arriba las capas de la plataforma Android:**

A) Núcleo Linux, Java API Framework, HAL, bibliotecas nativas y ART, aplicaciones
B) HAL, núcleo Linux, aplicaciones, bibliotecas nativas y ART, Java API Framework
C) Núcleo Linux, HAL, bibliotecas nativas y ART, Java API Framework, aplicaciones

<details><summary>Respuesta</summary>

**Correcta: C) Núcleo Linux, HAL, bibliotecas nativas y ART, Java API Framework, aplicaciones** El kernel Linux está en la base y las aplicaciones en la cima, con la capa de abstracción de hardware sobre el núcleo y el entorno de ejecución junto a las bibliotecas nativas.

*Referencia: §3.1.1 [ANDROID-ARCH]*
</details>

---

### Pregunta 31

**¿Qué relación existe entre Dalvik y ART?**

A) ART es el formato de bytecode y Dalvik el entorno que lo ejecuta
B) ART sustituyó a Dalvik desde Android 5.0, añadiendo compilación AOT en la instalación junto a JIT y perfiles
C) Ambos coexisten: Dalvik ejecuta las aplicaciones del sistema y ART las de terceros

<details><summary>Respuesta</summary>

**Correcta: B) ART sustituyó a Dalvik desde Android 5.0, añadiendo compilación AOT en la instalación junto a JIT y perfiles** Dalvik, vigente hasta Android 4.4, compilaba únicamente JIT en cada ejecución. El formato de bytecode sigue siendo DEX en ambos casos.

*Referencia: §3.1.1 [ANDROID-ARCH]*
</details>

---

### Pregunta 32

**¿Cuáles son los cuatro componentes fundamentales de una aplicación Android?**

A) Activity, Service, Broadcast Receiver y Content Provider
B) Activity, Intent, Fragment y Manifest
C) View, ViewModel, Repository y Database

<details><summary>Respuesta</summary>

**Correcta: A) Activity, Service, Broadcast Receiver y Content Provider** Todos se declaran en el AndroidManifest.xml y se activan mediante Intents. Una app Android no tiene un método principal único de entrada.

*Referencia: §3.1.2 [ANDROID-DEV]*
</details>

---

### Pregunta 33

**Un Intent implícito se caracteriza por:**

A) Nombrar la clase concreta del componente que debe atenderlo
B) Ejecutarse siempre de forma síncrona y bloqueante
C) Describir una acción y unos datos, siendo el sistema quien decide qué aplicación la atiende

<details><summary>Respuesta</summary>

**Correcta: C) Describir una acción y unos datos, siendo el sistema quien decide qué aplicación la atiende** Los intent filters declarados en el manifiesto anuncian qué intents implícitos sabe atender cada aplicación; si hay varias candidatas, el sistema muestra un selector.

*Referencia: §3.1.2 [ANDROID-DEV]*
</details>

---

### Pregunta 34

**¿Qué fichero declara en Android los componentes, los permisos y las versiones mínima y objetivo de la API?**

A) El AndroidManifest.xml
B) El fichero build.gradle del módulo de aplicación
C) El fichero Info.plist del proyecto

<details><summary>Respuesta</summary>

**Correcta: A) El AndroidManifest.xml** El fichero build.gradle define la construcción y las variantes, pero la declaración formal de la aplicación ante el sistema es el manifiesto. Info.plist es el equivalente de iOS.

*Referencia: §3.1.2 [ANDROID-DEV]*
</details>

---

### Pregunta 35

**Los permisos clasificados como *peligrosos* en Android:**

A) Se conceden automáticamente al instalar la aplicación desde Google Play
B) Deben solicitarse en tiempo de ejecución y el usuario puede concederlos solo mientras usa la app o solo una vez
C) Requieren que la aplicación esté firmada con el mismo certificado que la que los declara

<details><summary>Respuesta</summary>

**Correcta: B) Deben solicitarse en tiempo de ejecución y el usuario puede concederlos solo mientras usa la app o solo una vez** Los que se conceden automáticamente son los permisos normales; los que exigen firma coincidente son los permisos de firma.

*Referencia: §3.1.2 [ANDROID-DEV]*
</details>

---

### Pregunta 36

**Sobre Kotlin en el desarrollo Android, es cierto que:**

A) Sustituyó por completo a Java, que ya no está soportado por el SDK
B) Se ejecuta sobre una máquina virtual propia, distinta de la que ejecuta el código Java
C) Es el lenguaje preferente desde 2019, compila al mismo bytecode que Java y es plenamente interoperable con él

<details><summary>Respuesta</summary>

**Correcta: C) Es el lenguaje preferente desde 2019, compila al mismo bytecode que Java y es plenamente interoperable con él** Oficial desde 2017 y preferente desde 2019, permite migrar una aplicación existente clase a clase, sin reescribirla de golpe.

*Referencia: §3.1.3 [KOTLIN-DOC] [ANDROID-DEV]*
</details>

---

### Pregunta 37

**¿Qué aporta la seguridad frente a nulos (*null safety*) de Kotlin?**

A) El sistema de tipos distingue los tipos que admiten nulo de los que no, y el compilador impide desreferenciar un nulo
B) El recolector de basura elimina automáticamente las referencias nulas en tiempo de ejecución
C) Todas las variables se inicializan a un valor por defecto no nulo al declararse

<details><summary>Respuesta</summary>

**Correcta: A) El sistema de tipos distingue los tipos que admiten nulo de los que no, y el compilador impide desreferenciar un nulo** Es la respuesta directa a la excepción de puntero nulo, el error más común en Java. Swift resuelve lo mismo con sus opcionales.

*Referencia: §3.1.3 [KOTLIN-DOC]*
</details>

---

### Pregunta 38

**Ordene de arriba abajo las cuatro capas de iOS:**

A) Core OS, Core Services, Media, Cocoa Touch
B) Cocoa Touch, Core Services, Media, Core OS
C) Cocoa Touch, Media, Core Services, Core OS

<details><summary>Respuesta</summary>

**Correcta: C) Cocoa Touch, Media, Core Services, Core OS** Cocoa Touch es la capa superior, donde viven UIKit y SwiftUI; Core OS es la más cercana al hardware, con el núcleo Darwin y la seguridad del sistema.

*Referencia: §3.2.1 [APPLE-ARCH]*
</details>

---

### Pregunta 39

**El equivalente funcional de una Activity de Android en iOS es:**

A) El objeto UIApplication
B) El UIViewController
C) El fichero Info.plist

<details><summary>Respuesta</summary>

**Correcta: B) El UIViewController** Controla una pantalla, coordinando las vistas y los datos, con sus propios callbacks de ciclo de vida como viewDidLoad() y viewWillAppear().

*Referencia: §3.2.2 [APPLE-DEV]*
</details>

---

### Pregunta 40

**Si una aplicación iOS solicita acceso a la cámara sin declarar la cadena de descripción de uso en Info.plist:**

A) Falla en ejecución y, además, es motivo de rechazo en la revisión de la App Store
B) Funciona con normalidad, porque la descripción solo afecta a la ficha de la tienda
C) El sistema muestra una descripción genérica automática y concede el permiso

<details><summary>Respuesta</summary>

**Correcta: A) Falla en ejecución y, además, es motivo de rechazo en la revisión de la App Store** La cadena se muestra literalmente al usuario en el diálogo de consentimiento y debe justificar la finalidad del acceso.

*Referencia: §3.2.2 [APPLE-DEV] [APPSTORE-REVIEW]*
</details>

---

### Pregunta 41

**¿Qué mecanismo de gestión de memoria emplea Swift?**

A) Un recolector de basura generacional equivalente al de ART
B) Liberación manual de memoria mediante instrucciones explícitas del programador
C) ARC, conteo automático de referencias resuelto en tiempo de compilación

<details><summary>Respuesta</summary>

**Correcta: C) ARC, conteo automático de referencias resuelto en tiempo de compilación** Evita las pausas de un recolector de basura, pero obliga al programador a romper los ciclos de retención con referencias weak o unowned.

*Referencia: §3.2.3 [SWIFT-DOC]*
</details>

---

### Pregunta 42

**En una aplicación construida con Apache Cordova, ¿cómo accede el código JavaScript al GPS del dispositivo?**

A) Directamente, porque el WebView expone la API nativa de localización sin intermediarios
B) A través de un plugin con parte nativa, mediante un puente de comunicación asíncrono
C) Solicitando al servidor la posición del dispositivo y recibiéndola en la respuesta

<details><summary>Respuesta</summary>

**Correcta: B) A través de un plugin con parte nativa, mediante un puente de comunicación asíncrono** Sin plugin no hay acceso al hardware: es la principal dependencia y el principal riesgo de mantenimiento de este enfoque.

*Referencia: §4.1.1 [CORDOVA-DOC]*
</details>

---

### Pregunta 43

**Los ficheros HTML, CSS y JavaScript de una aplicación híbrida de contenedor web:**

A) Van empaquetados dentro del binario instalado, no se descargan de un servidor en cada uso
B) Se descargan del servidor en cada arranque, como en cualquier página web
C) Se compilan a código máquina durante la instalación en el dispositivo

<details><summary>Respuesta</summary>

**Correcta: A) Van empaquetados dentro del binario instalado, no se descargan de un servidor en cada uso** Es lo que permite que la aplicación arranque y funcione sin conexión, y lo que la distingue de abrir la misma web en el navegador.

*Referencia: §4.1.1 [CORDOVA-DOC]*
</details>

---

### Pregunta 44

**¿Qué aporta Ionic sobre el modelo de contenedor web?**

A) Un motor de renderizado gráfico propio que sustituye al WebView
B) Un catálogo de componentes de interfaz web que imitan el aspecto nativo de cada plataforma
C) La compilación del código JavaScript a Kotlin y a Swift

<details><summary>Respuesta</summary>

**Correcta: B) Un catálogo de componentes de interfaz web que imitan el aspecto nativo de cada plataforma** Se muestran al estilo Material en Android y al estilo iOS en Apple, e integra frameworks web como Angular, React o Vue. Para la capa nativa impulsa hoy Capacitor.

*Referencia: §4.1.1 [IONIC-DOC] [CAPACITOR-DOC]*
</details>

---

### Pregunta 45

**¿Con qué se corresponde un componente `<View>` de React Native en el dispositivo?**

A) Con un elemento HTML dentro de un WebView embebido
B) Con una superficie dibujada por el motor gráfico Skia
C) Con un componente nativo real del sistema: un ViewGroup en Android o un UIView en iOS

<details><summary>Respuesta</summary>

**Correcta: C) Con un componente nativo real del sistema: un ViewGroup en Android o un UIView en iOS** React Native no usa WebView: el código JavaScript maneja componentes nativos, y por eso la aplicación hereda el aspecto y el comportamiento del sistema anfitrión.

*Referencia: §4.2.1 [RN-DOC]*
</details>

---

### Pregunta 46

**En la nueva arquitectura de React Native, ¿qué sustituye al puente asíncrono con serialización JSON?**

A) JSI, una capa en C++ que permite a JavaScript invocar directamente objetos nativos
B) Un WebView optimizado con aceleración por hardware
C) La compilación anticipada del código JavaScript a bytecode DEX

<details><summary>Respuesta</summary>

**Correcta: A) JSI, una capa en C++ que permite a JavaScript invocar directamente objetos nativos** Sobre JSI se apoyan Fabric, el nuevo renderizador de interfaz, los TurboModules de carga perezosa y Codegen. Elimina el cuello de botella de la serialización.

*Referencia: §4.2.1 [RN-DOC]*
</details>

---

### Pregunta 47

**¿Cuál es la diferencia esencial entre React Native y Flutter?**

A) React Native es de código abierto y Flutter es una tecnología propietaria de pago
B) React Native renderiza con componentes nativos del sistema, mientras que Flutter dibuja cada píxel con su propio motor gráfico
C) React Native solo funciona en Android y Flutter solo en iOS

<details><summary>Respuesta</summary>

**Correcta: B) React Native renderiza con componentes nativos del sistema, mientras que Flutter dibuja cada píxel con su propio motor gráfico** De ahí que Flutter garantice una apariencia idéntica en todas las plataformas y React Native, una apariencia idéntica a la del sistema anfitrión.

*Referencia: §4.2 [RN-DOC] [FLUTTER-DOC]*
</details>

---

### Pregunta 48

**¿Cuáles son las tres capas de la arquitectura de Flutter?**

A) WebView, puente de plugins y aplicación contenedora
B) Presentación, lógica de negocio y acceso a datos
C) Framework en Dart, Engine en C/C++ y Embedder específico de cada plataforma

<details><summary>Respuesta</summary>

**Correcta: C) Framework en Dart, Engine en C/C++ y Embedder específico de cada plataforma** El Framework contiene los widgets que usa el programador; el Engine incorpora el motor de renderizado Skia o Impeller; el Embedder es la única parte específica de Android o iOS.

*Referencia: §4.2.2 [FLUTTER-DOC]*
</details>

---

### Pregunta 49

**¿Qué característica del lenguaje Dart hace posible la recarga en caliente (*hot reload*) durante el desarrollo?**

A) Que se interpreta línea a línea también en producción, sin fase de compilación
B) Que compila JIT durante el desarrollo y AOT a código máquina en producción
C) Que se ejecuta sobre la máquina virtual de Java, compartiendo su cargador de clases

<details><summary>Respuesta</summary>

**Correcta: B) Que compila JIT durante el desarrollo y AOT a código máquina en producción** La doble estrategia de compilación permite ver los cambios en menos de un segundo mientras se desarrolla, sin renunciar al rendimiento cercano al nativo en la versión publicada.

*Referencia: §4.2.2 [DART-DOC]*
</details>

---

### Pregunta 50

**Una desventaja característica de que Flutter dibuje su propia interfaz es:**

A) Que no hereda automáticamente los cambios de aspecto y comportamiento que introduce cada versión nueva del sistema
B) Que obliga a escribir una base de código distinta para Android y para iOS
C) Que impide utilizar componentes de diseño con estilo Material

<details><summary>Respuesta</summary>

**Correcta: A) Que no hereda automáticamente los cambios de aspecto y comportamiento que introduce cada versión nueva del sistema** A ello se suma un paquete de mayor tamaño, porque incorpora el motor de renderizado, y una accesibilidad que depende del puente propio de Flutter.

*Referencia: §4.2.2 [FLUTTER-DOC]*
</details>

---

### Pregunta 51

**Kotlin Multiplatform se caracteriza por:**

A) Ejecutar HTML y JavaScript dentro de un WebView en ambas plataformas
B) Compilar el mismo código de interfaz para Android, iOS y web con un motor gráfico propio
C) Compartir la lógica de negocio en Kotlin manteniendo una interfaz nativa en cada plataforma

<details><summary>Respuesta</summary>

**Correcta: C) Compartir la lógica de negocio en Kotlin manteniendo una interfaz nativa en cada plataforma** Es un compromiso intermedio entre el desarrollo nativo puro y la multiplataforma total, que preserva la experiencia de usuario propia de cada sistema.

*Referencia: §4.2.2 [KMP-DOC]*
</details>

---

### Pregunta 52

**.NET MAUI, sucesor de Xamarin.Forms, utiliza como lenguaje:**

A) Dart
B) C#
C) TypeScript

<details><summary>Respuesta</summary>

**Correcta: B) C#** Renderiza con controles nativos de cada plataforma y resulta especialmente atractivo cuando la organización ya trabaja sobre el ecosistema .NET.

*Referencia: §4.2.2 [MAUI-DOC]*
</details>

---

### Pregunta 53

**Ordene de mayor a menor rendimiento los enfoques de desarrollo móvil:**

A) Nativo, Flutter, React Native, híbrido de contenedor web
B) Híbrido de contenedor web, React Native, Flutter, nativo
C) React Native, nativo, híbrido de contenedor web, Flutter

<details><summary>Respuesta</summary>

**Correcta: A) Nativo, Flutter, React Native, híbrido de contenedor web** Cuantas más capas intermedias e interpretación existan, más ciclos de CPU y más memoria se consumen para el mismo resultado, y mayor es también el gasto de batería.

*Referencia: §5.1 [ISO25010]*
</details>

---

### Pregunta 54

**Respecto a una clave de API incrustada en el código de una aplicación móvil publicada:**

A) Es segura si el código se ofusca antes de compilar
B) Es segura si se guarda en un fichero de recursos y no en una constante del código
C) Debe considerarse comprometida, porque el paquete instalado es analizable por ingeniería inversa

<details><summary>Respuesta</summary>

**Correcta: C) Debe considerarse comprometida, porque el paquete instalado es analizable por ingeniería inversa** Las comprobaciones de seguridad decisivas se hacen siempre en el servidor: el cliente es manipulable por definición.

*Referencia: §5.1 [OWASP-MASVS] [OWASP-MOBILE]*
</details>

---

### Pregunta 55

**El catálogo de referencia de los riesgos de seguridad más críticos específicos de aplicaciones móviles es:**

A) El OWASP Mobile Top 10, complementado por el estándar de verificación MASVS
B) La norma EN 301 549, en su capítulo 11
C) El Esquema Nacional de Interoperabilidad, en su norma técnica de seguridad

<details><summary>Respuesta</summary>

**Correcta: A) El OWASP Mobile Top 10, complementado por el estándar de verificación MASVS** Recoge riesgos como el almacenamiento inseguro de datos, la comunicación insegura y la autenticación deficiente. La EN 301 549 es la norma de accesibilidad.

*Referencia: §5.1 [OWASP-MOBILE] [OWASP-MASVS]*
</details>

---

### Pregunta 56

**Sobre la afirmación «una sola base de código supone la mitad de trabajo»:**

A) Es exacta: el ahorro es del 50 % en desarrollo y en mantenimiento
B) Es inexacta: sigue habiendo que probar en ambas plataformas, adaptar comportamientos específicos, gestionar dos publicaciones y, a veces, escribir código nativo
C) Es inexacta porque los enfoques multiplataforma no permiten reutilizar código entre Android e iOS

<details><summary>Respuesta</summary>

**Correcta: B) Es inexacta: sigue habiendo que probar en ambas plataformas, adaptar comportamientos específicos, gestionar dos publicaciones y, a veces, escribir código nativo** El ahorro real es significativo pero no llega al 50 %, y el coste dominante a medio plazo es el mantenimiento, no el desarrollo inicial.

*Referencia: §5.2 [ISO25010]*
</details>

---

### Pregunta 57

**Respecto a las pruebas en el desarrollo móvil:**

A) El emulador reproduce fielmente el rendimiento, los sensores y el consumo de batería del dispositivo real
B) Basta con probar en un único dispositivo Android, porque el sistema garantiza el comportamiento uniforme
C) El emulador no sustituye al dispositivo real y la fragmentación de Android obliga a probar sobre una matriz de tamaños, densidades y versiones

<details><summary>Respuesta</summary>

**Correcta: C) El emulador no sustituye al dispositivo real y la fragmentación de Android obliga a probar sobre una matriz de tamaños, densidades y versiones** Cuando no se dispone del parque físico se recurre a granjas de dispositivos en la nube.

*Referencia: §5.2 [ANDROID-DEV]*
</details>

---

### Pregunta 58

**¿Qué formato de publicación es obligatorio en Google Play para las aplicaciones nuevas desde agosto de 2021?**

A) El AAB (*Android App Bundle*), a partir del cual Google Play genera los APK optimizados por dispositivo
B) El APK firmado con la clave de subida del desarrollador
C) El IPA generado desde el entorno de desarrollo

<details><summary>Respuesta</summary>

**Correcta: A) El AAB (*Android App Bundle*), a partir del cual Google Play genera los APK optimizados por dispositivo** El AAB reduce el tamaño de descarga al servir a cada dispositivo solo los recursos que necesita: su densidad, su arquitectura y su idioma. El IPA es el formato de la App Store.

*Referencia: §5.3 [PLAY-CONSOLE]*
</details>

---

### Pregunta 59

**Una diferencia relevante entre publicar en Google Play y en la App Store es que:**

A) Google Play exige una cuota anual y la App Store un pago único de alta
B) La App Store somete toda aplicación a revisión humana, mientras que en Google Play la revisión es mayoritariamente automatizada
C) Solo la App Store permite la publicación por fases a un porcentaje creciente de usuarios

<details><summary>Respuesta</summary>

**Correcta: B) La App Store somete toda aplicación a revisión humana, mientras que en Google Play la revisión es mayoritariamente automatizada** Además, la cuota es al revés de lo que sugiere la primera opción: pago único en Google Play y cuota anual en el Apple Developer Program. Ambas admiten publicación por fases.

*Referencia: §5.3 [PLAY-CONSOLE] [APPSTORE-REVIEW]*
</details>

---

### Pregunta 60

**A diferencia de una aplicación web, en una aplicación móvil publicada en una tienda:**

A) La actualización es instantánea para todos los usuarios en cuanto se publica
B) No es necesario versionar la API del servidor, porque todos los clientes están siempre al día
C) El usuario puede tardar semanas en actualizar o no actualizar nunca, por lo que hay que versionar la API y mantener compatibilidad hacia atrás

<details><summary>Respuesta</summary>

**Correcta: C) El usuario puede tardar semanas en actualizar o no actualizar nunca, por lo que hay que versionar la API y mantener compatibilidad hacia atrás** Por eso se recomienda además la publicación por fases y las banderas de característica, que permiten desactivar una funcionalidad sin depender de una actualización de la tienda.

*Referencia: §5.3 [PLAY-CONSOLE] [APPSTORE-REVIEW]*
</details>
