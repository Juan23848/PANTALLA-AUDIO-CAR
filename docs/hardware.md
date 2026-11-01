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

## Placa principal: lado A sin cinta (`fotos/03-placa-lado-a-sin-cinta.jpg`)

Misma cara que la foto 02, rotada y sin las cintas negras. Se agrega:

| Zona | Qué se ve | Interpretación |
|---|---|---|
| Abajo izquierda | Jack negro de 3,5 mm | Salida **AUX** |
| Arriba derecha | Conector de antena tipo `U.FL` con cable fino | Antena del módulo WiFi/BT (o del FM, a confirmar siguiendo el cable) |
| Izquierda | Conector `TP` | Táctil (touch panel) |
| Izquierda | Conector blanco de 2 pines con cables rojo/negro | Parlante interno |
| Izquierda | Chips chicos de 8–10 patas junto al conector del parlante | Probable amplificador de audio |
| Arriba izquierda | Fila de ~8 pads dorados | **Candidatos a pads de prueba/programación** |
| Izquierda | Círculo serigrafiado vacío | Lugar para pila de botón (no montada) |

## Placa principal: lado B (`fotos/04-placa-lado-b-t86.jpg`)

- Serigrafía: **`T86_V213` / `2022-11-01`**. Es el nombre de la placa: una placa
  genérica que varios vendedores usan para estas pantallas.
- Casi toda la cara está cubierta por una **lámina negra grande** (térmica o
  blindaje). Debajo está, con mucha probabilidad, el **procesador (SoC)**: coincide
  con la grilla de vías que se ve del lado A.
- Etiqueta blanca vertical a la derecha con texto ilegible en la foto.
- Borde inferior: **fila de 5–6 pads dorados** → buen candidato a **UART**.
- Arriba derecha: pulsador chico rodeado de 4–5 pads → posible botón de
  **recovery/boot** o de reset.
- Arriba: segundo jack de 3,5 mm y otro USB-C.
- Fuera de la placa: placa verde angosta con cables rojo/negro (¿micrófono o
  antena FM?) y el parlante.

## Pendiente

- [ ] Prueba de los botones de borde con el USB-C conectado a la PC (ver guía).

- [ ] Primeros planos de la **fila de 5–6 pads** del borde inferior del lado B
      y de los pads alrededor del pulsador.
- [ ] Leer la **etiqueta blanca** del lado B.
- [ ] Levantar con cuidado una esquina de la **lámina negra** para leer el procesador.
- [ ] Primer plano del chip de 8 patas (lado A) y del chip chico con cristal.

## Antenas (`fotos/05-antena-wifi-2.4-5.8ghz.jpg`)

- El cable negro fino con ficha `U.FL` (junto al módulo blindado del lado A) va a
  una antena plana pegada en la carcasa, con la inscripción **`2.4/5.8GHZ`**
  (se lee espejada en la foto). Es la **antena WiFi doble banda**: por ahí viaja
  Android Auto inalámbrico (WiFi 5 GHz). **No es el FM.** No desconectarla.
- Una antena de FM (88–108 MHz) necesita un conductor mucho más largo. Candidatos:
  una pista de la placa, un contacto a resorte contra la carcasa, o el propio
  cable de alimentación (muchos transmisores FM baratos lo usan como antena).

## Placa verde y botones de borde (`fotos/06-botones-de-borde.jpg`)

- Los cables rojo/negro de la **placa verde** terminan en los pads `KEY+` / `KEY-`
  (`按键` = "botón"). La placa verde es la **botonera física** del borde de la
  carcasa. **No es la antena FM** (descartado).
- Hay **dos pulsadores laterales soldados en los bordes de la placa** que no
  coinciden con ningún botón de la carcasa:
  1. Arriba, al lado de los pads `KEY+`/`KEY-`.
  2. Borde izquierdo, entre el conector `TP` y el cuadrado dorado que está junto
     al jack AUX.
- Botones así, sin acceso desde afuera, suelen ser de fábrica: **reset** y
  **boot/recovery** (mantenerlo apretado al encender pone al procesador en modo
  de grabación por USB). Si uno es boot, al enchufar el USB-C a una PC en ese
  modo aparece un dispositivo cuyo **VID/PID identifica la marca del
  procesador** sin soldar nada.
- El cuadrado dorado grande junto al jack AUX podría ser un contacto a resorte
  (¿antena?) o un pad de masa. A confirmar.

## Interfaz del equipo (`fotos/07-pantalla-principal-alimentada-por-usb-pc.jpg`)

- **Arranca alimentada solo desde un USB de PC** (5 V), hasta la pantalla principal.
- Pantalla principal (en español): reproductor ("No jugar" = nada sonando),
  **Apple CarPlay**, **Android Auto**, **AirPlay** y **"Salida de audio"**.
- Barra superior: íconos **FM**, WiFi (punto de acceso) y Bluetooth.
- Barra inferior: apagar, brillo, parlante/teléfono, **FM**, configuración.
- **Dato clave:** sin celular conectado, el FM aparece **disponible** en la
  pantalla principal. El bloqueo aparece cuando entra Android Auto. Es decir, es
  una decisión del firmware durante la sesión de Android Auto, no una falla del
  chip de FM.
