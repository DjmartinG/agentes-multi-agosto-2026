# execution/ — Capa 3: Ejecución (Hacer el trabajo)

Scripts de Python **deterministas**. Sin LLMs adentro: acá vive la lógica que debe dar el mismo resultado siempre.

## Convenciones

- Un script = una responsabilidad. Nombre en `snake_case`: `scrape_single_site.py`.
- **Antes de escribir un script nuevo, revisar si ya existe uno** que sirva.
- Argumentos por CLI (`argparse`), no valores hardcodeados.
- Secretos desde `.env` (`python-dotenv`), nunca en el código.
- Salidas a `.tmp/`, en JSON o CSV.
- Exit code `0` en éxito, distinto de `0` en error, con el mensaje a `stderr`.
- Rutas con `pathlib.Path` — el workspace tiene espacios en el nombre y romperá cualquier concatenación cruda de strings.

## Plantilla

```python
"""<Qué hace este script en una línea>."""
import argparse, json, sys
from pathlib import Path
from dotenv import load_dotenv

TMP = Path(__file__).resolve().parent.parent / ".tmp"

def main() -> int:
    load_dotenv()
    parser = argparse.ArgumentParser(description=__doc__)
    parser.add_argument("--out", type=Path, default=TMP / "output.json")
    args = parser.parse_args()

    TMP.mkdir(exist_ok=True)
    # ... trabajo determinista ...
    return 0

if __name__ == "__main__":
    sys.exit(main())
```
