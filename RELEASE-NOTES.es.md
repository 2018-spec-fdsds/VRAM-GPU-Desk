# VRAM GPU Desk 1.24

## Novedades de 1.24 — período de 60 días y activación del dispositivo sin conexión

**Corregidos la ruta del estado protegido y el inicio del control.** El estado de activación usa la carpeta canónica de datos de Windows para todo el equipo, también al iniciarse mediante una tarea programada con un entorno mínimo. Se evita así un error de ruta relativa y permisos que podía bloquear el control nativo de la GPU. Se mantienen las comprobaciones de propietario, acceso y recuperación; no se obtiene control exclusivo frente a otras utilidades de GPU.

**60 días desde el primer inicio compatible en este equipo.** El período comienza cuando una edición con activación se ejecuta por primera vez en el dispositivo; no se basa en registros antiguos no verificados. La fecha inicial local protegida se conserva en las actualizaciones normales y al desinstalar y reinstalar. Actualizar por sí solo no reinicia los 60 días ni detiene los avisos tras el vencimiento.

**Avisos sin restricciones funcionales.** Al terminar el período, todas las funciones siguen disponibles. Mientras se ejecuta la aplicación aparece, al menos una vez por hora, un aviso localizado y no modal sobre las ventanas normales de Windows. Entonces se muestra la casilla Activación. Abrir o cerrar el diálogo no desactiva el control de GPU, la refrigeración, la supervisión ni las acciones sobre procesos.

**Solicitud y respuesta sin conexión de 20 caracteres.** Abre Activación, genera una solicitud del dispositivo y guarda el código de 20 caracteres en un TXT UTF-8. El propietario utiliza un generador privado para crear una respuesta de 20 caracteres vinculada a esa identidad. Introduce la respuesta en la aplicación: una clave válida detiene los avisos. Si cambia la identidad del equipo, puede ser necesaria otra respuesta; el período original no se reinicia.

**Estado local y emisor privado.** La solicitud es un código opaco derivado del dispositivo; el proceso de activación no sube el HWID a Internet. El generador y el archivo de clave maestra del propietario no se publican. La verificación compacta sin conexión no garantiza protección contra ingeniería inversa o modificación de la aplicación. Se conservan los ajustes guardados, el control térmico y de refrigeración y la inversión de campos System/Graphite.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.24-Setup-x64.exe) · [ZIP](downloads/VRAM-GPU-Desk-1.24-Installer.zip)

# VRAM GPU Desk 1.23

## Novedades de 1.23 — campos numéricos compactos y contraste coherente

**Siete campos numéricos con botones horizontales −/+.** Objetivo de temperatura, umbral de aviso de sobrecalentamiento, objetivo de refrigeración en reposo, porcentaje mínimo de ventiladores, umbral de carga GPU de emergencia, intervalo de actualización y escala del overlay comparten campos compactos con unidades integradas y un fino acento de color. Se conservan la entrada por teclado y los límites dinámicos del modelo, incluidos los límites comunicados por el hardware.

**Entradas coherentes en ambos temas.** Los selectores de idioma, tema y GPU, la búsqueda y el editor de botones rápidos siguen el mismo estilo. System usa fondo blanco y texto oscuro en los campos; Graphite usa fondo oscuro y texto claro. El foco, los estados seleccionado y desactivado y las listas desplegables siguen el tema activo.

**Umbrales configurados más altos, más visibles.** El objetivo de temperatura gradual se muestra en rojo **por encima de 80 °C, desde 81 °C**; el umbral de aviso de sobrecalentamiento, **desde 86 °C**. El color describe el **umbral configurado**, no la temperatura actual de la GPU ni una alarma de temperatura activa. No cambian los algoritmos de control, los valores predeterminados de objetivo/aviso de 78/85 °C ni las preferencias guardadas. Se conservan la recuperación continua, el registro y las etiquetas de corriente máxima de contacto o total del conector de la versión 1.22.

[System — campos claros](images/temperature-fields-light.png) · [Graphite — campos oscuros](images/temperature-fields-dark.png)

Windows x64 EXE — `VRAM-GPU-Desk-1.23-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.23-Installer.zip`

# VRAM GPU Desk 1.22

## Novedades de 1.22 — recuperación continua, registro y corriente de fuente más clara

**Recuperación continua del control.** Mientras esté activada la recuperación forzada, los intentos comprobados continúan sin límite de cantidad: tras 5, 10, 30 y después cada 60 segundos. La última elección ACTIVADO/DESACTIVADO se conserva durante la parada y el reinicio del controlador. El aviso no modal de pérdida se cierra automáticamente solo cuando la telemetría reciente confirma la recuperación. Se mantienen las comprobaciones de propiedad, cierre del cliente anterior y límites del hardware; esto no proporciona control exclusivo frente a MSI Afterburner u otros reguladores.

**Registro de la aplicación.** Un botón independiente abre los eventos de pérdida, recuperación e intentos de control por GPU, junto con los estados iniciales y cambios de todas las casillas relacionadas con el control. Cada entrada incluye hora UTC y local. La temperatura se registra desde **78 °C**, con los cambios posteriores en grados enteros y el regreso por debajo de 78 °C. El visor muestra hasta 500 eventos de la sesión actual. Los archivos UTF-8 permanecen en `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`, con rotación a 2 MiB y cinco archivos de respaldo.

**Corriente máxima de contacto o total del conector.** Para cada uno de hasta dos puertos físicos de alimentación GPU de la fuente, la tarjeta muestra el máximo de las corrientes individuales disponibles si se conoce al menos una, incluso con datos incompletos. Si no hay lecturas individuales, muestra la corriente total medida del conector. Las etiquetas distinguen explícitamente **máximo** y **total**. Los sensores desconocidos siguen mostrando —; un cero medido sigue siendo cero. Las ayudas conservan las lecturas individuales y el total disponibles. La corriente de un raíl no sustituye la medición de un conector.

**Actualización desde una instalación antigua 1.9.** Una copia en LocalAppData puede seguir ejecutándose aunque 1.22 esté instalada correctamente en Program Files, mostrando la interfaz antigua sin opciones nuevas. Antes de instalar, salga de la copia antigua mediante el menú de la bandeja; después use el acceso directo actual del menú Inicio y compruebe **v1.22**. Si un acceso directo aún apunta a la carpeta antigua, abra la copia instalada en Program Files y corríjalo. Una ventana antigua abierta no significa que se hayan eliminado las opciones nuevas.

Windows x64 EXE — `VRAM-GPU-Desk-1.22-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.22-Installer.zip`

# VRAM GPU Desk 1.21

## Novedades de 1.21 — fuente de alimentación opcional y contraste automático

**Diseño opcional.** Si la supervisión está desactivada o no se detecta una fuente compatible, su tarjeta se oculta y las demás aprovechan el ancho disponible, sin dejar un espacio vacío. Una vez detectada la fuente, si las lecturas dejan de estar disponibles temporalmente, su tarjeta permanece con guiones.

**Panel más compacto.** Se ha retirado la tarjeta «Tiempo con VRAM > 50 %» de las vistas de una y dos GPU. Se conservan la clasificación de aplicaciones de 30 días y el historial guardado.

**La supervisión de la fuente está desactivada de forma predeterminada.** Una casilla independiente añade una tarjeta con la potencia de salida disponible y la corriente de hasta dos conectores reales de alimentación de GPU. Los datos ausentes o antiguos muestran —; las corrientes de los raíles no se presentan como corrientes de conectores individuales. El componente protegido de solo lectura se instala con la configuración UAC única de la aplicación y no adquiere el control de la GPU.

**La compatibilidad depende del modelo.** Se verificó la lectura en MSI MPG Ai1300TS. Ai1600TS está cualificada por su protocolo. Algunos Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS y, adicionalmente, NZXT E superaron pruebas sintéticas; queda pendiente la validación física. Corsair aporta vatios medidos, el total de Thermaltake se marca como calculado y NZXT aporta raíles sin inventar un total. Se investigó be quiet! Dark Power Pro 14 IO; no hay lector cualificado para Seasonic OptiGuard ni ASUS. No se declara compatibilidad universal con seis marcas. Véase [compatibilidad de fuentes](docs/psu-compatibility.md).

**El contraste automático del texto está activado por defecto.** El texto se adapta al fondo; desactive la opción para elegir manualmente texto claro u oscuro. Se conservan la transparencia, indicadores compactos, dos superposiciones NVIDIA independientes, doble clic para abrir la ventana, posiciones y colores/sonidos de temperatura.

Las capturas en grafito utilizan datos sintéticos, incluidos los de la fuente. Se mantienen los ajustes GPU, acciones de procesos, modos de emergencia y preferencias guardadas.

Windows x64 EXE — `VRAM-GPU-Desk-1.21-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.21-Installer.zip`
