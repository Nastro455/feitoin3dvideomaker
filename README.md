# Feitoin3d Video Maker

Ferramenta experimental dedicada para montagem de vídeos 3D gravados com a lente Feito In 3D.

## Recursos principais

- Upload de vídeo MP4, MOV ou WebM;
- Suporte para 2, 3 ou 4 quadros;
- Quadros lado a lado ou empilhados;
- Seleção de ponto de referência;
- Alinhamento e enquadramento manual;
- Controle de velocidade do efeito 3D;
- Exportação em WebM ou MP4 quando suportado pelo navegador;
- Ajustes criativos: efeito de cor, exposição, glow e RGB displaced.

## Como publicar no GitHub Pages

1. Crie um novo repositório no GitHub.
2. Envie o arquivo `index.html` para a raiz do repositório.
3. Vá em Settings > Pages.
4. Selecione a branch principal e a pasta raiz.
5. Aguarde o link do GitHub Pages.

## Observações

Esta é uma versão MVP. Para melhor performance, comece com vídeos curtos de 5 a 10 segundos.


## Atualização — Play/Pause no preview

- Adicionado botão de play/pause no preview.
- Ao clicar em selecionar ponto de referência, o preview pausa automaticamente para marcação mais precisa.


## Atualização — Correção de pontos por quadro

- Cada perspectiva agora exibe o ponto marcado no thumbnail.
- O usuário pode clicar em qualquer quadro para corrigir/definir a posição do ponto naquela perspectiva.
- O quadro selecionado fica destacado e o alinhamento é recalculado quando necessário.


## Atualização — Painel minimizado de ajuste fino no preview

- Adicionado painel flutuante minimizado no preview para ajuste fino dos pontos.
- O painel permite escolher Frame 1, 2, 3 ou 4 e mover o ponto com setas.
- Ao abrir o painel, o ponto selecionado também aparece sobre o preview para conferência.


## Correção — Upload de vídeo

- O carregamento agora registra os eventos de leitura antes de definir o arquivo de vídeo.
- Adicionado aviso de erro quando o navegador não consegue ler o formato/codec do vídeo.

## Atualização — Rastreamento de ponto no vídeo

- Adicionada opção **Rastrear ponto durante a exportação**.
- A ferramenta cria um pequeno template do ponto marcado e tenta acompanhá-lo em cada perspectiva ao longo do vídeo.
- Isso melhora a estabilização do efeito 3D quando existe movimento de câmera ou do objeto.
- Ainda é um tracking experimental: funciona melhor com pontos de alto contraste, bem iluminados e vídeos curtos.


## Correção — Upload após painel minimizado

Corrigido um conflito em que as funções do painel de ajuste de pontos ficavam presas dentro de um evento de slider, impedindo o carregamento correto do vídeo em alguns navegadores.

## Atualização — Tracking V2

- O tracking agora usa uma área maior ao redor do ponto marcado.
- A busca do ponto acontece em múltiplas etapas: ampla, média e ajuste fino.
- O template do ponto é atualizado dinamicamente durante a exportação, para acompanhar mudanças de luz e movimento.
- Foi adicionada suavização para reduzir tremidas entre frames.

## Redesign de lógica — Travar objeto principal

Esta versão muda a lógica central da ferramenta:

- O ponto marcado passa a ser tratado como **ponto âncora**.
- A ferramenta calcula offsets fixos entre as perspectivas.
- Durante a alternância, o objeto principal permanece travado.
- O fundo se desloca entre as perspectivas, criando o efeito 3D mais satisfatório.
- O tracking dinâmico ficou opcional e experimental, para casos em que o assunto muda muito de posição.

Fluxo ideal:
1. Pausar no melhor frame.
2. Marcar o ponto âncora no objeto principal.
3. Corrigir o ponto em cada perspectiva.
4. Aplicar alinhamento.
5. Exportar com “Travar objeto principal” ativado.
