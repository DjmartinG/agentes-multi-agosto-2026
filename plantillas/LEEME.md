# Permisos de Claude Code para la clase

## Qué resuelve

Por defecto Claude Code pide permiso antes de cada acción. Eso está bien para
el uso diario, pero en una clase de una hora significa que cada persona pasa
la sesión haciendo clic en "permitir" en vez de mirando lo que pasa.

`settings-clase.json` deja preaprobado todo lo que el agente necesita para el
ejercicio, y bloquea lo que nunca debería hacer.

## Cómo se instala

Se copia como `.claude/settings.json` **dentro de la carpeta del ejercicio**.

```bash
mkdir -p .claude
cp plantillas/settings-clase.json .claude/settings.json
```

La palabra importante es **dentro**. Los permisos de un `settings.json` de
proyecto solo aplican en esa carpeta. El agente se mueve con libertad ahí y en
ningún otro lugar del computador. Si alguien abre Claude Code en `Documentos` o
en el escritorio, vuelve a pedir permiso para todo, como debe ser.

## Qué queda permitido

- Leer, escribir y editar archivos del proyecto, sin preguntar (`acceptEdits`).
- Ejecutar Python, pip, node, npm, git y el CLI de monid.
- Comandos de navegación y lectura: `ls`, `dir`, `cat`, `mkdir`, `cp`, `mv`.
- Buscar y leer páginas web.

## Qué queda bloqueado

Estas reglas ganan siempre, incluso si el agente las pide:

- Borrado masivo (`rm -rf /`, `rm -rf ~`), formateo de disco, `diskpart`.
- Elevación de privilegios: `sudo`, `runas`.
- Apagado del equipo, borrado de registro de Windows.
- Descargar y ejecutar directamente desde internet (`curl ... | bash`,
  `iwr ... | iex`), que es el patrón clásico de infección.
- Leer secretos: `.env`, llaves SSH, credenciales de AWS, `credentials.json`,
  `token.json`.

## Lo que NO recomiendo

Existe un modo que quita todos los frenos de una vez:

```json
{ "permissions": { "defaultMode": "bypassPermissions" } }
```

También está la bandera `claude --dangerously-skip-permissions`. El nombre lo
dice todo: el agente ejecuta cualquier cosa, en cualquier carpeta, sin
preguntar ni una vez.

**No lo pongas en los computadores de la clase.** Son máquinas de trabajo con
correo corporativo, contratos y datos de clientes. Un agente sin frenos que
malinterpreta una instrucción, o que lee una página web con instrucciones
maliciosas escondidas, puede borrar o filtrar cosas sin que nadie alcance a
reaccionar. La configuración de arriba consigue el mismo efecto práctico en
clase (nadie hace clic en nada) sin abrir esa puerta.

Si aun así lo quieres para tu propia máquina de demostración, es tu decisión:
cambia `acceptEdits` por `bypassPermissions` en tu copia. En las de ellos, no.
