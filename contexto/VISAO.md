# Hora Certa — Visão do Produto

> Documento de contexto independente de linguagem. Use-o como base para implementar o app em qualquer tecnologia (Flutter, Kotlin, Java etc.).

## Origem
Trabalho de faculdade — disciplina **CitizenTech**: criar uma solução tecnológica de impacto social. Entrega atual: documentação + pitch (MVP conceitual, sem código).

## Problema
Idosos frequentemente tomam vários remédios por dia e têm consultas recorrentes. Esquecer doses, tomar em dobro ou perder consultas é comum. A família, que muitas vezes trabalha o dia todo, não tem como saber se o idoso tomou o remédio — e vive com essa preocupação.

## Solução
**Hora Certa** é um app mobile que conecta o **idoso** ao seu **cuidador/familiar**:
- lembra o idoso dos remédios e consultas na hora certa;
- confirma se o remédio foi tomado (botão grande "Tomei");
- avisa o cuidador pelo WhatsApp quando algo não foi confirmado;
- coloca as consultas na agenda de todos e facilita o transporte (Uber).

## Público-alvo (MVP)
Somente **idosos** e seus **cuidadores/familiares**.

## Personas
### Dona Maria — 78 anos (pessoa cuidada)
- Hipertensa e diabética, toma 5 remédios por dia.
- Mora sozinha, é independente, mas esquece doses e horários.
- Usa WhatsApp para falar com a família; tem pouca familiaridade com apps complexos.
- Dor: "Às vezes não lembro se já tomei o remédio da pressão."

### Carlos — 45 anos (cuidador/familiar)
- Filho da Dona Maria, trabalha o dia todo.
- Se preocupa sem saber se a mãe tomou os remédios ou foi às consultas.
- Dor: "Queria estar perto, mas não consigo ligar para ela toda hora."

## Proposta de valor
- **Para a Dona Maria:** autonomia e segurança, com um app simples de usar.
- **Para o Carlos:** tranquilidade — só é acionado quando realmente precisa.

## Diferenciais
1. Lembrete **escalonado** (app → WhatsApp do idoso → WhatsApp do cuidador).
2. Integração com **WhatsApp**, que o idoso já usa.
3. Consultas enviadas para **qualquer agenda** (Google, Outlook, Apple) via .ics.
4. **Pedir Uber** com 1 toque, com o endereço da consulta preenchido.
5. **Periodicidade inteligente:** 1 remédio = 1 configuração ("às 8h, de 8 em 8 horas"), sem criar vários alarmes.
6. **Estoque, SOS e relatório para o médico:** o remédio não acaba, a família é acionada numa emergência e o médico vê a adesão real.
7. **Acessibilidade** como regra: fonte grande, alto contraste, poucos botões.

## Princípio
O app **organiza e lembra a prescrição médica — nunca a contraria.**

## Próximos passos (fora do MVP)
- Expandir para outros públicos: pessoas com deficiência, doenças crônicas, pós-operatório, saúde mental, crianças com medicação controlada.
- Parceria formal com a Uber (desconto / conta corporativa).
- Integração direta via API com Google Calendar e Outlook.
