# Hora Certa — Identidade Visual (oficial, paleta azul)

> **Fonte de verdade:** `tokens.json` (valores) + este arquivo (regras de uso).
> Referência visual navegável: `referencia/Hora_Certa_Identidade_Visual.html` · handoff detalhado: `hora-certa-handoff.md`.
> A versão verde anterior está em `historico/` e **não deve ser usada**.

## Conceito
"Cada remédio na hora certa. Cada família em paz."
Logo/ícone: **um relógio que termina em confirmação** (✓ verde dentro do relógio, fundo azul).

## Regras fixas de UX (não negociáveis)
1. **Uma coisa por tela** — no máximo **3 botões** (exceção: SOS fixo no canto superior direito).
2. **Fale como gente** — "Já tomou?", nunca "Confirmar ingestão". Sem jargão, sem sigla.
3. **Cor nunca é a única pista** — todo status tem **ícone + palavra + cor**.
4. **Tamanhos mínimos** — texto ≥ 18; corpo 22; botão 26–34 bold.
5. **Toque** — área mínima 64; botão "Tomei" 88–96; espaço entre botões ≥ 16.
6. **Bordas de 3 px** em vez de sombras fracas.
7. **Dá para desfazer** — "Desfazer" visível por 10 s após "Tomei".
8. **Foto/ilustração da caixa** do remédio em alertas e cadastros.
9. **Resposta que se sente** — "Tomei" → tela verde, vibração, frase de elogio.
10. **Cuidador só quando precisa** — painel calmo (verde por padrão), alerta só quando algo foge do normal.

## Cores — semântica
| Cor | Token | Usar para | Nunca usar para |
|---|---|---|---|
| Azul `#1D4F9F` | primary | marca, títulos, navegação, botão secundário (contorno) | status |
| Verde Tomei `#1B7F45` | success | "Tomei", "tudo certo", tomado | qualquer outra ação |
| Âmbar Sol `#F5B335` | warning | próximo horário, atenção, estoque baixo | texto branco em cima |
| Terracota `#B8321F` | danger | **só** SOS e atraso | erros comuns, botões de excluir decorativos |
| Tinta `#1B2433` | ink | texto, botão de ação externa (Uber) | — |
| Névoa `#F5F8FD` | background | fundo das telas (em vez de branco puro) | — |

Escalonamento por cor: **azul (na hora) → âmbar (+10 min) → terracota (+30 min)**.

## Tipografia
- Títulos: **Nunito** 800/900. Texto: **Atkinson Hyperlegible** 400/700 (Google Fonts, licença OFL).
- Escala: Display 40/48 · Título 32/40 · Corpo 22/32 · Botão 28 bold · Apoio 18/26.

## Forma
Raios: campo 16 · botão 24 · cartão 32 (compacto 28) · chip 999.

## Componentes
| Componente | Especificação |
|---|---|
| **Botão Tomei** (principal) | fundo success, texto branco 28 bold, ícone ✓, altura 88–96, raio 24, **"degrau"**: sombra sólida 6 px abaixo em successDark (sem blur) |
| **Botão secundário** | fundo surface, borda 3 px primary, texto primary 28 bold, ícone à esquerda, altura ≥ 72 — nunca compete com o Tomei |
| **Botão ação externa** (Pedir carro/Uber) | fundo ink, texto branco, ícone de carro |
| **Botão SOS** | fundo danger, texto branco, ícone ⚠, "SOS", ≥ 64×64, canto superior direito; toque abre confirmação "Avisar sua família agora?" |
| **Etiqueta de status** | chip raio 999, ícone + palavra: ✓ "Tomado às 8h02" (successTint/successDark) · 🕐 "Próximo: 14h" (warningTint/ink) · ⚠ "Atrasado 30 min" (dangerTint/dangerDark) |
| **Campo de formulário** | rótulo acima (18–22, bold), caixa raio 16, borda 3 px border → primary no foco, altura ≥ 64, texto 22 |
| **Cartão** | fundo surface, raio 32, borda 3 px border (sem sombra) |
| **Barra de doses/estoque** | segmentos: verde = tomada, terracota = não confirmada, vazia (contorno) = pendente; sempre com legenda em texto |

## Ícones
Ícones de **linha** (ex.: Material Symbols Rounded / Lucide), traço grosso, sempre acompanhados de palavra. **Não usar emoji** na interface.
