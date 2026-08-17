# Tema 24 — Catálogo de Diagramas

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
>
> **Versión**: v1.0
> **Fecha**: 2026-08-17
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 14 diagramas embebidos en la misma página.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Familias de dispositivos y restricciones de recursos | §1.1 | Esquema | 680×320 |
| D2 | Las cuatro estrategias de desarrollo móvil | §1.2 | Comparativa | 680×360 |
| D3 | Ciclo de vida: Activity de Android frente a app de iOS | §2.1.1 | Flujo comparado | 680×380 |
| D4 | Mecanismos de persistencia local | §2.1.2 | Tabla visual | 680×340 |
| D5 | Densidades de pantalla: dp, sp y factores @1x/@2x/@3x | §2.2.1 | Esquema anotado | 680×300 |
| D6 | Hilo principal y trabajo en segundo plano | §2.3.1 | Flujo temporal | 680×300 |
| D7 | Arquitectura de las notificaciones push (FCM/APNs) | §2.3.2 | Flujo | 680×320 |
| D8 | Patrón *offline-first* y cola de sincronización | §2.3.2 | Flujo | 680×300 |
| D9 | La pila de la plataforma Android | §3.1.1 | Capas | 680×340 |
| D10 | Los cuatro componentes de Android y el Intent | §3.1.2 | Bloques | 680×320 |
| D11 | Las cuatro capas de iOS | §3.2.1 | Capas | 680×320 |
| D12 | Híbrido de contenedor web: WebView y puente de plugins | §4.1.1 | Bloques | 680×320 |
| D13 | React Native frente a Flutter: dos formas de renderizar | §4.2 | Flujo comparado | 680×360 |
| D14 | Árbol de decisión del enfoque y publicación en tiendas | §5 | Árbol + comparativa | 680×400 |

---

## D1 · Familias de dispositivos y restricciones de recursos

**Sección**: §1.1 — Caracterización y evolución del ecosistema móvil
**Propósito**: Situar las familias de dispositivos que el desarrollador debe soportar y las tres restricciones de recursos que gobiernan todas sus decisiones de diseño.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Familias de dispositivos móviles (teléfono, tableta, plegable, reloj y terminal de campo) y las tres restricciones de recursos: batería, memoria y procesamiento, con su consecuencia práctica en el diseño de la aplicación">
  <style>.t1{font:700 11px system-ui,sans-serif;fill:#fff}.s1{font:9.5px system-ui,sans-serif;fill:#fff}.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 11px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h1">Dispositivos y restricciones de recursos</text>
  <rect x="20" y="36" width="120" height="52" rx="5" fill="#0055a0"/><text x="80" y="58" text-anchor="middle" class="t1">Teléfono</text><text x="80" y="76" text-anchor="middle" class="s1">objetivo principal</text>
  <rect x="150" y="36" width="120" height="52" rx="5" fill="#0055a0"/><text x="210" y="58" text-anchor="middle" class="t1">Tableta</text><text x="210" y="76" text-anchor="middle" class="s1">maestro-detalle</text>
  <rect x="280" y="36" width="120" height="52" rx="5" fill="#0055a0"/><text x="340" y="58" text-anchor="middle" class="t1">Plegable</text><text x="340" y="76" text-anchor="middle" class="s1">cambia en caliente</text>
  <rect x="410" y="36" width="120" height="52" rx="5" fill="#888"/><text x="470" y="58" text-anchor="middle" class="t1">Reloj</text><text x="470" y="76" text-anchor="middle" class="s1">app complementaria</text>
  <rect x="540" y="36" width="120" height="52" rx="5" fill="#888"/><text x="600" y="58" text-anchor="middle" class="t1">Terminal campo</text><text x="600" y="76" text-anchor="middle" class="s1">uso profesional</text>
  <line x1="20" y1="102" x2="660" y2="102" stroke="#ccc" stroke-width="1"/>
  <text x="340" y="122" text-anchor="middle" class="k1">Restricciones de recursos y su consecuencia de diseño</text>
  <rect x="20" y="134" width="205" height="118" rx="5" fill="#d13c3c"/>
  <text x="122" y="156" text-anchor="middle" class="t1">BATERÍA</text>
  <text x="122" y="178" text-anchor="middle" class="s1">Pantalla, radio y GPS: lo que</text>
  <text x="122" y="194" text-anchor="middle" class="s1">más consume</text>
  <text x="122" y="216" text-anchor="middle" class="s1">→ agrupar envíos (batching)</text>
  <text x="122" y="234" text-anchor="middle" class="s1">→ diferir lo no urgente</text>
  <rect x="237" y="134" width="206" height="118" rx="5" fill="#e89822"/>
  <text x="340" y="156" text-anchor="middle" class="t1">MEMORIA</text>
  <text x="340" y="178" text-anchor="middle" class="s1">El sistema puede terminar el</text>
  <text x="340" y="194" text-anchor="middle" class="s1">proceso en segundo plano</text>
  <text x="340" y="216" text-anchor="middle" class="s1">→ guardar estado al perder</text>
  <text x="340" y="234" text-anchor="middle" class="s1">el primer plano</text>
  <rect x="455" y="134" width="205" height="118" rx="5" fill="#2d8659"/>
  <text x="557" y="156" text-anchor="middle" class="t1">PROCESAMIENTO</text>
  <text x="557" y="178" text-anchor="middle" class="s1">SoC que equilibra potencia</text>
  <text x="557" y="194" text-anchor="middle" class="s1">y consumo</text>
  <text x="557" y="216" text-anchor="middle" class="s1">→ trabajo pesado fuera del</text>
  <text x="557" y="234" text-anchor="middle" class="s1">hilo principal (si no: ANR)</text>
  <rect x="90" y="264" width="500" height="34" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="340" y="286" text-anchor="middle" class="k1">El árbitro de los tres recursos es el sistema operativo, no la aplicación</text>
  <text x="670" y="312" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-DEV; APPLE-DEV]</text>
</svg>
```

---

## D2 · Las cuatro estrategias de desarrollo móvil

**Sección**: §1.2 — Estrategias y paradigmas de desarrollo
**Propósito**: Comparar de un vistazo las cuatro estrategias, destacando que lo decisivo es **cómo se dibuja la interfaz**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Comparativa de las cuatro estrategias de desarrollo móvil: nativa, híbrida de contenedor web, multiplataforma compilada y aplicación web progresiva, indicando para cada una el lenguaje, cómo se dibuja la interfaz, la distribución y el rendimiento">
  <style>.t2{font:700 10.5px system-ui,sans-serif;fill:#fff}.s2{font:9px system-ui,sans-serif;fill:#fff}.d2{font:9px system-ui,sans-serif;fill:#333}.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h2">Las cuatro estrategias de desarrollo móvil</text>
  <rect x="20" y="34" width="152" height="36" rx="5" fill="#0055a0"/><text x="96" y="49" text-anchor="middle" class="t2">NATIVA</text><text x="96" y="63" text-anchor="middle" class="s2">SDK de cada plataforma</text>
  <rect x="187" y="34" width="152" height="36" rx="5" fill="#e89822"/><text x="263" y="49" text-anchor="middle" class="t2">HÍBRIDA (web)</text><text x="263" y="63" text-anchor="middle" class="s2">Cordova · Ionic</text>
  <rect x="354" y="34" width="152" height="36" rx="5" fill="#2d8659"/><text x="430" y="49" text-anchor="middle" class="t2">MULTIPLATAFORMA</text><text x="430" y="63" text-anchor="middle" class="s2">React Native · Flutter</text>
  <rect x="521" y="34" width="152" height="36" rx="5" fill="#888"/><text x="597" y="49" text-anchor="middle" class="t2">PWA</text><text x="597" y="63" text-anchor="middle" class="s2">web instalable</text>
  <text x="20" y="88" class="k2">LENGUAJE</text>
  <rect x="20" y="94" width="152" height="38" rx="4" fill="#eef3f8"/><text x="96" y="110" text-anchor="middle" class="d2">Kotlin / Java (Android)</text><text x="96" y="124" text-anchor="middle" class="d2">Swift / Objective-C (iOS)</text>
  <rect x="187" y="94" width="152" height="38" rx="4" fill="#eef3f8"/><text x="263" y="117" text-anchor="middle" class="d2">HTML + CSS + JS</text>
  <rect x="354" y="94" width="152" height="38" rx="4" fill="#eef3f8"/><text x="430" y="110" text-anchor="middle" class="d2">JS/TS (React Native)</text><text x="430" y="124" text-anchor="middle" class="d2">Dart (Flutter)</text>
  <rect x="521" y="94" width="152" height="38" rx="4" fill="#eef3f8"/><text x="597" y="117" text-anchor="middle" class="d2">HTML + CSS + JS</text>
  <text x="20" y="150" class="k2">CÓMO SE DIBUJA LA INTERFAZ</text>
  <rect x="20" y="156" width="152" height="52" rx="4" fill="#0055a0"/><text x="96" y="176" text-anchor="middle" class="s2">Componentes nativos</text><text x="96" y="192" text-anchor="middle" class="s2">del sistema</text>
  <rect x="187" y="156" width="152" height="52" rx="4" fill="#e89822"/><text x="263" y="176" text-anchor="middle" class="s2">WebView embebido</text><text x="263" y="192" text-anchor="middle" class="s2">(motor web)</text>
  <rect x="354" y="156" width="152" height="52" rx="4" fill="#2d8659"/><text x="430" y="172" text-anchor="middle" class="s2">Nativos (React Native)</text><text x="430" y="188" text-anchor="middle" class="s2">o motor gráfico propio</text><text x="430" y="202" text-anchor="middle" class="s2">(Flutter)</text>
  <rect x="521" y="156" width="152" height="52" rx="4" fill="#888"/><text x="597" y="176" text-anchor="middle" class="s2">Navegador del</text><text x="597" y="192" text-anchor="middle" class="s2">sistema</text>
  <text x="20" y="220" class="k2">DISTRIBUCIÓN</text>
  <rect x="20" y="226" width="152" height="28" rx="4" fill="#eef3f8"/><text x="96" y="244" text-anchor="middle" class="d2">Tiendas</text>
  <rect x="187" y="226" width="152" height="28" rx="4" fill="#eef3f8"/><text x="263" y="244" text-anchor="middle" class="d2">Tiendas (empaquetada)</text>
  <rect x="354" y="226" width="152" height="28" rx="4" fill="#eef3f8"/><text x="430" y="244" text-anchor="middle" class="d2">Tiendas</text>
  <rect x="521" y="226" width="152" height="28" rx="4" fill="#eef3f8"/><text x="597" y="244" text-anchor="middle" class="d2">Web (sin tienda)</text>
  <text x="20" y="272" class="k2">RENDIMIENTO</text>
  <rect x="20" y="278" width="152" height="24" rx="4" fill="#2d8659"/><text x="96" y="294" text-anchor="middle" class="s2">Máximo</text>
  <rect x="187" y="278" width="152" height="24" rx="4" fill="#d13c3c"/><text x="263" y="294" text-anchor="middle" class="s2">Menor</text>
  <rect x="354" y="278" width="152" height="24" rx="4" fill="#2d8659"/><text x="430" y="294" text-anchor="middle" class="s2">Alto / muy alto</text>
  <rect x="521" y="278" width="152" height="24" rx="4" fill="#d13c3c"/><text x="597" y="294" text-anchor="middle" class="s2">Menor</text>
  <rect x="60" y="312" width="560" height="30" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="340" y="332" text-anchor="middle" style="font:700 10.5px system-ui;fill:#0055a0">Lo decisivo no es «usa o no web», sino CÓMO se dibuja la interfaz</text>
  <text x="670" y="354" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: CORDOVA-DOC; RN-DOC; FLUTTER-DOC; MDN-PWA]</text>
</svg>
```

---

## D3 · Ciclo de vida: Activity de Android frente a app de iOS

**Sección**: §2.1.1 — Estados de ejecución y gestión de eventos
**Propósito**: Contraponer la secuencia de *callbacks* de una `Activity` de Android con los estados de ejecución de una aplicación de iOS.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 380" role="img" aria-label="Comparación del ciclo de vida: en Android la Activity recorre onCreate, onStart, onResume, primer plano, onPause, onStop y onDestroy; en iOS la aplicación pasa por los estados Not running, Inactive, Active, Background y Suspended, con los callbacks del UIViewController">
  <style>.t3{font:700 11px system-ui,sans-serif;fill:#fff}.s3{font:9.5px system-ui,sans-serif;fill:#fff}.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.c3{font:700 11px system-ui,sans-serif;fill:#0055a0}.m3{font:10px ui-monospace,monospace;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h3">Ciclo de vida comparado: Android e iOS</text>
  <text x="170" y="42" text-anchor="middle" class="c3">ANDROID — Activity</text>
  <text x="510" y="42" text-anchor="middle" class="c3">iOS — estados de la app</text>
  <rect x="30" y="52" width="280" height="28" rx="4" fill="#0055a0"/><text x="170" y="71" text-anchor="middle" class="m3">onCreate()</text>
  <rect x="30" y="88" width="280" height="28" rx="4" fill="#0055a0"/><text x="170" y="107" text-anchor="middle" class="m3">onStart()</text>
  <rect x="30" y="124" width="280" height="28" rx="4" fill="#0055a0"/><text x="170" y="143" text-anchor="middle" class="m3">onResume()</text>
  <rect x="30" y="160" width="280" height="28" rx="4" fill="#2d8659"/><text x="170" y="179" text-anchor="middle" class="t3">EN PRIMER PLANO</text>
  <rect x="30" y="196" width="280" height="28" rx="4" fill="#e89822"/><text x="170" y="215" text-anchor="middle" class="m3">onPause()</text>
  <rect x="30" y="232" width="280" height="28" rx="4" fill="#e89822"/><text x="170" y="251" text-anchor="middle" class="m3">onStop()</text>
  <rect x="30" y="268" width="280" height="28" rx="4" fill="#d13c3c"/><text x="170" y="287" text-anchor="middle" class="m3">onDestroy()</text>
  <rect x="370" y="52" width="280" height="28" rx="4" fill="#888"/><text x="510" y="71" text-anchor="middle" class="t3">Not running</text>
  <rect x="370" y="88" width="280" height="28" rx="4" fill="#0055a0"/><text x="510" y="107" text-anchor="middle" class="t3">Inactive (sin eventos)</text>
  <rect x="370" y="124" width="280" height="28" rx="4" fill="#2d8659"/><text x="510" y="143" text-anchor="middle" class="t3">Active — primer plano</text>
  <rect x="370" y="160" width="280" height="28" rx="4" fill="#e89822"/><text x="510" y="179" text-anchor="middle" class="t3">Background (tiempo limitado)</text>
  <rect x="370" y="196" width="280" height="30" rx="4" fill="#d13c3c"/><text x="510" y="208" text-anchor="middle" class="t3">Suspended</text><text x="510" y="221" text-anchor="middle" class="s3">en memoria, sin ejecutar código</text>
  <rect x="370" y="232" width="280" height="64" rx="4" fill="#0055a0"/>
  <text x="510" y="250" text-anchor="middle" class="s3">UIViewController:</text>
  <text x="510" y="266" text-anchor="middle" class="m3">viewDidLoad() · viewWillAppear()</text>
  <text x="510" y="284" text-anchor="middle" class="m3">viewDidDisappear()</text>
  <rect x="30" y="308" width="620" height="46" rx="5" fill="#d13c3c"/>
  <text x="340" y="327" text-anchor="middle" class="t3">Girar la pantalla en Android DESTRUYE y RECREA la Activity</text>
  <text x="340" y="345" text-anchor="middle" class="s3">Si el estado no se guarda en onSaveInstanceState() o en un ViewModel, se pierde lo escrito</text>
  <text x="670" y="372" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-LIFECYCLE; APPLE-DEV]</text>
</svg>
```

---

## D4 · Mecanismos de persistencia local

**Sección**: §2.1.2 — Persistencia de datos local
**Propósito**: Ordenar las opciones de almacenamiento local de menor a mayor capacidad, con su equivalencia entre plataformas y la advertencia sobre datos sensibles.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Tabla de mecanismos de persistencia local: pares clave-valor, ficheros, base de datos SQLite y almacén seguro, con su equivalente en Android y en iOS y su uso adecuado, más la advertencia de guardar credenciales solo en Keystore o Keychain">
  <style>.t4{font:700 10px system-ui,sans-serif;fill:#fff}.s4{font:9.5px system-ui,sans-serif;fill:#fff}.d4{font:9.5px system-ui,sans-serif;fill:#333}.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 10px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h4">Persistencia local: del ajuste simple a la base de datos</text>
  <rect x="20" y="34" width="150" height="26" rx="4" fill="#0055a0"/><text x="95" y="51" text-anchor="middle" class="k4">MECANISMO</text>
  <rect x="175" y="34" width="145" height="26" rx="4" fill="#0055a0"/><text x="247" y="51" text-anchor="middle" class="k4">ANDROID</text>
  <rect x="325" y="34" width="145" height="26" rx="4" fill="#0055a0"/><text x="397" y="51" text-anchor="middle" class="k4">iOS</text>
  <rect x="475" y="34" width="185" height="26" rx="4" fill="#0055a0"/><text x="567" y="51" text-anchor="middle" class="k4">USO ADECUADO</text>
  <rect x="20" y="66" width="150" height="44" rx="4" fill="#888"/><text x="95" y="93" text-anchor="middle" class="t4">Clave-valor</text>
  <rect x="175" y="66" width="145" height="44" rx="4" fill="#eef3f8"/><text x="247" y="85" text-anchor="middle" class="d4">SharedPreferences</text><text x="247" y="99" text-anchor="middle" class="d4">DataStore</text>
  <rect x="325" y="66" width="145" height="44" rx="4" fill="#eef3f8"/><text x="397" y="93" text-anchor="middle" class="d4">UserDefaults</text>
  <rect x="475" y="66" width="185" height="44" rx="4" fill="#eef3f8"/><text x="567" y="93" text-anchor="middle" class="d4">Preferencias y ajustes</text>
  <rect x="20" y="116" width="150" height="44" rx="4" fill="#888"/><text x="95" y="143" text-anchor="middle" class="t4">Ficheros</text>
  <rect x="175" y="116" width="145" height="44" rx="4" fill="#eef3f8"/><text x="247" y="136" text-anchor="middle" class="d4">Almacenamiento</text><text x="247" y="150" text-anchor="middle" class="d4">interno / externo</text>
  <rect x="325" y="116" width="145" height="44" rx="4" fill="#eef3f8"/><text x="397" y="136" text-anchor="middle" class="d4">Sandbox de la app</text><text x="397" y="150" text-anchor="middle" class="d4">(Documents, Caches)</text>
  <rect x="475" y="116" width="185" height="44" rx="4" fill="#eef3f8"/><text x="567" y="143" text-anchor="middle" class="d4">Fotos, adjuntos, cachés</text>
  <rect x="20" y="166" width="150" height="44" rx="4" fill="#0055a0"/><text x="95" y="187" text-anchor="middle" class="t4">Base de datos</text><text x="95" y="201" text-anchor="middle" class="s4">SQLite embebido</text>
  <rect x="175" y="166" width="145" height="44" rx="4" fill="#eef3f8"/><text x="247" y="193" text-anchor="middle" class="d4">Room (sobre SQLite)</text>
  <rect x="325" y="166" width="145" height="44" rx="4" fill="#eef3f8"/><text x="397" y="186" text-anchor="middle" class="d4">Core Data</text><text x="397" y="200" text-anchor="middle" class="d4">SwiftData</text>
  <rect x="475" y="166" width="185" height="44" rx="4" fill="#eef3f8"/><text x="567" y="186" text-anchor="middle" class="d4">Datos estructurados</text><text x="567" y="200" text-anchor="middle" class="d4">y trabajo sin conexión</text>
  <rect x="20" y="216" width="150" height="44" rx="4" fill="#2d8659"/><text x="95" y="243" text-anchor="middle" class="t4">Almacén seguro</text>
  <rect x="175" y="216" width="145" height="44" rx="4" fill="#eef3f8"/><text x="247" y="236" text-anchor="middle" class="d4">Keystore + cifrado</text><text x="247" y="250" text-anchor="middle" class="d4">de preferencias</text>
  <rect x="325" y="216" width="145" height="44" rx="4" fill="#eef3f8"/><text x="397" y="243" text-anchor="middle" class="d4">Keychain</text>
  <rect x="475" y="216" width="185" height="44" rx="4" fill="#eef3f8"/><text x="567" y="236" text-anchor="middle" class="d4">Credenciales, tokens</text><text x="567" y="250" text-anchor="middle" class="d4">y claves</text>
  <rect x="20" y="270" width="640" height="42" rx="5" fill="#d13c3c"/>
  <text x="340" y="288" text-anchor="middle" class="t4">NUNCA credenciales ni datos sensibles en preferencias o ficheros en claro</text>
  <text x="340" y="304" text-anchor="middle" class="s4">Van al Keystore (Android) o al Keychain (iOS) — OWASP Mobile: almacenamiento inseguro</text>
  <text x="670" y="332" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: SQLITE; JETPACK; COREDATA; OWASP-MOBILE]</text>
</svg>
```

---

## D5 · Densidades de pantalla: dp, sp y factores @1x/@2x/@3x

**Sección**: §2.2.1 — Principios de diseño adaptativo y accesibilidad
**Propósito**: Explicar por qué un botón de 48 dp mide lo mismo físicamente en pantallas de densidad distinta, y la diferencia entre dp y sp.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Esquema de densidades de pantalla: un botón de 48 dp ocupa 48 píxeles a 160 ppp, 96 píxeles a 320 ppp y 192 píxeles a 640 ppp, manteniendo el mismo tamaño físico; equivalencia con los factores de escala de iOS 1x, 2x y 3x, y diferencia entre dp y sp">
  <style>.t5{font:700 10.5px system-ui,sans-serif;fill:#fff}.s5{font:9.5px system-ui,sans-serif;fill:#fff}.d5{font:10px system-ui,sans-serif;fill:#333}.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h5">Un mismo tamaño físico en densidades distintas</text>
  <text x="340" y="40" text-anchor="middle" class="d5">Un botón declarado de 48 dp ocupa siempre lo mismo en el dedo del usuario</text>
  <rect x="30" y="56" width="190" height="96" rx="6" fill="#0055a0"/>
  <text x="125" y="78" text-anchor="middle" class="t5">mdpi — 160 ppp</text>
  <text x="125" y="98" text-anchor="middle" class="s5">1 dp = 1 píxel</text>
  <text x="125" y="120" text-anchor="middle" class="s5">48 dp = 48 px</text>
  <text x="125" y="140" text-anchor="middle" class="s5">iOS: @1x</text>
  <rect x="245" y="56" width="190" height="96" rx="6" fill="#2d8659"/>
  <text x="340" y="78" text-anchor="middle" class="t5">xhdpi — 320 ppp</text>
  <text x="340" y="98" text-anchor="middle" class="s5">1 dp = 2 píxeles</text>
  <text x="340" y="120" text-anchor="middle" class="s5">48 dp = 96 px</text>
  <text x="340" y="140" text-anchor="middle" class="s5">iOS: @2x</text>
  <rect x="460" y="56" width="190" height="96" rx="6" fill="#e89822"/>
  <text x="555" y="78" text-anchor="middle" class="t5">xxxhdpi — 640 ppp</text>
  <text x="555" y="98" text-anchor="middle" class="s5">1 dp = 4 píxeles</text>
  <text x="555" y="120" text-anchor="middle" class="s5">48 dp = 192 px</text>
  <text x="555" y="140" text-anchor="middle" class="s5">iOS: @3x</text>
  <rect x="30" y="168" width="300" height="76" rx="6" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="180" y="190" text-anchor="middle" style="font:700 11px system-ui;fill:#0055a0">dp — longitudes</text>
  <text x="180" y="212" text-anchor="middle" class="d5">Independiente de la densidad.</text>
  <text x="180" y="230" text-anchor="middle" class="d5">Márgenes, botones, iconos.</text>
  <rect x="350" y="168" width="300" height="76" rx="6" fill="none" stroke="#d13c3c" stroke-width="2"/>
  <text x="500" y="190" text-anchor="middle" style="font:700 11px system-ui;fill:#d13c3c">sp — TEXTO</text>
  <text x="500" y="212" text-anchor="middle" class="d5">Como dp, pero escalado además por</text>
  <text x="500" y="230" text-anchor="middle" class="d5">el tamaño de fuente del usuario.</text>
  <rect x="130" y="254" width="420" height="28" rx="5" fill="#0055a0"/>
  <text x="340" y="273" text-anchor="middle" class="t5">Los textos se miden SIEMPRE en sp, por accesibilidad</text>
  <text x="670" y="294" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-UI; APPLE-DEV; WCAG22]</text>
</svg>
```

---

## D6 · Hilo principal y trabajo en segundo plano

**Sección**: §2.3.1 — Consumo de servicios web y APIs RESTful
**Propósito**: Mostrar por qué la petición de red debe salir del hilo principal y qué ocurre si no lo hace.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Esquema temporal: el hilo principal lanza la petición de red a un hilo secundario y sigue respondiendo al usuario; cuando llega el resultado, vuelve al hilo principal para actualizar la interfaz. Bloquear el hilo principal provoca un ANR en Android o la congelación de la interfaz en iOS">
  <style>.t6{font:700 10.5px system-ui,sans-serif;fill:#fff}.s6{font:9.5px system-ui,sans-serif;fill:#fff}.d6{font:10px system-ui,sans-serif;fill:#333}.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h6">La red nunca en el hilo principal</text>
  <text x="24" y="62" class="d6">Hilo principal (UI)</text>
  <rect x="140" y="46" width="510" height="34" rx="5" fill="#0055a0"/>
  <text x="395" y="68" text-anchor="middle" class="t6">Dibuja la interfaz y responde al usuario — nunca se bloquea</text>
  <text x="24" y="152" class="d6">Hilo secundario</text>
  <rect x="140" y="136" width="510" height="34" rx="5" fill="#2d8659"/>
  <text x="395" y="158" text-anchor="middle" class="t6">Petición HTTPS · lectura de base de datos · procesado de imagen</text>
  <path d="M230 84 L230 132" stroke="#e89822" stroke-width="3" marker-end="url(#a6)"/>
  <text x="240" y="112" style="font:700 10px system-ui;fill:#e89822">lanza (async)</text>
  <path d="M560 132 L560 84" stroke="#e89822" stroke-width="3" marker-end="url(#a6)"/>
  <text x="418" y="112" style="font:700 10px system-ui;fill:#e89822">devuelve el resultado a la UI</text>
  <defs><marker id="a6" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#e89822"/></marker></defs>
  <rect x="60" y="192" width="560" height="60" rx="6" fill="#d13c3c"/>
  <text x="340" y="214" text-anchor="middle" class="t6">Si el hilo principal se bloquea</text>
  <text x="340" y="232" text-anchor="middle" class="s6">Android: diálogo ANR (Application Not Responding)</text>
  <text x="340" y="246" text-anchor="middle" class="s6">iOS: interfaz congelada y posible cierre por el watchdog del sistema</text>
  <text x="340" y="276" text-anchor="middle" class="d6">Kotlin: corrutinas (suspend, Dispatchers.IO) · Swift: async/await</text>
  <text x="670" y="294" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-DEV; APPLE-DEV; KOTLIN-DOC; SWIFT-DOC]</text>
</svg>
```

---

## D7 · Arquitectura de las notificaciones push (FCM/APNs)

**Sección**: §2.3.2 — Notificaciones push y sincronización de datos
**Propósito**: Dejar claro que el servidor de la aplicación no entrega la notificación al dispositivo: lo hace el servicio de la plataforma mediante el token de registro.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Arquitectura de notificaciones push: la aplicación obtiene un token de FCM o APNs y lo envía al servidor del Ayuntamiento; cuando cambia el estado de un aviso, el servidor envía el mensaje con ese token a FCM o APNs, que lo entrega al dispositivo aunque la aplicación esté cerrada">
  <style>.t7{font:700 10.5px system-ui,sans-serif;fill:#fff}.s7{font:9.5px system-ui,sans-serif;fill:#fff}.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.l7{font:700 10px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h7">Notificaciones push: el servidor no habla con la app</text>
  <rect x="20" y="34" width="640" height="42" rx="5" fill="#e89822"/>
  <text x="340" y="52" text-anchor="middle" class="t7">Paso previo — REGISTRO</text>
  <text x="340" y="68" text-anchor="middle" class="s7">La app obtiene de FCM/APNs un TOKEN único del dispositivo y lo envía al servidor municipal</text>
  <rect x="20" y="106" width="145" height="80" rx="6" fill="#0055a0"/>
  <text x="92" y="136" text-anchor="middle" class="t7">SERVIDOR</text>
  <text x="92" y="154" text-anchor="middle" class="s7">Ayto. de Madrid</text>
  <text x="92" y="170" text-anchor="middle" class="s7">(el aviso se resuelve)</text>
  <rect x="195" y="106" width="145" height="80" rx="6" fill="#2d8659"/>
  <text x="267" y="136" text-anchor="middle" class="t7">FCM / APNs</text>
  <text x="267" y="154" text-anchor="middle" class="s7">servicio de la</text>
  <text x="267" y="170" text-anchor="middle" class="s7">plataforma</text>
  <rect x="370" y="106" width="145" height="80" rx="6" fill="#0055a0"/>
  <text x="442" y="136" text-anchor="middle" class="t7">DISPOSITIVO</text>
  <text x="442" y="154" text-anchor="middle" class="s7">conexión única</text>
  <text x="442" y="170" text-anchor="middle" class="s7">persistente</text>
  <rect x="545" y="106" width="115" height="80" rx="6" fill="#888"/>
  <text x="602" y="140" text-anchor="middle" class="t7">Notificación</text>
  <text x="602" y="158" text-anchor="middle" class="s7">al ciudadano</text>
  <path d="M167 146 L191 146" stroke="#0055a0" stroke-width="3" marker-end="url(#a7)"/>
  <path d="M342 146 L366 146" stroke="#0055a0" stroke-width="3" marker-end="url(#a7)"/>
  <path d="M517 146 L541 146" stroke="#0055a0" stroke-width="3" marker-end="url(#a7)"/>
  <defs><marker id="a7" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#0055a0"/></marker></defs>
  <text x="180" y="200" text-anchor="middle" class="l7">mensaje + token</text>
  <text x="355" y="200" text-anchor="middle" class="l7">entrega push</text>
  <text x="530" y="200" text-anchor="middle" class="l7">se muestra</text>
  <rect x="40" y="220" width="600" height="60" rx="6" fill="#d13c3c"/>
  <text x="340" y="242" text-anchor="middle" class="t7">El servidor NUNCA entrega la notificación directamente al dispositivo</text>
  <text x="340" y="260" text-anchor="middle" class="s7">Siempre pasa por FCM (Android) o APNs (iOS), que la entregan usando el token</text>
  <text x="340" y="274" text-anchor="middle" class="s7">El usuario debe autorizar las notificaciones y puede revocarlas en cualquier momento</text>
  <text x="670" y="304" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: FCM; APNS]</text>
</svg>
```

---

## D8 · Patrón *offline-first* y cola de sincronización

**Sección**: §2.3.2 — Notificaciones push y sincronización de datos
**Propósito**: Describir el flujo que permite que la app funcione sin cobertura y sincronice después sin duplicar registros.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Patrón offline-first: la interfaz lee y escribe siempre en el repositorio local SQLite, que actúa como única fuente de verdad; los registros pendientes quedan marcados como no sincronizados y un planificador de trabajo diferido los envía al servidor cuando hay red, usando un identificador único para evitar duplicados">
  <style>.t8{font:700 10.5px system-ui,sans-serif;fill:#fff}.s8{font:9.5px system-ui,sans-serif;fill:#fff}.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.l8{font:700 10px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h8">Offline-first: la interfaz nunca espera a la red</text>
  <rect x="20" y="40" width="130" height="70" rx="6" fill="#0055a0"/>
  <text x="85" y="70" text-anchor="middle" class="t8">INTERFAZ</text>
  <text x="85" y="88" text-anchor="middle" class="s8">lee y escribe</text>
  <text x="85" y="102" text-anchor="middle" class="s8">solo en local</text>
  <rect x="185" y="40" width="180" height="70" rx="6" fill="#2d8659"/>
  <text x="275" y="66" text-anchor="middle" class="t8">REPOSITORIO LOCAL</text>
  <text x="275" y="84" text-anchor="middle" class="s8">SQLite / Room / Core Data</text>
  <text x="275" y="100" text-anchor="middle" class="s8">única fuente de verdad</text>
  <rect x="400" y="40" width="150" height="70" rx="6" fill="#e89822"/>
  <text x="475" y="66" text-anchor="middle" class="t8">COLA PENDIENTE</text>
  <text x="475" y="84" text-anchor="middle" class="s8">registros marcados</text>
  <text x="475" y="100" text-anchor="middle" class="s8">sincronizado = false</text>
  <path d="M152 75 L181 75" stroke="#0055a0" stroke-width="3" marker-end="url(#a8)"/>
  <path d="M367 75 L396 75" stroke="#0055a0" stroke-width="3" marker-end="url(#a8)"/>
  <defs><marker id="a8" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#0055a0"/></marker></defs>
  <rect x="150" y="132" width="240" height="62" rx="6" fill="#0055a0"/>
  <text x="270" y="154" text-anchor="middle" class="t8">PLANIFICADOR DE TRABAJO</text>
  <text x="270" y="172" text-anchor="middle" class="s8">WorkManager (Android)</text>
  <text x="270" y="186" text-anchor="middle" class="s8">BGTaskScheduler (iOS)</text>
  <rect x="430" y="132" width="220" height="62" rx="6" fill="#888"/>
  <text x="540" y="154" text-anchor="middle" class="t8">SERVIDOR MUNICIPAL</text>
  <text x="540" y="172" text-anchor="middle" class="s8">recibe cuando hay red,</text>
  <text x="540" y="186" text-anchor="middle" class="s8">batería y permiso del sistema</text>
  <path d="M475 114 L300 128" stroke="#e89822" stroke-width="3" marker-end="url(#a8b)"/>
  <path d="M392 163 L426 163" stroke="#2d8659" stroke-width="3" marker-end="url(#a8c)"/>
  <defs>
    <marker id="a8b" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#e89822"/></marker>
    <marker id="a8c" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#2d8659"/></marker>
  </defs>
  <rect x="40" y="214" width="600" height="56" rx="6" fill="#d13c3c"/>
  <text x="340" y="236" text-anchor="middle" class="t8">Cada envío lleva un identificador único de operación (UUID)</text>
  <text x="340" y="256" text-anchor="middle" class="s8">El servidor lo trata como clave de idempotencia: reintentar tras un corte NO duplica el aviso</text>
  <text x="670" y="292" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: JETPACK; APPLE-DEV; SQLITE]</text>
</svg>
```

---

## D9 · La pila de la plataforma Android

**Sección**: §3.1.1 — Arquitectura del sistema y entorno de ejecución
**Propósito**: Presentar las capas de Android de abajo arriba y situar el entorno de ejecución ART.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Pila de la plataforma Android de abajo arriba: núcleo Linux, capa de abstracción de hardware HAL, bibliotecas nativas junto al entorno de ejecución ART, marco de trabajo de la API Java y, en la cima, las aplicaciones">
  <style>.t9{font:700 11.5px system-ui,sans-serif;fill:#fff}.s9{font:9.5px system-ui,sans-serif;fill:#fff}.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h9">Arquitectura de la plataforma Android</text>
  <rect x="30" y="34" width="620" height="48" rx="5" fill="#0055a0"/>
  <text x="340" y="54" text-anchor="middle" class="t9">APLICACIONES</text>
  <text x="340" y="72" text-anchor="middle" class="s9">Apps del sistema y de terceros — todas sobre la misma API pública</text>
  <rect x="30" y="88" width="620" height="48" rx="5" fill="#2d8659"/>
  <text x="340" y="108" text-anchor="middle" class="t9">JAVA API FRAMEWORK</text>
  <text x="340" y="126" text-anchor="middle" class="s9">ActivityManager · PackageManager · gestor de vistas · notificaciones · proveedores</text>
  <rect x="30" y="142" width="620" height="60" rx="5" fill="#e89822"/>
  <text x="340" y="162" text-anchor="middle" class="t9">BIBLIOTECAS NATIVAS (C/C++) + ANDROID RUNTIME (ART)</text>
  <text x="340" y="180" text-anchor="middle" class="s9">OpenGL/Vulkan · Media · SQLite · SSL — ART ejecuta bytecode DEX</text>
  <text x="340" y="194" text-anchor="middle" class="s9">AOT en la instalación + JIT con perfiles (sustituyó a Dalvik desde Android 5.0)</text>
  <rect x="30" y="208" width="620" height="44" rx="5" fill="#888"/>
  <text x="340" y="228" text-anchor="middle" class="t9">HAL — CAPA DE ABSTRACCIÓN DE HARDWARE</text>
  <text x="340" y="244" text-anchor="middle" class="s9">Interfaces estándar de cámara, Bluetooth, sensores y audio del fabricante</text>
  <rect x="30" y="258" width="620" height="48" rx="5" fill="#d13c3c"/>
  <text x="340" y="278" text-anchor="middle" class="t9">NÚCLEO LINUX</text>
  <text x="340" y="296" text-anchor="middle" class="s9">Procesos, memoria, controladores, energía — cada app es un USUARIO distinto (sandbox)</text>
  <text x="670" y="330" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-ARCH]</text>
</svg>
```

---

## D10 · Los cuatro componentes de Android y el Intent

**Sección**: §3.1.2 — Componentes fundamentales de la aplicación
**Propósito**: Fijar los cuatro tipos de componente, su activación mediante Intents y el papel del manifiesto.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Los cuatro componentes de una aplicación Android (Activity, Service, Broadcast Receiver y Content Provider) se activan mediante Intents, que pueden ser explícitos o implícitos, y se declaran todos en el fichero AndroidManifest.xml">
  <style>.t10{font:700 10.5px system-ui,sans-serif;fill:#fff}.s10{font:9px system-ui,sans-serif;fill:#fff}.h10{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h10">Componentes de una aplicación Android e Intents</text>
  <rect x="20" y="36" width="150" height="62" rx="5" fill="#0055a0"/>
  <text x="95" y="58" text-anchor="middle" class="t10">ACTIVITY</text>
  <text x="95" y="76" text-anchor="middle" class="s10">Una pantalla con</text>
  <text x="95" y="90" text-anchor="middle" class="s10">interfaz de usuario</text>
  <rect x="185" y="36" width="150" height="62" rx="5" fill="#2d8659"/>
  <text x="260" y="58" text-anchor="middle" class="t10">SERVICE</text>
  <text x="260" y="76" text-anchor="middle" class="s10">Trabajo prolongado</text>
  <text x="260" y="90" text-anchor="middle" class="s10">sin interfaz</text>
  <rect x="350" y="36" width="150" height="62" rx="5" fill="#e89822"/>
  <text x="425" y="58" text-anchor="middle" class="t10">BROADCAST RECEIVER</text>
  <text x="425" y="76" text-anchor="middle" class="s10">Responde a anuncios</text>
  <text x="425" y="90" text-anchor="middle" class="s10">del sistema</text>
  <rect x="515" y="36" width="145" height="62" rx="5" fill="#888"/>
  <text x="587" y="58" text-anchor="middle" class="t10">CONTENT PROVIDER</text>
  <text x="587" y="76" text-anchor="middle" class="s10">Comparte datos con</text>
  <text x="587" y="90" text-anchor="middle" class="s10">otras apps vía URI</text>
  <path d="M280 138 L95 102" stroke="#0055a0" stroke-width="2" marker-end="url(#a10)"/>
  <path d="M320 138 L260 102" stroke="#2d8659" stroke-width="2" marker-end="url(#a10b)"/>
  <path d="M370 138 L425 102" stroke="#e89822" stroke-width="2" marker-end="url(#a10c)"/>
  <path d="M410 138 L580 102" stroke="#888" stroke-width="2" marker-end="url(#a10d)"/>
  <defs>
    <marker id="a10" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#0055a0"/></marker>
    <marker id="a10b" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#2d8659"/></marker>
    <marker id="a10c" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#e89822"/></marker>
    <marker id="a10d" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8 z" fill="#888"/></marker>
  </defs>
  <rect x="175" y="142" width="330" height="66" rx="6" fill="#0055a0"/>
  <text x="340" y="164" text-anchor="middle" class="t10">INTENT — mensaje asíncrono que activa componentes</text>
  <text x="340" y="184" text-anchor="middle" class="s10">EXPLÍCITO: nombra la clase destino concreta (dentro de mi app)</text>
  <text x="340" y="200" text-anchor="middle" class="s10">IMPLÍCITO: acción + datos; el SISTEMA elige qué app lo atiende</text>
  <rect x="60" y="224" width="560" height="62" rx="6" fill="#d13c3c"/>
  <text x="340" y="246" text-anchor="middle" class="t10">AndroidManifest.xml</text>
  <text x="340" y="264" text-anchor="middle" class="s10">Declara los cuatro componentes, los permisos, los intent filters,</text>
  <text x="340" y="280" text-anchor="middle" class="s10">las versiones mínima y objetivo de la API y el hardware requerido</text>
  <text x="670" y="310" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ANDROID-DEV]</text>
</svg>
```

---

## D11 · Las cuatro capas de iOS

**Sección**: §3.2.1 — Arquitectura del sistema y capas Cocoa Touch
**Propósito**: Fijar el orden de las capas de iOS y situar Cocoa Touch como la capa superior con la que trabaja el programador.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Las cuatro capas de iOS de arriba abajo: Cocoa Touch con UIKit y SwiftUI, la capa Media con gráficos y audio, Core Services con Foundation y Core Data, y Core OS con el núcleo Darwin y la seguridad del sistema">
  <style>.t11{font:700 11.5px system-ui,sans-serif;fill:#fff}.s11{font:9.5px system-ui,sans-serif;fill:#fff}.h11{font:700 13px system-ui,sans-serif;fill:#0055a0}.n11{font:700 10px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h11">Arquitectura por capas de iOS</text>
  <text x="340" y="38" text-anchor="middle" class="n11">↑ más cercana al programador</text>
  <rect x="30" y="48" width="620" height="52" rx="5" fill="#0055a0"/>
  <text x="340" y="70" text-anchor="middle" class="t11">COCOA TOUCH — capa superior</text>
  <text x="340" y="88" text-anchor="middle" class="s11">UIKit y SwiftUI · eventos táctiles · multitarea · notificaciones · cámara · MapKit</text>
  <rect x="30" y="108" width="620" height="48" rx="5" fill="#2d8659"/>
  <text x="340" y="128" text-anchor="middle" class="t11">MEDIA</text>
  <text x="340" y="146" text-anchor="middle" class="s11">Core Graphics · Core Animation · Metal · AVFoundation</text>
  <rect x="30" y="164" width="620" height="48" rx="5" fill="#e89822"/>
  <text x="340" y="184" text-anchor="middle" class="t11">CORE SERVICES</text>
  <text x="340" y="202" text-anchor="middle" class="s11">Foundation · Core Data · Core Location · red · ficheros · iCloud</text>
  <rect x="30" y="220" width="620" height="52" rx="5" fill="#888"/>
  <text x="340" y="242" text-anchor="middle" class="t11">CORE OS</text>
  <text x="340" y="260" text-anchor="middle" class="s11">Núcleo Darwin/XNU · memoria y procesos · controladores · Keychain y Secure Enclave</text>
  <text x="340" y="292" text-anchor="middle" class="n11">Cada app se ejecuta en su propio sandbox, con permisos concedidos en tiempo de ejecución</text>
  <text x="670" y="312" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: APPLE-ARCH; APPLE-DEV]</text>
</svg>
```

---

## D12 · Híbrido de contenedor web: WebView y puente de plugins

**Sección**: §4.1.1 — Arquitectura y componentes de Apache Cordova e Ionic
**Propósito**: Mostrar las tres piezas del enfoque de contenedor web y por qué todo acceso al hardware pasa por el puente.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Arquitectura de una aplicación híbrida de contenedor web: una aplicación nativa contenedora aloja un WebView a pantalla completa que ejecuta el HTML, CSS y JavaScript empaquetados; el acceso al hardware pasa por un puente asíncrono hacia plugins nativos que exponen cámara, GPS y NFC">
  <style>.t12{font:700 10.5px system-ui,sans-serif;fill:#fff}.s12{font:9.5px system-ui,sans-serif;fill:#fff}.h12{font:700 13px system-ui,sans-serif;fill:#0055a0}.n12{font:700 10px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h12">Híbrido de contenedor web (Cordova · Ionic · Capacitor)</text>
  <rect x="20" y="38" width="370" height="216" rx="8" fill="none" stroke="#0055a0" stroke-width="2.5"/>
  <text x="205" y="58" text-anchor="middle" class="n12">APLICACIÓN NATIVA CONTENEDORA</text>
  <rect x="38" y="68" width="334" height="170" rx="6" fill="#e89822"/>
  <text x="205" y="88" text-anchor="middle" class="t12">WebView a pantalla completa</text>
  <text x="205" y="104" text-anchor="middle" class="s12">motor de renderizado web del sistema, sin barra de direcciones</text>
  <rect x="56" y="118" width="298" height="106" rx="5" fill="#0055a0"/>
  <text x="205" y="146" text-anchor="middle" class="t12">HTML + CSS + JavaScript</text>
  <text x="205" y="168" text-anchor="middle" class="s12">Empaquetados DENTRO del binario:</text>
  <text x="205" y="184" text-anchor="middle" class="s12">no se descargan de un servidor</text>
  <text x="205" y="208" text-anchor="middle" class="s12">Ionic aporta componentes de interfaz por plataforma</text>
  <rect x="404" y="68" width="66" height="170" rx="6" fill="#d13c3c"/>
  <text x="437" y="140" text-anchor="middle" class="t12">PUENTE</text>
  <text x="437" y="158" text-anchor="middle" class="s12">asíncrono</text>
  <text x="437" y="174" text-anchor="middle" class="s12">(bridge)</text>
  <path d="M356 152 L400 152" stroke="#0055a0" stroke-width="3" marker-end="url(#a12)"/>
  <path d="M472 152 L516 152" stroke="#2d8659" stroke-width="3" marker-end="url(#a12b)"/>
  <defs>
    <marker id="a12" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#0055a0"/></marker>
    <marker id="a12b" markerWidth="9" markerHeight="9" refX="4.5" refY="4.5" orient="auto"><path d="M0 0 L9 4.5 L0 9 z" fill="#2d8659"/></marker>
  </defs>
  <rect x="520" y="68" width="140" height="78" rx="6" fill="#2d8659"/>
  <text x="590" y="94" text-anchor="middle" class="t12">PLUGINS NATIVOS</text>
  <text x="590" y="114" text-anchor="middle" class="s12">parte nativa + API</text>
  <text x="590" y="130" text-anchor="middle" class="s12">JavaScript</text>
  <rect x="520" y="160" width="140" height="78" rx="6" fill="#888"/>
  <text x="590" y="186" text-anchor="middle" class="t12">HARDWARE</text>
  <text x="590" y="206" text-anchor="middle" class="s12">cámara · GPS · NFC</text>
  <text x="590" y="222" text-anchor="middle" class="s12">contactos · ficheros</text>
  <path d="M590 148 L590 156" stroke="#2d8659" stroke-width="3"/>
  <rect x="20" y="266" width="640" height="34" rx="5" fill="#d13c3c"/>
  <text x="340" y="287" text-anchor="middle" class="t12">Sin plugin no hay hardware: si el plugin queda sin mantenimiento, la función se rompe</text>
  <text x="670" y="314" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: CORDOVA-DOC; IONIC-DOC; CAPACITOR-DOC]</text>
</svg>
```

---

## D13 · React Native frente a Flutter: dos formas de renderizar

**Sección**: §4.2 — Soluciones de compilación y renderizado nativo
**Propósito**: Contraponer las dos arquitecturas multiplataforma dominantes y explicar la consecuencia visual de cada una.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Comparación entre React Native y Flutter: React Native ejecuta JavaScript en un motor propio y maneja componentes nativos reales del sistema a través de JSI; Flutter compila Dart a código máquina y dibuja cada píxel con su motor gráfico Skia o Impeller">
  <style>.t13{font:700 10.5px system-ui,sans-serif;fill:#fff}.s13{font:9.5px system-ui,sans-serif;fill:#fff}.h13{font:700 13px system-ui,sans-serif;fill:#0055a0}.c13{font:700 11.5px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h13">Dos formas de llevar una base de código a la pantalla</text>
  <text x="170" y="42" text-anchor="middle" class="c13">REACT NATIVE — componentes nativos</text>
  <text x="510" y="42" text-anchor="middle" class="c13">FLUTTER — motor gráfico propio</text>
  <rect x="25" y="54" width="290" height="46" rx="5" fill="#0055a0"/>
  <text x="170" y="74" text-anchor="middle" class="t13">JavaScript / TypeScript + React</text>
  <text x="170" y="90" text-anchor="middle" class="s13">componentes declarativos</text>
  <rect x="25" y="110" width="290" height="46" rx="5" fill="#0055a0"/>
  <text x="170" y="130" text-anchor="middle" class="t13">Motor JS (Hermes / JavaScriptCore)</text>
  <text x="170" y="146" text-anchor="middle" class="s13">se ejecuta en un hilo propio</text>
  <rect x="25" y="166" width="290" height="56" rx="5" fill="#e89822"/>
  <text x="170" y="186" text-anchor="middle" class="t13">Puente asíncrono → hoy JSI (C++)</text>
  <text x="170" y="202" text-anchor="middle" class="s13">Fabric (renderizador) · TurboModules</text>
  <text x="170" y="216" text-anchor="middle" class="s13">JSI llama al código nativo sin serializar</text>
  <rect x="25" y="228" width="290" height="52" rx="5" fill="#2d8659"/>
  <text x="170" y="250" text-anchor="middle" class="t13">COMPONENTES NATIVOS REALES</text>
  <text x="170" y="268" text-anchor="middle" class="s13">ViewGroup / UIView, TextView / UILabel</text>
  <rect x="365" y="54" width="290" height="46" rx="5" fill="#0055a0"/>
  <text x="510" y="74" text-anchor="middle" class="t13">Dart — «todo es un widget»</text>
  <text x="510" y="90" text-anchor="middle" class="s13">JIT en desarrollo (hot reload), AOT en producción</text>
  <rect x="365" y="110" width="290" height="46" rx="5" fill="#0055a0"/>
  <text x="510" y="130" text-anchor="middle" class="t13">Framework (Dart)</text>
  <text x="510" y="146" text-anchor="middle" class="s13">widgets Material y Cupertino · gestos · animación</text>
  <rect x="365" y="166" width="290" height="56" rx="5" fill="#e89822"/>
  <text x="510" y="186" text-anchor="middle" class="t13">Engine (C/C++) — Skia / Impeller</text>
  <text x="510" y="202" text-anchor="middle" class="s13">runtime de Dart · composición · texto</text>
  <text x="510" y="216" text-anchor="middle" class="s13">Embedder: única parte específica de Android/iOS</text>
  <rect x="365" y="228" width="290" height="52" rx="5" fill="#2d8659"/>
  <text x="510" y="250" text-anchor="middle" class="t13">DIBUJA CADA PÍXEL EN UN LIENZO</text>
  <text x="510" y="268" text-anchor="middle" class="s13">no usa componentes del sistema</text>
  <rect x="25" y="292" width="290" height="46" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="170" y="312" text-anchor="middle" style="font:700 10px system-ui;fill:#0055a0">Se ve como el sistema anfitrión</text>
  <text x="170" y="330" text-anchor="middle" style="font:9.5px system-ui;fill:#444">y hereda sus cambios automáticamente</text>
  <rect x="365" y="292" width="290" height="46" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <text x="510" y="312" text-anchor="middle" style="font:700 10px system-ui;fill:#0055a0">Se ve idéntico en todas partes</text>
  <text x="510" y="330" text-anchor="middle" style="font:9.5px system-ui;fill:#444">pero no hereda los cambios del sistema</text>
  <text x="670" y="354" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: RN-DOC; FLUTTER-DOC; DART-DOC]</text>
</svg>
```

---

## D14 · Árbol de decisión del enfoque y publicación en tiendas

**Sección**: §5 — Comparativa tecnológica y criterios de selección
**Propósito**: Ofrecer una regla de decisión aplicable en orden y resumir las diferencias de publicación entre las dos tiendas.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 400" role="img" aria-label="Árbol de decisión del enfoque de desarrollo móvil aplicado en orden, desde la necesidad de hardware específico que lleva a nativo hasta el caso sin hardware ni tienda que lleva a una aplicación web progresiva, y comparación de la publicación en Google Play y en la App Store">
  <style>.t14{font:700 10.5px system-ui,sans-serif;fill:#fff}.s14{font:9.5px system-ui,sans-serif;fill:#fff}.q14{font:10.5px system-ui,sans-serif;fill:#222}.h14{font:700 13px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="20" text-anchor="middle" class="h14">Criterios de selección, aplicados en este orden</text>
  <rect x="20" y="34" width="400" height="40" rx="5" fill="#eef3f8" stroke="#0055a0"/>
  <text x="36" y="59" class="q14">1. ¿Hardware o API muy específicas, o de última hora?</text>
  <rect x="450" y="34" width="210" height="40" rx="5" fill="#0055a0"/>
  <text x="555" y="59" text-anchor="middle" class="t14">NATIVO</text>
  <rect x="20" y="82" width="400" height="40" rx="5" fill="#eef3f8" stroke="#0055a0"/>
  <text x="36" y="107" class="q14">2. ¿Máximo rendimiento gráfico o de interacción?</text>
  <rect x="450" y="82" width="210" height="40" rx="5" fill="#0055a0"/>
  <text x="555" y="107" text-anchor="middle" class="t14">NATIVO o FLUTTER</text>
  <rect x="20" y="130" width="400" height="40" rx="5" fill="#eef3f8" stroke="#0055a0"/>
  <text x="36" y="155" class="q14">3. ¿Dos plataformas, un equipo y presupuesto ajustado?</text>
  <rect x="450" y="130" width="210" height="40" rx="5" fill="#2d8659"/>
  <text x="555" y="149" text-anchor="middle" class="t14">MULTIPLATAFORMA</text>
  <text x="555" y="163" text-anchor="middle" class="s14">React Native · Flutter</text>
  <rect x="20" y="178" width="400" height="40" rx="5" fill="#eef3f8" stroke="#0055a0"/>
  <text x="36" y="203" class="q14">4. ¿Equipo web y necesidades de dispositivo básicas?</text>
  <rect x="450" y="178" width="210" height="40" rx="5" fill="#e89822"/>
  <text x="555" y="197" text-anchor="middle" class="t14">HÍBRIDO</text>
  <text x="555" y="211" text-anchor="middle" class="s14">contenedor web</text>
  <rect x="20" y="226" width="400" height="40" rx="5" fill="#eef3f8" stroke="#0055a0"/>
  <text x="36" y="251" class="q14">5. ¿Sin hardware ni tienda, con actualización inmediata?</text>
  <rect x="450" y="226" width="210" height="40" rx="5" fill="#888"/>
  <text x="555" y="251" text-anchor="middle" class="t14">PWA</text>
  <line x1="20" y1="282" x2="660" y2="282" stroke="#ccc" stroke-width="1"/>
  <text x="340" y="302" text-anchor="middle" style="font:700 11px system-ui;fill:#0055a0">La publicación NO depende del enfoque elegido</text>
  <rect x="20" y="312" width="315" height="64" rx="6" fill="#2d8659"/>
  <text x="177" y="332" text-anchor="middle" class="t14">GOOGLE PLAY</text>
  <text x="177" y="350" text-anchor="middle" class="s14">AAB obligatorio · pago único de alta</text>
  <text x="177" y="366" text-anchor="middle" class="s14">revisión sobre todo automática · tracks y rollout</text>
  <rect x="345" y="312" width="315" height="64" rx="6" fill="#0055a0"/>
  <text x="502" y="332" text-anchor="middle" class="t14">APP STORE</text>
  <text x="502" y="350" text-anchor="middle" class="s14">IPA vía Xcode · cuota ANUAL del programa</text>
  <text x="502" y="366" text-anchor="middle" class="s14">revisión HUMANA siempre · TestFlight</text>
  <text x="670" y="392" text-anchor="end" style="font:11px system-ui;fill:#666">[Fuente: ISO25010; PLAY-CONSOLE; APPSTORE-REVIEW]</text>
</svg>
```

---
