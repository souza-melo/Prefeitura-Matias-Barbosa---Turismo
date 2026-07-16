# Descubra Matias Barbosa — Template de Turismo (PortalFacil)

Portal de turismo do município de **Matias Barbosa/MG**, com a **estrutura** do
[descubrajuizdefora.com](https://descubrajuizdefora.com) e a **identidade visual** da
Prefeitura de Matias Barbosa. Entregue como **template PortalFacil** (Next.js + Bootstrap 5),
pronto para publicação.

---

## 1. Conceito visual

**"Onde a serra encontra a história."** Um portal editorial, fotográfico e acolhedor que
convida o visitante a descobrir a cidade — natureza da Mata Atlântica, herança ferroviária,
fé e gastronomia mineira — mantendo a autoridade institucional da Prefeitura.

- **Ritmo editorial** (herança do descubra JF): seções numeradas (`01`, `02`…), títulos
  grandes em serifa com **uma palavra-acento** colorida (ex.: *"Tem de tudo em **Matias Barbosa**"*),
  muito espaço em branco e fotografia como protagonista.
- **Identidade Matias Barbosa**: azul institucional como cor-âncora, verde da Mata Atlântica
  como cor de turismo, vermelho de marca nas palavras-acento e amarelo nos realces/badges.
- **Acolhedor**: fundo off-white quente (`#F6F2EA`) alternando com branco; cantos generosos;
  sombras suaves; seção de eventos em azul-noite profundo para contraste dramático.

## 2. Justificativa das decisões de UX/UI

| Decisão | Porquê |
|---|---|
| Estrutura idêntica ao descubra JF (hero → O que fazer → Onde ficar → Onde comer → Eventos) | Familiaridade com um portal público de referência; leitura em "F" e escaneável. |
| 4 blocos como **matérias** (`MateriaBox`) | A Secretaria de Turismo publica atrativos, hotéis, restaurantes e eventos como conteúdo — sem depender de TI para atualizar. |
| Cabeçalho numerado + palavra-acento | Cria hierarquia clara e um "fio condutor" editorial que guia o olhar seção a seção. |
| Cards de "O que fazer" com foto de fundo + título sobreposto | Máximo destaque à fotografia (tratamento fotográfico pedido); o card inteiro é clicável. |
| Barra de **Acesso rápido** (Roteiros, Mapa, Serviços ao Cidadão, Transparência) | Preserva a navegação familiar do cidadão — turismo não afasta os serviços essenciais. |
| Busca proeminente no topo | Descoberta rápida de atrativos/eventos; atende ao padrão de portais gov.br. |
| Rodapé "Secretaria de Turismo" + Prefeitura + selo Cadastur | Credibilidade institucional e conformidade turística. |

## 3. Estrutura completa da homepage (`index_1.html`)

```
HEADER
 ├─ header-top ....... acessibilidade (pular p/ conteúdo/menu/busca/rodapé) · Serviços ao Cidadão · Transparência · redes
 └─ header-bottom .... logo "Descubra Matias Barbosa" · <MenuPortal> · <BuscaAvancadaBox>
HERO
 └─ hero-area ........ <BannerBox slider> — atrativo em destaque (título sobreposto + "Saiba mais")
ACESSO RÁPIDO ........ chips: Roteiros · Mapa turístico · Onde ficar · Agenda · Serviços · Transparência
MAIN
 ├─ 01 · O que fazer ...... "Tem de tudo em Matias Barbosa" — <MateriaBox> 6 cards (foto+overlay), 3 col
 ├─ 02 · Onde ficar ....... "Estadias memoráveis" — <MateriaBox> 4 cards (foto-topo), 4 col · fundo quente
 ├─ 03 · Onde comer ....... "Sabores das Geraes" — <MateriaBox> 3 cards, 3 col
 └─ 04 · Eventos .......... "O que está rolando na cidade" — <MateriaBox> 6 cards c/ badge de data, 3 col · seção escura
FOOTER
 ├─ Secretaria de Turismo + Prefeitura + tagline + redes + selo Cadastur
 ├─ Colunas: Explorar · O que fazer · Secretaria de Turismo (contato)
 └─ barra inferior: copyright · LGPD · Acessibilidade · Mapa do site
```

## 4. Wireframe textual das seções

- **Hero** — imagem full-bleed (16:7), véu escuro à esquerda, kicker "EM DESTAQUE" (amarelo),
  título serifa grande (branco), botão-pílula vermelho "Saiba mais →", dots de paginação (pílula branca).
- **Acesso rápido** — faixa branca com chips arredondados centralizados; ícone azul + rótulo.
- **O que fazer** — cabeçalho `01 · O que fazer` + h2 com acento vermelho + botão "Ver todos".
  Grade 3×2 de cards-foto; badge/título ao rodapé sobre gradiente; hover = leve elevação + zoom da foto.
- **Onde ficar** (fundo quente) — cabeçalho `02` + acento; grade 4× de cards foto-topo/título-embaixo.
- **Onde comer** — cabeçalho `03` + acento; grade 3× de cards com chamada curta.
- **Eventos** (fundo azul-noite) — cabeçalho `04` (kicker e acento amarelos); grade 3×2 de cards escuros
  com **badge de data amarelo** no canto da foto.
- **Rodapé** — 4 colunas; azul-escuro; hover dos links desliza levemente à direita.

## 5. Design System resumido

**Cores** (tokens em `css/style.css :root`, nomes PT-BR)
```
--cor-primaria        #123E8C   azul institucional (âncora)
--cor-primaria-escura #0E2E68   header sticky, rodapé
--cor-secundaria      #178A4E   verde Mata Atlântica (kickers, turismo)
--cor-destaque        #D8232A   vermelho de marca (palavras-acento)
--cor-destaque-2      #F2B01E   amarelo (badges, realces)
--cor-fundo-secao     #F6F2EA   off-white quente (acolhedor)
--cor-fundo-escuro    #10203C   seção de eventos
--cor-texto-titulos   #14161C   quase-preto editorial
```
**Tipografia** — Display: **Fraunces** (serifa editorial, 500–700 + itálico p/ acento) ·
Texto/UI: **Plus Jakarta Sans** (400–800). *(não usa Inter/Roboto/Arial)*

**Grid** — `container` 1240px · Bootstrap 5 (`row`/`col-*`); grades de card via CSS Grid
(3/4/3/3 col → 2 col em ≤992px → 1 col em ≤576px).

**Componentes** — Botões (`.ver-todos` outline-pílula, `.bt-vejamais` sólido, hero CTA),
Cards (`.materia-box-static-item` — 3 variantes: overlay / foto-topo / escuro-com-data),
Inputs (`.busca-avancada-box`), Badges (kicker, data, selo Cadastur), Navegação (`#menunavegacao`),
Chips de acesso rápido, Ícones (Font Awesome no HTML + Bootstrap Icons nos boxes).

> **Regra de ouro respeitada:** todo CSS que mira um box usa a classe **real** renderizada
> pelo componente (`.materia-box-static-item`, `.banner-img`, `.embla__dot`, `#menunavegacao .nav-link`…),
> nunca classes inventadas. Verificado no `preview.html`.

## 6. Recomendações de acessibilidade (WCAG 2.2)

- **Skip links** (`accesskey` 1–4: conteúdo/menu/busca/rodapé) na `header-top`.
- **Contraste**: azul/branco, texto quase-preto sobre claro, branco sobre azul-noite — todos ≥ 4.5:1.
  O vermelho de acento é usado apenas em **texto grande** (títulos), onde 3:1 já basta.
- **Foco visível**: contorno amarelo de 3px (`:focus-visible`) em todos os interativos.
- **Teclado**: navegação, busca e menu 100% operáveis por teclado (Bootstrap `navbar`/`dropdown`).
- **Semântica**: `header`/`main`/`footer`/`nav` com landmarks; hierarquia `h2 → h4` coerente;
  `alt` em todas as imagens; ícones decorativos com `aria-hidden`; ícones-botão com `aria-label`.
- **Movimento**: `@media (prefers-reduced-motion: reduce)` desliga transições e revela tudo de imediato.
- **Idioma**: conteúdo em pt-BR; sem entidades HTML no texto (usa `©` direto).

## 7. Animações e microinterações

- **Reveal ao rolar** — seções sobem e surgem (`.reveal` → `.is-visible`), por checagem de posição
  (robusta; conteúdo nunca fica preso invisível — há fallback em `load`/`resize`/timeout).
- **Cards** — hover eleva o card e aplica leve *zoom* na foto (0.6s).
- **Hero** — botão "Saiba mais →" desliza no hover; dots em pílula.
- **Botões "Ver todos"** — a seta desliza à direita no hover.
- **Header sticky** — ganha sombra ao rolar (`.is-sticky`).
- **Voltar ao topo** — surge após 400px; rolagem suave.
- **Rodapé** — links deslizam levemente à direita no hover.

## 8. Estrutura para implementação (HTML + Bootstrap 5 · PortalFacil)

```
template-descubra-matias-barbosa/
├── index_1.html          Home (documento completo com tags de box)
├── index_2.html          Página interna (<InternalContent>) — header/footer idênticos
├── head_elements_1.json  <head> da home (fontes, ícones, CSS)
├── head_elements_2.json  <head> das internas
├── css/
│   ├── style.css         tokens :root + estilos (HTML próprio + classes reais dos boxes)
│   └── responsive.css    1200 / 992 / 768 / 576
├── js/script.js          ano no rodapé, sticky, voltar-ao-topo, reveal
├── images/               logo.svg · logo-rodape.svg · brasao-rodape.svg  (+ icon.png a incluir)
├── preview.html          PRÉ-VISUALIZAÇÃO estática (abre no navegador; não faz parte do deploy)
└── README.md             este arquivo
```

### Como publicar no PortalFacil
1. Copie a pasta como `templateN/` em `Portal.BackOffice.Api/wwwroot/`.
2. No BackOffice, **vincule as categorias** de matéria a cada box pelo `id`:
   `mat-oquefazer`, `mat-ondeficar`, `mat-gastronomia`, `mat-eventos`; e cadastre os banners do hero.
3. Configure o menu `local="main"` (Início, O que fazer, Onde comer, Onde ficar, Eventos, Roteiros).
4. Adicione `images/icon.png` (favicon 32×32) e, se desejar, versões `.min.css` (cache-busting).

### Notas técnicas
- **Boxes** usados: `<MenuPortal>`, `<BuscaAvancadaBox>`, `<BannerBox>`, `<MateriaBox>` — todos
  fechados explicitamente (o parser aninha tags auto-fechadas).
- **`{BASE_PATH}`** em todos os assets locais; scripts como `<NextScript … defer>`.
- **Bootstrap 5.3 + Bootstrap Icons** são pré-requisitos (grid, navbar, dropdown, `bi bi-…`).
- Os **eventos são matérias** (`MateriaBox`, categoria "Eventos") conforme solicitado — não `AgendaBox`.
  Se preferir a agenda nativa com navegação de mês, troque por `<AgendaBox>` (CSS `.agenda-box` já previsto no catálogo).

---

*Dados de contato, endereços e telefones no rodapé são exemplos — substituir pelos oficiais da
Secretaria de Turismo. Imagens do `preview.html` são placeholders (Lorem Picsum); no portal, o
conteúdo vem dos boxes.*
