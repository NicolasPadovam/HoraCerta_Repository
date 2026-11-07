# Hora Certa — Modelo de Dados

> Entidades usam termos genéricos (**PessoaCuidada**, **Cuidador**) para facilitar a futura expansão a outros públicos.

```
Usuario 1──1 PessoaCuidada
Usuario 1──1 Cuidador
PessoaCuidada N──N Cuidador   (via Vinculo)
PessoaCuidada 1──N Remedio 1──1 Agendamento
Agendamento 1──N Dose
PessoaCuidada 1──N Consulta
```

## Usuario
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| nome | texto | |
| telefone | texto | WhatsApp (formato E.164) |
| email | texto | opcional, usado para convites .ics |
| tipo | enum | `PESSOA_CUIDADA`, `CUIDADOR` |
| criadoEm | data/hora | |

## Vinculo
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| pessoaCuidadaId | UUID | |
| cuidadorId | UUID | |
| parentesco | texto | ex.: "filho" |
| status | enum | `PENDENTE`, `ATIVO`, `REVOGADO` |
| consentimentoEm | data/hora | quando o idoso aceitou (LGPD) |

## Remedio
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| pessoaCuidadaId | UUID | |
| nome | texto | ex.: "Losartana" |
| dosagem | texto | ex.: "1 comprimido 50mg" |
| observacao | texto | ex.: "em jejum" |
| dataInicio / dataFim | data | dataFim opcional |
| imagemUrl | texto | imagem de referência (catálogo), trocável pelo cuidador |
| estoqueAtual | número | unidades restantes |
| unidadesPorDose | número | ex.: 1 comprimido |
| ativo | booleano | |

## Agendamento (1 por remédio)
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| remedioId | UUID | único — 1 remédio, 1 agendamento |
| tipo | enum | `INTERVALO`, `HORARIOS_FIXOS` |
| primeiroHorario | hora | ex.: 08:00 (tipo INTERVALO) |
| intervaloHoras | int | ex.: 8 → 08:00, 16:00, 00:00 (tipo INTERVALO) |
| horariosFixos | lista de hora | ex.: [08:00, 20:00] (tipo HORARIOS_FIXOS) |
| diasSemana | lista | ex.: [SEG..DOM] |
| duracaoDias | int | opcional — encerra o tratamento automaticamente |

## Dose (ocorrência de um horário em um dia)
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| agendamentoId | UUID | |
| previstaPara | data/hora | |
| status | enum | `PENDENTE`, `TOMADA`, `ATRASADA`, `NAO_CONFIRMADA` |
| confirmadaEm | data/hora | |
| confirmadaPor | UUID | usuário que confirmou |
| nivelAlerta | int | 0=app, 1=WhatsApp idoso, 2=WhatsApp cuidador |

## Consulta
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| pessoaCuidadaId | UUID | |
| especialidade | texto | ex.: "Cardiologista" |
| profissional | texto | opcional |
| dataHora | data/hora | |
| endereco | texto | usado no deep link da Uber |
| observacao | texto | ex.: "levar exames" |

## AlertaSOS
| Campo | Tipo | Obs. |
|---|---|---|
| id | UUID | |
| pessoaCuidadaId | UUID | |
| acionadoEm | data/hora | |
| latitude / longitude | número | localização enviada aos cuidadores |

## Regras de negócio
- **Estoque:** cada Dose `TOMADA` subtrai `unidadesPorDose` de `estoqueAtual`. Dias restantes = estoqueAtual ÷ (unidadesPorDose × doses por dia). Alerta quando ≤ 5 dias.
- **Relatório:** calculado a partir das Doses do período (sem entidade própria).
- **Geração de doses:** tipo INTERVALO → horários = primeiroHorario + k × intervaloHoras (k = 0, 1, 2… enquanto < 24h); tipo HORARIOS_FIXOS → a própria lista. Uma Dose é criada para cada horário em cada dia aplicável, até dataFim ou duracaoDias.
- Alterar o Agendamento recalcula só as Doses futuras com status `PENDENTE`.
- Escalonamento: `PENDENTE` → (+10 min) nivelAlerta 1 → (+30 min do horário) nivelAlerta 2 e status `NAO_CONFIRMADA` se não houver confirmação.
- Só cuidadores com Vinculo `ATIVO` recebem alertas e veem dados.
