# Tema 24 — Changelog

> **Título oficial**: Desarrollo para dispositivos móviles. Frameworks nativos e híbridos.

---

## v1.2 — 2026-09-06 — Corrección de formato en el conversor

**Estado**: pendiente de validación por el IAM.

**Motivo**: el texto mostraba marcas de Markdown sin convertir (`**`) en la descripción de la arquitectura de React Native.

### Alcance

- Se porta a este tema el **arreglo del conversor** que la serie incorporó a partir del Tema 28: la negrita se procesa **antes** que la cursiva y sin ser codiciosa.
- **Sin cambios de contenido**: solo formato. El defecto venía de la primera publicación del tema.

---

## v1.1 — 2026-09-06 — Ficha de extensión y tiempo de estudio

**Estado**: sin cambios de contenido. Solo se añade información sobre el propio tema.

**Motivo**: petición del IAM (Jesús Cuadrado, 02-09-2026) al validar el Tema 30. Acepta la extensión de los temas «compuestos» a condición de que se informe de «su extensión en palabras y tiempo estimado de estudio». Al revisarlo se vio que ese dato solo aparecía en 16 de los 40 temas, y que faltaba justo en los más largos.

### Alcance

- Ficha bajo la cabecera del tema, y al final de la pestaña Índice donde esa pestaña existe:
  - **Extensión**: ~12.500 palabras · 14 diagramas · 60 preguntas de test
  - **Tiempo estimado de estudio**: 13-15 horas (primera vuelta completa, sin contar repasos)
- La cifra de palabras de la tabla de entregables se sincroniza con la ficha, para que el tema no muestre dos recuentos distintos.
- Las horas salen de una fórmula común a los 40 temas, para que sean comparables entre sí: contenido a 1.500 palabras/hora (ritmo de estudio activo), diagramas a una hora por cada cinco y test a dos minutos por pregunta. Se publica como intervalo de dos horas.
- Generado con `_tools-qa/ficha_estudio.py`, idempotente y reejecutable tras cualquier regeneración con `build_tNN.py`.

---

## v1.0 — 2026-08-17 — Primera versión

**Estado**: pendiente de validación por María y Ana, y de revisión técnica del IAM (Jesús Cuadrado).

**Motivo**: desarrollo del Tema 24, dentro de la serie de temas técnicos generados desde cero, replicando la estructura y el formato de los Temas 1, 11, 17-23 ya consolidados. Con este tema, el bloque técnico queda **completo y sin huecos de T11 a T24**.

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | ~12.300 palabras · 5 secciones (fieles al esqueleto oficial) con 34 epígrafes numerados |
| Diagramas SVG inline | 14 (accesibles con `role`/`aria-label`, clases con sufijo único anti-colisión) |
| Banco de preguntas tipo test | 60 preguntas A/B/C con explicación y referencia, balanceadas **20/20/20** (verificado por el generador) |
| Casos prácticos | 3 (elección de enfoque para la app de avisos; ciclo de vida, offline y sincronización; accesibilidad, permisos, seguridad y publicación) · 10 puntos cada uno |
| Fuentes Tier 1 | 26 referencias canónicas (Android/AOSP, Apple, W3C, IETF, Ecma, OWASP, ISO, SQLite) |

### Decisiones de generación

1. **Sin material de cliente**: solo el esqueleto `Test_Prompting/temas agosto/24.md`. Desarrollado desde fuentes canónicas (documentación oficial de Android y Apple, especificaciones W3C/IETF/Ecma, catálogo OWASP Mobile y modelo de calidad ISO/IEC 25010), todas referenciadas.
2. **Estructura fiel al esqueleto oficial**, con numeración jerárquica de hasta tres niveles donde el esqueleto lo exige (H2 > H3 > H4), respetando sus 5 secciones y sus 34 epígrafes sin añadir secciones nuevas de primer nivel.
3. **Ampliaciones dentro de los epígrafes existentes** (decisión de generación, no del esqueleto): modelo de permisos de Android (normales, peligrosos, de firma y especiales), capacidades y *entitlements* de iOS, patrones de navegación, notificaciones locales y silenciosas frente a push, y estrategia de pruebas. Todas encajan en epígrafes ya previstos y cubren huecos que en examen se preguntan con frecuencia.
4. **Ejemplos de código reales en Kotlin, Swift, Dart, JavaScript, XML y JSON** (decisión de Joan, mismo criterio que T21 con Java/Jakarta y T23 con HTML/JS/PHP): el tema consiste precisamente en comparar estas plataformas concretas, y un pseudocódigo agnóstico impediría apreciar las diferencias que son su objeto.
5. **Caso de referencia único para todo el tema**: una **aplicación municipal de avisos ciudadanos** (fotografía + geolocalización, consulta de estado, notificación al resolverse), planteada como **supuesto simplificado** y no como descripción de una aplicación real concreta. Concentra casi todas las dificultades del desarrollo móvil: hardware, permisos, conectividad intermitente, trabajo en segundo plano, accesibilidad obligatoria y doble publicación.
6. **Núcleo conceptual reforzado**: la distinción entre *híbrido de contenedor web* (WebView) y *multiplataforma compilado* (React Native con componentes nativos, Flutter con motor gráfico propio) se ha tratado como el eje del tema, porque es la confusión más frecuente y la que más rinde en examen. Se refuerza con dos diagramas dedicados (D2 y D13) y con varias preguntas de test.
7. **Frontera con temas vecinos** cuidada: los sistemas operativos móviles en cuanto sistemas al Tema 14; la arquitectura de ordenadores y los periféricos a los Temas 11 y 12; los fundamentos de lenguajes de programación al Tema 18; POO y patrones al Tema 20; Java EE al Tema 21; arquitecturas cliente/servidor y servicios web al Tema 22; el desarrollo web y las PWA como tecnología web al Tema 23; accesibilidad y usabilidad como disciplina y seguridad en el desarrollo al Tema 25; seguridad de sistemas al Tema 32; TCP/IP y HTTP/TLS a los Temas 34 y 35; seguridad en redes al Tema 36; ENS/ENI al Tema 39.
8. **Referencias cruzadas validadas contra BOAM 10.032**: T11, T12, T14, T18, T20, T21, T22, T23, T25, T32, T34, T35, T36, T39. Todas comprobadas contra el enunciado oficial de cada tema.
9. **Anti-colisión de SVG**: las clases CSS de cada diagrama llevan **sufijo numérico único** (`.t1`…`.t14`), evitando el fallo sistémico de estilos que se filtran de un SVG a otro al estar todos embebidos en la misma página (lección de T5).
10. **Distribución A/B/C planificada antes de redactar** y verificada con el generador (lección de T23, donde la rotación cíclica pretendida no se cumplió): la secuencia de letras correctas se fijó de antemano y `build_t24.py` confirma **20/20/20**.
11. **Cómputo de extensión medido, no estimado**: la cifra de ~12.300 palabras procede de `wc -w` sobre el `.md`. Medidos con el mismo criterio, los temas anteriores de la serie arrojan cifras menores que las declaradas en sus cabeceras (T21 ≈ 10.500, T22 ≈ 9.100, T23 ≈ 9.200), de modo que este tema es, de hecho, **el más extenso de la serie técnica** pese a declarar una cifra inferior a la de T23.

### Pendientes para QA / próxima iteración

- Validación de profundidad por María/Ana/IAM (¿alguna sección a ampliar o recortar?).
- Confirmar si conviene desarrollar el **OWASP Mobile Top 10** riesgo a riesgo en §5.1, al modo en que T23 desarrolló el OWASP Top 10 web, o si el nivel actual basta al existir los Temas 25 y 32.
- **Revisión de vigencia antes de cada convocatoria**: es, junto al Tema 31 (cloud), el tema más sensible a la obsolescencia del bloque técnico (versiones de frameworks, requisitos de las tiendas, arquitecturas en migración).
- Verificación ortográfica con corrector es_ES (cuidado con falsos positivos por términos técnicos en inglés: *widget*, *bridge*, *runtime*, *sandbox*, *token*, *rollout*, *bundle*, *hot reload*, *wearable*…).

### Origen

Generado el 2026-08-17 en el flujo de trabajo de eTrivium, replicando el patrón de los Temas 1 (v2.1), 11 (v3.2), 17-23 (v1.0). `build_t24.py` y `_build_css.txt` persistidos en el repo.
