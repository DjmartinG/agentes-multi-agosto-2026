# DESIGN.md

Sistema vigente: **CG — Experimentos Diseños, v1.0 (agosto 2026)**.

Este archivo ya no describe una propuesta propia. Los tokens de abajo son copia
literal del sistema de la marca. Toda decisión visual sale de aquí; ningún color
suelto en el código.

Valores declarados por el sistema: *diseño con sentido · claridad visual · calma ·
respaldo humano*.

## Color

```
--cg-cream #F7F1E5   --cg-sand  #EFE4D2   --cg-beige #E8D9C1   --cg-white #FFFFFF
--cg-orange #E39A54  --cg-orange-soft #EDBB85  --cg-sienna #A8502E
--cg-olive  #6E7147  --cg-olive-soft  #9A9C6E  --cg-warm-gray #8C8175
--cg-ink    #362E25  --cg-ink-soft    #6E6155  --cg-line   #E2D6C1
```

Proporciones de uso que fija el sistema: crema 44%, arena 18%, beige 14%,
naranja 12%, oliva 8%, sienna 4%. El crema domina; el naranja y el sienna son
acentos, no fondos.

### Restricciones de contraste (medidas, no estimadas)

Estas dos reglas no están en el sistema pero se derivan de él y son obligatorias:

- **`--cg-orange` no se usa nunca como texto.** Da 2.07 sobre crema y 2.33 sobre
  blanco, muy por debajo del mínimo AA de 4.5. Falla incluso en texto grande.
  Su lugar es el relleno: botones, barras, marcas. El texto de acento va en
  **sienna** (4.85 sobre crema). Sobre relleno naranja, el texto va en tinta (5.73).
- **`--cg-warm-gray` solo cumple en texto grande** (3.39 sobre crema). Las
  etiquetas pequeñas usan `--text-muted` (5.33).

Pares seguros de un vistazo: tinta/crema 11.86 · tinta-suave/crema 5.33 ·
sienna/crema 4.85 · oliva/crema 4.54 · crema/sienna 4.85 · tinta/naranja 5.73.

### Semántica

Error y alerta en **sienna**. Éxito y confirmación en **oliva**. Acento y
llamada a la acción en **naranja**. Nunca color solo: cada estado lleva también
su palabra.

## Tipografía

- **Títulos:** Newsreader SemiBold (600)
- **Subtítulos y entradillas:** Newsreader Italic
- **Cuerpo:** Hanken Grotesk Regular
- **Código:** el sistema no define monoespaciada. Se usa la del sistema operativo
  (`ui-monospace, SFMono-Regular, Menlo, Consolas`) en vez de importar una tercera
  familia que compita con las dos de la marca.

## Forma y profundidad

Radios 6 / 12 / 20 / 32 / píldora. Sombras suaves en tres pasos.
Transición `240ms cubic-bezier(.2,.6,.2,1)`.

## Reglas propias del proyecto

- **Altura táctil mínima 44px**, fijada con `min-height`, no por suma de padding.
  El público objetivo lee en celular.
- **Tema único claro.** El sistema declara `color-scheme:light`; todo color se
  pinta explícito, sin depender del tema del visor.
- **Nada puede quedar invisible.** Lo que se revela al hacer scroll arranca en
  opacidad cero; si `IntersectionObserver` no dispara, un temporizador de 2,5s
  lo muestra igual.
