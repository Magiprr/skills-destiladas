# Skills destiladas

Una selección de 24 skills de Claude Code sacadas de dos librerías, la de Matt Pocock y pstack, más dos propias, `skill-advisor` y `beginner-coach`. Son las que más rinden para alguien que recién empieza.

## Si nunca has usado esto, empieza aquí

Una **skill** es una receta que Claude sigue para hacer bien un tipo de tarea. No tienes que aprenderte ninguna. Instálalas y Claude te va enseñando de a poco.

1. Abre Claude Code. Si no lo tienes, sigue la guía oficial: https://docs.claude.com/en/docs/claude-code/quickstart
2. Copia este mensaje y pégaselo a Claude tal cual:

   ```
   Instala las skills de este repo siguiendo la sección «Para Claude» del README: https://github.com/Magiprr/skills-destiladas
   ```

3. Claude te va a preguntar si quieres que te vaya enseñando. Responde «sí».

Desde ahí, cada vez que le pidas algo, Claude hace lo que pediste. De vez en cuando te explica una palabra nueva (una sola vez) o te da un consejo corto para pedir mejor. Si quieres menos, dile «menos consejos». Si quieres que pare, «para».

## Para Claude

Si un usuario te pidió instalar este repo:

1. Clona el repo en `~/skills-destiladas` y enlaza cada carpeta de `skills/` en `~/.claude/skills/` (comando en «Instalación»). Si ya existe una skill con el mismo nombre, no la pises: pregúntale al usuario.
2. Agrega estas dos líneas al `~/.claude/CLAUDE.md` del usuario (créalo si no existe) y muéstrale lo que agregaste:

   ```
   Antes de cada tarea, aplica la skill skill-advisor.
   Si el usuario es nuevo en Claude Code, aplica la skill beginner-coach.
   ```

3. Corre la skill `beginner-coach`. Ella pregunta si quiere aprender.
4. Explícale en dos frases simples qué instalaste. Asume que no sabe qué es una terminal.

## beginner-coach

Para gente que no sabe nada de Claude Code ni de la terminal. Hace lo que la persona pidió y, de paso, le enseña de a poco:

- Pregunta primero si quiere aprender.
- Explica cada palabra nueva una sola vez, con una comparación cotidiana, justo donde aparece.
- Cuando la persona tiene que hacer algo ella misma, le dice dónde, qué pegar, qué va a ver si funcionó y qué mandar si no.
- Da como máximo un consejo por respuesta, sacado de lo que la persona acaba de escribir, y no en todas las respuestas.
- Sigue un camino de tres niveles: pedir bien, trabajar juntos, usar herramientas.
- Guarda en `~/.claude/beginner-coach/progress.md` lo que ya enseñó. No repite lo que la persona ya sabe y deja de mencionar lo que ya usa sola.

## skill-advisor

Antes de responder un prompt, revisa si alguna skill instalada calza. Si calza, te dice cuál y por qué en una línea, y te reescribe el prompt para llamarla.

La reescritura no es para que el prompt suene mejor. Cada cosa que agrega tiene que cambiar el resultado: qué cuenta como terminado, la evidencia que el agente no encontraría solo, qué no se toca, cómo se prueba, y qué decisiones te devuelve a ti.

Para que se aplique en todos los chats, va la línea de `CLAUDE.md` de la sección «Para Claude».

## Las skills

| Skill | Origen | Para qué |
|---|---|---|
| beginner-coach | propia | Enseña de a poco a quien parte de cero, sin repetir lo que ya sabe |
| skill-advisor | propia | Recomienda la skill que calza y reescribe el prompt para que rinda más |
| diagnosing-bugs | Matt Pocock | Encontrar la causa de un bug difícil o de una lentitud |
| resolving-merge-conflicts | Matt Pocock | Resolver choques al juntar ramas |
| prototype | Matt Pocock | Prototipo desechable para responder una duda de diseño |
| handoff | Matt Pocock | Resumir el chat para que otro agente siga |
| grilling (y grill-me) | Matt Pocock | Interrogarte hasta aclarar un plan |
| research | Matt Pocock | Investigar en fuentes primarias y dejar un .md |
| ketchup | pstack | Ponerte al día y listar lo que espera tu decisión |
| bro | pstack | Repetir lo último en simple |
| unslop | pstack | Sacarle a un texto las marcas de IA |
| blast-radius | pstack | Qué puede romper un cambio fuera de lo que tocó |
| what-did-i-get-done | pstack | Resumir los commits de un período |
| recall | pstack | Reconstruir en qué ibas |
| arena | pstack | Varios intentos en paralelo y quedarse con lo mejor de cada uno |
| automate-me | pstack | Convertir tu forma de trabajar en una skill |
| correct | pstack | Volver imposible un error que el agente repite |
| create-verification-skill | pstack | Crear una skill que prueba tu app como un usuario |
| principle-prove-it-works | pstack | No decir «listo» sin probarlo en lo real |
| principle-exhaust-the-design-space | pstack | 2 o 3 prototipos lado a lado antes de elegir |
| principle-experience-first | pstack | El deleite del usuario antes que lo cómodo de programar |
| principle-fix-root-causes | pstack | Arreglar donde nace el bug |
| principle-attack-the-premise | pstack | Si dos arreglos fallan igual, revisar la idea de fondo |
| principle-explain-the-number | pstack | Ver qué limita una medición antes de creerle |
| principle-encode-lessons-in-structure | pstack | Si una regla se repite, volverla un chequeo |

## Qué cambió respecto de los originales

- Se sacaron las rayas (— y –) de los textos.
- Se sacaron las instrucciones para otras plataformas (Codex, Copilot, Muse, Antigravity) y las referencias a skills de pstack que no vienen aquí.
- `recall` y `automate-me` traen su propia copia del script que ubica los transcripts.
- `automate-me` usa `anthropic-skills:skill-creator` en vez de `plugin-dev:skill-development`.
- `unslop` trae una sección en español.

## Instalación

```sh
git clone https://github.com/Magiprr/skills-destiladas ~/skills-destiladas
for d in ~/skills-destiladas/skills/*/; do ln -sfn "$d" ~/.claude/skills/"$(basename "$d")"; done
```

## Licencias

Las dos fuentes tienen licencia MIT. Las licencias van en `licencias/`.

- Matt Pocock: https://github.com/mattpocock/skills
- pstack de Lauren Tan, port para Claude Code de Michael Denyer: https://github.com/michael-denyer/pstack-claude
