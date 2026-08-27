# DESIGN.md

Sistema vigente: **NATURA · Diseño con propósito, v1.0**.

Valores declarados: *diseño con sentido · claridad visual · armonía · conexión humana*.

Sustituye a la propuesta anterior. Todo color sale de una variable.

## Color

```
--na-cream  #F3EDE2   10%      --na-orange #E39A52   20%
--na-sand   #D6C2A1   20%      --na-sienna #A3572B   20%
--na-gray   #8D8274   10%      --na-olive  #6E6F4B   20%
```

### Dos derivaciones obligatorias, medidas

**1. La paleta no trae color de texto.** Ninguno de los seis alcanza el mínimo
AA de 4.5 sobre el crema:

| color | contraste sobre crema | veredicto |
|---|---|---|
| naranja `#E39A52` | 2.00 | no sirve como texto |
| arena `#D6C2A1` | 1.49 | no sirve como texto |
| gris `#8D8274` | 3.23 | solo texto grande |
| oliva `#6E6F4B` | 4.46 | solo texto grande |
| sienna `#A3572B` | 4.56 | pasa, justo |

Se deriva **`--na-ink #2E2F1F`**, un oliva muy oscuro que respeta el matiz de la
marca y da **11.68** sobre crema. El secundario es `#55563C` (6.48).

**2. El naranja nunca es texto.** Vive en rellenos, marcas e ilustración. El
texto de acento va en sienna.

### Semántica

Error en sienna, éxito en oliva, acento y llamada a la acción en naranja.
Nunca color solo: cada estado lleva su palabra.

## Tipografía

- **Títulos:** Montserrat SemiBold (600)
- **Subtítulos:** Montserrat Medium (500)
- **Cuerpo:** Lato Regular
- **Código:** el sistema no define monoespaciada; se usa la del sistema operativo
  en vez de importar una tercera familia que compita con las dos de la marca.

Montserrat no tiene rol de cursiva en este sistema: los subtítulos se distinguen
por peso, no por inclinación.

## Ilustración

Figuras geométricas planas construidas con polígonos angulares en la paleta,
sin contornos, cara sin rasgos. Motivos de apoyo: brote de dos hojas, círculo de
contorno fino, rejilla de puntos, línea de horizonte, disco solar degradado.

Tres estilos, como en el manual: **exploración** (catalejo), **conexión**
(sostiene un brote), **crecimiento** (apila bloques).

Hechas en SVG en línea, no como imágenes: escalan sin pérdida, pesan poco y
toman el color de los mismos tokens.

### Reglas de construcción aprendidas dibujándolas

Estas tres salieron de ver fallar las primeras versiones:

1. **Nunca crema sobre crema.** El fondo de página ES crema. Una manga o un
   zapato en crema simplemente desaparece, y el brazo parece amputado con la
   mano flotando. Las prendas claras van en **arena**; los zapatos en **oliva**.
2. **La mano se centra en el punto final exacto del trazo del brazo**, y el
   objeto arranca en ese mismo punto. Un par de píxeles de diferencia se lee
   como una mano suelta en el aire.
3. **El brazo trasero baja más abajo del borde del torso.** Si termina por
   encima, el torso lo tapa y solo asoma una cuchilla puntiaguda.

## Forma y movimiento

Radios 6 / 12 / 20 / 32 / píldora. Sombras suaves en tres pasos.
Transición `240ms cubic-bezier(.2,.6,.2,1)`.

## Reglas propias del proyecto

- **Altura táctil mínima 44px**, fijada con `min-height`.
- **Tema único claro**, pintado explícito.
- **Nada puede quedar invisible**: lo que se revela al hacer scroll tiene una red
  de seguridad a los 2,5s por si `IntersectionObserver` no dispara.
