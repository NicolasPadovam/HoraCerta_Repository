# Hora Certa — Repositório de contexto (core)

App que conecta o **idoso** ao **cuidador/familiar**: lembra remédios e consultas, confirma a dose ("Tomei"), avisa o cuidador pelo WhatsApp quando algo não é confirmado, manda consultas para a agenda (.ics) e facilita o transporte (Uber).
**Princípio:** o app organiza e lembra a prescrição médica — nunca a contraria.

Este repositório **não contém código do app**. Ele é a fonte da verdade (produto + design) usada pelos projetos em **Flutter**, **Android/Kotlin** e **Java**.

## Estrutura
| Pasta | Conteúdo |
|---|---|
| `contexto/` | Produto: `VISAO.md`, `REQUISITOS.md`, `MODELO-DADOS.md`, `TELAS.md` |
| `design/` | Identidade visual oficial: `DESIGN.md` (regras), `tokens.json` (valores), `hora-certa-handoff.md` (telas detalhadas), `referencia/` (HTML navegável) |
| `features/` | Backlog: MVP, futuro, descartadas |
| `decisoes/` | Registro das decisões (sessões grill-me) |
| `.claude/skills/aplicar-identidade-hora-certa/` | Skill que aplica a identidade visual em projetos Flutter, Android (Compose ou XML) e Java |
| `pitch/` | Slides do pitch (v1, ainda com o visual antigo) |

## Como aplicar o design num projeto (Flutter / Kotlin / Java)
1. Copie a pasta `.claude/skills/aplicar-identidade-hora-certa/` para `.claude/skills/` do projeto (ou para `~/.claude/skills/` para usar em todos).
2. No Claude Code, dentro do projeto, peça: **"aplique a identidade visual do Hora Certa"**.
3. A skill detecta a plataforma, cria o tema a partir de `design/tokens.json`, cria os componentes base e restiliza as telas sem mexer na lógica, e no fim lista o que mudou e o que ainda viola as regras.

> Mudou uma cor ou tamanho? Altere **só** `design/tokens.json` e `design/DESIGN.md`; depois rode a skill de novo nos projetos.
