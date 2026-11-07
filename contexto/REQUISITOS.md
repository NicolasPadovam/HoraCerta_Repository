# Hora Certa — Requisitos

## Atores
- **Pessoa cuidada (idoso):** recebe lembretes e confirma.
- **Cuidador (familiar/profissional):** cadastra remédios e consultas, acompanha e é alertado.

## Requisitos funcionais (MVP)

### RF01 — Vínculo idoso ↔ cuidador
- Um idoso pode ter **vários cuidadores**; um cuidador pode acompanhar **vários idosos**.
- O vínculo exige **consentimento do idoso** (convite aceito).

### RF02 — Cadastro de remédios
- Campos: nome, dosagem (ex.: "1 comprimido 50mg"), **agendamento** (ver RF02.1), dias da semana, data de início/fim (opcional), observação (ex.: "em jejum").
- Pode ser feito pelo cuidador ou pelo idoso.
- Regra: **1 remédio = 1 agendamento**. Não é preciso criar vários alarmes para o mesmo remédio.

### RF02.1 — Periodicidade (1 remédio, 1 configuração de alarmes)
- O usuário informa o **primeiro horário** e a **periodicidade**, e o app gera todos os lembretes do dia sozinho.
- Ex.: "Amoxicilina às **08:00**, de **8 em 8 horas**" → lembretes às 08:00, 16:00 e 00:00.
- Tipos de agendamento:
  - **Intervalo:** primeiro horário + "a cada N horas" (opções rápidas: 4h, 6h, 8h, 12h, 24h).
  - **Horários fixos:** lista livre (ex.: 08:00 e 20:00) para casos que não seguem intervalo exato.
- **Duração do tratamento** opcional (ex.: "por 7 dias") — o agendamento encerra sozinho.
- A tela de cadastro mostra uma **prévia** dos horários gerados antes de salvar ("Você será lembrado às 08:00, 16:00 e 00:00").
- **Horário de sono (opcional):** se um horário gerado cair na madrugada, o app avisa o cuidador para conferir com o médico (não altera a dose sozinho).
- Editar o agendamento atualiza todos os lembretes futuros de uma vez; doses já registradas não mudam.

### RF03 — Lembrete escalonado de remédio
1. **No horário:** notificação no app do idoso (som + tela cheia) com botão **"Tomei"**.
2. **+10 min sem confirmação:** mensagem de WhatsApp para o idoso.
3. **+30 min do horário sem confirmação:** mensagem de WhatsApp para o(s) cuidador(es).
4. O cuidador pode **ligar para o idoso com 1 toque** (abre ligação do WhatsApp/telefone).
- Confirmação registra data/hora e quem confirmou. Tempos de escalonamento configuráveis pela família (padrão +10 min e +30 min).

### RF03.1 — Resposta ao "Tomei" e adiamento
- "Tomei" → tela verde "Muito bem, Maria!" + vibração; botão **Desfazer** visível por **10 s**.
- "Lembrar em 10 min" → "Eu aviso de novo às 08:10" + atalho "Já tomei agora".

### RF04 — Agendamento de consultas
- Campos: especialidade/médico, data, hora, endereço, observações (ex.: "levar exames").
- Gera convite **.ics** enviado ao idoso e aos cuidadores — compatível com Google, Outlook e Apple.
- Lembretes: 1 dia antes e 2 horas antes (idoso + cuidador).

### RF05 — Pedir Uber
- No dia da consulta, botão **"Pedir Uber"** abre o app da Uber via deep link com o destino (endereço da consulta) já preenchido.

### RF06 — Histórico
- Lista de doses tomadas, atrasadas e não confirmadas, visível para idoso e cuidador.

### RF07 — Controle de estoque
- Ao cadastrar o remédio, informar a quantidade em estoque (ex.: 30 comprimidos).
- Cada "Tomei" desconta a dose do estoque.
- Com base na periodicidade, o app calcula quantos dias restam e avisa idoso e cuidador quando faltarem **5 dias**: "A Losartana acaba em 5 dias".
- Botão "Comprei mais" para repor o estoque.

### RF08 — Identificação visual do remédio
- Cada remédio exibe uma **imagem de referência** da caixa/comprimido obtida de um catálogo/banco de imagens pelo nome do remédio — o idoso **não precisa tirar foto**.
- A imagem aparece no cadastro, na lista de remédios e no alerta (T2), ajudando quem tem dificuldade de leitura.
- O cuidador pode trocar a imagem se a sugerida não corresponder à embalagem real.

### RF09 — Botão de emergência (SOS)
- Botão grande e sempre visível no app do idoso.
- Ao tocar (com confirmação para evitar toque acidental): envia **WhatsApp com a localização** para todos os cuidadores e mostra atalho para ligar **192 (SAMU)**.

### RF10 — Relatório para o médico
- Gera **PDF** com a adesão do período (padrão: último mês): doses tomadas, atrasadas e não confirmadas, por remédio.
- Na véspera de uma consulta, o lembrete inclui: "Leve o relatório de remédios" com link para gerar/compartilhar.

## Princípio: o app não contraria a prescrição
O Hora Certa **organiza e lembra** o que o médico prescreveu — nunca sugere, altera ou questiona dose, horário ou combinação de remédios. Por isso ficaram fora do escopo: leitura automática de receita (OCR) e alerta de interação medicamentosa.

## Requisitos não funcionais

### RNF01 — Acessibilidade (regra fixa)
- Fonte grande (mín. 20pt no corpo), alto contraste.
- **No máximo 3 botões por tela.**
- Linguagem simples, sem jargão técnico; ícones sempre acompanhados de texto.

### RNF02 — Privacidade (LGPD)
- Dados de saúde são **dados pessoais sensíveis** (LGPD, art. 11).
- Consentimento explícito do idoso para compartilhar dados com cuidadores; pode revogar a qualquer momento.
- Coleta mínima, dados criptografados, exclusão de conta a pedido.

### RNF03 — Plataforma
- App mobile **Android e iOS** + **backend** (API, agendamento de notificações, envio de WhatsApp, geração de .ics).
- Notificações locais devem funcionar mesmo sem internet.

## Restrições técnicas conhecidas
- **WhatsApp:** envio de mensagens via WhatsApp Business API (templates aprovados). Ligação automática **não** é suportada pela API — por isso a ligação é feita pelo cuidador com 1 toque.
- **Uber:** integração via deep link (não exige parceria). Parceria formal é próximo passo.
