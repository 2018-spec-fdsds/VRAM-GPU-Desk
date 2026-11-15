# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Supervisión local de memoria y control de temperatura de GPU NVIDIA para Windows x64. Solo NVIDIA; las GPU AMD e Intel no son compatibles.**

## Para qué sirve la aplicación

- **Supervisar y liberar VRAM de NVIDIA en Windows.** Forzar el cierre de aplicaciones para liberar VRAM, también mediante botones rápidos configurables de un clic vinculados a la instancia exacta seleccionada.
- **Gestionar aplicaciones que compiten por la VRAM.** Para varias tareas simultáneas: modelos locales de generación de código, generación de imágenes y vídeo, transcripción y análisis de datos.
- **Control gradual de temperatura y refrigeración.** Regular la temperatura de la GPU de forma flexible mediante los límites de potencia y frecuencia admitidos, y refrigerarla tanto bajo carga como en reposo.
- **Modo de emergencia ante sobrecalentamiento.** Un modo opcional puede forzar el cierre de aplicaciones con alta carga de GPU para reducir la carga. Está DESACTIVADO en cada inicio; el cierre forzado puede causar pérdida de trabajo sin guardar.

## Funciones principales

- Supervisión local de VRAM, carga y temperatura NVIDIA, RAM del sistema y utilización de CPU, con gráficos y barras por núcleo.
- Memoria GPU por proceso, búsqueda, ordenación y exportación CSV en UTF-8.
- Control de temperatura y refrigeración en reposo adaptados a las capacidades de cada GPU.
- Cuatro botones configurables de un clic vinculados a instancias concretas de procesos; la finalización de emergencia opcional está DESACTIVADA en cada inicio.
- Historial de VRAM de 24 horas y las 10 aplicaciones principales de los últimos 30 días.
- 12 idiomas, dos temas, bandeja del sistema e inicio opcional con Windows.
- Dos paneles NVIDIA con ajustes independientes; el control de la segunda GPU es experimental.
- Aviso de pérdida de control y reintento manual; recuperación ACTIVADA para ajustes nuevos, respetando la desactivación guardada.

Versión **1.20** · [Instalador Windows](downloads/VRAM-GPU-Desk-1.20-Setup-x64.exe) · [ZIP del instalador](downloads/VRAM-GPU-Desk-1.20-Installer.zip)

![VRAM GPU Desk — tema grafito](images/dashboard-graphite.png)

## 1.20 — Monitor flotante de GPU

Monitor compacto y transparente sobre las ventanas normales de Windows, sin panel de fondo. Una superposición independiente de ≈164 × 114 píxeles físicos por GPU NVIDIA; hasta dos tarjetas. Posición independiente guardada, bloqueo, escala y contraste ajustables. Monitor oculto por defecto; sonido activado por defecto y desactivable por separado. Utiliza la telemetría existente sin control adicional de GPU.

Uso de VRAM y carga de GPU; temperatura: ≤40 verde, 41–75 amarillo, 76–81 naranja, 82–86 rojo, ≥87 parpadeo. Sonido desde 88 °C.

![ Monitor flotante de GPU ](images/floating-monitor-dark.png)



Datos sintéticos de demostración y estados simulados de los reguladores. Ambas opciones de emergencia están DESACTIVADAS en cada inicio. La recuperación está ACTIVADA para ajustes nuevos; se respeta la desactivación guardada.


> **Control de GPU:** El control de los parámetros de temperatura de la GPU requiere una confirmación UAC al instalar el componente de control. Después, activar el control de temperatura y la refrigeración no genera nuevas solicitudes UAC. La supervisión por sí sola no requiere UAC.

> **Control simultáneo de GPU:** El control de los parámetros de temperatura de la GPU puede entrar en conflicto con otros programas que cambien al mismo tiempo la potencia, las frecuencias o la velocidad de los ventiladores, como MSI Afterburner. Utilice un único controlador activo para estos ajustes. La advertencia se refiere a cambios simultáneos, no a la supervisión pasiva.


## Novedades de 1.19: adaptación por dispositivo para NVIDIA RTX 30, 40 y 50

**Límites reales del dispositivo, no una potencia fija.** Cada sesión consulta los límites de potencia de su GPU y guarda el límite inicial como techo de sesión y referencia de restauración, en lugar del valor de fábrica. Adquirir la sesión no escribe inicialmente potencia ni frecuencia. Los cambios de potencia se escalan al **1% del valor inicial de sesión por segundo**, dentro de los límites consultados y del techo de sesión. Los ajustes de frecuencia son relativos a un intervalo compatible validado.

**Solo controles disponibles.** Si el control de frecuencia no está admitido, sigue disponible la regulación compatible solo por potencia. Una temperatura válida permite ese modo aunque la utilización GPU sea desconocida. Se bloquea un objetivo superior al límite térmico de hardware comunicado; los límites ausentes siguen siendo desconocidos. Las funciones incompatibles permanecen visibles como no disponibles. La recuperación de ventiladores es independiente de la del cliente de potencia. BIOS, OEM, controlador y restricciones del portátil pueden variar las capacidades; cada GPU se evalúa por separado.

**Las referencias no son órdenes de control.** La [referencia RTX 30 y posteriores](docs/nvidia-rtx30-plus/README.md) y el [CSV UTF-8](docs/nvidia-rtx30-plus/REFERENCE-GPUS.csv) incluyen **45 grupos de modelos/variantes: 27 de sobremesa y 18 de portátil**. Son grupos documentales, no 45 pruebas de hardware; las potencias publicadas y el TGP no son preajustes ejecutables. La fila RTX 3060 Ti de 200 W corresponde a la especificación de referencia, no a todas las variantes GDDR6X u OEM.

**Área CPU compacta con dos GPU.** El borde inferior de la tarjeta CPU se alinea con el panel contiguo de refrigeración en reposo, por encima de las filas de emergencia y recuperación. La RAM permanece arriba; siguen visibles la carga CPU y las barras de núcleos físicos. La vista de seis tarjetas para una GPU no cambia.

## Novedades de 1.18: utilización de CPU y espacio más claro para dos GPU

**Carga de CPU junto a la RAM del sistema.** La tarjeta CPU muestra utilización total, número de núcleos físicos e hilos lógicos y una barra de utilización instantánea por núcleo físico. Cada barra agrupa los hilos lógicos de su núcleo; el porcentaje global se pondera por procesadores lógicos. Las mediciones integradas de Windows no necesitan UAC adicional, controladores ni otra aplicación de supervisión. Las lecturas ausentes, inválidas o de más de seis segundos muestran **—** y barras de núcleo no disponibles.

**Una GPU: seis tarjetas a 1200×900.** Las cuatro tarjetas GPU, la RAM y la carga de CPU permanecen visibles juntas. **Dos GPU NVIDIA: mínimo 1920×1050.** Cada GPU tiene su bloque 2×2 de cuatro tarjetas, mediciones alineadas y todos sus controles. Separadores verticales finos delimitan las áreas GPU y la columna compartida de la derecha: RAM arriba y una tarjeta CPU más alta debajo. RAM y CPU aparecen una sola vez y no dependen de la selección de GPU. El control de la segunda GPU sigue siendo experimental.

Los tres indicadores de ventilador siguen visibles mediante el ajuste a otra línea cuando falta espacio. La lógica de control de ventiladores no cambia. Se conservan los botones rápidos compactos, la legibilidad de los procesos y todos los ajustes anteriores.

## Novedades de 1.17: RAM del sistema de un vistazo

Una quinta tarjeta **RAM del sistema** muestra memoria física usada/total en GiB, porcentaje de uso, memoria disponible y un gráfico de cinco minutos. El total corresponde a la RAM física utilizable por Windows; es memoria del sistema, separada de la VRAM y del límite de memoria comprometida con el archivo de paginación.

Las lecturas de RAM corresponden a todo el equipo y no dependen de la GPU seleccionada. Con dos paneles NVIDIA, el principal tiene cinco tarjetas y el secundario conserva sus cuatro tarjetas GPU; la RAM aparece una sola vez. Los controles GPU existentes siguen disponibles.

La RAM se actualiza con el intervalo existente y no requiere UAC. Las lecturas ausentes, inválidas o de más de seis segundos muestran **—**, dejando un hueco en el gráfico en lugar de un valor inventado.

## Novedades de 1.16: recuperación más fiable y minimización opcional en la bandeja

**La recuperación del control empieza activada en ajustes nuevos o sin este parámetro.** Se guarda por GPU y respeta una desactivación explícita anterior. La reconexión se dirige a la misma tarjeta, con pausas y finalización confirmada del cliente anterior. No concede control exclusivo frente a MSI Afterburner u otros reguladores.

**Elija cómo minimizar la ventana.** «Minimizar en la bandeja» está activado por defecto. Desactívelo para minimizar normalmente en la barra de tareas de Windows. La elección se guarda; el inicio con Windows sigue siendo independiente.

**Comunicación más fiable y estado más claro.** El plazo de las solicitudes Java pasa a 7 segundos para cubrir la ventana de respuesta de 6 segundos del canal nativo con un margen. El watchdog nativo empieza después de adquirir correctamente la GPU; mantiene su protección de 6 segundos. Los errores y datos antiguos ya no se muestran como recientes: se ocultan las RPM obsoletas y se distinguen los tiempos de espera de los cambios externos confirmados. Un registro local limitado conserva errores y metadatos de respuestas lentas sin secretos de conexión.

## Novedades de 1.15: paneles NVIDIA independientes y recuperación del control

Dos GPU NVIDIA compatibles tienen métricas propias, cuatro gráficos por GPU y ajustes independientes. **El control de la segunda GPU NVIDIA es experimental.** Una NVIDIA junto con AMD/Intel utiliza un panel NVIDIA. El selector GPU filtra la lista compartida de procesos y el historial; no cambia el destino de los reguladores.

**Los cuatro botones rápidos compactos siguen en una fila horizontal.** El menú común `⋮` permite asignar/reasignar, renombrar y borrar cada espacio, incluso si el destino ha desaparecido. El nombre personalizado se cambia sin volver a vincular; el texto se adapta al ancho y la ayuda conserva el nombre completo. Se mantienen las comprobaciones exactas de PID, hora de creación y ruta.

**La pérdida del control muestra una advertencia y un reintento manual. En 1.16 la recuperación está ACTIVADA en ajustes nuevos o sin el parámetro y se guarda por GPU; se respeta la desactivación explícita guardada.** Usa intervalos de 5/10/30/60 segundos, finalización confirmada del cliente anterior y datos recientes de la misma GPU. Las comprobaciones nativas de lease, propiedad, lectura y seguridad siguen siendo obligatorias. No puede bloquear exclusivamente MSI Afterburner u otro regulador. Ambas opciones de emergencia están DESACTIVADAS en cada inicio.

Verificado para 1.15: **2262 comprobaciones UI**, **215 nativas**, **61 de ciclo de vida/I/O de clientes**, **48 de recuperación**, **167 archivos** y **93 clases Java**. Mínimo: una GPU **1200×900**, dos paneles **1600×950**. Se conservan el cierre con consentimiento en el instalador y el inicio final marcado por defecto de 1.14.

![NVIDIA GPU panels — demonstration](images/dual-gpu-graphite.png)

## Novedades de 1.14

**1.12 – Graphite Studio:** La interfaz compacta muestra todos los 17 ajustes y doce acciones principales a 1200×900, con siete columnas, seis filas de procesos, cuatro gráficos y el historial Top 10. Los nombres de procesos usan 14 pt en negrita y alto contraste. Los perfiles nuevos usan Graphite; se conserva una selección explícita guardada de System o Graphite.

**1.13 – histéresis visible:** Se muestra el margen fijo de 4 °C. La explicación dinámica incluye ejemplos como 32→36 °C y 35→39 °C. Este cambio no modifica el algoritmo de refrigeración.

**1.14 – actualización y apertura:** Si sigue abierta la instancia JVM propia y verificada, el instalador pregunta Sí/No/Cancelar antes de cerrarla. Utiliza Windows Restart Manager con flags 0, sin forzar la terminación, y espera el cierre normal de los controladores y la liberación de archivos. No, rechazo, espera agotada o archivos bloqueados impiden actualizar. La instalación silenciosa no cierra aplicaciones automáticamente.

«Abrir VRAM GPU Desk al terminar» está **marcado por defecto** y puede desmarcarse. Un lanzador fijo permite iniciar con token Medium del mismo usuario; si ese contexto no está disponible, abra el acceso directo normal del menú Inicio. Se conserva la elección independiente de inicio con Windows.

Se verificaron 107 comprobaciones RM, 17 del lanzador y nueve casos de integración Pascal, además de los 166 archivos, 88 clases Java y arranques del paquete en rutas Unicode.

## Funciones

- Muestra VRAM física ocupada/libre, uso y temperatura GPU con gráficos históricos compactos.
- Enumera aplicaciones y servicios locales que usan memoria GPU, con búsqueda, ordenación y filtro opcional **más de 0,5 GiB**.
- Muestra las diez aplicaciones principales y «Otras» como porcentajes normalizados de las lecturas de memoria de procesos de los últimos 30 días observados. Suman 100 %; representan lecturas históricas, no un desglose aditivo de VRAM física.
- Muestra el porcentaje del tiempo observado válido de las últimas 24 horas con ocupación de VRAM física superior al 50 %. Excluye los intervalos sin supervisión.
- Exporta CSV UTF-8 a una ruta local elegida.
- Permite guardar la elección entre minimizar en la bandeja y en la barra de tareas de Windows, restaura la ventana existente al ejecutarlo de nuevo y ofrece inicio opcional con Windows.
- Ofrece temas del sistema y grafito oscuro, doce idiomas y actualización de 1–5 segundos, por defecto 2 segundos.
- Control térmico suave opcional mediante límites admitidos de potencia y frecuencia del núcleo. La protección es independiente del refresco de interfaz.
- Refrigeración en reposo, RPM e iconos animados. Los ajustes nuevos solicitan control térmico y refrigeración en reposo activados; se conserva una desactivación manual guardada. Solo muestra control activo tras confirmar la conexión.
- Puede avisar cuando la temperatura permanece estrictamente por encima del umbral elegido de 75–92 °C al menos diez segundos. Los picos breves no generan avisos.
- Opción de emergencia independiente, inicialmente desactivada, para la aplicación seleccionada expresamente. Cerrar/terminar puede perder trabajo sin guardar; se excluyen procesos protegidos o no verificables.


## Cuatro botones de acción rápida

Asigne **Cerrar aplicación** o **Terminar proceso** a uno de los cuatro botones y cambie la asignación mediante el menú `⋮` adyacente. Cada vínculo identifica únicamente la instancia seleccionada por PID, hora de creación y ruta del ejecutable. Cuando termina, no se selecciona automáticamente otro proceso ni un PID reutilizado.

El botón configurado actúa con un clic **sin confirmación adicional**. Puede perderse trabajo sin guardar. Se conservan las comprobaciones nativas de procesos protegidos, críticos o no verificables. La opción de emergencia separada empieza desactivada y mantiene su comportamiento para la aplicación elegida.

![VRAM GPU Desk — tema del sistema](images/dashboard-system.png)

## Emergencia: terminar procesos con alta carga GPU — 1.11

Una opción **separada y desactivada en cada inicio** puede terminar los procesos accesibles con alta carga de la GPU seleccionada cuando la temperatura permanece estrictamente por encima del umbral de sobrecalentamiento durante al menos **diez segundos**. El límite de carga es **20 % por defecto**, ajustable entre **10 y 100 %**; cada proceso debe mantener esa carga al menos **tres segundos**. Se mide su motor GPU más ocupado, **no la cantidad de VRAM**.

**Advertencia: puede terminar tanto aplicaciones necesarias como no deseadas y perder trabajo sin guardar.** Actúa una sola vez y se desactiva después del intento. Para otro intento debe activarse expresamente de nuevo. No puede activarse sin datos de carga de procesos confirmados y un sensor válido; los datos desconocidos o antiguos no autorizan una terminación.

Se vincula una GPU inequívoca y se vuelven a comprobar temperatura e identidad antes de actuar. PID, hora de creación, ruta EXE y el mismo identificador de proceso impiden seleccionar automáticamente un PID reutilizado. Se omiten componentes protegidos de Windows/NVIDIA, procesos críticos o no verificables y la propia herramienta. No termina árboles de procesos, no detiene servicios ni solicita más privilegios. La opción de emergencia existente para una aplicación seleccionada permanece independiente. Es una medida adicional, no una garantía contra daños GPU.

Comprobado en 1.11: 40 pruebas CPU nativas con terminaciones simuladas, 256 comprobaciones Java/catálogos/guardas, 673 comprobaciones de interfaz en 48 casos de doce idiomas y dos temas, lectura de contadores PDH reales, revisión nativa independiente, los 164 archivos y hashes de brokers, instalación/desinstalación aislada y arranque empaquetado con Java incluida en rutas Unicode.

## Objetivos de temperatura e histéresis

Umbrales distintos de parada/reinicio y esperas breves evitan cambios frecuentes ante pequeñas fluctuaciones.

| Ajuste | Comportamiento real | Motivo |
|---|---|---|
| Objetivo en reposo, **32 °C** por defecto, ajustable 28–40 °C | Tras tres segundos a 32 °C o menos en reposo, vuelve al modo AUTO del firmware. Reinicia a 36 °C, objetivo +4 °C. Con objetivo 35 °C, reinicia a 39 °C. | La histéresis de 4 °C evita arranques/paradas repetidos. El firmware AUTO decide si detener totalmente los ventiladores. |
| Reposo/carga | Hasta 10 % de uso GPU permite reposo; desde 15 % aplica la curva de carga. Entre 11–14 % conserva la clasificación anterior. Uso desconocido mantiene la refrigeración. | Evita alternar por pequeñas variaciones. |
| Objetivo térmico suave, 70–88 °C | Potencia y frecuencia cambian gradualmente según la tendencia térmica. La temperatura puede quedar por debajo o superar brevemente el objetivo. | Inercia, sensores y límites del controlador impiden un techo exacto. Es un objetivo de regulación, no un corte de emergencia. |
| Aviso de sobrecalentamiento | Lectura estrictamente superior al umbral al menos diez segundos. | Suprime picos breves. |

La temperatura de reposo **no** es el límite bajo carga sostenida. Ambiente, firmware y controlador afectan la temperatura alcanzable y los ventiladores. No utilice reguladores de ventilación o frecuencia competidores a la vez sobre la misma tarjeta.

## Hardware y requisitos

Para NVIDIA GeForce **RTX 5000 Series**. Supervisión y controles dependen de GPU y controlador; las funciones no compatibles quedan no disponibles, sin simularlas.

Windows 10/11 x64, .NET Framework 4.8 y controlador NVIDIA compatible. Java viene incluido, sin instalación separada. El usuario Windows conectado debe ser administrador con token de escritorio filtrado normal. El instalador solicita UAC una vez y coloca el componente en una carpeta Program Files fija y protegida; no admite credenciales de otro administrador. Dos tareas protegidas, solo bajo demanda, usan lanzadores fijos y comunicación local tipada. El canal instalado está diseñado para iniciar control sin más UAC; si no se autentica, queda no disponible sin intentar otra elevación.

No se restringen versiones ni hashes DLL por listas de autorización. NVML del sistema debe superar firma Windows sin conexión con firmante NVIDIA Corporation verificado, rutas seguras y API necesarias. Actualizar el driver no requiere añadir versión/hash. Puede fallar si faltan datos locales de confianza; la aplicación no descarga certificados ni controladores.

## Instalación y privacidad

1. Descargue el instalador y compare SHA-256 con [SHA256SUMS.txt](SHA256SUMS.txt).
2. Ejecute normalmente desde la cuenta administradora conectada y acepte UAC. Si hay una instancia propia abierta, elija si permite su cierre normal. El instalador espera el cierre de los controladores y archivos libres; No, rechazo, timeout o bloqueos impiden actualizar. La carpeta protegida es fija.
3. Mantenga marcado el lanzamiento al terminar o desmárquelo. Si no existe un contexto Medium adecuado, abra el acceso directo normal del menú Inicio. Seleccione GPU y compruebe el estado confirmado. Los ajustes son locales y se conservan las desactivaciones. Este lanzamiento no activa el inicio con Windows.

Usa interfaces locales Windows/GPU. No incorpora envíos de telemetría, inferencia en la nube, actualizador ni descargas de modelos en ejecución. CSV, historial y ajustes permanecen locales. Esto **no** garantiza aislamiento de red del sistema ni comportamiento de drivers externos, diagnóstico Windows o sincronización.

El instalador no está firmado. Se distribuyen binarios compilados; **el código fuente de la aplicación no se publica en este repositorio**. El bytecode Java no está cifrado ni garantiza resistencia a descompilación. Se conservan licencias del runtime externo.

Las capturas usan datos sintéticos y estado de control simulado. Ilustran la interfaz, no demuestran funcionamiento o rendimiento del hardware.

## Cambios en 1.10

- Cuatro botones configurables vinculados a una instancia para cerrar/terminar con un clic, reasignables, conservando comprobaciones nativas.
- Descripciones pequeñas y gráficos aumentados de 35 a 55 píxeles; conserva el icono de bandeja de alto contraste.
- Instalación única del componente protegido con UAC. Ajustes nuevos de temperatura/reposo activos; conserva desactivaciones manuales guardadas.
- Corrección conservadora de alias: excluye alias confirmados de pantalla indirecta sin renderizado, sin fusionar GPU físicas distintas por nombre o memoria.
- Repara instalaciones incompletas seguras e informa fase, código y HRESULT concretos si falla el componente.
- Conserva temas, doce idiomas, historial local, CSV UTF-8, identidad GPU y políticas de arrendamiento, vigilancia y restauración.

Verificado: 48 casos aislados de interfaz en doce idiomas y dos temas, iconos, valores iniciales, vínculos/ejecución de botones, comprobaciones reales de tokens CLR, rutas Unicode, los 163 archivos y hashes de brokers incluidos, instalación/desinstalación aislada y registro real elevado de tareas temporales con lectura XML/DACL, reversión y limpieza. Las tareas **no se ejecutaron**; el ensayo no llamó tareas de producción.

Las capturas son sintéticas con control simulado.

## Licencia

El uso no comercial es gratuito bajo [PolyForm Noncommercial 1.0.0](LICENSE.md), respetando sus condiciones y avisos obligatorios. El uso comercial requiere un permiso independiente. No es una licencia de código abierto; el código fuente de la aplicación no se publica. Las licencias del runtime de terceros no cambian.


![GPU × 2](images/dual-floating-monitors-dark.png)

[Fondo claro](images/floating-monitor-light.png) · [GPU × 2](images/dual-floating-monitors-light.png)

**1080p → ≈122 × 86 px · 1440p → ≈164 × 114 px · 2160p / 4K → ≈245 × 171 px**
