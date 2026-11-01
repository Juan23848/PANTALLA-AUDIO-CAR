# Firmware de la RC04

## Lo que muestra el equipo (`fotos/09-version-de-firmware.jpg`)

| Campo | Valor |
|---|---|
| Versión | `20230607` |
| Configuración | `M28_CPAPAA_V200B` |
| Número de serie | `30671d4e0145c0810000bc0000000000` |
| Parámetro | `dDg2cG5kfDIwMjMwNjA2fGhkMgoA` |

El "Parámetro" es texto en **base64**. Decodificado:

```
t86pnd|20230606|hd2
```

- `t86` → familia de placa **T86** (coincide con la serigrafía `T86_V213`).
- `pnd` → variante "PND" (pantalla portátil, *portable navigation device*).
- `20230606` → fecha de compilación.
- `hd2` → probablemente perfil de pantalla/hardware.
- `CPAPAA` en la configuración → **C**ar**P**lay + **A**ndroid **A**uto
  (otras variantes de la familia usan `CPAPAAMC`).

## Menú "Salida de audio" (`fotos/08-menu-salida-de-audio.jpg`)

Cuatro opciones: **Altavoz**, **Carplay/Auto** (ícono Bluetooth), **FM** y **AUX**.
La pantalla FM permite elegir la frecuencia (en la foto: 106.9 MHz).

## La familia T86 en internet

- Hay pantallas de otras marcas con la misma familia (`T86PND`, `T86B1`,
  `T86MP5`) y configuraciones parecidas (`M28_CPAPAAMC`, `M35_CPAPAAMC`).
- **Se actualizan por microSD**: se copia un archivo `.img` a la tarjeta, se
  enciende la pantalla y aparece una barra de progreso verde. Se recomienda
  apagar WiFi/Bluetooth del celular para que no entre CarPlay/Android Auto
  durante la actualización.
- Ejemplo de nombre de archivo de la familia (de otro fabricante, **no
  compatible con la RC04**):
  `T86BA_PND_1026_1600X600M35_CPAPAAMC_20240123_V1_MS_GLYHWIFIMC 2.img`.
  El nombre codifica placa, variante, resolución (`1600X600`), configuración y fecha.
- Advertencia de la comunidad: un `.img` de una variante distinta puede **no
  ser compatible** aunque la placa se llame parecido. Para la RC04 hay que
  buscar algo con `M28`, `CPAPAA` y resolución `1024X600`.

Fuentes: hilo de XDA "T86B1 Wireless Android Auto / Carplay Display Firmware
Flash", guía de actualización de Team 1EV / EV Sportline, manuales T86PND y
T86MP5 en manuals.plus / device.report.

## Plan con el firmware

1. Conseguir un `.img` de la familia T86 lo más parecido posible
   (`M28` / `CPAPAA` / `1024X600`).
2. **Desarmarlo y analizarlo acá** (sin grabarlo todavía): ver su formato,
   si está firmado, dónde vive la lógica que fuerza la salida a "Altavoz"
   durante Android Auto, y qué controla el chip de FM.
3. Recién con eso, decidir: grabar una versión más nueva tal cual, o una
   versión modificada que deje el FM activo durante Android Auto.
