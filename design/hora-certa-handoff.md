# Hora Certa — Handoff de design para implementação

Projeto de faculdade (CitizenTech). App mobile que conecta idoso e cuidador: lembra remédios e consultas, confirma a dose ("Tomei"), avisa o cuidador pelo WhatsApp quando algo não é confirmado, manda consultas para a agenda (.ics) e facilita o transporte (Uber).
Princípio: o app organiza e lembra a prescrição médica, nunca a contraria.
Público do MVP: somente idosos e seus cuidadores/familiares.

Design de referência (canvas, paleta azul): https://claude.ai/artifact/Kqkf7uVxUB1dZj5FUMtnUL
Stack: [PREENCHER: Flutter / Kotlin / Java]

## Regras fixas de UX
- Fonte grande, alto contraste, no máximo 3 botões por tela (exceção: SOS fixo no canto).
- Linguagem simples: "Já tomou?", nunca "Confirmar ingestão".
- Cor nunca é a única pista: todo status tem ícone + palavra + cor.
- Menor texto permitido: 18 px. Corpo: 22 px. Botão: 26–34 px bold.
- Área de toque mínima 64 px; botão principal "Tomei" 88–96 px.
- Espaço entre botões >= 16 px. Bordas de 3 px em vez de sombras fracas.
- Dá para desfazer: "Desfazer" visível por 10 s após "Tomei".
- Foto/ilustração da caixa do remédio em alertas e cadastros.

## Tokens (paleta azul escolhida)
Cores
- primary / Azul        #1D4F9F  (texto branco 7,9:1) — marca, títulos, navegação
- primary-tint / Névoa  #E4ECF8  — fundos de apoio
- primary-line          #BBCDEC
- background            #F5F8FD
- border                #D9E2F1  (divisor suave #E6ECF6)
- ink                   #1B2433  — texto principal
- ink-muted             #4A5568  — texto de apoio (7,1:1 no fundo)
- success / Verde Tomei #1B7F45  (texto branco 5,1:1); escuro #145C33; tint #DDF1E4
- warning / Âmbar Sol   #F5B335  (sempre com texto escuro); tint #FDE9BA
- danger / Terracota    #B8321F  (texto branco 6,0:1); escuro #8E2414; tint #F9DCD6
Uso: verde só para "tomei/tudo certo"; âmbar para próximo horário e atenção; terracota só para SOS e atraso.

Tipografia
- Títulos: Nunito 800/900. Texto: Atkinson Hyperlegible 400/700 (Google Fonts).
- Escala: Display 40/48, Título 32/40, Corpo 22/32, Botão 28 bold, Apoio 18.

Forma
- Raios: 16 campos, 24 botões, 32 cartões (28 em cartões compactos), 999 etiquetas/chips.
- Botão principal verde com "degrau" inferior (sombra sólida 6 px na cor escura).

## Telas
App do idoso (Dona Maria)
- T1 Início ("Hoje"): saudação "Bom dia, Maria!", próximo remédio em destaque (nome, dose, horário), próxima consulta, 3 botões [Meus remédios] [Minhas consultas] [Ligar para família]. SOS fixo no canto superior direito: toque -> confirmação ("Avisar sua família agora?") -> tela "Sua família foi avisada" com [Ligar 192].
- T2 Alerta de remédio (tela cheia): "Hora do remédio!", nome + dose, imagem da caixa, botões [Tomei] (verde, grande) e [Lembrar em 10 min]. Tomei -> tela verde "Muito bem, Maria!" + Desfazer. Adiar -> "Eu aviso de novo às 08:10" + "Já tomei agora".
- T3 Consulta do dia: "14h — Cardiologista", endereço com mapa ilustrativo, botões [Pedir Uber] (abre o app com destino preenchido) e [Ver endereço] (endereço em tela cheia).
- T8 Aviso de estoque: "Restam 5 dias", barra de estoque, [Comprei mais] -> seletor de quantidade (+/- 10) -> "Estoque atualizado!"; [Lembrar amanhã].

App do cuidador (Carlos)
- T4 Painel: lista de pessoas acompanhadas com status do dia ("3 de 5 remédios tomados"), barra de doses (verde tomadas, terracota não confirmada, vazia pendente), alerta em terracota com [Ligar]. [Convidar alguém].
- T5 Detalhe da pessoa: abas Remédios (com estoque) | Consultas | Histórico; [Relatório para o médico] gera PDF (adesão dos últimos 30 dias); botões [+ Remédio] [+ Consulta] [Ligar].
- T6 Cadastro de remédio: nome, dosagem, observação; "Primeiro horário" + "Repetir a cada" (4h, 6h, 8h, 12h, 1x ao dia, ou escolher horários); "Por quanto tempo?" (uso contínuo / N dias); estoque inicial (calcula dias de duração); imagem sugerida; prévia "Lembretes às 08:00 · 16:00 · 00:00"; [Salvar].
- T7 Cadastro de consulta: especialidade, dia, hora, endereço, observação; [Salvar e enviar para agendas] (gera .ics para Maria e Carlos; lembretes 1 dia antes e 2 h antes).
- T9 Estoque: lista de remédios com barra e "dá para N dias"; item em alerta (<= 5 dias) com [Comprei mais] e seletor de quantidade.

## Fluxos e regras de negócio
- F1 Lembrete escalonado: 08:00 notificação no app -> sem resposta, WhatsApp para a Maria (+10/15 min) -> sem resposta, WhatsApp para o Carlos (+30 min): "Sua mãe ainda não confirmou a Losartana das 08h". Tempos configuráveis pela família. Carlos toca em Ligar.
- F2 Consulta: Carlos cadastra -> convite .ics para os dois -> lembretes 1 dia antes e 2 h antes -> no dia, Maria toca Pedir Uber.
- F3 Vínculo: Carlos convida a Maria pelo telefone -> ela aceita (consentimento) -> vínculo ativo. (Tela ainda não desenhada; sem LGPD no escopo atual do design.)
- F4 SOS: confirma -> WhatsApp com localização para todos os cuidadores -> atalho Ligar 192.
- F5 Estoque: "Tomei" desconta 1 -> faltam <= 5 dias? -> aviso para Maria e Carlos -> [Comprei mais] atualiza o estoque.
- Periodicidade inteligente: 1 remédio = 1 configuração ("às 8h, de 8 em 8 horas"), sem criar vários alarmes. Exemplo: 08:00 + 8h => 08:00, 16:00, 00:00.

## Dados de exemplo usados no design
Maria (mãe, 78 anos): Losartana 50 mg (a cada 12h), Metformina 850 mg (a cada 8h), Sinvastatina 20 mg (1x ao dia). Consulta: Cardiologista hoje às 14h, Rua X, 123. Seu Antônio é pessoa de exemplo no painel.

## Fora do MVP
Outros públicos, parceria formal com Uber, integração via API com Google Calendar e Outlook.
