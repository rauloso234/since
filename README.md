# Since

**Every moment counts.** Aplicación Android para contar el tiempo desde un acontecimiento, anticipar fechas y conservar recuerdos personales.

El proyecto actual es una plantilla Kotlin y Jetpack Compose. El MVP propuesto cubre Since y Until, la gestión de contadores y una pantalla de inicio personalizable. Since Memories amplía el producto en la fase 6 con hitos y fotos opcionales.

## Desarrollo

Abre la raíz en Android Studio. La configuración actual requiere la plataforma Android 37 y un JDK 25 para el daemon de Gradle. El código está configurado con compatibilidad Java 11. El objetivo del producto es Android 8.0 (API 26), con interfaz en español e inglés y funciones básicas disponibles sin conexión ni cuenta.

```sh
./gradlew assembleDebug
./gradlew testDebugUnitTest
./gradlew connectedDebugAndroidTest
```

Consulta el [estado verificado](docs/PROJECT_STATUS.md), el [alcance](docs/FEATURES.md), la [arquitectura](ARCHITECTURE.md), el [diseño](docs/DESIGN_SYSTEM.md), las [pruebas](docs/TESTING.md) y el [roadmap](ROADMAP.md).
