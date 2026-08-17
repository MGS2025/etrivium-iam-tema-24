# Tema 24 — Índice

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Introducción al desarrollo para dispositivos móviles**
   1.1. Caracterización y evolución del ecosistema móvil
   1.1.1. Tipos de dispositivos y capacidades hardware
   1.1.2. Limitaciones de recursos: batería, memoria y procesamiento
   1.2. Estrategias y paradigmas de desarrollo
   1.2.1. Enfoque nativo
   1.2.2. Enfoque híbrido y multiplataforma
   1.2.3. Aplicaciones Web Progresivas (PWA)

2. **Arquitectura y fundamentos de aplicaciones móviles**
   2.1. Ciclo de vida de las aplicaciones
   2.1.1. Estados de ejecución y gestión de eventos
   2.1.2. Persistencia de datos local
   2.2. Interfaz y experiencia de usuario (UI/UX)
   2.2.1. Principios de diseño adaptativo y accesibilidad
   2.2.2. Componentes gráficos y maquetación
   2.3. Comunicación y conectividad
   2.3.1. Consumo de servicios web y APIs RESTful
   2.3.2. Notificaciones push y sincronización de datos

3. **Frameworks y desarrollo nativo**
   3.1. Plataforma Android
   3.1.1. Arquitectura del sistema y entorno de ejecución
   3.1.2. Componentes fundamentales de la aplicación
   3.1.3. Lenguajes de programación: Kotlin y Java
   3.2. Plataforma iOS
   3.2.1. Arquitectura del sistema y capas Cocoa Touch
   3.2.2. Componentes fundamentales de la aplicación
   3.2.3. Lenguajes de programación: Swift y Objective-C

4. **Frameworks y desarrollo híbrido**
   4.1. Soluciones basadas en contenedores web
   4.1.1. Arquitectura y componentes de Apache Cordova e Ionic
   4.2. Soluciones de compilación y renderizado nativo
   4.2.1. React Native: arquitectura, puente de comunicación y componentes
   4.2.2. Flutter: motor gráfico, lenguaje Dart y arquitectura de widgets

5. **Comparativa tecnológica y criterios de selección**
   5.1. Evaluación de rendimiento, consumo de recursos y seguridad
   5.2. Reutilización de código, mantenibilidad y costes de desarrollo
   5.3. Publicación, distribución en tiendas de aplicaciones y despliegue

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| Aplicación nativa | Se compila a código máquina de la plataforma y usa su SDK oficial (Android/Kotlin, iOS/Swift): **máximo rendimiento y acceso al hardware**, pero **una base de código por plataforma** |
| Aplicación híbrida (contenedor web) | HTML/CSS/JS ejecutados dentro de un **WebView** empaquetado como app; el acceso al hardware pasa por un **puente de plugins** (Cordova, Ionic/Capacitor) |
| Multiplataforma compilada | Una base de código que **se compila o renderiza de forma nativa**: React Native (componentes nativos vía puente/JSI) y Flutter (motor gráfico propio que pinta cada píxel) |
| PWA | Aplicación web instalable con **Service Worker** + **Web App Manifest**: funciona offline y admite push, pero con acceso limitado al hardware y **fuera de las tiendas** (en iOS con más restricciones) |
| Ciclo de vida | El **sistema operativo**, no el programador, decide cuándo pausar o destruir la app: hay que **guardar el estado antes de perder el foco** |
| Activity / UIViewController | Unidad de pantalla de Android / de iOS; ambas tienen callbacks de ciclo de vida (`onCreate`/`onPause`; `viewDidLoad`/`viewWillDisappear`) |
| Intent | Mensaje asíncrono de Android que activa componentes: **explícito** (clase concreta) o **implícito** (acción + datos, resuelto por el sistema) |
| ART | *Android Runtime*: entorno de ejecución de Android, con compilación **AOT + JIT** y formato **DEX**; sustituyó a Dalvik desde Android 5.0 |
| SQLite | Motor de base de datos **embebido, sin servidor**, base de la persistencia estructurada local tanto en Android (Room) como en iOS (Core Data) |
| Hilo principal (UI thread) | **Toda** operación de red o E/S debe salir del hilo principal; bloquearlo provoca ANR en Android o congelación de la interfaz en iOS |
| Notificación push | El servidor **no** habla con la app: envía el mensaje a **FCM** (Android) o **APNs** (iOS), que lo entregan al dispositivo mediante un *token* de registro |
| Densidad de pantalla | Android usa unidades **dp/sp** independientes de densidad; iOS usa **puntos** con factor de escala @1x/@2x/@3x |
| Diseño responsivo móvil | Un mismo diseño se adapta a tamaños, orientaciones y densidades; la accesibilidad del sector público la exige el **RD 1112/2018** (norma EN 301 549, WCAG 2.2 nivel AA) |
| Firma digital de la app | Android firma el APK/AAB con la clave del desarrollador (Play App Signing); iOS exige certificado + *provisioning profile* emitidos por Apple |
| Formato de publicación | Google Play distribuye **AAB** (*Android App Bundle*, obligatorio para apps nuevas desde agosto de 2021); App Store distribuye **IPA** enviado con Xcode/Transporter |

---

*Tiempo estimado de estudio: 14-16 horas*
*Extensión del contenido: ~12.300 palabras · 14 diagramas SVG embebidos*
