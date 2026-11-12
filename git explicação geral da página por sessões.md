# Explicação geral da página por seções

O inventário técnico de pastas, arquivos, elementos e linhas atuais está em `mapa.md`.

## 1. Hero

- Implementado em `src/sections/home/Hero.astro` e renderizado por `src/pages/index.astro`.
- Apresenta o título “Sua próxima aula ganha forma.”, a descrição, os links “Criar meu plano” e “Ver um exemplo” e a chamada “Experimente antes de criar seu plano”.
- Segue o print com fundo roxo quadriculado, título serifado, botão principal verde e botão secundário translúcido. A navegação fica para outra tarefa.
- Mantém os estilos específicos no próprio Hero e usa a mesma estrutura HTML em todas as larguras. No celular, os botões ocupam a largura disponível. A seção recorta eventuais decorações dentro dos seus limites.
- O Hero ocupa no mínimo a altura visível da tela e centraliza o bloco de conteúdo nos dois eixos. O espaçamento mínimo acima e abaixo é de 96 px no desktop e 64 px no celular; em telas baixas, a seção cresce para acomodar o conteúdo sem cortes.
- Centralização conferida no Chromium em 360 × 900, 1440 × 900 e 360 × 568: bloco no centro horizontal, espaços superior e inferior iguais e nenhuma rolagem lateral.
- O fundo roxo agora preenche toda a página, inclusive abaixo do Hero, sem as margens brancas padrão. `src/styles/global.css`, importado pela página inicial, define o fundo global e a textura quadriculada com células de 24 px e linhas claras sutis, seguindo a referência enviada. O Hero fica transparente para manter a continuidade da textura. Não há bloqueio de rolagem horizontal no body.
- Fundo verificado no Chromium em 360 × 900 e 1440 × 900: margem de 0 px, altura mínima de 900 px, textura de 24 px e nenhuma rolagem horizontal nas duas larguras.
- `src/styles/tokens.css` está vazio; por isso, os valores visuais são locais. A integração com os tokens depende da sua definição futura.
- Pendências: README ausente e imagens decorativas laterais indisponíveis em `src/assets`.
- Os links apontam para `#criar-plano` e `#demonstracao`, cujos destinos ainda precisam ser implementados nas tarefas correspondentes.
- Verificação: página respondendo HTTP 200 e conferida no Chromium em 360 px e 1440 px, sem rolagem horizontal (largura do documento igual à largura da viewport em ambos os casos).

## Execução local

- Astro 7.4.1 instalado após a autorização para colocar o projeto para rodar. `package.json` define os comandos `dev`, `build` e `preview`; `package-lock.json` registra as versões instaladas.
- `astro.config.mjs` usa a configuração padrão. `.gitignore` exclui dependências e artefatos gerados; `.nvmrc` seleciona o Node 22.22.3 já disponível na máquina.
- `src/pages/index.astro` inclui o documento em português, título e viewport para a visualização correta no celular, mantendo a composição com o Hero.
- Servidor local iniciado em `http://127.0.0.1:4321/`. Para iniciar novamente: entrar em `mentormind-web`, executar `nvm use` e `npm run dev`.
- A instalação foi concluída sem vulnerabilidades reportadas pelo npm. A verificação desta entrega cobre a página inicial em desenvolvimento; o build de produção e as páginas vazias do blog não foram validados.

## Personagens do Hero

- As três imagens fornecidas foram adicionadas como assets em `public/characters/`: leitor (`1.png`), personagem com caderno (`2.png`) e ciclista (`3.png`). Os arquivos foram copiados sem alteração.
- O Hero mantém o conteúdo e os estilos existentes; foram acrescentados somente os três elementos de imagem e regras de posicionamento. O leitor fica no alto à esquerda, a personagem com caderno à direita e a ciclista na base esquerda, como na referência. O cabeçalho da referência não foi implementado.
- As imagens são decorativas, sem texto alternativo para leitura em voz alta e sem capturar cliques. A seção recorta os trechos que ultrapassam seus limites.
- Conferido no Chromium em 360 px e 1440 px: os três PNGs carregam e a largura do documento corresponde à largura da tela, sem rolagem lateral.

## Seção 02

- `src/pages/index.astro` renderiza `DemoSection.astro` após o Hero, com o marcador `<!-- Seção 02 -->`.
- Por enquanto, a seção é uma área vazia inteiramente branca, com no mínimo a altura da tela. Ela permite rolar após o Hero e serve como destino do link “Ver um exemplo” por meio de `#demonstracao`.
- Verificação no Chromium em 360 px e 1440 px: a Seção 02 começa após o Hero, tem fundo branco, mede 900 px numa janela de 900 px de altura e a página pode rolar até 1800 px, sem rolagem horizontal.
- A imagem `4.png` foi copiada sem alteração para `public/section-02-preview.png`. Ela é renderizada em `DemoSection.astro`, centralizada horizontalmente e com o meio alinhado à fronteira entre o Hero e a Seção 02, conforme a referência. Em telas pequenas, sua largura é de 86% da viewport.
- O painel da imagem recebe fundo branco, cantos arredondados e uma sombra discreta para evitar que o PNG levemente translúcido revele os personagens do Hero através dele. A checagem no Chromium em 360 px e 1440 px confirmou carregamento, alinhamento à divisão das seções e ausência de rolagem lateral; no desktop, o centro visual considera os 15 px ocupados pela barra de rolagem.
- A imagem `5.png` foi copiada sem alteração para `public/section-02-coffee.png`. Abaixo do painel de prévia, a Seção 02 apresenta a xícara à esquerda e, à direita, o lettering “A rotina é real / Só tem quadro e papel? Dá para começar por aí.”, o texto de apoio e o CTA. O conjunto ocupa a largura central da área branca indicada na referência e empilha no celular. Os estilos foram acrescentados em `DemoSection.astro`, preservando o código existente.
- O CTA “Experimentar com uma aula” aponta para `#criar-plano`, cuja funcionalidade pertence à futura demonstração interativa.
- Verificação no Chromium em 360 px e 1440 px: a xícara carrega, o lettering e o CTA permanecem dentro da Seção 02, o arranjo fica lado a lado no desktop e empilhado no celular, sem rolagem horizontal.

## Seção 03

- `src/pages/index.astro` renderiza `HowItWorks.astro` após a Seção 02, com o marcador `<!-- Seção 03 -->`.
- A nova seção é uma área vazia inteiramente branca, com altura mínima de uma tela, pronta para receber o conteúdo seguinte. A página agora permite rolar além da Seção 02.
- Verificação no Chromium em 360 px e 1440 px: a Seção 03 começa logo após a Seção 02, tem 900 px de altura numa janela de 900 px, fundo branco e nenhuma rolagem horizontal.
- A Seção 03 contém um painel azul centralizado na área branca, com proporção e largura próximas à referência. O raio das bordas é de 18 px, igual ao painel de prévia da Seção 02. A forma é feita em CSS e não exige imagem ou dependência nova.
- Conferido no Chromium em 360 px e 1440 px: o painel fica centralizado nos dois eixos, mantém o raio de 18 px e não cria rolagem lateral.
- A imagem `6.png` foi copiada sem alteração para `public/section-03-card.png` e adicionada no centro do painel azul. O tamanho é proporcional ao painel e a imagem é decorativa.
- Conferido no Chromium em 360 px e 1440 px: a imagem carrega, permanece centralizada dentro do painel e não cria rolagem lateral.
- A imagem 6 agora aparece três vezes dentro do painel azul, em três colunas com espaçamento responsivo, reutilizando o mesmo arquivo PNG.
- Conferido no Chromium em 360 px e 1440 px: as três instâncias carregam e permanecem inteiras dentro do painel, sem rolagem lateral.
- O gradiente azul original foi restaurado no painel após a comparação com o roxo do Hero.
- A frase “Da sua primeira ideia ao plano de aula, com espaço para ensinar do seu jeito.” foi colocada no canto superior esquerdo do painel em Arial, em branco. As três imagens foram deslocadas para abrir espaço. Até 600 px, o painel fica um pouco mais alto para preservar a leitura.
- Verificação no Chromium em 360 px e 1440 px: a frase não encobre as imagens e não há rolagem lateral.
- A frase passou a usar o mesmo Arial, peso normal, tamanho responsivo e entrelinha da descrição do Hero. A largura foi ajustada para três linhas em 360 px e 1440 px; as imagens continuam separadas do texto, sem rolagem lateral.
- O padding interno do painel e o recuo da frase agora usam o mesmo valor responsivo (`--panel-inset`), de 16 px no celular e cerca de 50 px em 1440 px. Verificado em 360 px e 1440 px: a frase segue em três linhas, sem tocar nas imagens ou criar rolagem lateral.
- As três formas internas exibem a imagem original branca `section-03-card.png`. Cada aba mostra “DESENVOLVIMENTO DE NEGÓCIOS” em Courier New verde claro `#e3ee88`, sem sombra. No celular, as formas ficam empilhadas.
- Conferido no Chromium em 360 px e 1440 px: as três imagens carregam e permanecem dentro do painel azul, sem rolagem lateral.
- Na branch `reestruturacao`, a Seção 03 anterior foi substituída por uma experiência em largura e altura total. Uma timeline GSAP/ScrollTrigger fixa a cena e vincula a abertura, três artigos e as camadas verde/roxo, roxo/laranja e azul à posição do scroll. Os trechos de leitura e transição estão concentrados em `TIMING` dentro de `HowItWorks.astro`; a coluna numérica e o alcance do laranja são controlados por CSS local. Em movimento reduzido, a seção mostra os três artigos em fluxo normal sem pin. A frase de abertura e o asset branco `section-03-card.png` foram preservados. `package.json` e `package-lock.json` receberam GSAP 3.15.1. A página `index.astro` continua apenas compondo as seções.
- Conferido no Chromium em 1440 × 900, 360 × 900 e 360 × 640 px: as etapas e os fundos avançam e retrocedem com o scroll, o laranja ocupa uma área ampla à direita e embaixo, o azul preenche o final e não há rolagem lateral. Redimensionar durante a etapa laranja mantém a etapa visível e recalcula a largura. Com movimento reduzido, não há pin e os três artigos seguem em fluxo normal.

## Seção 04

- `src/pages/index.astro` renderiza `EditorPreview.astro` após a Seção 03, com o marcador `<!-- Seção 04 -->`.
- A Seção 04 tem no mínimo a altura da tela. O fundo agora é cinza escuro sólido `#292929`, com a mesma grade branca discreta de 24 px usada no Hero. A imagem 7 não é usada como fundo e permanece no projeto apenas como arquivo sem referência.
- Conferido no Chromium em 360 px e 1440 px após a troca para cinza: a grade cobre os 900 px de altura da seção e não há rolagem lateral.
- A Seção 04 agora usa fundo preto sólido e apenas o lettering da referência: título “O futuro da educação continua humano.” em Georgia; “Valorizamos quem ensina.”, os textos de apoio e a chamada sublinhada em Arial; “CONTINUE ESSA CONVERSA” em Courier New. A imagem central da referência não foi adicionada. A chamada do blog é texto visual, sem link nesta etapa.
- Conferido no Chromium em 360 px e 1440 px: título e blocos permanecem dentro da seção, que tem 900 px de altura numa janela de 900 px, sem rolagem horizontal.
- O padding superior da Seção 04 foi reduzido para aproximar o título do topo. O subtítulo, os textos de apoio, o rótulo em Courier New e a chamada sublinhada ficaram menores. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- O título principal da Seção 04 foi reduzido levemente, de `clamp(48px, 7.5vw, 128px)` para `clamp(46px, 7.1vw, 120px)`. Os demais textos mantêm o tamanho anterior. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- O fundo da Seção 04 passou para `#F3EBDD` e todo o texto para preto. A tipografia, o posicionamento e os tamanhos permanecem como estavam. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- O fundo da Seção 04 passou para cinza claro sólido `#F1F1F1`, aproximado do tom da amostra enviada. Os textos continuam pretos e o layout foi preservado. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- O fundo da Seção 04 foi alterado para branco sólido `#fff`; o texto permanece preto. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- A imagem original `8.png` foi copiada para `public/section-04-monitor.png` e inserida no centro da Seção 04. A área transparente lateral é enquadrada pelo componente, sem editar o arquivo. No desktop, a base do monitor fica alinhada à base dos blocos de texto inferiores; no celular, imagem e textos ficam empilhados. Conferido no Chromium em 360 px e 1440 px: a imagem carrega, a seção cresce quando necessário e não há rolagem lateral.
- No título da Seção 04, apenas a palavra “humano” passou a usar o verde claro `#e3ee88` do Hero; o ponto final e o restante do texto continuam pretos. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- A palavra “humano” passou do verde para o laranja `#cb5230`, amostrado do tênis da imagem 8. O ponto final e o restante do título continuam pretos. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- O fundo da Seção 04 voltou ao preto sólido `#000`. Título, textos inferiores e chamada ficaram brancos; somente “humano” mantém o laranja `#cb5230`. A imagem do monitor e o layout foram preservados.
- Conferido no Chromium em 360 px e 1440 px: fundo preto, textos brancos, “humano” laranja, monitor carregado e nenhuma rolagem lateral.
- Na branch `reestruturacao`, a Seção 04 foi reorganizada conforme a nova referência: rótulo “QUEM ENSINA IMPORTA”, título em três linhas, descrição, frase em negrito e chamada do blog na coluna esquerda; monitor ampliado à direita. O ponto final de “humano.” acompanha o laranja. No celular, a mesma estrutura empilha o monitor após o texto. Conferido no Chromium em 360 px e 1440 px: imagem carregada, texto legível e ausência de rolagem lateral.
- A Seção 04 ganhou uma pausa curta ao chegar ao topo: ScrollTrigger fixa a seção por 45% de uma tela no desktop e 20% no celular, com ajuste em `HOLD_SCREENS`. A fixação não é aplicada em movimento reduzido. Conferido no Chromium em 360 px e 1440 px: entrada, permanência, saída e retorno funcionam sem prender a rolagem ou criar rolagem lateral; a Seção 05 permanece acessível.

## Seção 05

- `src/pages/index.astro` renderiza `TeacherStories.astro` após a Seção 04, com o marcador `<!-- Seção 05 -->`.
- A Seção 05 é uma área inteiramente branca, com altura mínima de uma tela, permitindo rolar além da Seção 04. Ainda não contém outros elementos visíveis.
- Conferido no Chromium em 360 px e 1440 px: a Seção 05 começa imediatamente após a Seção 04, tem 900 px de altura numa janela de 900 px, fundo branco e nenhuma rolagem horizontal.
- O topo da Seção 05 recebeu o lettering “SUA AULA, SUAS ESCOLHAS / A aula ganha forma com você.” e a descrição “Revise, adapte e acrescente suas ideias. O plano acompanha o seu jeito de ensinar.”, usando Courier New, Georgia e Arial. O conjunto fica centralizado e se adapta à largura da tela.
- A imagem 4 foi reutilizada do arquivo existente `public/section-02-preview.png`, centralizada abaixo do lettering. Logo abaixo aparece “Criar meu plano” em roxo, como texto visual nesta etapa. Conferido no Chromium em 360 px e 1440 px: a imagem carrega, o texto permanece visível e não há rolagem lateral.
- A imagem 4 foi removida da Seção 05 e substituída por um layout demonstrativo em HTML e CSS, marcado no código com `<!-- layout demonstrativo -->`. A composição segue a referência com cinco abas escuras, área central cinza, moldura em gradiente e faixa escura inferior; os textos das abas e da faixa foram adaptados ao planejamento de aula. “Criar meu plano” permanece em roxo abaixo. Conferido no Chromium em 360 px e 1440 px, sem rolagem lateral.
- A barra escura agora alcança as bordas internas da moldura. As cinco abas (Objetivo, Tempo, Recursos, Turma e Plano) paginam o conteúdo demonstrativo com JavaScript, atualizando título, descrição, contador, faixa inferior e estado selecionado. As teclas de seta, Home e End também navegam pelas abas. Conferido no Chromium em 360 px e 1440 px: todas as páginas abrem, o teclado funciona e não há rolagem lateral.

## Seção 06

- `src/pages/index.astro` renderiza `Pricing.astro` após a Seção 05, com o marcador `<!-- Seção 06 -->`.
- A Seção 06 é uma área inteiramente branca e vazia, com altura mínima de uma tela para permitir continuar o scroll.
- Conferido no Chromium em 360 px e 1440 px: a Seção 06 começa imediatamente após a Seção 05, tem fundo branco e 900 px de altura numa janela de 900 px, sem rolagem horizontal.
- A Seção 06 recebeu um cartão central de comentários, inspirado na referência. O cartão tem rótulo, aspas verdes, texto demonstrativo, identificação e um círculo roxo sólido no lugar da foto de perfil. Os pontos inferiores são apenas visuais. O código da seção inclui comentários sobre cada elemento e seus estilos; o depoimento demonstrativo deve ser substituído por um comentário autorizado antes da publicação.

## Seção 07

- `src/pages/index.astro` renderiza `Faq.astro` após a Seção 06, com o marcador `<!-- Seção 07 -->`.
- A Seção 07 é uma área inteiramente branca e vazia, com altura mínima de uma tela para permitir continuar o scroll.
- Conferido no Chromium em 360 px e 1440 px: a Seção 07 começa imediatamente após a Seção 06, mede 900 px numa janela de 900 px de altura, tem fundo branco e não causa rolagem lateral.

## Versionamento

- `mentormind-web/` passa a ser a raiz do repositório Git `https://github.com/neocortexvisual/mentormind-landing.git`, preservando o estado das seções 01 a 07 antes da reestruturação.
