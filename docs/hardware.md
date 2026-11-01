# Hardware de la Toguard RC04

Estado: **reconocimiento inicial**, a partir de fotos. Lo marcado como
"probable" está sin confirmar hasta leer las inscripciones de los chips.

## Datos del fabricante

- Pantalla 7", 1024×600, táctil capacitiva.
- CarPlay y Android Auto inalámbricos (Bluetooth 5.1 + WiFi).
- Salidas de audio: parlante interno, AUX (3,5 mm), transmisor FM.
- Alimentación 12–24 V por encendedor.
- Panel LCD: etiqueta `SH0721S150-07ID521-88`, fecha 2023-03-22.
- Número de serie: `202305301829RC04 DXXXX`.

## Placa principal: lado A (`fotos/02-placa-lado-a.jpg`)

| Zona | Qué se ve | Interpretación |
|---|---|---|
| Arriba izquierda | Conector USB-C, serigrafía `MIPI` / `屏幕` ("pantalla") | Alimentación/datos; el conector de panel MIPI está cerca |
| Arriba derecha | Ranura microSD | **Posible vía de actualización de firmware** |
| Izquierda, centro | Chip de 8 patas (SOIC-8) | **Probable memoria flash SPI**: objetivo del backup con CH341A |
| Centro (recuadro blanco) | Grilla densa de vías, sin chip grande | El **procesador (SoC) está del otro lado** de la placa |
| Abajo izquierda | Módulo con blindaje metálico, 34 pines | Módulo WiFi/Bluetooth |
| Abajo izquierda | Conector `像头` (de `摄像头`, "cámara") | Entrada de cámara (función desactivada por el fabricante) |
| Abajo centro | Pads `按键` ("botón") `KEY+` / `KEY-` con cables rojo/negro | Botón o parlante (a confirmar) |
| Abajo derecha | Pads `电池` ("batería") `−` `+` | Entrada de alimentación/batería |
| Derecha | Chip QFN chico junto a un cristal | Candidato a chip de FM o códec de audio |
| Izquierda y derecha | Cinta negra tapando componentes | Hay que despegarla para ver qué esconde |

## Pendiente

- [ ] Fotos del **lado B** de la placa (donde está el procesador).
- [ ] Primeros planos legibles de: procesador, chip de 8 patas, chip QFN
      junto al cristal, módulo WiFi.
- [ ] Ver qué hay debajo de las cintas negras.
- [ ] Buscar pads de puerto serie (grupos de 3–4 pads: `TX`, `RX`, `GND`, `3V3`).
- [ ] Identificar el chip transmisor de FM y su antena.
