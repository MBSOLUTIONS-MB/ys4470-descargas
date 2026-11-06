# YS-4470 · Firmware MB + MB Meter

Firmware alternativo para el multímetro y fuente **YS-4470**, y **MB Meter**, su programa para Windows.
Pensado para el banco de reparación de teléfonos: medir, ver el consumo al encender y comparar una placa buena contra una mala.

**Versión actual:** firmware MB 0.9.9 · MB Meter 0.2.0

<p align="center"><img src="img/eq_inicio.png" width="640" alt="Pantalla de Inicio del equipo con seis funciones"></p>

## Descargar

1. Entra a **[Releases](https://github.com/MBSOLUTIONS-MB/ys4470-descargas/releases/latest)** (no hace falta cuenta).
2. Descarga `MB-Meter_x.y.z_x64-setup.exe` y ejecútalo (Windows 10/11).
3. Abre MB Meter. Si tu equipo todavía tiene el firmware de fábrica, sigue los pasos de abajo para instalar el firmware MB.

Las siguientes versiones llegan solas: MB Meter avisa cuando hay una nueva, del programa o del firmware.

## Instalar el firmware MB en el equipo

### La primera vez (equipo con el firmware de fábrica)

El firmware de fábrica no se comunica con MB Meter, así que la primera vez se graba en **modo FEL**. Se hace una sola vez y tarda unos 5 minutos.

1. Abre MB Meter y entra a **Rescate (FEL)** (tecla F9).
2. Si el instalador no puso el driver FEL, pulsa **Instalar driver FEL…** una vez.
3. **Desconecta y apaga** el multímetro.
4. **Mantén apretado el botón de atrás**, el que está encima del USB «Power Equipment». Sin soltarlo, conecta el USB a la PC y enciende el equipo. Suelta el botón a los 2 o 3 segundos.
5. **La pantalla se queda apagada:** es normal, así es el modo FEL. Cuando MB Meter lo detecta, el botón cambia de «Grabar (esperando equipo)» a «Grabar».
6. Elige **Firmware MB más reciente** y deja marcada la **copia completa de la flash** (16 MB, unos 3 min). La primera vez la copia es obligatoria: con ella siempre puedes volver al firmware original.
7. Pulsa **Grabar**. MB Meter graba, relee y comprueba. No desconectes el cable mientras graba.
8. Cuando diga «Listo», desconecta el USB y enciende el equipo normal. Debe mostrar **FW MB 0.9.9**.

La copia queda en `Documentos\MB Meter\Respaldos`. Guárdala: es única de tu equipo.

### Las siguientes veces (por USB, sin modo FEL)

1. Enciende el equipo normal y conéctalo por USB.
2. En MB Meter entra a **Actualizar** (F8). Si hay versión nueva, pulsa **Actualizar por USB**. Si tienes un archivo, usa **Desde un archivo .bin…**.
3. MB Meter envía el firmware y lo comprueba completo.
4. Cuando el equipo pregunte **«¿Actualizar firmware?»**, pulsa **OK** en el multímetro.
5. El equipo instala en unos 10 segundos y se reinicia solo con la versión nueva.

No apagues ni desconectes el equipo mientras instala.

### Si algo sale mal

- **El equipo no arranca:** vuelve a grabarlo en modo FEL con los pasos de «La primera vez».
- **Quieres el firmware original:** en **Rescate (FEL)** elige **Volver al firmware original**. Se graba desde tu copia y no toca la serie ni los ajustes del equipo.
- **Falla una actualización por USB:** el paso exacto queda anotado en `%APPDATA%\com.mbsolutions.mbmeter\actualizacion.log`.

## El firmware en el equipo

**Inicio con seis funciones, sin menús perdidos.** F1 a F6 directo con tecla o tocando la tarjeta.

| | |
|---|---|
| <img src="img/eq_main.png" alt="Pantalla de medida"> | **Multímetro (F1).** V DC, V AC, Ω, continuidad, diodo y capacidad. Número grande, barra de escala y debajo mínimo, máximo y promedio: ves si la lectura es estable sin anotar nada. |
| <img src="img/eq_fuente.png" alt="Fuente principal"> | **Fuente principal (F2).** Voltaje y corriente que toma la placa. Si la corriente se sale de rango marca **«OL»** en vez de un número falso: señal de corto. Alarma de voltaje configurable, ahora también en 2.00 V. |
| <img src="img/eq_grafica.png" alt="Gráfica de encendido"> | **Análisis de encendido (F3).** La curva de consumo al prender: pico, voltaje y tiempo en vivo. Una placa en corto, que no arranca o que se reinicia se reconoce por su curva. |
| <img src="img/eq_carga.png" alt="Carga PD"> | **Carga PD (F4).** USB-C o USB-A: V, A, W y mAh acumulados. |

También: **Historial (F5)** con las mediciones guardadas y **Ajustes (F6)** con tema de color, sonido, brillo y calibración.

## MB Meter en la PC

<p align="center"><img src="img/pc_vivo.png" width="760" alt="MB Meter, pantalla En vivo"></p>

**En vivo.** El equipo en grande en tu PC. Cambias de función en el equipo y el programa cambia solo. Suma tiempo, mAh y Wh, y tiene ventana flotante para dejarla encima de otros programas.

<p align="center"><img src="img/pc_comparar.png" width="760" alt="Comparar placas"></p>

**Comparar placas.** Mides una placa buena y luego la que falla, en el mismo orden. El programa marca qué puntos son iguales, cuáles se salen de tolerancia y cuáles están en corto o abiertos. Guarda solo cuando la lectura se estabiliza, y la tolerancia se ajusta por función, de 0.5 % a 50 %.

<p align="center"><img src="img/pc_encendido.png" width="760" alt="Análisis de encendido en MB Meter"></p>

**Análisis de encendido.** Compara la curva de una placa contra la de una placa buena del mismo modelo, guardada antes.

<p align="center"><img src="img/pc_carga.png" width="760" alt="Log de carga"></p>

**Log de carga.** Toda la carga registrada, con las líneas CC1, CC2, D+ y D− y el protocolo negociado (por ejemplo USB PD 9 V). Se guarda como CSV o imagen.

Además: **Historial**, **Reportes** para el cliente, **Actualizar** y **Rescate (FEL)**.

## Actualizar y rescatar sin miedo

- **Por USB, desde MB Meter.** El archivo se envía y se comprueba completo antes de tocar nada. El equipo no se graba hasta que pulses **OK** en él. Cada bloque se graba, se relee y se reintenta si falla.
- **Copia de seguridad.** La primera vez que grabas, MB Meter guarda la memoria entera del equipo (16 MB) en Documentos. Con esa copia siempre puedes volver al firmware de fábrica.

El logo de arranque de fábrica no se cambia; si quieres uno propio, se pone desde MB Meter.

## Novedades de esta versión

- Actualización por USB confiable: reintenta cada bloque y lo comprueba; si algo falla queda anotado en `%APPDATA%\com.mbsolutions.mbmeter\actualizacion.log`.
- Ya no se queda pitando al instalar.
- Un solo instalador con programa, herramienta de grabado, driver opcional y firmware.

## Aviso

**No uses salidas de 19–23 V con teléfonos.** Revisa el voltaje antes de conectar una placa.

---
MB.SOLUTIONS · Servicio Técnico Especializado
