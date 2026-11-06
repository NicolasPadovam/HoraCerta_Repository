# Hora Certa — Design System (esboço v0)

> Esboço inicial para discussão. Tudo aqui é proposta — ajuste à vontade.

## Princípios
1. **Calmo e confiável** — saúde sem cara de hospital.
2. **Grande e óbvio** — o idoso nunca deve procurar onde tocar.
3. **Uma ação por vez** — no máximo 3 botões por tela (SOS é a exceção).
4. **Texto + ícone sempre** — ícone nunca aparece sozinho.

## Cores
| Token | Hex | Uso |
|---|---|---|
| `primaria` | `#0B5D5B` | Verde-petróleo: marca, títulos, botões principais |
| `primaria-clara` | `#EEF6F5` | Fundos de cards |
| `acento` | `#F26B4E` | Coral: hora do remédio, chamadas de atenção |
| `sucesso` | `#2E9E5B` | "Tomei", doses confirmadas |
| `alerta` | `#F6B93B` | Atrasado, estoque baixo |
| `perigo` | `#D63B3B` | SOS, dose não confirmada |
| `texto` | `#1F2A2E` | Texto principal |
| `texto-suave` | `#5A6B70` | Legendas |
| `fundo` | `#FFFFFF` | Fundo das telas |

Contraste mínimo **WCAG AAA (7:1)** para texto do app do idoso.

## Tipografia
| Estilo | Fonte | Tamanho (app do idoso) | Tamanho (app do cuidador) |
|---|---|---|---|
| Título | Merriweather / Cambria (serifada, acolhedora) | 32 | 26 |
| Corpo | Inter / Calibri | 22 | 17 |
| Botão | Inter Bold | 24 | 18 |
| Legenda | Inter | 18 | 14 |

## Componentes
- **Botão principal:** altura mínima 72px (idoso) / 52px (cuidador), cantos 16px, largura total.
- **Card de remédio:** imagem do remédio (64px) + nome + dose + próximo horário.
- **Chip de status:** ✅ Tomado · ⏰ Pendente · ⚠️ Atrasado · ❌ Não confirmado.
- **Botão SOS:** vermelho, circular, fixo no canto inferior direito.

## Dois "modos" visuais
- **Idoso:** fontes grandes, pouco conteúdo, fundo branco, alto contraste.
- **Cuidador:** mais denso (painel), mesmas cores, fontes normais.

## Motivo visual
**Círculos** — relógio/hora certa. Ícones dentro de círculos coloridos, avatares circulares, linha do tempo de doses com pontos.
