# Decisão 001 — Definição do MVP (sessão grill-me)

Sessão de perguntas usando a skill *grill-me* (mattpocock/skills) para definir o projeto.

| # | Pergunta | Decisão |
|---|---|---|
| Q1 | O que é o projeto | App de lembrete de remédios e consultas para idosos |
| Q2 | Tipo | App |
| Q3 | Motivação/prazo | Trabalho CitizenTech; MVP para pitch no fim da semana |
| Q4 | Sucesso | Virar contexto reutilizável em outras matérias (Flutter, Java, Kotlin) |
| Q5 | Quem usa | Idoso + cuidador/familiar |
| Q6 | MVP | Remédios, consultas integradas a agendas, lembrete para idoso e cuidador via WhatsApp, Uber |
| Q7 | Entrega | Só documentação e pitch |
| Q8 | Formato do contexto | Markdown independente de linguagem |
| Q9 | Acessibilidade | Fonte grande, alto contraste, máx. 3 botões, linguagem simples |
| Q10 | Equipe | Grupo, com slides |
| Q11 | Escalonamento | App → +15 min WhatsApp idoso → +15 min WhatsApp cuidador → ligação 1 toque pelo cuidador |
| Q12 | Agendas | Idoso e cuidador; qualquer agenda |
| Q13 | Uber | Deep link agora; parceria formal no futuro |
| Q14 | Vínculo | N idosos ↔ N cuidadores |
| Q15 | Plataforma | Android + iOS + backend |
| Q16 | LGPD | Seção de privacidade e consentimento |
| Q17/Q22 | Persona | Dona Maria (78) e Carlos (45) |
| Q18–Q20 | Público | Só idosos; outros públicos como próximos passos |
| Q21 | Padrão de agenda | .ics |
| Q23 | Nome | Hora Certa |
| Q24–Q26 | Pitch | .pptx, 5 min, 8 slides |

# Decisão 002 — Novas features (2ª rodada)

| # | Feature | Decisão |
|---|---|---|
| — | Periodicidade ("às 8h, de 8 em 8h") | ✅ MVP (proposta do Nicolas) |
| Q27 | Controle de estoque | ✅ MVP |
| Q28 | OCR de receita | ❌ Depende muito da prescrição |
| Q29 | Imagem do remédio | ✅ MVP — imagem da internet/catálogo, sem foto do idoso |
| Q30 | Botão SOS | ✅ MVP |
| Q31 | Relatório para o médico | ✅ MVP |
| Q32 | Voz | ❌ |
| Q33 | Sinais vitais | ❌ |
| Q34 | Interação medicamentosa | ❌ Se está prescrito, o app não pode contrariar |
| Q35 | Repositório | GitHub: NicolasPadovam/HoraCerta_Repository |

**Princípio que emergiu:** o app organiza e lembra a prescrição — nunca a contraria.
