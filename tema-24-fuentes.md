# Tema 24 — Fuentes

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
>
> **Criterio**: todo dato del contenido cita un **ID** inline (p. ej. `[ANDROID-DEV]`). Tier 1 = documentación oficial de las plataformas y especificaciones de estándares abiertos (Google/AOSP, Apple, W3C, IETF, Ecma, OWASP, ISO); Tier 2 = documentación de frameworks, motores y servicios concretos, citada para ilustrar sin atar el tema a un único producto; Tier 3 = marco normativo y del puesto, no citado como contenido técnico puro.

---

## Tier 1 — Documentación oficial de plataforma y especificaciones

| ID | Referencia |
|---|---|
| `[ANDROID-DEV]` | Google. *Android Developers — Guides: Application Fundamentals, Activities, Services, Broadcast Receivers, Content Providers, Intents and Intent Filters*. developer.android.com/guide. Documentación normativa del modelo de aplicación de Android. |
| `[ANDROID-ARCH]` | Android Open Source Project (AOSP). *Platform Architecture* — kernel Linux, HAL, ART, bibliotecas nativas, *Java API Framework*. source.android.com y developer.android.com/guide/platform. |
| `[ANDROID-LIFECYCLE]` | Google. *The Activity Lifecycle* y *Guide to app architecture*. developer.android.com/guide/components/activities/activity-lifecycle. |
| `[ANDROID-UI]` | Google. *Android Developers — UI layouts, resource qualifiers, densidades de pantalla (dp/sp), Jetpack Compose*. developer.android.com/develop/ui. |
| `[ANDROID-A11Y]` | Google. *Android Accessibility — Principles and testing*. developer.android.com/guide/topics/ui/accessibility. |
| `[KOTLIN-DOC]` | JetBrains. *Kotlin Language Documentation* (null safety, corrutinas, interoperabilidad con Java). kotlinlang.org/docs. Kotlin es lenguaje preferente de Android desde 2019 [ANDROID-DEV]. |
| `[APPLE-DEV]` | Apple. *Developer Documentation — UIKit, App Life Cycle, View Controller Programming Guide*. developer.apple.com/documentation. |
| `[APPLE-ARCH]` | Apple. *iOS Technology Overview / arquitectura por capas* (Core OS, Core Services, Media, Cocoa Touch) y *Darwin/XNU*. developer.apple.com. |
| `[SWIFT-DOC]` | Apple. *The Swift Programming Language* (opcionales, ARC, protocolos, concurrencia `async/await`). docs.swift.org. |
| `[SWIFTUI-DOC]` | Apple. *SwiftUI — Declarative UI framework*. developer.apple.com/documentation/swiftui. |
| `[HIG]` | Apple. *Human Interface Guidelines* — principios de diseño de interfaz de las plataformas Apple. developer.apple.com/design/human-interface-guidelines. |
| `[MATERIAL]` | Google. *Material Design 3* — sistema de diseño de referencia de Android. m3.material.io. |
| `[WCAG22]` | W3C WAI. *Web Content Accessibility Guidelines (WCAG) 2.2*. w3.org/TR/WCAG22. Criterios de accesibilidad aplicables también a aplicaciones móviles vía EN 301 549. |
| `[SERVICE-WORKERS]` | W3C. *Service Workers Specification*. w3.org/TR/service-workers. Fundamento técnico del funcionamiento offline de las PWA. |
| `[WEB-APP-MANIFEST]` | W3C. *Web Application Manifest*. w3.org/TR/appmanifest. Metadatos de instalación de una PWA. |
| `[ECMA262]` | Ecma International. *ECMA-262: ECMAScript Language Specification*. Base de JavaScript en contenedores web, React Native y PWA. |
| `[RFC9110]` | IETF HTTP Working Group. *RFC 9110: HTTP Semantics* (2022). Métodos, cabeceras y códigos de estado usados por el cliente móvil al consumir una API. |
| `[RFC8446]` | IETF. *RFC 8446: The Transport Layer Security (TLS) Protocol Version 1.3*. Cifrado del tráfico app-servidor. |
| `[RFC6749]` | IETF. *RFC 6749: The OAuth 2.0 Authorization Framework*. |
| `[RFC8252]` | IETF. *RFC 8252: OAuth 2.0 for Native Apps* (BCP 212). Recomienda el navegador del sistema y **PKCE** frente a WebView embebido para la autorización en apps móviles. |
| `[RFC7636]` | IETF. *RFC 7636: Proof Key for Code Exchange (PKCE)*. Protección del flujo de código de autorización en clientes públicos como una app móvil. |
| `[FIELDING2000]` | Fielding, R. T. *Architectural Styles and the Design of Network-based Software Architectures* (UC Irvine, 2000). Origen del estilo REST consumido por el cliente móvil. |
| `[OWASP-MASVS]` | OWASP Foundation. *Mobile Application Security Verification Standard (MASVS)* y *Mobile Application Security Testing Guide (MASTG)*. mas.owasp.org. Referencia canónica de seguridad en aplicaciones móviles. |
| `[OWASP-MOBILE]` | OWASP Foundation. *OWASP Mobile Top 10* — riesgos más críticos en aplicaciones móviles (almacenamiento inseguro, comunicación insegura, autenticación inadecuada…). owasp.org/www-project-mobile-top-10. |
| `[ISO25010]` | ISO/IEC 25010 (SQuaRE). *Modelo de calidad del producto software* — adecuación funcional, eficiencia de desempeño, compatibilidad, usabilidad, fiabilidad, seguridad, mantenibilidad y portabilidad. Marco de los criterios comparativos de §5. |
| `[SQLITE]` | SQLite Consortium. *SQLite Documentation — About SQLite, serverless, zero-configuration*. sqlite.org. Motor embebido usado por Android e iOS. |

## Tier 2 — Frameworks, motores y servicios concretos

| ID | Referencia |
|---|---|
| `[JETPACK]` | Google. *Android Jetpack* — Room (persistencia), WorkManager (trabajo diferido), DataStore (preferencias), Navigation. developer.android.com/jetpack. |
| `[COREDATA]` | Apple. *Core Data Programming Guide* y *SwiftData*. developer.apple.com/documentation/coredata. |
| `[FCM]` | Google. *Firebase Cloud Messaging — Architectural Overview*. firebase.google.com/docs/cloud-messaging. Servicio de entrega de notificaciones push en Android. |
| `[APNS]` | Apple. *Apple Push Notification service (APNs) — Sending notification requests to APNs*. developer.apple.com/documentation/usernotifications. |
| `[CORDOVA-DOC]` | The Apache Software Foundation. *Apache Cordova Documentation* — arquitectura WebView + plugins, `config.xml`. cordova.apache.org/docs. |
| `[IONIC-DOC]` | Ionic. *Ionic Framework Documentation* — componentes de interfaz web adaptados a cada plataforma. ionicframework.com/docs. |
| `[CAPACITOR-DOC]` | Ionic. *Capacitor Documentation* — runtime nativo sucesor de Cordova en el ecosistema Ionic. capacitorjs.com/docs. |
| `[RN-DOC]` | Meta. *React Native Documentation* — arquitectura clásica (*bridge* asíncrono) y nueva arquitectura (**JSI**, **Fabric**, **TurboModules**, Codegen). reactnative.dev. |
| `[FLUTTER-DOC]` | Google. *Flutter Documentation — Architectural overview*: capas Framework/Engine/Embedder, motor de renderizado (Skia e Impeller), árbol de widgets. docs.flutter.dev. |
| `[DART-DOC]` | Google. *Dart Language Documentation* — compilación JIT en desarrollo (*hot reload*) y AOT en producción. dart.dev. |
| `[MAUI-DOC]` | Microsoft. *.NET MAUI Documentation* (sucesor de Xamarin.Forms). learn.microsoft.com/dotnet/maui. |
| `[KMP-DOC]` | JetBrains. *Kotlin Multiplatform* — compartición de lógica de negocio manteniendo interfaz nativa. kotlinlang.org/docs/multiplatform.html. |
| `[MDN-PWA]` | Mozilla Developer Network. *Progressive web apps*. developer.mozilla.org/en-US/docs/Web/Progressive_web_apps. |
| `[PLAY-CONSOLE]` | Google. *Google Play Console Help — Publish, App Bundle, release tracks, staged rollout, Play App Signing*. support.google.com/googleplay/android-developer. |
| `[APPSTORE-REVIEW]` | Apple. *App Store Review Guidelines* y *App Store Connect Help* — TestFlight, revisión, publicación por fases. developer.apple.com/app-store/review/guidelines. |
| `[LIGHTHOUSE-DOC]` | Google. *Lighthouse — auditoría de PWA y rendimiento*. developer.chrome.com/docs/lighthouse. |

## Tier 3 — Marco normativo y del puesto (contexto, no contenido técnico)

| ID | Referencia |
|---|---|
| `[RD1112-2018]` | Real Decreto 1112/2018, de 7 de septiembre, sobre accesibilidad de los sitios web y **aplicaciones para dispositivos móviles** del sector público. Transpone la Directiva (UE) 2016/2102. Aplicable directamente a una app municipal. |
| `[EN301549]` | Norma EN 301 549 (*Requisitos de accesibilidad para productos y servicios TIC*), estándar armonizado de referencia del RD 1112/2018; incorpora WCAG 2.x y añade el capítulo 11 sobre software, con criterios específicos para aplicaciones móviles. |
| `[ENS]` | Real Decreto 311/2022, Esquema Nacional de Seguridad — requisitos de autenticación, cifrado en tránsito, trazabilidad y gestión del ciclo de vida aplicables a una app del sector público. |
| `[RGPD]` | Reglamento (UE) 2016/679 (RGPD) y LO 3/2018 (LOPDGDD) — base legal del tratamiento de datos personales, geolocalización e identificadores del dispositivo en una aplicación móvil. |
| `[BOAM10032]` | BOAM 10.032 (23-dic-2025). Bases específicas TIC C1 Ayto. Madrid — temario oficial. |

---

*Las referencias Tier 1 fijan el fundamento del tema: la documentación oficial de las dos plataformas dominantes (Android/AOSP y Apple), las especificaciones de estándares abiertos implicadas (W3C para PWA y accesibilidad, IETF para HTTP/TLS/OAuth, Ecma para JavaScript), el catálogo de seguridad móvil de OWASP y el modelo de calidad ISO/IEC 25010 que estructura la comparativa. Tier 2 documenta frameworks y servicios concretos citados como ejemplo (Cordova/Ionic, React Native, Flutter, FCM/APNs, tiendas) sin que el tema dependa de ninguno en particular. Tier 3 enmarca la normativa de accesibilidad, seguridad y protección de datos que condiciona el desarrollo de una aplicación móvil del Ayuntamiento de Madrid.*
