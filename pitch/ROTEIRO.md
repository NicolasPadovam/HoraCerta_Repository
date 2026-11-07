# Hora Certa — Roteiro do vídeo pitch (5 min, 3 pessoas)

**Regras da GS:** no máximo 5 min, gravação horizontal em HD, alunos aparecendo e com voz própria (sem voz de IA), link público no YouTube, **pelo menos metade do tempo mostrando o software** e todos os integrantes falando.

**Distribuição (sorteada):** A = **Nicolas** · B = **Vitor** · C = **Enzo**

> Lembrete: o pitch vende a **ideia**. Não precisa estar 100% funcionando; o importante é mostrar o protótipo com segurança e citar as tecnologias de cada matéria.

**Formato:**
- **Pessoa A** (abertura e problema) e **Pessoa C** (arquitetura e encerramento) falam para a câmera, com o slide ao lado ou atrás.
- **Pessoa B** apresenta a demonstração com a tela do app gravada, de preferência no OBS com a webcam num canto.

| Tempo | Quem | Tela | Bloco |
|---|---|---|---|
| 0:00–0:20 | Nicolas | Slide 1 | Abertura |
| 0:20–1:05 | Nicolas | Slides 2–3 | Problema e dados |
| 1:05–1:30 | Nicolas | Slides 4–5 | Personas e concorrência |
| 1:30–4:00 | Vitor | **Protótipo do app** (slides 6–8 de apoio) | Demonstração (2 min 30 s = 50%) |
| 4:00–4:35 | Enzo | Slides 10–11 | Arquitetura e tecnologias |
| 4:35–5:00 | Enzo (+ os três no fim) | Slide 12 | Conclusão |

---

## 0:00–0:20 · Abertura (Nicolas, para a câmera)
> "Oi, nós somos a equipe **HoraCerta**: eu sou o **Nicolas**, esse é o **Vitor** e esse é o **Enzo**. Vamos apresentar o **Hora Certa**: cada remédio na hora certa, cada família em paz."

## 0:20–1:05 · Problema e dados (Nicolas)
**Slide 2**
> "Quem tem pai, mãe ou avó já se perguntou: *será que ela tomou o remédio da pressão?* O idoso toma vários remédios em horários diferentes, esquece uma dose, às vezes toma em dobro. E quem cuida trabalha o dia todo e não tem como saber sem ligar toda hora."

**Slide 3**
> "E isso não é um caso isolado. O Brasil tem **32 milhões de pessoas com mais de 60 anos**, e **5,7 milhões moram sozinhas**. **93% dos idosos usam remédio contínuo**, e a OMS estima que **metade dos pacientes crônicos não segue o tratamento como foi prescrito**. Isso vira internação evitável e preocupação diária para a família."

## 1:05–1:30 · Personas e concorrência (Nicolas)
**Slide 4**
> "Criamos o app pensando em duas pessoas: a **Dona Maria**, 78 anos, que mora sozinha e toma três remédios, e o filho dela, o **Carlos**, que cuida à distância."

**Slide 5**
> "Já existem alarmes e apps de lembrete, mas eles param no lembrete. Nenhum fecha o ciclo com a família pelo canal que o idoso já usa, que é o WhatsApp. Vou passar para o Vitor mostrar como funciona."

## 1:30–4:00 · Demonstração (Vitor, tela do protótipo)
> Gravem a tela do protótipo (Flutter ou Kotlin, o que estiver mais bonito). WhatsApp, agenda e Uber são simulados no MVP: mostrem a tela e digam "no MVP isso é simulado".

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
> "Tudo isso segue uma regra: o app organiza e lembra o que o médico prescreveu, **nunca contraria a prescrição**. Passo para o Enzo."

## 4:00–4:35 · Arquitetura e tecnologias (Enzo)
**Slide 10**
> "Por trás disso, o app existe em duas versões: **Flutter**, para Android e iOS, e **Kotlin**, nativo para Android. Os dois conversam com **microsserviços em Java**: pessoas e vínculos, remédios e doses, alertas e consultas. Cada um roda em um contêiner **Docker**, publicado no **Azure**. Os dados ficam no **Oracle Database**, e é em **PL/SQL** que geramos as doses a partir da periodicidade e damos baixa no estoque."

**Slide 11**
> "A gestão e os testes do projeto estão no **Azure DevOps**: board de tarefas, repositório, pipeline e planos de teste. No MVP, as integrações com WhatsApp, agenda e Uber são simuladas e estão prontas para entrar em produção."

## 4:35–5:00 · Conclusão (Enzo, depois os três juntos)
**Slide 12**
> "O Hora Certa contribui para os **ODS 3, 10 e 11**. Os próximos passos são testar com idosos reais, formalizar a parceria com a Uber e ampliar para pessoas com deficiência e doenças crônicas."

**Os três, para a câmera:**
> Nicolas: "Porque ninguém precisa cuidar sozinho." · Vitor e Enzo: "Obrigado!"

---

## Checklist antes de gravar
- [ ] Gravar a demo com dados de exemplo: Maria, Losartana, Metformina, Sinvastatina, Cardiologista às 14h.
- [ ] Ensaiar com cronômetro: a demo precisa de pelo menos 2 min 30 s.
- [ ] Exportar em HD, subir no YouTube como **público** e testar o link deslogado.
- [ ] O PDF dos slides e o link do vídeo vão num .ZIP na área de Software Projects Quality Assurance.
