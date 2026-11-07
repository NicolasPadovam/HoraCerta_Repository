# Hora Certa — Roteiro do vídeo pitch (5 min, 3 pessoas)

**Regras da GS:** no máximo 5 min, gravação horizontal em HD, alunos aparecendo e com voz própria (sem voz de IA), link público no YouTube, **pelo menos metade do tempo mostrando o software** e todos os integrantes falando.

**Distribuição:**
- **Pessoa A** (abertura e problema) e **Pessoa C** (arquitetura e encerramento) falam para a câmera, com o slide ao lado ou atrás.
- **Pessoa B** apresenta a demonstração com a tela do app gravada, de preferência no OBS com a webcam num canto.

| Tempo | Quem | Tela | Bloco |
|---|---|---|---|
| 0:00–0:20 | A | Slide 1 | Abertura |
| 0:20–1:05 | A | Slides 2–3 | Problema e dados |
| 1:05–1:30 | A | Slides 4–5 | Personas e concorrência |
| 1:30–4:00 | B | **App rodando** (slides 6–8 de apoio) | Demonstração (2 min 30 s = 50%) |
| 4:00–4:35 | C | Slides 10–11 | Arquitetura e tecnologias |
| 4:35–5:00 | C (+ A e B no fim) | Slide 12 | Conclusão |

---

## 0:00–0:20 · Abertura (Pessoa A, para a câmera)
> "Oi, nós somos a equipe **[nome]**: eu sou **[A]**, esse é o **[B]** e essa é a **[C]**. Vamos apresentar o **Hora Certa**: cada remédio na hora certa, cada família em paz."

## 0:20–1:05 · Problema e dados (Pessoa A)
**Slide 2**
> "Quem tem pai, mãe ou avó já se perguntou: *será que ela tomou o remédio da pressão?* O idoso toma vários remédios em horários diferentes, esquece uma dose, às vezes toma em dobro. E quem cuida trabalha o dia todo e não tem como saber sem ligar toda hora."

**Slide 3**
> "E isso não é um caso isolado. O Brasil tem **32 milhões de pessoas com mais de 60 anos**, e **5,7 milhões moram sozinhas**. **93% dos idosos usam remédio contínuo**, e a OMS estima que **metade dos pacientes crônicos não segue o tratamento como foi prescrito**. Isso vira internação evitável e preocupação diária para a família."

## 1:05–1:30 · Personas e concorrência (Pessoa A)
**Slide 4**
> "Criamos o app pensando em duas pessoas: a **Dona Maria**, 78 anos, que mora sozinha e toma três remédios, e o filho dela, o **Carlos**, que cuida à distância."

**Slide 5**
> "Já existem alarmes e apps de lembrete, mas eles param no lembrete. Nenhum fecha o ciclo com a família pelo canal que o idoso já usa, que é o WhatsApp. Vou passar para o [B] mostrar como funciona."

## 1:30–4:00 · Demonstração (Pessoa B, tela do app)
> Gravem a tela do app real. Se uma parte ainda não estiver pronta, usem o protótipo navegável e digam isso claramente.

**1:30 · Cadastro com periodicidade (app do cuidador, T6)**
> "Aqui o Carlos cadastra a Metformina. Em vez de criar três alarmes, ele diz só uma coisa: **primeira dose às 8h, de 8 em 8 horas**. O app já mostra a prévia (8h, 16h e meia-noite) e avisa que meia-noite é de madrugada. Ele informa que tem 60 comprimidos, e o app calcula quantos dias o remédio dura."

**2:00 · Início do idoso (T1)**
> "Esse é o celular da Dona Maria. Tela simples: letra grande, só o próximo remédio e três botões. O SOS fica sempre no canto."

**2:15 · Hora do remédio (T2)**
> "Chegou a hora. O alarme mostra a **foto da caixa**, o nome e a dose. Ela toca em **Tomei**: tela verde, vibração e um elogio. Se tocou sem querer, pode **desfazer** por 10 segundos."

**2:40 · Lembrete escalonado (slide 7 de apoio + painel T4)**
> "E se ela não confirmar? Dez minutos depois, o app manda um WhatsApp para ela. Trinta minutos depois, avisa o Carlos. No painel dele aparece em terracota: *Losartana das 8h, atrasado 30 minutos*, com o botão **Ligar**. O Carlos só é acionado quando realmente precisa."

**3:10 · Consulta e transporte (T3)**
> "O Carlos marcou cardiologista para hoje às 14h. A consulta foi para a agenda dos dois, e no dia a Dona Maria toca em **Pedir carro**: a Uber abre com o endereço preenchido."

**3:30 · Estoque, SOS e relatório (T8, T5)**
> "Quando faltam 5 dias de remédio, os dois recebem um aviso. O SOS manda a localização para a família pelo WhatsApp. E antes da consulta o Carlos gera um **relatório em PDF** com a adesão do mês para mostrar ao médico."

**3:50 · Fechamento da demo**
> "Tudo isso segue uma regra: o app organiza e lembra o que o médico prescreveu, **nunca contraria a prescrição**. Passo para a [C]."

## 4:00–4:35 · Arquitetura e tecnologias (Pessoa C)
**Slide 10**
> "Por trás disso temos dois apps (idoso e cuidador) conversando com a **API do Hora Certa**, que gera as doses a partir da periodicidade, controla o escalonamento e se integra com o **WhatsApp Business**, com as agendas via **.ics**, com a **Uber** e com notificações push. Os alarmes são locais, então funcionam sem internet."

**Slide 11**
> "Usamos **[Flutter e Kotlin]** no mobile, **[Java com Spring Boot]** e **[Oracle]** no back-end, versionamento no GitHub e testes com **[JUnit]**. E toda a interface segue as regras de acessibilidade: letra mínima de 18, botões de 64 px e cor nunca como única pista."

## 4:35–5:00 · Conclusão (Pessoa C, depois os três juntos)
**Slide 12**
> "O Hora Certa contribui para os **ODS 3, 10 e 11**. Os próximos passos são testar com idosos reais, formalizar a parceria com a Uber e ampliar para pessoas com deficiência e doenças crônicas."

**Os três, para a câmera:**
> A: "Porque ninguém precisa cuidar sozinho." · B e C: "Obrigado!"

---

## Checklist antes de gravar
- [ ] Preencher no slide 1: nome da equipe, nomes e RMs.
- [ ] Confirmar no slide 11 as tecnologias entre colchetes.
- [ ] Gravar a demo com dados de exemplo: Maria, Losartana, Metformina, Sinvastatina, Cardiologista às 14h.
- [ ] Ensaiar com cronômetro: a demo precisa de pelo menos 2 min 30 s.
- [ ] Exportar em HD, subir no YouTube como **público** e testar o link deslogado.
- [ ] O PDF dos slides e o link do vídeo vão num .ZIP na área de Software Projects Quality Assurance.
