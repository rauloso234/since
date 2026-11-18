# Arquitectura propuesta

## Módulo y dependencias

Un único módulo `:app` reduce el trabajo de configuración durante el MVP. Organizar por responsabilidades bajo `com.vaxni.since` al realizar la migración.

| Paquete | Responsabilidad |
|---|---|
| `presentation` | Pantallas Compose por funcionalidad, ViewModels, eventos y estados de UI inmutables |
| `domain` | Modelos Kotlin, contratos de repositorio y casos de uso cuando haya reglas reutilizables |
| `data` | Implementación de repositorios, Room, DAO, conversiones y preferencias con DataStore |
| `core` | Diseño, navegación y utilidades de tiempo y medios cuando se necesiten |
| `di` | Composición de dependencias con Hilt |
| `widget` | Adaptación de datos para Glance a partir de la fase 8 |

Los ViewModels reciben eventos y publican `StateFlow`. Compose observa el estado según el ciclo de vida. La UI consume el dominio, y los repositorios de datos implementan sus contratos. Room será la fuente de verdad de contadores y recuerdos. DataStore almacenará preferencias. Incorporar DAO, entidades, casos de uso y módulos de DI a medida que tengan consumidores.

## Tiempo

Guardar el instante de referencia y conservar la zona asociada cuando la interpretación calendárica la requiera. Inyectar un reloj para pruebas. Diferenciar duración exacta y unidades de calendario, con cobertura de bisiestos, fin de mes, cambios de zona y horario de verano. Recalcular al recuperar visibilidad y actualizar según la menor unidad mostrada. Until llega a cero al ocurrir el evento y puede convertirse a Since con confirmación, preservando el historial.

## Datos y fotos

Introducir Counter en la fase 3. Añadir Milestone y MilestonePhoto cuando entren los recuerdos, y Goal, Achievement, HabitEntry y CounterHistory según sus funcionalidades. Versionar el esquema y probar migraciones antes de publicar cambios que afecten a datos existentes.

Photo Picker y Activity Result con TakePicture y FileProvider permitirán escoger o capturar fotos. La app copiará archivos a almacenamiento privado, validará el resultado y guardará referencias y metadatos en Room. La lectura usará miniaturas y carga diferida. Definir límites, orientación, compresión, limpieza de capturas canceladas, recuperación de huérfanos y eliminación de archivos asociados. Definir la política de backup de datos y fotografías antes de almacenar recuerdos reales.
