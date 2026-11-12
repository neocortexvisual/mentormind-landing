# Mapa do código — MentorMind

## Versionamento

Esta cópia `mentormind-web-dev/` usa a branch `reestruturacao` do repositório `https://github.com/neocortexvisual/mentormind-landing.git`. A pasta `mentormind-web/` permanece na branch `main` como referência e não é alterada por esta implementação. O `.gitignore` exclui `node_modules/`, `dist/` e `.astro/`; o código, os assets, as regras e esta documentação são versionados.

Estado documentado em 12/11/2026. Este mapa descreve o que existe no projeto agora; a implementação nos arquivos de código é a fonte de verdade. Os números de linha abaixo são pontos de partida para localizar elementos e devem ser conferidos novamente após cada edição.

## Como a página é montada

`src/pages/index.astro` é a entrada da landing. Importa as sete seções e o CSS global nas linhas 1–9, define o documento HTML nas linhas 12–36 e compõe as seções dentro de `<main>` nas linhas 20–34, nesta ordem:

| Ordem | Marcador na página | Componente | Elemento raiz | Situação |
| --- | --- | --- | --- | --- |
| 01 | `src/pages/index.astro:21` | `src/sections/home/Hero.astro` | `.hero` | Implementado |
| 02 | `src/pages/index.astro:22–23` | `src/sections/home/DemoSection.astro` | `#demonstracao.section-02` | Implementado |
| 03 | `src/pages/index.astro:24–25` | `src/sections/home/HowItWorks.astro` | `#secao-03.section-03` | Experiência fixada no scroll com três etapas e degradês |
| 04 | `src/pages/index.astro:26–27` | `src/sections/home/EditorPreview.astro` | `#secao-04.section-04` | Manifesto à esquerda e monitor ampliado à direita sobre preto |
| 05 | `src/pages/index.astro:28–29` | `src/sections/home/TeacherStories.astro` | `#secao-05.section-05` | Lettering e demonstração com cinco etapas interativas |
| 06 | `src/pages/index.astro:30–31` | `src/sections/home/Pricing.astro` | `#secao-06.section-06` | Cartão central de depoimento demonstrativo |
| 07 | `src/pages/index.astro:32–33` | `src/sections/home/Faq.astro` | `#secao-07.section-07` | Área branca vazia |

O CSS de `src/styles/global.css:1–14` define o fundo roxo quadriculado no `html` e remove a margem padrão do `body`. Cada seção mantém seus estilos no próprio arquivo `.astro`. `src/styles/tokens.css` está vazio: as cores, fontes e medidas atuais estão escritas localmente nas seções.

## Árvore de pastas e arquivos

```text
mentormind-web/
├── mapa.md                             ← este inventário e roteiro de auditoria
├── git explicação geral da página por sessões.md  ← histórico descritivo por seção
├── rules/
│   ├── 1.md                           ← regras de escopo e entrega
│   └── 2.md                           ← regras de arquitetura e responsividade
├── public/                             ← arquivos servidos diretamente pela URL
│   ├── characters/
│   │   ├── reader.png                  ← personagem leitor da seção 01
│   │   ├── writer.png                  ← personagem com caderno da seção 01
│   │   └── cyclist.png                 ← personagem na bicicleta da seção 01
│   ├── section-02-preview.png          ← imagem 4 usada na seção 02
│   ├── section-02-coffee.png           ← xícara da seção 02
│   ├── section-03-card.png             ← forma branca reutilizada nos três conteúdos da seção 03
│   ├── section-04-background.png       ← cópia da imagem 7, atualmente sem uso
│   ├── section-04-monitor.png          ← imagem 8, pessoa sobre monitor na seção 04
│   ├── favicon.svg                     ← vazio
│   └── robots.txt                      ← vazio
├── src/
│   ├── pages/
│   │   ├── index.astro                 ← documento e ordem das seções
│   │   └── blog/
│   │       ├── index.astro             ← vazio; lista futura
│   │       └── [slug].astro            ← vazio; artigo futuro
│   ├── sections/home/
│   │   ├── Hero.astro                  ← seção 01
│   │   ├── DemoSection.astro           ← seção 02
│   │   ├── HowItWorks.astro            ← seção 03
│   │   ├── TeacherRoutine.astro        ← vazio
│   │   ├── EditorPreview.astro         ← seção 04, manifesto com monitor central
│   │   ├── TeacherStories.astro        ← seção 05, lettering e demonstração interativa
│   │   ├── Pricing.astro               ← seção 06, cartão de depoimento demonstrativo
│   │   ├── Faq.astro                   ← seção 07, área branca vazia
│   │   ├── FinalCta.astro              ← vazio
│   │   └── BlogPreview.astro           ← vazio
│   ├── layouts/
│   │   ├── SiteLayout.astro            ← vazio
│   │   └── ArticleLayout.astro         ← vazio
│   ├── components/
│   │   ├── ui/                          ← vazio; componentes visuais futuros
│   │   └── site/                        ← vazio; componentes do site futuros
│   ├── features/
│   │   ├── lesson-demo/                ← vazio; interação futura
│   │   └── coffee-scene/               ← vazio; cena futura
│   ├── content/blog/                   ← vazio; artigos futuros
│   ├── assets/                         ← vazio; assets importados futuros
│   ├── styles/
│   │   ├── global.css                  ← fundo e margem da página
│   │   └── tokens.css                  ← vazio
│   ├── config/site.ts                  ← vazio
│   └── content.config.ts               ← vazio
├── astro.config.mjs                    ← configuração padrão do Astro
├── package.json                        ← scripts e dependências Astro e GSAP
├── package-lock.json                   ← versões instaladas
├── .nvmrc                              ← Node 22.22.3
└── .gitignore                           ← ignora node_modules, dist e .astro
```

`README.md` não existe. As pastas vazias não contêm implementação oculta. A navegação/header, os layouts, o blog e as features ainda não estão montados na página.

## Índice de elementos por seção

Os intervalos indicam a localização atual, não uma API estável. Para encontrar um elemento depois de mudanças, procure também pelo seletor ou pelo texto indicado.

### Seção 01 — Hero (`src/sections/home/Hero.astro`, linhas 1–227)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Limite da seção e título acessível | 1–21 | 24–40 | `.hero`, `hero-title` |
| Bloco central | 2–17 | 43–48 e 156–159 | `.hero__content` |
| Selo “Planejamento de aula” | 3 | 50–63 | `.hero__eyebrow` |
| Título principal | 4 | 65–73 | `#hero-title` |
| Descrição | 5–7 | 75–81 | `.hero__description` |
| Grupo de ações | 8–15 | 83–118 | `.hero__actions`, `.hero__button` |
| Estados dos botões | 9–14 | 120–127 | `:hover`, `:focus-visible` |
| Nota abaixo dos botões | 16 | 129–133 | `.hero__note` |
| Leitor, escritora e ciclista | 18–20 | 161–226 | `.hero__character` |
| Ajustes de celular | — | 135–154 e 208–226 | `@media` |

Assets ligados ao Hero: `public/characters/reader.png`, `writer.png` e `cyclist.png`. As imagens são decorativas (`alt=""`) e o Hero recorta a decoração com `overflow: hidden` **na própria seção**. “Ver um exemplo” aponta para `#demonstracao` (seção 02); “Criar meu plano” aponta para `#criar-plano`, ainda sem destino implementado.

### Seção 02 — Demonstração/rotina (`src/sections/home/DemoSection.astro`, linhas 1–139)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Seção branca | 2–13 | 16–21 | `#demonstracao`, `.section-02` |
| Janela cruzando a fronteira com o Hero | 3 | 23–41 | `.section-02__preview` |
| Grade do conteúdo | 4–12 | 43–53 e 123–130 | `.section-02__story` |
| Xícara | 5 | 55–61 e 131–133 | `.section-02__coffee` |
| Coluna do texto | 6–11 | 63–66 | `.section-02__copy` |
| Selo “A rotina é real” | 7 | 68–76 | `.section-02__eyebrow` |
| Título | 8 | 78–85 | `.section-02__copy h2` |
| Descrição | 9 | 87–92 | `.section-02__description` |
| CTA | 10 | 94–121 e 135–137 | `.section-02__action` |

Assets: `public/section-02-preview.png` e `public/section-02-coffee.png`. A janela tem raio de **18 px** (`DemoSection.astro:31`) e fica centralizada sobre a divisão das seções por `top: 0`, `left: 50%` e `transform: translate(-50%, -50%)`. A grade fica em duas colunas no desktop e uma coluna até 700 px. O CTA aponta para `#criar-plano`, ainda sem destino implementado.

### Seção 03 — Jornada controlada pelo scroll (`src/sections/home/HowItWorks.astro`, linhas 1–458)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Área em largura total e cena | 2–66 | 69–100 e 251–261 | `#secao-03`, `.section-03__scene` |
| Três camadas de degradê | 5–9 | 92–120 | `.section-03__color--green`, `--orange`, `--blue` |
| Título de abertura | 11–14 | 128–160 | `.section-03__opening` |
| Coluna numérica | 18–22 | 162–167 e 280–292 | `.section-03__numbers` |
| Três artigos de conteúdo | 24–64 | 169–249 e 294–312 | `.section-03__stage` |
| Forma branca original | 31–35, 44–48, 57–61 | 211–249 | `.section-03__card` |
| Ajustes para celular | — | 317–382 | `@media (max-width: 700px)` |
| Timeline e ScrollTrigger | — | 384–458 | `TIMING`, `scrollTrigger`, `media.add` |

A seção agora ocupa toda a largura e pelo menos uma tela. O título preserva a frase “Da sua primeira ideia ao plano de aula, com espaço para ensinar do seu jeito.”; os três artigos apresentam ideia, contexto e plano. O arquivo `public/section-03-card.png` continua como forma decorativa dentro de cada artigo. O fundo é formado por três degradês CSS independentes: verde/roxo, roxo/laranja e azul. Os valores locais em `HowItWorks.astro:70–75` reutilizam as cores já usadas no site; `tokens.css` permanece vazio. A área laranja cresce pela direita e por baixo, ocupa aproximadamente metade da composição e desaparece antes do azul final.

O script usa GSAP + ScrollTrigger em uma timeline com pin e scrub, sem loop automático. Para alterar o ritmo, edite `TIMING.read`, `TIMING.transition` e `TIMING.scrollScreens` em `HowItWorks.astro:402`; para mover a coluna numérica, altere `--section-03-number-center` em `HowItWorks.astro:75`; para mudar a proporção da mancha laranja, ajuste o degradê em `HowItWorks.astro:112–116`. As camadas, o título, os números e os artigos têm animações separadas. Com `prefers-reduced-motion: reduce` (ou sem JavaScript), os três artigos aparecem em fluxo normal, sem pin. `package.json` e `package-lock.json` incluem GSAP 3.15.1. O marcador `<!-- Seção 03 -->` permanece em `src/pages/index.astro:24`.

### Seção 04 — Manifesto com monitor (`src/sections/home/EditorPreview.astro`, linhas 1–159)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Área preta de pelo menos uma tela | 2–14 | 17–30 | `#secao-04`, `.section-04` |
| Coluna de texto à esquerda | 3–9 | 32–37 | `.section-04__copy` |
| Rótulo “Quem ensina importa” | 4 | 39–47 | `.section-04__eyebrow` |
| Título serifado e laranja | 5 | 49–60 | `#section-04-title`, `.section-04__highlight` |
| Descrição e frase em negrito | 6–7 | 62–73 | `.section-04__description`, `.section-04__emphasis` |
| Chamada sublinhada do blog | 8 | 75–81 | `.section-04__callout` |
| Monitor ampliado à direita | 11–13 | 83–102 | `.section-04__figure`, `.section-04__figure img` |
| Empilhamento no celular | — | 104–130 | `@media (max-width: 800px)` |
| Pausa curta no scroll | — | 133–159 | `HOLD_SCREENS`, `ScrollTrigger.create` |

A Seção 04 começa após a Seção 03 e mantém fundo preto sólido `#000`, com texto branco `#fff`, sem grade. A coluna esquerda reúne o novo rótulo “QUEM ENSINA IMPORTA”, o título em três linhas, a descrição, “Valorizamos quem ensina.” e a chamada do blog. O título usa Georgia; “humano.”, inclusive o ponto, usa o laranja `#cb5230` do tênis. Os textos de apoio usam Arial e o rótulo usa Courier New. O monitor original `public/section-04-monitor.png` aparece ampliado à direita e é recortado pela própria seção; a figura enquadra as margens transparentes do PNG. Até 800 px, texto e imagem ficam empilhados na mesma estrutura HTML, sem rolagem lateral. A chamada “Confira a matéria completa no blog ↗” permanece texto visual, sem link nesta etapa. A cópia `public/section-04-background.png` permanece no projeto sem uso. O marcador `<!-- Seção 04 -->` está em `src/pages/index.astro:26`.

Ao chegar ao topo, a Seção 04 fica fixada por uma distância adicional de scroll equivalente a 45% da altura da tela no desktop ou 20% no celular. Ajuste esses valores em `HOLD_SCREENS` (`EditorPreview.astro:142`). O script usa o GSAP/ScrollTrigger já instalado; `refreshPriority: -1` faz a medição ocorrer depois da Seção 03. Com `prefers-reduced-motion: reduce`, não há fixação.

### Seção 05 — Lettering e demonstração interativa (`src/sections/home/TeacherStories.astro`, linhas 1–329)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Área branca de pelo menos uma tela | 2–31 | 34–41 | `#secao-05`, `.section-05` |
| Rótulo roxo | 4 | 48–57 | `.section-05__eyebrow` |
| Título serifado | 5 | 59–68 | `#section-05-title`, `.section-05 h2` |
| Descrição | 6 | 70–78 | `.section-05__description` |
| Marcador do layout | 8 | — | `<!-- layout demonstrativo -->` |
| Abas interativas | 10–16 | 95–135 e 254–329 | `.section-05__demo-tabs`, `role="tab"`, `showPage` |
| Área de prévia cinza | 17–21 | 137–168 | `#section-05-demo-panel` |
| Faixa informativa inferior | 22–29 | 170–207 | `.section-05__demo-footer` |
| Chamada roxa abaixo do layout | 30 | 209–216 | `.section-05__callout` |
| Ajustes para celular | — | 218–252 | `@media (max-width: 520px)` |

A Seção 05 vem após a Seção 04, com fundo branco e altura mínima de uma viewport. No topo, mostra “SUA AULA, SUAS ESCOLHAS” em Courier New roxo `#6913bf`, “A aula ganha forma com você.” em Georgia e a descrição em Arial. O layout demonstrativo substitui a imagem 4 nesta seção e tem largura máxima de 820 px. A faixa preta das abas agora alcança as bordas laterais da moldura (`TeacherStories.astro:98`). As cinco abas são botões: JavaScript local troca o texto e o número da prévia cinza, o destaque da aba e a faixa inferior para cada etapa. Setas esquerda/direita, Home e End também navegam entre elas. Abaixo aparece “Criar meu plano” em roxo; nesta etapa é texto, sem ação de clique. A imagem 4 continua em `public/section-02-preview.png` para a Seção 02. O marcador `<!-- Seção 05 -->` está em `src/pages/index.astro:28`.

### Seção 06 — Comentários de professores (`src/sections/home/Pricing.astro`, linhas 1–141)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Área branca de uma tela | 2–28 | 31–40 | `#secao-06`, `.section-06` |
| Cartão central | 4–27 | 42–58 | `.section-06__card` |
| Rótulo e aspas | 6–7 | 60–78 | `.section-06__eyebrow`, `.section-06__quote-mark` |
| Comentário demonstrativo | 10–12 | 80–87 | `.section-06__quote` |
| Círculo roxo e identificação | 15–21 | 89–114 | `.section-06__avatar`, `.section-06__author-copy` |
| Pontos decorativos | 24–26 | 116–132 | `.section-06__dots` |
| Ajuste para celular | — | 134–140 | `@media (max-width: 520px)` |

A Seção 06 vem após a Seção 05, com fundo branco e altura mínima de uma viewport para continuar o scroll. Um cartão branco com borda sutil fica centralizado na seção. O círculo de perfil é roxo sólido `#6913bf`; não há imagem de avatar. O texto e a identificação são demonstrativos, explicitamente marcados no código para substituição por um depoimento autorizado. Os três pontos reproduzem a referência visual e não têm ação de navegação. Cada bloco de HTML e CSS da seção contém comentários que explicam sua função. O marcador `<!-- Seção 06 -->` está em `src/pages/index.astro:30`.

### Seção 07 — Área branca (`src/sections/home/Faq.astro`, linhas 1–10)

| Elemento | HTML atual | Estilo atual | Seletor ou texto de busca |
| --- | --- | --- | --- |
| Área branca de uma tela | 2 | 5–9 | `#secao-07`, `.section-07` |

A Seção 07 vem após a Seção 06, com fundo branco e altura mínima de uma viewport para continuar o scroll. O marcador `<!-- Seção 07 -->` está em `src/pages/index.astro:32`. O conteúdo da seção ainda não foi definido.

## Como separar os elementos daqui para frente

1. **Página compõe.** Mantenha `src/pages/index.astro` como índice de imports e ordem das seções. Ao adicionar outra seção, inclua um marcador numerado, o componente e uma entrada neste mapa. Evite pôr o conteúdo visual diretamente na página.
2. **Seção apresenta.** Mantenha HTML, textos e CSS específico no `.astro` da própria seção. Nomeie classes pelo prefixo da seção (`hero__...`, `section-02__...`, `section-03__...`) para localizar estilos sem afetar outras áreas.
3. **Elemento compartilhado exige uso real.** Só mova botão, selo, cartão ou outro elemento para `src/components/ui/` ou `src/components/site/` quando houver pelo menos dois usos com comportamento e aparência compatíveis. Registre no mapa quais seções o importam.
4. **Interação é feature.** Quando a demonstração de aula ou a cena da xícara ganhar estado/controles, implemente em `src/features/lesson-demo/` ou `src/features/coffee-scene/` e mantenha na seção apenas a apresentação e o ponto de montagem. As duas pastas estão vazias hoje.
5. **Global é global.** `src/styles/global.css` deve conter apenas regras da página inteira. Quando `tokens.css` ganhar valores aprovados, documente os nomes e substitua gradualmente valores repetidos; não invente tokens antes de existirem.
6. **Assets têm dono identificável.** Use nomes que indiquem a seção e a função, como `section-02-coffee.png`. Registre o caminho e o uso neste mapa; mantenha os arquivos originais enquanto forem a referência visual.

Essa separação é uma convenção para futuras edições; não implica criar agora os arquivos vazios ou refatorar o código que já funciona.

## Como filtrar, verificar e auditar

Execute os comandos abaixo na raiz da cópia `mentormind-web-dev/`, branch `reestruturacao`. Use `rg -n` para obter o número de linha atual, pois os números deste documento mudam quando o código muda.

```bash
# Localizar as seções e sua ordem na página
rg -n 'import (Hero|DemoSection|HowItWorks|EditorPreview|TeacherStories|Pricing|Faq)|Seção 0[1234567]|<(Hero|DemoSection|HowItWorks|EditorPreview|TeacherStories|Pricing|Faq) />' src/pages/index.astro src/sections/home

# Localizar exatamente um elemento e todos os seus estilos
rg -n 'hero__button|section-02__coffee|section-03__stage|section-03__color' src/sections/home

# Auditar IDs e links internos; todo href="#..." deve ter um id correspondente
rg -n 'href="#[^"]+"|id="[^"]+"' src

# Listar referências a assets e confirmar que os arquivos existem
rg -n 'src="/' src/sections/home
rg --files public

# Conferir quais arquivos continuam vazios
python3 -c 'from pathlib import Path; print("\n".join(str(p) for p in Path("src").rglob("*") if p.is_file() and p.stat().st_size == 0))'

# Conferir as linhas atuais de cada seção
rg -n '^<section|^  <|^  \.|^  @media' src/sections/home/{Hero,DemoSection,HowItWorks,EditorPreview,TeacherStories,Pricing}.astro
```

Para auditar a origem das imagens, compare os hashes SHA-256 abaixo com `sha256sum public/characters/*.png public/section-02-*.png public/section-03-*.png public/section-04-*.png`. Um hash diferente indica que o arquivo mudou, não necessariamente um problema; investigue antes de atualizar o registro.

| Asset | SHA-256 nesta versão |
| --- | --- |
| `public/characters/reader.png` | `8dad8a0c582d99013a543a8b379ceab1c3a6f4a18842bc118e76016480c4536b` |
| `public/characters/writer.png` | `98a3b93021cb63caad30f3c576ad45ec56c24dc0303ec667a429e8bd9fac9e7f` |
| `public/characters/cyclist.png` | `f5ab57812a8422e40338a1c175c6bcec49a43621cf311caf6588cc4f69bb1564` |
| `public/section-02-preview.png` | `544a2c9b66fbe690f356a6e67cb5cae6a379b729d4caf395c12096915f70a308` |
| `public/section-02-coffee.png` | `b8f3848ad94aef93560f41b02335a7ed1182dd0e7230ee71657a33a00a965d82` |
| `public/section-03-card.png` | `932cd979b83175b9d070702e2d92d14329d54a5dfb8020ab83556777299657c9` |
| `public/section-04-background.png` | `e934f6bfea09790a6329b19ddf1da9e6e0fe1b1b0707f308e227f84aa5a6ad2d` |
| `public/section-04-monitor.png` | `26bf908ba48532fde0a6353ee1fecc7531f207ec581fd9cfe7556eb2e8ce9f1e` |

Ao revisar uma mudança, confirme: **(a)** seção/elemento afetado e arquivo responsável, **(b)** linhas e seletores atualizados, **(c)** assets e hashes alterados, **(d)** links com destino existente, **(e)** resposta HTTP e ausência de rolagem horizontal em 360 px e 1440 px, **(f)** atualização deste mapa e da explicação por seções. O projeto não tem teste automatizado de interface; essa revisão visual continua necessária para mudanças de layout. O diretório `mentormind-web/` não é atualmente um repositório Git, então não presuma que `git diff` ou `git status` funcionem nele.
