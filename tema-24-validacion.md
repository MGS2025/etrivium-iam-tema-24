# Tema 24 — Checklist de Validación

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-17
> **Revisores**: María y Ana (eTrivium) · revisión técnica IAM (Jesús Cuadrado)
> **Instrucciones**: marcar cada ítem. Los cambios no se guardan en la web (imprimir o exportar a PDF si se desea fijarlos).

---

## 1. Cobertura del temario oficial

- [ ] **Introducción al desarrollo móvil**: ecosistema, tipos de dispositivos y capacidades hardware, limitaciones de batería/memoria/procesamiento — §1.1
- [ ] **Estrategias y paradigmas**: enfoque nativo, enfoque híbrido y multiplataforma, PWA — §1.2
- [ ] **Ciclo de vida**: estados de ejecución y gestión de eventos, persistencia de datos local — §2.1
- [ ] **Interfaz y experiencia de usuario**: diseño adaptativo y accesibilidad, componentes gráficos y maquetación — §2.2
- [ ] **Comunicación y conectividad**: servicios web y APIs RESTful, notificaciones push y sincronización — §2.3
- [ ] **Plataforma Android**: arquitectura y entorno de ejecución, componentes fundamentales, Kotlin y Java — §3.1
- [ ] **Plataforma iOS**: arquitectura y capas Cocoa Touch, componentes fundamentales, Swift y Objective-C — §3.2
- [ ] **Soluciones de contenedor web**: arquitectura y componentes de Apache Cordova e Ionic — §4.1
- [ ] **Soluciones de compilación y renderizado nativo**: React Native y Flutter — §4.2
- [ ] **Comparativa y criterios**: rendimiento/recursos/seguridad, reutilización/mantenibilidad/costes, publicación y despliegue — §5.1-5.3

## 2. Contenido teórico

- [ ] El nivel de profundidad (5 secciones, 34 epígrafes, ~12.300 palabras) es adecuado para C1 (¿hay que ampliar o recortar alguna sección?)
- [ ] La distinción entre **híbrido de contenedor web** (WebView) y **multiplataforma compilado** (React Native / Flutter) queda suficientemente nítida — es el núcleo conceptual del tema y la confusión más frecuente
- [ ] Las definiciones de dp/sp, Dalvik/ART, Intent explícito/implícito, ARC/recolector de basura y AAB/IPA son correctas y están bien diferenciadas
- [ ] La decisión de usar **snippets de código reales** (Kotlin, Swift, Dart, JavaScript) en lugar de pseudocódigo neutro es adecuada (¿o se prefiere un enfoque más conceptual?)
- [ ] Los bloques añadidos más allá del enunciado literal del esqueleto (modelo de permisos de Android, capacidades y *entitlements* de iOS, patrones de navegación, notificaciones locales, estrategia de pruebas) aportan valor y no desbordan el nivel C1
- [ ] La frontera con los Temas 14 (sistemas operativos móviles), 18 (lenguajes de programación), 20 (POO), 22 (arquitecturas cliente/servidor y servicios web), 23 (aplicaciones web y PWA), 25 (accesibilidad y seguridad en el desarrollo), 32 (seguridad de sistemas), 34/35 (TCP/IP, HTTP/TLS), 36 (seguridad en redes) y 39 (ENS/ENI) está clara y sin duplicidades innecesarias
- [ ] Los ejemplos Ayto Madrid (app de avisos ciudadanos) son verosímiles y coherentes entre secciones
- [ ] **Vigencia tecnológica**: al tratarse del tema más volátil del bloque, conviene confirmar que las versiones y afirmaciones citadas siguen vigentes en la fecha del examen (nueva arquitectura de React Native, Impeller en Flutter, requisitos de las tiendas)

## 3. Fuentes

- [ ] Todas las afirmaciones técnicas están respaldadas por fuente Tier 1 (documentación oficial de Android/AOSP y Apple, W3C, IETF, Ecma, OWASP, ISO)
- [ ] Las referencias inline se corresponden con `tema-24-fuentes.md`
- [ ] Atribuciones históricas correctas (App Store y Android Market 2008, PhoneGap/Cordova 2011, Swift 2014, React Native 2015, Kotlin oficial 2017 y preferente 2019, Flutter estable 2018, AAB obligatorio agosto 2021)

## 4. Test (60 preguntas)

- [ ] Cada pregunta tiene una sola respuesta correcta e inequívoca
- [ ] Los distractores (A/B/C) son plausibles
- [ ] La distribución de la opción correcta entre A/B/C está equilibrada (**verificada 20/20/20** por el generador)
- [ ] Las explicaciones y referencias de cada respuesta son correctas

## 5. Casos prácticos (3)

- [ ] Realistas y propios del Ayuntamiento (elección de enfoque para la app de avisos; ciclo de vida, offline y sincronización; accesibilidad, permisos, seguridad y publicación)
- [ ] Soluciones orientativas técnicamente correctas (Kotlin y Swift funcionales en su forma simplificada)
- [ ] La puntuación de cada caso suma 10 puntos

## 6. Diagramas (14 SVG)

- [ ] Cada diagrama es correcto y legible (también impreso en blanco y negro)
- [ ] Accesibilidad: todos tienen `role="img"` y `aria-label`
- [ ] Sin desbordes de texto ni colisiones de estilo entre SVG (clases con sufijo único, QA de caja contenedora con render en navegador)

## 7. Referencias cruzadas a otros temas

- [ ] Validadas contra BOAM 10.032 (T11, T12, T14, T18, T20, T21, T22, T23, T25, T32, T34, T35, T36, T39)
- [ ] Ninguna referencia cruzada cita un enunciado de tema incorrecto

## 8. Calidad editorial

- [ ] Ortografía verificada (tildes y ñ) — sin diacríticos perdidos, también dentro de los `aria-label` de los SVG
- [ ] Coherencia de versión (v1.0) en title, badges, banner y footer del `index.html`
- [ ] El `index.html` abre, navega entre las 8 pestañas y el motor de test funciona
- [ ] Las listas anidadas del Contenido se muestran con sus niveles (sin aplanar)
- [ ] Los bloques de código Kotlin/Swift/Dart/JavaScript/XML/JSON se muestran correctamente formateados, sin markdown crudo

---

## Observaciones abiertas

_(Espacio para anotaciones de María, Ana y la revisión IAM.)_

- Pendiente confirmar con el IAM si interesa **ampliar la comparativa económica** (§5.2) con horquillas orientativas de coste y plazo, o si el enfoque cualitativo actual es el adecuado para C1.
- Pendiente confirmar si conviene desarrollar más la **seguridad móvil** (§5.1) con el detalle del OWASP Mobile Top 10 riesgo a riesgo, como se hizo con el OWASP Top 10 web en el Tema 23, o si el nivel actual es suficiente al existir ya el Tema 25 y el Tema 32.
- Este es, junto al Tema 31 (cloud), el tema **más sensible a la obsolescencia** del bloque técnico: conviene fijar una revisión de vigencia antes de cada convocatoria.
