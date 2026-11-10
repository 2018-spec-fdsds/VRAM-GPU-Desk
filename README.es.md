# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Supervisión local de memoria GPU y control de temperatura para Windows x64.**

Versión **1.10** · [Instalador Windows](downloads/VRAM-GPU-Desk-1.10-Setup-x64.exe) · [ZIP del instalador](downloads/VRAM-GPU-Desk-1.10-Installer.zip)

![VRAM GPU Desk — tema del sistema](images/dashboard-system.png)

## Funciones

- Muestra VRAM física ocupada/libre, uso y temperatura GPU con gráficos históricos compactos.
- Enumera aplicaciones y servicios locales que usan memoria GPU, con búsqueda, ordenación y filtro opcional **más de 0,5 GiB**.
- Muestra las diez aplicaciones principales y «Otras» como porcentajes normalizados de las lecturas de memoria de procesos de los últimos 30 días observados. Suman 100 %; representan lecturas históricas, no un desglose aditivo de VRAM física.
- Muestra el porcentaje del tiempo observado válido de las últimas 24 horas con ocupación de VRAM física superior al 50 %. Excluye los intervalos sin supervisión.
- Exporta CSV UTF-8 a una ruta local elegida.
- Se minimiza en la bandeja, restaura la ventana existente al ejecutarlo de nuevo y permite inicio opcional con Windows.
- Ofrece temas del sistema y grafito oscuro, doce idiomas y actualización de 1–5 segundos, por defecto 2 segundos.
- Control térmico suave opcional mediante límites admitidos de potencia y frecuencia del núcleo. La protección es independiente del refresco de interfaz.
- Refrigeración en reposo, RPM e iconos animados. Los ajustes nuevos solicitan control térmico y refrigeración en reposo activados; se conserva una desactivación manual guardada. Solo muestra control activo tras confirmar la conexión.
- Puede avisar cuando la temperatura permanece estrictamente por encima del umbral elegido de 75–92 °C al menos diez segundos. Los picos breves no generan avisos.
- Opción de emergencia independiente, inicialmente desactivada, para la aplicación seleccionada expresamente. Cerrar/terminar puede perder trabajo sin guardar; se excluyen procesos protegidos o no verificables.

![VRAM GPU Desk — tema grafito](images/dashboard-graphite.png)

## Cuatro botones de acción rápida

Asigne **Cerrar aplicación** o **Terminar proceso** a uno de los cuatro botones y cambie la asignación mediante el menú `⋮` adyacente. Cada vínculo identifica únicamente la instancia seleccionada por PID, hora de creación y ruta del ejecutable. Cuando termina, no se selecciona automáticamente otro proceso ni un PID reutilizado.

El botón configurado actúa con un clic **sin confirmación adicional**. Puede perderse trabajo sin guardar. Se conservan las comprobaciones nativas de procesos protegidos, críticos o no verificables. La opción de emergencia separada empieza desactivada y mantiene su comportamiento para la aplicación elegida.

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
2. Salga de la copia anterior desde la bandeja. Ejecute normalmente desde la cuenta administradora conectada y acepte UAC. La carpeta protegida es fija.
3. Abra el acceso directo nuevo, seleccione GPU y compruebe el estado confirmado. Configure controles y botones. Los ajustes son locales; las desactivaciones guardadas se conservan.

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

Verificado: 48 casos aislados de interfaz en doce idiomas y dos temas, iconos, valores iniciales, vínculos/ejecución de botones, comprobaciones reales de tokens CLR, rutas Unicode, los 163 archivos y hashes de brokers incluidos, instalación/desinstalación aislada y registro real elevado de tareas temporales con lectura XML/DACL, reversión y limpieza. Las tareas **no se ejecutaron**; el ensayo no llamó funciones de modificación GPU ni tareas de producción.

El ensayo no ejecutó el flujo completo del instalador de producción ni el control posterior GPU sin UAC. No demuestra rendimiento térmico bajo carga sostenida. Las capturas son sintéticas con control simulado.
