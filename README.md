# Casa Oli

Site institucional da **Casa Oli** — presentes afetivos personalizados e artesanais.
_Carinho em cada detalhe._

🔗 **Site no ar:** https://briancruuz.github.io/casa-oli/

## Estrutura

```
casa-oli/
├── index.html        # site (página única) — entrada do GitHub Pages
├── assets/           # imagens usadas no site (logo + fotos de referência)
├── docs/             # documentação do projeto (identidade, calendário, precificação)
├── _work/            # arquivos de trabalho (ignorado pelo git)
└── _local/           # PDFs pesados de origem (ignorado pelo git)
```

Documentação completa em [`docs/DOCUMENTACAO.md`](docs/DOCUMENTACAO.md).

## Atualizar o site

Depois de editar qualquer arquivo:

```bash
git add .
git commit -m "descrição da mudança"
git push
```

O GitHub Pages republica sozinho em ~1 minuto.

## Publicação (referência)

- **Repositório:** https://github.com/briancruuz/casa-oli (branch `main`)
- **GitHub Pages:** Settings → Pages → Branch `main` / `(root)`
- Os PDFs e a pasta `_work/` ficam só na máquina local (ver `.gitignore`).
