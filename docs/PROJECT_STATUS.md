# Estado del proyecto · Fases 0 y 0.1

Auditoría realizada el 18 de noviembre de 2026 en la carpeta de Since de Android Studio. Especificación oficial leída íntegramente de `Texto pegado(2).txt`, 1.505 líneas.

| Elemento | Configuración detectada |
|---|---|
| Proyecto | Since, módulo único `:app`, Kotlin DSL y catálogo de versiones |
| Identidad | `namespace`, `applicationId` y paquetes de plantilla `com.example.since`. Objetivo `com.vaxni.since` |
| SDK | Mínimo 24, compilación 37, objetivo 37. Mínimo de producto 26. Plataformas locales `android-36` y `android-37.0` |
| Versionado | `versionCode 1`, `versionName 1.0` |
| Gradle y AGP | Wrapper 9.5.0 con SHA-256 y AGP 9.3.3 |
| Java y Kotlin | Daemon configurado para Java 25. `java -version` devolvió JDK 25.0.4. `java_home -V` no encontró un JDK registrado. Compilación Java configurada a 11. Plugin Compose de Kotlin 2.2.10 |
| Compose | Activado. BOM 2026.02.01, Material 3, UI, gráficos, vista previa y herramientas. Activity Compose 1.8.0, Core KTX 1.10.1 y Lifecycle Runtime KTX 2.6.1 |
| Pruebas | JUnit 4.13.2, AndroidX JUnit 1.1.5, Espresso 3.5.1 y dependencia Compose UI Test |
| Repositorio | Inicialización local pendiente. La sesión tiene acceso de solo lectura a `.git`. Exclusiones verificadas con Git temporal |
| Repositorios Gradle | Google, Maven Central y Plugin Portal para plugins. Resolución de toolchain con Foojay 1.0.0 |
| Entorno | macOS 26.6.2, ARM64 y ADB 37.0.1 |

## Código y recursos

MainActivity es la actividad de inicio y usa `setContent`, edge-to-edge, Scaffold y un saludo de plantilla. El tema Material 3 ofrece esquemas claro y oscuro y color dinámico por defecto en Android 12 o superior. Hay iconos de plantilla, un tema XML de arranque y un único recurso de texto para el nombre. El saludo está en Kotlin. El manifiesto fuente carece de permisos declarados, exporta el launcher y habilita backups con reglas de plantilla. Release tiene la optimización desactivada.

## Hallazgos y decisiones pendientes

- AGP 9.3 documenta soporte para API 37 y Gradle 9.5.0. Los APK debug y de instrumentación disponibles acreditan que la plantilla se compiló con su configuración actual. [Compatibilidad de AGP 9.3](https://developer.android.com/build/releases/agp-9-3-0-release-notes)
- En fase 1, coordinar la migración de identidad con las declaraciones de paquetes, imports, manifiesto resuelto y aserción instrumentada. Alinear el mínimo con API 26 y validar el arranque en esa API.
- Confirmar la disponibilidad local del JDK 25 al reproducir el build fuera de esta sesión. Establecer una referencia versionada antes de desarrollar funcionalidades.
- Definir las reglas de copia y transferencia de datos antes de incorporar almacenamiento personal. Revisar optimización y firma de release en la etapa de publicación.

## Cierre de auditoría · 18 de noviembre de 2026

- **Fase 0 completada con advertencias (PASS WITH WARNINGS).** Se comprobaron el APK debug, el APK de instrumentación y el XML de la prueba unitaria generados en el proyecto. La prueba local registró 1 ejecución, 0 fallos, 0 errores y 0 omisiones. La ejecución instrumentada en dispositivo sigue pendiente de evidencia. El APK de pruebas acredita su compilación.
- **Fase 0.1 parcialmente completada.** Se revisaron los nueve documentos y sus enlaces internos. Se reforzó `.gitignore` y se verificaron 17 exclusiones y 13 rutas versionables mediante `git check-ignore` con un repositorio temporal. `git ls-files --others --exclude-standard` mostró el código, la configuración compartida y la documentación.
- **Limitación de Git.** `git init -b main` devolvió `.git: Operation not permitted`. Para terminar la preparación del repositorio normal, ejecutar ese comando desde una terminal con acceso de escritura a `.git`. No hay commits.
- **Limitaciones de validación.** El entorno de Codex restringe la escritura en la caché global de Gradle y los sockets locales usados por Gradle y ADB. La verificación de esta fase se basa en los artefactos existentes. Consulta [TESTING.md](TESTING.md).
- **Fase 1 pendiente de autorización.**
