# Hora Certa — Roteiro do vídeo pitch (5 min, 3 pessoas)

**Regras da GS:** no máximo 5 min, gravação horizontal em HD, alunos aparecendo e com voz própria (sem voz de IA), link público no YouTube, **pelo menos metade do tempo mostrando o software** e todos os integrantes falando.

**Distribuição (sorteada):** Nicolas abre, Vitor demonstra, Enzo encerra.

> Lembrete: o pitch vende a **ideia**. Não precisa estar 100% funcionando; o importante é mostrar o protótipo com segurança e citar as tecnologias de cada matéria.

**Formato:**
- **Nicolas** abre e apresenta o problema, falando para a câmera com o slide ao lado ou atrás.
- **Vitor** conduz a demonstração com a tela do protótipo gravada (de preferência no OBS, com a webcam num canto).
- **Enzo** apresenta a arquitetura e as tecnologias e faz o encerramento, para a câmera.

**Tom:** apresentação de produto, como um lançamento. As transições acontecem pela própria narrativa, sem "passo para fulano".

| Tempo | Quem | Tela | Bloco |
|---|---|---|---|
| 0:00–0:20 | Nicolas | Slide 1 | Abertura |
| 0:20–1:00 | Nicolas | Slides 2–3 | Problema e dados |
| 1:00–1:20 | Nicolas | Slides 4–5 | Personas e concorrência |
| 1:20–3:30 | Vitor | **Protótipo do app** (slides 6–8 de apoio) | Demonstração |
| 3:30–4:05 | Enzo | Slides 10–11 | Arquitetura e tecnologias |
| 4:05–5:00 | Enzo | Slide 12 | Encerramento |

> Software e infraestrutura somam **2 min 45 s**, acima da metade exigida pela GS.

---

## 0:00–0:20 · Abertura (Nicolas, para a câmera)
> "Nós somos a equipe **HoraCerta**: Nicolas, Vitor e Enzo. E este é o **Hora Certa**, o aplicativo que garante que cada remédio seja tomado na hora certa, e que cada família fique em paz."

## 0:20–1:00 · Problema e dados (Nicolas)
**Slide 2**
> "Quem tem pai, mãe ou avó conhece esta pergunta: *será que ela tomou o remédio da pressão?* O idoso esquece doses ou toma em dobro, e a família, que trabalha o dia todo, não tem como saber."

**Slide 3**
> "Esse não é um caso isolado. O Brasil tem **32 milhões de pessoas com mais de 60 anos**, e **5,7 milhões delas moram sozinhas**. **93% dos idosos usam medicamentos de uso contínuo**, e, segundo a Organização Mundial da Saúde, **metade dos pacientes crônicos não segue o tratamento como foi prescrito**. O resultado são internações evitáveis e preocupação diária."

## 1:00–1:20 · Personas e concorrência (Nicolas)
**Slide 4**
> "Pensamos na **Dona Maria**, 78 anos, que mora sozinha, e no filho dela, o **Carlos**, que cuida à distância."

**Slide 5**
> "As soluções que existem hoje param no lembrete. Nenhuma fecha o ciclo entre o idoso e a família, no canal que eles já usam todos os dias. É esse o espaço que o Hora Certa ocupa."

## 1:20–3:30 · Demonstração (Vitor, tela do protótipo)
> Gravem a tela do protótipo (Flutter ou Kotlin, o que estiver mais bonito). O texto conta **um dia da Dona Maria**: as funcionalidades aparecem dentro da história, não como lista. A coluna da direita indica a tela a mostrar enquanto se fala.

| Fala | Tela |
|---|---|
| "Vamos acompanhar um dia da Dona Maria. Tudo começa quando o Carlos cadastra os remédios da mãe. Em vez de criar um alarme para cada horário, ele informa apenas a primeira dose e a frequência: **Metformina, às oito da manhã, de oito em oito horas**. O Hora Certa calcula sozinho os horários e, com a quantidade de comprimidos em casa, já sabe por quantos dias o remédio vai durar." | T6 Cadastro |
| "No celular da Dona Maria aparece só o que importa agora: o próximo remédio, a próxima consulta e botões grandes, com a emergência sempre ao alcance." | T1 Início |
| "Quando chega a hora, o alarme toma a tela com a **foto da caixa**, o nome e a dose, porque quem reconhece a embalagem erra menos. Um toque em **Tomei** e pronto: a tela fica verde, o celular vibra e ela recebe um elogio. Se tocar sem querer, pode desfazer." | T2 Alerta → tela verde |
| "Mas e se ela não responder? É aqui que o Hora Certa se diferencia. Dez minutos depois, ela recebe uma mensagem no WhatsApp. Se ainda assim não confirmar, meia hora depois do horário o Carlos é avisado, e no painel dele o alerta já vem com o botão para ligar para a mãe. O cuidador só é chamado quando realmente precisa." | Slide 7 → T4 Painel |
| "À tarde, a Dona Maria tem cardiologista. A consulta já está na agenda dela e na do Carlos e, na hora de sair, um toque em **Pedir carro** abre o aplicativo de transporte com o endereço preenchido." | T3 Consulta |
| "Quando o remédio está para acabar, os dois são avisados com cinco dias de antecedência. Antes da consulta, o Carlos gera um **relatório com a adesão do mês** para o médico ver como o tratamento realmente está sendo seguido. Tudo isso com um princípio claro: o Hora Certa organiza e lembra o que o médico prescreveu, e **nunca contraria a prescrição**." | T8 Estoque → T5 Relatório |

> No MVP, WhatsApp, agenda e transporte são simulados. Se a banca perguntar: "no MVP essas integrações são simuladas; em produção usam a API oficial do WhatsApp, convites de calendário e o link da Uber".

## 3:30–4:05 · Arquitetura e tecnologias (Enzo, para a câmera)
> O briefing pede para mostrar o que foi produzido em **software, banco de dados e infraestrutura**. Enquanto o Enzo fala, insiram 2 ou 3 segundos de tela real de cada item: contêineres rodando no Docker, recurso no portal do Azure, tabelas ou procedure no Oracle e o board no Azure DevOps.
**Slide 10**
> "Para sustentar essa experiência, o Hora Certa foi desenvolvido em duas versões: **Flutter**, para Android e iOS, e **Kotlin**, nativo para Android. Os aplicativos se comunicam com **microsserviços em Java**, cada um em um contêiner **Docker** publicado no **Azure**. Os dados ficam no **Oracle Database**, onde rotinas em **PL/SQL** geram as doses a partir da periodicidade e controlam o estoque."

**Slide 11**
> "Todo o projeto é gerenciado e testado no **Azure DevOps**, com quadro de tarefas, repositório, pipeline e planos de teste."

## 4:05–5:00 · Encerramento (Enzo)
**Slide 12**
> "O Hora Certa nasceu de uma pergunta simples e está alinhado a três Objetivos de Desenvolvimento Sustentável da ONU."
>
> "Ao **ODS 3, Saúde e Bem-Estar**, porque ajuda o idoso a seguir o tratamento corretamente e reduz internações que poderiam ser evitadas."
>
> "Ao **ODS 10, Redução das Desigualdades**, porque foi desenhado para quem tem mais dificuldade com tecnologia: letra grande, poucos botões e o WhatsApp, que eles já conhecem."
>
> "E ao **ODS 11, Cidades e Comunidades Sustentáveis**, porque fortalece a rede de cuidado em volta de quem envelhece, conectando família, médico e transporte."
>
> "Os próximos passos são testar com idosos e cuidadores reais, firmar a parceria com a Uber e chegar a novos públicos, como pessoas com deficiência."
>
> "Porque cuidar de quem a gente ama não deveria depender de memória nem de sorte. **Hora Certa: ninguém precisa cuidar sozinho.**"

---

## Checklist antes de gravar
- [ ] Os rostos e as vozes dos três aparecem no vídeo (obrigatório; nada de voz gerada por IA).
- [ ] Trocar os mockups do slide 8 por **prints reais** do protótipo em Flutter ou Kotlin (o briefing pede "printscreen de protótipos").
- [ ] Colocar o link público do vídeo no slide 1 e gerar o PDF final.
- [ ] Gravar a demo com os dados de exemplo: Maria, Losartana, Metformina, Sinvastatina, cardiologista às 14h.
- [ ] Deixar as telas abertas na ordem da tabela da demo, para a narração não travar.
- [ ] Ensaiar com cronômetro: demo (Vitor) + arquitetura (Enzo) precisam somar pelo menos 2 min 30 s.
- [ ] Exportar em HD, subir no YouTube como **público** e testar o link deslogado.
- [ ] Só um integrante entrega o .ZIP (PDF dos slides + link do vídeo) na área de Software Projects Quality Assurance, até **19/11/2026 às 23h55**. Depois baixem o arquivo enviado e confiram.
