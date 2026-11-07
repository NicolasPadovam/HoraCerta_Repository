# Hora Certa — Telas e Fluxos

> Visual oficial: `design/DESIGN.md` (paleta azul). Especificação detalhada de cada tela: `design/hora-certa-handoff.md`.

> Regra fixa: fonte grande, alto contraste, **no máximo 3 botões por tela**, linguagem simples.

## App do idoso (Dona Maria)

### T1 — Início ("Hoje")
- Saudação: "Bom dia, Maria!"
- Próximo remédio em destaque (nome, dose, horário).
- Próxima consulta (se houver).
- Botões: **[Meus remédios] [Minhas consultas] [Ligar para família]**
- Botão **SOS** fixo no **canto superior direito** (exceção à regra de 3 botões). Toque → "Avisar sua família agora?" → "Sua família foi avisada" + [Ligar 192].

### T2 — Alerta de remédio (tela cheia)
- "Hora do remédio! Losartana — 1 comprimido"
- Imagem de referência do remédio (catálogo).
- Botões: **[✅ Tomei] [⏰ Lembrar em 10 min]**

### T3 — Consulta do dia
- "Hoje às 14h — Cardiologista — Rua X, 123"
- Botões: **[🚗 Pedir Uber] [Ver endereço]**

### T8 — Aviso de estoque
- "Losartana: restam 5 dias", barra de estoque.
- Botões: **[Comprei mais]** (seletor de quantidade +/- 10 → "Estoque atualizado!") **[Lembrar amanhã]**

## App do cuidador (Carlos)

### T4 — Painel
- Lista de pessoas acompanhadas, com status do dia (ex.: "Mãe: 3 de 5 remédios tomados ✅").
- Alertas em vermelho para doses não confirmadas.

### T5 — Detalhe da pessoa cuidada
- Abas: Remédios (com estoque: "acaba em 5 dias") | Consultas | Histórico.
- Ação **[📄 Relatório para o médico]** gera o PDF.
- Botões: **[+ Remédio] [+ Consulta] [📞 Ligar]**

### T6 — Cadastro de remédio
- Nome, dosagem, observação.
- **Quando tomar:** "Primeiro horário" (ex.: 08:00) + "Repetir a cada" [4h] [6h] [8h] [12h] [1x ao dia] — ou "Escolher horários".
- "Por quanto tempo?" [Uso contínuo] [N dias].
- **Estoque:** "Quantos comprimidos você tem?" — imagem do remédio sugerida automaticamente.
- **Prévia:** "Lembretes às 08:00 · 16:00 · 00:00".
- Botão **[Salvar]**.

### T7 — Cadastro de consulta
- Especialidade, data/hora, endereço, observação. Botão **[Salvar e enviar para agendas]**.

### T9 — Estoque
- Lista de remédios com barra e "dá para N dias"; item em alerta (≤ 5 dias) com [Comprei mais] e seletor de quantidade.

## Fluxos principais

### F1 — Lembrete escalonado
```
08:00 Notificação no app da Maria ── Tomei? ── sim ──► registra TOMADA ✅
                                        │ não
08:10 WhatsApp para Maria ─────────── Tomei? ── sim ──► registra TOMADA ✅
                                        │ não
08:30 WhatsApp para Carlos: "Sua mãe ainda não confirmou a Losartana das 08h"
                                        │
      Carlos toca em [📞 Ligar] ──► conversa com a mãe
```

### F2 — Consulta
```
Carlos cadastra consulta ──► convite .ics para Maria e Carlos (qualquer agenda)
1 dia antes + 2h antes ──► lembretes para os dois
No dia ──► Maria toca [Pedir Uber] ──► Uber abre com destino preenchido
```

### F3 — Vínculo
```
Carlos convida Maria pelo telefone ──► Maria aceita (consentimento LGPD) ──► vínculo ATIVO
```

### F4 — SOS
```
Maria toca [🆘 SOS] ──► confirma ──► WhatsApp com localização para todos os cuidadores
                                    └─► tela com atalho [Ligar 192]
```

### F5 — Estoque
```
"Tomei" ──► estoque −1 ──► faltam ≤ 5 dias? ──► aviso para Maria e Carlos ──► [Comprei mais]
```

## Dados de exemplo (usar em protótipos e telas)
- **Maria** (mãe, 78): Losartana 50 mg (a cada 12h), Metformina 850 mg (a cada 8h), Sinvastatina 20 mg (1x ao dia).
- Consulta: Cardiologista hoje às 14h, Rua X, 123.
- **Seu Antônio**: segunda pessoa de exemplo no painel do cuidador.
