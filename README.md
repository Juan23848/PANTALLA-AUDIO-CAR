# PANTALLA-AUDIO-CAR

Proyecto experimental para mejorar una pantalla **Toguard RC04** (CarPlay /
Android Auto portátil, 7", 1024×600) instalada en una camioneta con estéreo
original sin Bluetooth.

## El problema

Con Android Auto conectado, el audio sale siempre por el parlante interno de
la pantalla y la opción **FM queda deshabilitada** en el menú. El estéreo de
la camioneta no tiene Bluetooth, así que el FM es la única vía para que el
sonido llegue a los parlantes del vehículo. El soporte del fabricante ya no
responde (equipo con más de dos años).

## El plan

- **Camino A — hackear la pantalla:** identificar el hardware, hacer backup
  completo de la memoria flash, analizar el firmware y forzar el encendido del
  transmisor FM.
- **Camino B — transmisor FM propio:** ESP32 + módulo transmisor (QN8027 /
  KT0803L) alimentado desde la salida de audio de la pantalla, con firmware
  propio en este repo.

El propietario del equipo asume el riesgo del experimento. Regla de oro del
camino A: **nada se escribe en la pantalla sin un backup completo verificado
de la flash.**

## Documentación

- [`docs/hardware.md`](docs/hardware.md): lo que sabemos del hardware hasta ahora.
- [`docs/firmware.md`](docs/firmware.md): versión, plataforma T86 y vía de actualización por microSD.
