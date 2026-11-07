---
name: aplicar-identidade-hora-certa
description: Aplica a identidade visual oficial do Hora Certa (paleta azul, Nunito + Atkinson Hyperlegible, botão Tomei com degrau, regras de acessibilidade para idosos) em um projeto JÁ EXISTENTE em Flutter, Android/Kotlin (Jetpack Compose ou XML) ou Java (Android Views). Use quando pedirem para "aplicar o design", "aplicar a identidade visual", "deixar no padrão Hora Certa", "remodelar as telas", "trocar as cores/fontes do app" ou revisar se uma tela segue o padrão visual.
---

# Aplicar a identidade visual Hora Certa

Você vai **restilizar um app que já está sendo construído por outra pessoa**. Seu papel é só a **camada visual**: tema, tokens, componentes e aparência das telas. **Não mude** arquitetura, navegação, regras de negócio, nomes de classes públicas, chamadas de API ou estrutura de pastas além do necessário para adicionar o tema.

## Fonte de verdade
Repositório de contexto: https://github.com/NicolasPadovam/HoraCerta_Repository
- `design/tokens.json` — **todos os valores** (cores, fontes, tamanhos, raios). Nunca invente um valor que não esteja aqui.
- `design/DESIGN.md` — regras de uso e especificação dos componentes.
- `design/hora-certa-handoff.md` — o que cada tela (T1–T9) deve mostrar.
- `contexto/TELAS.md` — telas, fluxos e dados de exemplo.

Se esses arquivos não estiverem no diretório atual, clone o repositório (raso) numa pasta temporária e leia de lá. Se `tokens.json` divergir dos exemplos de código deste skill, **o tokens.json vence**.

## Passo a passo
1. **Detecte a plataforma**:
   - `pubspec.yaml` → Flutter → leia `references/flutter.md`
   - `build.gradle(.kts)` com `compose` / `@Composable` → Kotlin Compose → `references/android-compose.md`
   - `res/layout/*.xml`, Activities em Java ou Kotlin com Views → `references/android-views.md` (vale para **Java** e Kotlin XML)
2. **Mapeie o que existe**: tema atual, cores/fontes hardcoded (`Color(0x…)`, `#…`, `Colors.blue`, `textSize`), botões e campos customizados, e quais telas T1–T9 já existem.
3. **Crie o tema central** a partir de `tokens.json` (um único lugar com cores, tipografia, formas e dimensões), seguindo o arquivo de referência da plataforma.
4. **Adicione as fontes** Nunito (800, 900) e Atkinson Hyperlegible (400, 700) como arquivos locais do projeto (Google Fonts, licença OFL). Prefira arquivos empacotados a download em tempo de execução: o app precisa funcionar offline.
5. **Crie os componentes base** (nomes sugeridos, adapte à convenção do projeto): `TomeiButton`, `SecondaryButton`, `ExternalActionButton`, `SosButton`, `StatusTag`, `HcTextField`, `HcCard`, `DoseBar`.
6. **Substitua nas telas** os estilos hardcoded por tokens e os botões/campos genéricos pelos componentes base. Trabalhe **uma tela por vez**.
7. **Rode o checklist** abaixo em cada tela tocada e corrija.
8. **Relate**: liste arquivos criados/alterados, telas restilizadas, e qualquer violação que não pôde corrigir sem mexer em lógica (ex.: tela com 5 botões) — **não reestruture a tela, só aponte**.

## Checklist (toda tela)
- [ ] Nenhuma cor/fonte/tamanho hardcoded — tudo vem do tema.
- [ ] Fundo `background` (#F5F8FD), não branco puro.
- [ ] Nenhum texto < 18; corpo 22; botões 26–34 bold.
- [ ] Toda área tocável ≥ 64; botão Tomei 88–96; espaço entre botões ≥ 16.
- [ ] App do idoso: no máximo 3 botões por tela (+ SOS no canto superior direito).
- [ ] Verde só para tomei/tudo certo; terracota só para SOS/atraso; âmbar sempre com texto escuro.
- [ ] Todo status com **ícone + palavra + cor**.
- [ ] Bordas de 3 px em vez de sombras com blur (exceção: degrau sólido do Tomei).
- [ ] Ícones de linha com rótulo; **sem emoji** na interface.
- [ ] Textos em linguagem simples ("Já tomou?", "Lembrar em 10 min", "Pedir carro").
- [ ] Rótulos de acessibilidade (contentDescription / Semantics) nos botões só-ícone e imagens de remédio.
- [ ] Testado com fonte do sistema em 130%: nada cortado (use quebra de linha, não reduza fonte).

## Comportamentos visuais obrigatórios
- **Tomei**: ao tocar → tela/realce verde, vibração curta, frase "Muito bem, Maria!", botão **Desfazer** por 10 s.
- **Lembrar em 10 min**: mostrar "Eu aviso de novo às HH:MM" + "Já tomei agora".
- **SOS**: toque → diálogo "Avisar sua família agora?" → tela "Sua família foi avisada" + [Ligar 192].
Se a lógica dessas ações não existir no projeto, implemente **só o visual** com um callback vazio/TODO e avise no relatório.
