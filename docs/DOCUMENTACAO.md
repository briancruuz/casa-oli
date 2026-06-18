# Casa Oli — Documentação do Projeto

> *Carinho em cada detalhe.*
> Documentação técnica e de marca · v1.1 · 17/06/2026

Este documento descreve **o que existe na pasta do projeto**, o **sistema visual** da Casa Oli, os **assets** usados, como **abrir e editar o site** e como as imagens foram **extraídas** (de forma reproduzível).

---

## 1. Visão geral

A Casa Oli é uma marca de **presentes afetivos personalizados e artesanais** (canecas, kits e papelaria feitos à mão). Este projeto reúne a estratégia, a identidade e uma **página-site de apresentação** da empresa (`casa-oli.html`).

### Arquivos da pasta

| Arquivo | O que é |
|---|---|
| `casa-oli.html` | **Site/visão da empresa** — página única, abre no navegador. Logo, "A cara da empresa", catálogo, kits, preços, campanha e roadmap. |
| `Casa-Oli-Identidade.md` | Documento-base: DNA da marca, posicionamento, personas, precificação, plano financeiro. |
| `Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md` | Calendário de conteúdo e a campanha completa de Dia dos Pais (09/08/2026). |
| `DOCUMENTACAO.md` | **Este arquivo.** |
| `assets/` | Imagens usadas pelo site (logo + fotos de referência). |
| `Precificacao-Casa-Oli.xlsx` | Planilha de precificação (regra 3× o custo). |
| `Plano de Negócios Casa Oli (Apresentação)...pdf` | Apresentação original (Canva). **Fonte da logo.** |
| `referencia-inicial.pdf` | Capturas do Instagram @lojapilgrim (marca-referência). **Fonte das fotos de referência.** |
| `_work/` | Recortes intermediários da extração (rascunho — pode ser apagado). |

Documentos relacionados: ver [Casa-Oli-Identidade.md](Casa-Oli-Identidade.md) e [Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md](Calendario-Conteudo-e-Campanha-Dia-dos-Pais.md).

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

As cores estão definidas como variáveis CSS no topo de `casa-oli.html` (bloco `:root`).

### 2.2 Tipografia

| Fonte | Papel | Onde |
|---|---|---|
| **Fraunces** (serifada macia) | Títulos e números | Headings, preços, níveis dos kits, FAQ |
| **Jost** (sem-serifa) | Texto corrido | Parágrafos, navegação, rótulos |
| **Caveat** (manuscrita) | Assinatura afetiva | "Oli", taglines pontuais |

> A fonte de títulos foi trocada de Cormorant Garamond para **Fraunces** (mais calor e personalidade artesanal). Para experimentar outra, troque o `<link>` do Google Fonts e o `font-family:'Fraunces',serif` no CSS.

Carregadas via Google Fonts (único recurso externo do site).

### 2.3 Logo

- Arquivo: `assets/logo-casa-oli.png` — "Casa Oli" com ramo de oliveira aquarelado e tagline *Carinho em cada detalhe*.
- Arquivo padrão do site: **`assets/logo-casa-oli-transparente.png`** — fundo removido (RGBA), funciona sobre qualquer cor.
- O original `logo-casa-oli.png` (fundo creme) fica como arquivo-fonte/backup.
- A versão transparente foi gerada com `_work/transp.py` (Python puro): decodifica o PNG, remove por **limiar global de cor** todo pixel próximo do creme `rgb(242,232,221)` — inclusive os miolos de letras como o "O" — com borda suavizada (alpha parcial), e reencoda como RGBA. Parâmetros: `T_FULL=32` (transparência total), `T_EDGE=72` (zona de borda).
- Para regerar: `python3 _work/transp.py` (a partir da pasta do projeto).

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

## 4. O site `casa-oli.html`

### Como abrir
```bash
xdg-open /home/lbruz/casa-oli/casa-oli.html
```
Ou arraste o arquivo para o navegador. Precisa de internet só para as fontes (funciona offline, com fonte alternativa).

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
Os links de contato são **provisórios** — procure por `PLACEHOLDER` no HTML (3 ocorrências, na seção Contato) e também os repita no footer:
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

---

## 5. Como as imagens foram extraídas (reproduzível)

Ambiente sem PIL/ImageMagick; usado **poppler** (`pdftoppm`, `pdfinfo`).

### Logo (do plano de negócios)
```bash
pdftoppm -png -f 1 -l 1 -r 200 \
  -x 1040 -y 280 -W 1650 -H 1500 \
  "Plano de Negócios Casa Oli (Apresentação)_20260617_203117_0000.pdf" logo
```

### Fotos de referência (do `referencia-inicial.pdf`, página 2 — grade 3×3 @ r150)
```bash
P="referencia-inicial.pdf"
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 52   -W 350 -H 350 "$P" ref-cesta
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 520  -W 350 -H 360 "$P" ref-pilha-rose
pdftoppm -png -f 2 -l 2 -r 150 -x 175 -y 600  -W 330 -H 300 "$P" ref-canecas-nomes
pdftoppm -png -f 2 -l 2 -r 150 -x 448 -y 640  -W 350 -H 420 "$P" ref-mae-editorial
pdftoppm -png -f 2 -l 2 -r 150 -x 830 -y 1090 -W 350 -H 360 "$P" ref-caneca-flores
```
> `-x/-y` = canto superior esquerdo do recorte; `-W/-H` = largura/altura em pixels na resolução `-r`.

---

## 6. Próximos passos sugeridos

- [ ] **Fotografar as peças reais** da Casa Oli e substituir as imagens `ref-*` no moodboard e nos cards-âncora.
- [x] ~~Gerar a **logo com fundo transparente** (PNG) para uso sobre qualquer cor.~~ ✅ `logo-casa-oli-transparente.png`
- [ ] Opcional: versão da logo em **SVG vetorial** (nitidez infinita) — exige redesenho/vetorização.
- [ ] Adicionar **links clicáveis** de WhatsApp e Instagram nos botões do site.
- [ ] Criar uma **versão para impressão / PDF** (pitch deck) a partir do HTML.
- [ ] Publicar o site (ex.: GitHub Pages, Netlify) quando quiser um link público.

---

*Documento vivo — Casa Oli. Atualize a cada marco alcançado.*
