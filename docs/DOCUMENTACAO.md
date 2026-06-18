# Casa Oli — Documentação do Projeto

> *Carinho em cada detalhe.*
> Documentação técnica e de marca · v2.0 · 18/06/2026

Este documento descreve **o que existe na pasta do projeto**, a **estrutura para o GitHub Pages**, o **sistema visual** da Casa Oli, os **assets** usados, como **abrir/editar/publicar o site** e como as imagens foram **extraídas** (de forma reproduzível).

---

## 0. Status & publicação (atual)

- **Site publicado:** https://briancruuz.github.io/casa-oli/
- **Repositório:** https://github.com/briancruuz/casa-oli (branch `main`)
- **Hospedagem:** GitHub Pages — `main` / `(root)`, servindo `index.html`.
- O projeto **passou a ser um repositório git** em 18/06/2026 (a decisão anterior de "trabalhar só local, sem git" foi revertida para permitir o GitHub Pages).

### Fluxo de atualização do site
Depois de editar qualquer arquivo:
```bash
cd /home/lbruz/casa-oli
git add .
git commit -m "descrição da mudança"
git push
```
O GitHub Pages republica sozinho em ~1 min. Para o `push` não pedir credencial toda vez, configure `gh auth login` ou uma chave SSH.

---

## 1. Visão geral

A Casa Oli é uma marca de **presentes afetivos personalizados e artesanais** (canecas, kits e papelaria feitos à mão). Este projeto reúne a estratégia, a identidade e a **página-site de apresentação** da empresa (`index.html`).

### Estrutura de pastas

```
casa-oli/
├── index.html        # SITE (página única) — entrada do GitHub Pages
├── assets/           # imagens usadas pelo site (logo + fotos de referência)
├── docs/             # documentação do projeto (este arquivo, identidade, calendário, planilha)
├── README.md         # apresentação do repositório + passos de publicação
├── .nojekyll         # impede o Jekyll do GitHub de processar/ignorar arquivos
├── .gitignore        # exclui _work/, _local/, *.pdf, .claude/
├── _work/            # arquivos de trabalho (NÃO versionado) — ver §5
└── _local/           # PDFs pesados de origem (NÃO versionado) — ver abaixo
```

### O que vai e o que NÃO vai para o GitHub

| Vai (versionado / publicado) | Não vai (só local — `.gitignore`) |
|---|---|
| `index.html`, `assets/`, `docs/`, `README.md`, `.nojekyll` | `_work/` (recortes e scripts de trabalho) |
| | `_local/` (PDFs grandes de origem) |
| | `.claude/` (config local do editor) |

> ⚠️ Os PDFs `_local/plano-de-negocios.pdf` (19 MB) e `_local/referencia-inicial.pdf` (169 MB) ficam **só na máquina local**: o GitHub rejeita arquivos acima de 100 MB. Por isso estão no `_local/` e no `.gitignore` (regra `*.pdf`). São as **fontes** da logo e das fotos de referência.

### Conteúdo de `docs/`

| Arquivo | O que é |
|---|---|
| `DOCUMENTACAO.md` | **Este arquivo** — doc técnica e de marca. |
| `Casa-Oli-Identidade.md` | DNA da marca, posicionamento, personas, precificação, plano financeiro. |
| `Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md` | Calendário de conteúdo + campanha de Dia dos Pais (09/08/2026). |
| `Precificacao-Casa-Oli.xlsx` | Planilha de precificação (regra 3× o custo). |

Documentos relacionados: [Casa-Oli-Identidade.md](Casa-Oli-Identidade.md) e [Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md](Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md).

---

## 2. Sistema visual (brand kit)

### 2.1 Paleta de cores

Extraída da logo oficial. Base neutra e quente + rosé como cor-assinatura + verde do ramo de oliveira.

| Cor | HEX | Uso |
|---|---|---|
| Creme / Areia | `#F2E8E0` | Base neutra e quente (fundo da logo, footer) |
| Blush | `#F6E7E1` | Fundos suaves, chips, badges de ícone |
| Rosé | `#D99B8E` | Cor-assinatura da marca |
| Rosé profundo | `#C07E70` | Ações, botões, destaques, links |
| Malva | `#8A6B63` | Títulos e texto forte (palavra "Casa" na logo) |
| Sálvia | `#9AAB8B` | Verde do ramo de oliveira (acento natural) |
| Bordô | `#9C5B63` | Acento dos frutos da oliveira |
| Dourado | `#BD9A5F` | Toque premium artesanal (rótulos, detalhes) |

> **Por que combinam:** a paleta parte de neutros quentes (creme/blush) que acalmam o olhar; o rosé dá identidade afetiva; o verde-sálvia (do ramo de oliveira da logo) equilibra com o natural; dourado e bordô entram só como acentos pontuais. Nada compete — tudo conversa.

As cores estão definidas como variáveis CSS no topo de `index.html` (bloco `:root`).

### 2.2 Tipografia

| Fonte | Papel | Onde |
|---|---|---|
| **Fraunces** (serifada macia) | Títulos e números | Headings, preços, níveis dos kits, FAQ |
| **Jost** (sem-serifa) | Texto corrido | Parágrafos, navegação, rótulos |
| **Caveat** (manuscrita) | Assinatura afetiva | "Oli", taglines pontuais |

> A fonte de títulos foi trocada de Cormorant Garamond para **Fraunces** (mais calor e personalidade artesanal). Para experimentar outra, troque o `<link>` do Google Fonts e o `font-family:'Fraunces',serif` no CSS.

Carregadas via Google Fonts (único recurso externo do site).

### 2.3 Logo

- Arquivo-fonte: `assets/logo-casa-oli.png` — "Casa Oli" com ramo de oliveira aquarelado e tagline *Carinho em cada detalhe* (fundo creme).
- Arquivo padrão do site: **`assets/logo-casa-oli-transparente.png`** — fundo removido (RGBA), funciona sobre qualquer cor.
- A versão transparente foi gerada com `_work/scripts/transp.py` (Python puro): decodifica o PNG, remove por **limiar global de cor** todo pixel próximo do creme `rgb(242,232,221)` — inclusive os miolos de letras como o "O" — com borda suavizada (alpha parcial), e reencoda como RGBA. Parâmetros: `T_FULL=32` (transparência total), `T_EDGE=72` (zona de borda).
- Para regerar: `python3 _work/scripts/transp.py` (a partir da pasta do projeto).

### 2.4 Ícones

Os ícones do site são **SVG de linha minimalistas**, definidos uma vez como `<symbol>` (sprite no topo do `<body>`) e reusados via `<use href="#ic-...">`. Cor herda da paleta (rosé/sálvia). Substituíram os emojis decorativos da versão anterior.

---

## 3. Assets (`assets/`)

| Arquivo | Conteúdo | Origem | Uso no site |
|---|---|---|---|
| `logo-casa-oli-transparente.png` | **Logo com fundo transparente (RGBA)** | Derivada da logo (fundo creme removido) | **Nav, hero, footer e seção da logo** — usada sobre qualquer cor |
| `logo-casa-oli.png` | Logo original (fundo creme) | Pág. 1 do plano de negócios (PDF) | Arquivo-fonte / backup |
| `ref-cesta.png` | Cesta com caneca + laço | @lojapilgrim (referência) | Card "Kits", moodboard |
| `ref-pilha-rose.png` | Pilha de canecas rosé | @lojapilgrim (referência) | Card "Canecas", moodboard |
| `ref-canecas-nomes.png` | Canecas com nomes | @lojapilgrim (referência) | Moodboard |
| `ref-mae-editorial.png` | Editorial com tulipas | @lojapilgrim (referência) | Moodboard |
| `ref-caneca-flores.png` | Caneca + flores secas | @lojapilgrim (referência) | Moodboard (destaque) |

> ⚠️ **Importante (uso honesto):** as 5 fotos `ref-*` são **referências de mercado do Instagram @lojapilgrim**, usadas apenas como inspiração de estilo/embalagem/fotografia. **Não são produtos da Casa Oli** e estão rotuladas assim no site. Devem ser **substituídas pelas fotos reais** das peças da Casa Oli assim que existirem.

---

## 4. O site `index.html`

### Como abrir localmente
```bash
xdg-open /home/lbruz/casa-oli/index.html
```
Ou arraste o arquivo para o navegador. Precisa de internet só para as fontes (funciona offline, com fonte alternativa). Online: https://briancruuz.github.io/casa-oli/

### Estrutura das seções (ordem)
1. **Nav** (fixa) — logo + links
2. **Hero** — logo, pitch, números-chave
3. **A cara da empresa** — paleta, tipografia, logo (claro/colorido), moodboard
4. **Essência** · 5. **Posicionamento**
6. **O que entrego** — catálogo (8 produtos; 2 âncoras com foto)
7. **Como funciona o pedido** — 4 passos (conversa → personalização → produção → entrega)
8. **Diferenciais** · 9. **Kits** · 10. **Preços**
11. **Personas** · 12. **Campanha** · 13. **Conteúdo** · 14. **Roadmap** · 15. **Checklist**
16. **Depoimentos** — *placeholders* até ter relatos reais
17. **FAQ** — dúvidas frequentes (accordion `<details>`)
18. **Contato** — botões WhatsApp / Instagram / e-mail
19. **Footer** — logo + links de contato

### ⚠️ Contatos a configurar (placeholders)
Os links de contato são **provisórios** — procure por `PLACEHOLDER` no HTML (na seção Contato) e repita no footer:
- **WhatsApp:** `https://wa.me/5599999999999` → troque por `55` + DDD + número.
- **Instagram:** `https://instagram.com/casa.oli` → troque pelo @ real.
- **E-mail:** `mailto:contato@casaoli.com.br` → troque pelo e-mail real.

### SEO / compartilhamento
`<head>` já traz `meta description`, **Open Graph** e **Twitter Card** (para o link aparecer bonito ao compartilhar) e **favicon** (a logo transparente).

### Como editar
- **Cores:** bloco `:root` no `<style>`.
- **Textos:** direto no HTML de cada seção.
- **Trocar imagens:** substitua o arquivo em `assets/` mantendo o nome (ou ajuste o `src`).
- **Ícones:** adicione um novo `<symbol id="ic-...">` no sprite e use `<use href="#ic-...">`.
- **Publicar a mudança:** `git add . && git commit -m "..." && git push` (ver §0).

---

## 5. Arquivos de trabalho `_work/` (não versionado)

Recortes intermediários e scripts da fase de extração de imagens. **Pode ser apagado** sem afetar o site — fica fora do git (`.gitignore`). Organizado em:

| Subpasta | Conteúdo |
|---|---|
| `capturas/` | Capturas brutas do `pdftoppm`: páginas inteiras de referência (`ref-1..8`) e extração da logo (`plano_*`, `logo_crop-*`). |
| `recortes/` | Experimentos de recorte de produtos (`c_*`, `f_*`, `g_*`, `t_*`, `p*`, `grid_full`). |
| `previews/` | Previews de paleta (`preview_dark/rose/sage`). |
| `scripts/` | `transp.py` — gera a logo transparente (ver §2.3). |

---

## 6. Como as imagens foram extraídas (reproduzível)

Ambiente sem PIL/ImageMagick; usado **poppler** (`pdftoppm`, `pdfinfo`). As fontes (PDFs) ficam em `_local/`.

### Logo (do plano de negócios)
```bash
pdftoppm -png -f 1 -l 1 -r 200 \
  -x 1040 -y 280 -W 1650 -H 1500 \
  "_local/plano-de-negocios.pdf" logo
```

### Fotos de referência (do `_local/referencia-inicial.pdf`, página 2 — grade 3×3 @ r150)
```bash
P="_local/referencia-inicial.pdf"
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 52   -W 350 -H 350 "$P" ref-cesta
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 520  -W 350 -H 360 "$P" ref-pilha-rose
pdftoppm -png -f 2 -l 2 -r 150 -x 175 -y 600  -W 330 -H 300 "$P" ref-canecas-nomes
pdftoppm -png -f 2 -l 2 -r 150 -x 448 -y 640  -W 350 -H 420 "$P" ref-mae-editorial
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 1090 -W 350 -H 360 "$P" ref-caneca-flores
```
> `-x/-y` = canto superior esquerdo do recorte; `-W/-H` = largura/altura em pixels na resolução `-r`.

---

## 7. Histórico de marcos

- **17/06/2026** — Criação do site (`casa-oli.html`), brand kit, extração de logo e fotos de referência, docs base. Logo transparente gerada via `transp.py`.
- **18/06/2026** — Reorganização para GitHub Pages: `casa-oli.html` → `index.html`, criação de `docs/` e `_local/`, `.gitignore`/`.nojekyll`/`README.md`. `git init` + 1º commit, push para `github.com/briancruuz/casa-oli`, site no ar via GitHub Pages. `_work/` reorganizado em subpastas.

---

## 8. Próximos passos sugeridos

- [ ] **Fotografar as peças reais** da Casa Oli e substituir as imagens `ref-*` no moodboard e nos cards-âncora.
- [x] ~~Gerar a **logo com fundo transparente** (PNG).~~ ✅ `logo-casa-oli-transparente.png`
- [x] ~~**Publicar o site** (GitHub Pages).~~ ✅ https://briancruuz.github.io/casa-oli/
- [ ] **Ativar o GitHub Pages** em Settings → Pages (`main` / root), caso ainda não esteja ativo.
- [ ] Configurar `gh auth login` ou SSH para não recolar token a cada `push`.
- [ ] Adicionar os **contatos reais** (WhatsApp, Instagram, e-mail) — ver §4.
- [ ] Opcional: versão da logo em **SVG vetorial** (nitidez infinita).
- [ ] Opcional: **domínio próprio** (ex.: casaoli.com.br) apontando para o GitHub Pages.

---

*Documento vivo — Casa Oli. Atualize a cada marco alcançado.*
