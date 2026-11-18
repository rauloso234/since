# Pruebas

## Referencia inicial

| Comando | Resultado |
|---|---|
| `./gradlew assembleDebug` | El Wrapper no pudo abrir el bloqueo en el directorio Gradle del usuario por permisos |
| `GRADLE_USER_HOME=<caché temporal> ./gradlew --offline --no-daemon assembleDebug testDebugUnitTest assembleDebugAndroidTest` | Gradle 9.5.0 arrancó. La creación de `FileLockContentionHandler` falló por una restricción de sockets. Ninguna tarea se ejecutó |
| `adb devices -l` (ADB del SDK) | El servidor no pudo abrir su socket local. No se verificó ningún dispositivo |
| `git status --short --branch` | El directorio no pertenece a un repositorio Git |

La prueba local de plantilla comprueba una suma. La instrumentada verifica el identificador `com.example.since` y deberá actualizarse al migrar. La prueba instrumentada sigue pendiente de ejecución verificada.

## Evidencias revisadas en la Fase 0.1

| Evidencia local | Resultado |
|---|---|
| `app/build/outputs/apk/debug/app-debug.apk` | APK válido como ZIP, con manifiesto y DEX. Metadatos de variante debug e identificador `com.example.since` |
| `app/build/test-results/testDebugUnitTest/TEST-com.example.since.ExampleUnitTest.xml` | `addition_isCorrect` aprobada. 1 prueba, 0 fallos, 0 errores y 0 omisiones |
| `app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk` | APK de pruebas válido como ZIP, con manifiesto y DEX. Ejecución en dispositivo pendiente de informe |

## Cobertura por funcionalidad

- **Unidad.** Validación, cambios de reloj, DST, año bisiesto, fin de mes, transición de Until y cálculo de rachas y progreso.
- **Integración.** DAO, persistencia, repositorios, migraciones de Room e importación, limpieza y recuperación de fotos.
- **UI.** Onboarding, navegación, CRUD de contadores e hitos, cámara, selector de fotos, cancelaciones, estados vacíos y restauración de estado.
- **Dispositivos.** Verificar API 26 y una versión reciente. Probar teléfono y pantalla grande, modo oscuro, texto ampliado y lector de pantalla.

Para verificar la ejecución instrumentada, usar `./gradlew connectedDebugAndroidTest` con un dispositivo o emulador en un entorno que permita los sockets locales.
