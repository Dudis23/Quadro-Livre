# Quadro Livre (Bootstrap 5) — explicação das classes

Páginas (uma por arquivo, como no projeto original): `index.html` (início), `sobre.html`, `contato.html`, `postar.html` · CSS próprio: `css/estilo.css` (só ajustes pequenos) · **nenhum JavaScript escrito por mim** (só o JS interno do Bootstrap, via CDN).

## Onde está cada item pedido
| Item | Página |
|---|---|
| Navbar + Dropdown | todas (menu das 3 barrinhas com todas as páginas) |
| Carousel | `index.html` |
| Cards | `index.html` (posts e perfil), `postar.html`, `contato.html` |
| Alertas | `index.html`, `contato.html`, `sobre.html` |
| Bs5 Flex | `index.html`, `sobre.html` (seção Flexbox) e em todas as páginas (rodapé, perfil) |
| Tipografia, Cores, Imagens, Botões | `sobre.html` (e botões também em `index.html`) |
| Formulários (optativo) | `contato.html` e `postar.html` |

## Como o Bootstrap entra no código
- `<meta name="viewport" ...>`: sem ela o layout responsivo não funciona no celular (abordagem *mobile first*).
- `<link ... bootstrap.min.css>` no `<head>`: traz todas as classes. Meu `estilo.css` vem **depois**, para poder sobrescrever algo.
- `<script ... bootstrap.bundle.min.js>` no fim do `<body>`: dá vida ao carousel, ao dropdown botão de fechar alerta (o *bundle* já inclui o Popper, que posiciona o dropdown).
- Os componentes interativos funcionam com atributos `data-bs-*` (ex.: `data-bs-toggle="dropdown"`), sem escrever JavaScript.

## 1. Navbar + Dropdown (menu das 3 barrinhas)
| Classe | O que faz |
|---|---|
| `navbar` | Cria a barra de navegação. |
| `navbar-dark bg-primary` | Texto/ícones claros sobre fundo azul. |
| `sticky-top` | Barra fica fixa no topo ao rolar. |
| `shadow` | Sombra abaixo da barra. |
| `container` | Centraliza o conteúdo com largura máxima por breakpoint. |
| `navbar-brand` | Nome/logo "Quadro Livre" à esquerda. |
| `d-flex align-items-center gap-2` | Agrupa o botão "Postar ideia" e o menu lado a lado, alinhados na vertical. |
| `dropdown` | Contêiner do menu suspenso. |
| `data-bs-toggle="dropdown"` (no botão) | Faz o botão abrir/fechar o menu. |
| `navbar-toggler-icon` | Desenha as 3 barrinhas (ícone de hambúrguer). |
| `dropdown-menu dropdown-menu-end` | A caixa do menu; `-end` alinha à direita, para não sair da tela. |
| `dropdown-item` | Cada página do menu; `active` marca a página atual. |
| `dropdown-divider` | Linha separadora. |
| `btn btn-light btn-sm` | Botão "Postar ideia" pequeno e claro. |


## 2. Carousel (só texto)
- `carousel slide`: contêiner com animação de deslize. `data-bs-ride="carousel"` inicia sozinho.
- `carousel-inner` > `carousel-item` (o primeiro com `active`): os slides. `data-bs-interval` define o tempo de cada um.
- `carousel-indicators`: bolinhas; `data-bs-slide-to="n"` vai para o slide n.
- `carousel-control-prev/next` (+ `-icon`): setas. `data-bs-slide="prev|next"` define a direção.
- `bg-primary` / `bg-success` / `bg-dark` no `carousel-item`: cor de fundo de cada slide (no lugar de imagens). O texto fica dentro de um `div` com `d-flex flex-column justify-content-center align-items-center text-center text-white` (centraliza em coluna, texto branco).
- `display-5 fw-bold` no título e `lead` no subtítulo: tipografia do banner.

## 3. Tipografia
- `display-4`, `display-6`: títulos grandes de destaque. `lead`: parágrafo de abertura maior.
- `h1`…`h6` como classes: dão o tamanho de um título sem mudar a tag (ex.: `<h2 class="h3">`).
- `fw-bold` / `fw-light`: peso da fonte. `fst-italic`: itálico. `text-uppercase`: maiúsculas. `text-decoration-underline`: sublinhado.
- `text-start|center|end`: alinhamento. `text-muted`: cinza discreto.
- `blockquote`, `blockquote-footer`: citação com autor. `<mark>`, `<small>`, `<del>`: marcar, diminuir, riscar.

## 4. Cores
- `text-{cor}`: cor do texto. `bg-{cor}`: cor de fundo.
- `text-bg-{cor}`: fundo **e** texto com contraste certo ao mesmo tempo.
- `bg-opacity-25`: deixa o fundo 25% opaco. `border border-primary`: borda colorida.
- Cores: `primary` azul, `secondary` cinza, `success` verde, `danger` vermelho, `warning` amarelo, `info` ciano, `light`, `dark`.

## 5. Imagens
- `img-fluid`: `max-width:100%; height:auto` (responsiva).
- `rounded`: cantos arredondados. `rounded-circle`: círculo (foto de perfil; usei 150×150 no CSS com `object-fit: cover` para não deformar).
- `img-thumbnail`: moldura com borda e padding.
- `figure`, `figure-img`, `figure-caption`: imagem com legenda.

## 6. Alertas
- `alert alert-{cor}`: caixa colorida de aviso (`role="alert"` ajuda leitores de tela).
- `alert-link`: link com cor combinando. `alert-heading`: título dentro do alerta.
- `alert-dismissible fade show` + `<button class="btn-close" data-bs-dismiss="alert">`: alerta com botão X que o fecha.

## 7. Botões
- `btn` é a base; `btn-{cor}` preenche; `btn-outline-{cor}` só contorno; `btn-link` parece link.
- `btn-lg` / `btn-sm`: tamanhos. `disabled`: desabilitado.
- `btn-group`: botões colados (`active` marca o selecionado).
- `d-grid`: o botão ocupa toda a largura da coluna (`col-md-4` limita a coluna).

## 8. Cards
- `card`: caixa. `card-body`: miolo com padding. `card-footer`: rodapé (usei para curtir/não curtir). `shadow-sm`: sombra leve.
- Card de perfil (`aside`): `card-body d-flex flex-column align-items-center text-center` centraliza foto, nome e contadores; `rounded-circle` deixa a foto redonda.
- Posts: cards vazios (só a estrutura: foto, "Data" e botões de curtir), empilhados com `d-flex flex-column gap-3`. A página usa `row g-4` com `col-lg-8` (posts) e `col-lg-4` (perfil).
- `badge`: etiquetas usadas na seção de Flex em `sobre.html`.

## 9. Flex (Bs5 Flex)
| Classe | Efeito (CSS equivalente) |
|---|---|
| `d-flex` | `display:flex` |
| `flex-row` / `flex-column` | direção (`flex-direction`) |
| `flex-column flex-md-row` | coluna no celular, linha a partir de `md` |
| `justify-content-between/center/end` | alinhamento no eixo principal |
| `align-items-center` | alinhamento no eixo cruzado (vertical) |
| `flex-wrap` | quebra de linha quando falta espaço |
| `gap-2`, `gap-3` | espaço entre os itens |
| `flex-fill` | itens dividem o espaço igualmente |
| `flex-grow-1` | o item cresce e ocupa o que sobra |
| `ms-auto` | margem esquerda automática: empurra o item para a direita |
| `order-1`, `order-2` | muda a ordem visual |

Também uso a grade (`row`, `col-md-6`, `col-6 col-md-3`) que é feita em flexbox: 12 colunas, e o prefixo `col-md-` indica o breakpoint em que a divisão passa a valer.

## 10. Formulário (optativo) — `contato.html` e `postar.html`
- `form-label`, `form-control`, `form-select`: rótulo e campos estilizados.
- `input-group` + `input-group-text`: o "@" colado no campo de e-mail.
- `form-check`, `form-check-input`, `form-check-label`: radio/checkbox; `form-switch`: vira interruptor.
- `form-floating`: rótulo que flutua dentro do campo.
- `row g-3` + `col-md-6`: campos lado a lado no desktop e empilhados no celular.
- Sem JavaScript: a obrigatoriedade vem do atributo HTML `required`, e quem mostra o aviso é o próprio navegador.

## Utilitários de espaçamento usados em tudo
`m`/`p` = margin/padding; `t b s e x y` = lado (top, bottom, start, end, eixo x, eixo y); número 0–5 = tamanho. Ex.: `mb-3` margem inferior, `py-5` padding vertical, `me-2` margem à direita.

## O que sobrou de CSS próprio e por quê
`banner-texto` (altura mínima do banner), `texto-post` (altura mínima do espaço de texto do post vazio), `foto-perfil`/`avatar`/`icone` (tamanhos das imagens), `scroll-margin-top` (a navbar fixa não cobre o título ao clicar nos links) e `area-ideia` (altura do textarea com `form-floating`).
