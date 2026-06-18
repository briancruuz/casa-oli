# Casa Oli

Site institucional da **Casa Oli** — presentes afetivos personalizados e artesanais.
_Carinho em cada detalhe._

🔗 Site: https://SEU-USUARIO.github.io/casa-oli/

## Estrutura

```
casa-oli/
├── index.html        # site (página única) — entrada do GitHub Pages
├── assets/           # imagens usadas no site (logo + fotos de referência)
├── docs/             # documentação do projeto (identidade, calendário, precificação)
├── _work/            # arquivos de trabalho (ignorado pelo git)
└── _local/           # PDFs pesados de origem (ignorado pelo git)
```

## Publicar no GitHub Pages

1. Criar um repositório no GitHub (ex.: `casa-oli`).
2. Na raiz do projeto:
   ```bash
   git init
   git add .
   git commit -m "Site Casa Oli"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/casa-oli.git
   git push -u origin main
   ```
3. No GitHub: **Settings → Pages → Branch: `main` / `(root)` → Save**.
4. O site fica disponível em `https://SEU-USUARIO.github.io/casa-oli/`.

> Os PDFs e a pasta `_work/` ficam só na máquina local (ver `.gitignore`).
