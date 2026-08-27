# DESIGN.md

## Estrategia de color: Committed

Un solo color saturado carga el 30 a 60% de la superficie: **naranja de seguridad
industrial**, el color del casco y del chaleco reflectivo. Elegido porque Martín viene de
construcción y porque es literalmente el color de las cosas que se están construyendo.
Referencia nombrada: un drench tipo Klim, pero en naranja de obra sobre grafito.

Rechazado a propósito: verde neón sobre negro (reflejo de primer orden para "IA") y
crema con terracota (reflejo de segundo orden, estética editorial).

Neutros tintados hacia el naranja, nunca grises puros. Sin #000 ni #fff.

```
--pitch  oklch(0.13 0.010 55)   fondo profundo
--void   oklch(0.17 0.013 55)   fondo base
--raise  oklch(0.22 0.015 55)   superficie elevada
--line   oklch(0.32 0.018 55)   filetes
--bone   oklch(0.95 0.008 75)   texto principal
--dim    oklch(0.72 0.014 65)   texto secundario
--faint  oklch(0.56 0.014 60)   etiquetas
--hi     oklch(0.70 0.190 45)   naranja de obra
--hi-deep oklch(0.56 0.165 42)  naranja presionado
```

## Tema

Compromiso deliberado con **un solo mundo visual oscuro**. Escena: alguien en el sofá,
de noche, con el celular, decidiendo si el domingo vale la pena. Todo color se pinta
explícitamente, sin depender del tema del visor.

## Tipografía

Familia única con contraste extremo de ancho y peso, en vez de un par display + body tímido.

- **Archivo** (variable, ejes wdth 62 a 125 y wght 400 a 900). Expandida y pesada para
  titulares, normal para lectura. Grotesca de señalética industrial: es la letra de un
  manifiesto de equipo, no de una revista.
- **Azeret Mono** solo para números de paso, etiquetas de dato y el bloque del prompt,
  donde el monoespaciado es literalmente correcto porque es código.

Rechazadas por reflejo: Inter, Space Grotesk, IBM Plex, Newsreader, Fraunces.

Escala fluida con clamp(), razón mínima 1.25 entre pasos.

## Layout

Rejilla estricta y visible como voz, no composición asimétrica. Filetes de un píxel que
se ven, estaciones numeradas, alineación a línea base compartida. La página se lee como
un documento de obra: ordenado, medido, con consecuencia.

## Movimiento

Una sola secuencia de entrada escalonada. Curvas ease-out exponenciales, sin rebote.
Respeta prefers-reduced-motion.
