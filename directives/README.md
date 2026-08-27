# directives/ — Capa 1: Directivas (Qué hacer)

SOPs en Markdown. Cada archivo es el conjunto de instrucciones de un flujo.

**Un archivo por flujo**, nombrado en `snake_case`: `scrape_website.md`, `enrich_company.md`.

## Estructura mínima de una directiva

```markdown
# <Nombre del flujo>

## Objetivo
Qué logra este flujo y cuándo se usa.

## Entradas
Qué necesita para arrancar (archivos, parámetros, credenciales).

## Herramientas / Scripts
Qué script de `execution/` ejecuta cada paso, en qué orden.

## Salidas
Qué produce y dónde lo deja (normalmente `.tmp/`).

## Casos extremos
Errores conocidos, rate limits, tiempos esperados, qué hacer cuando falla.
```

## Reglas

- Las directivas son **documentos vivos**: se actualizan con lo aprendido (rate limits reales, gotchas, tiempos).
- **No crear ni sobrescribir una directiva sin preguntar**, salvo instrucción explícita del usuario.
- Si un aprendizaje aplica a todo el sistema y no a un flujo puntual, va al *Registro de aprendizajes* de `CLAUDE.md` / `AGENTS.md` / `GEMINI.md`.
