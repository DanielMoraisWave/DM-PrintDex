# DM-PrintDex

Site estático **Hugo** para vitrine de Pokémon impressos em 3D e pintados à mão. Sem loja, sem pagamentos, contacto apenas via WhatsApp.

## Estrutura do projeto

```
DM-PrintDex/
├── content/
│   ├── _index.md      # Página inicial
│   ├── gallery.md     # Galeria de Pokémon (layout: gallery)
│   └── sobre.md       # Sobre o projeto
├── data/
│   └── pokemon.json   # Lista de Pokémon (id + name)
├── layouts/
│   ├── _default/
│   │   ├── baseof.html
│   │   └── single.html
│   ├── index.html
│   └── gallery.html
├── static/
│   └── pokemon/       # Imagens por ID: 001/1.jpg, 004/1.jpg, etc.
├── assets/
│   └── css/
│       └── style.css
├── hugo.toml
└── .github/workflows/
    └── hugo.yml       # Deploy automático para GitHub Pages
```

## Requisitos

- [Hugo](https://gohugo.io/installation/) (extended recomendado)

## Setup local

1. Clona o repositório e entra na pasta:
   ```bash
   cd DM-PrintDex
   ```

2. Configura o número de WhatsApp em `hugo.toml`:
   ```toml
   [params]
   whatsapp_number = "351912345678"   # só dígitos, com código do país
   ```

3. (Opcional) Ajusta o `baseURL` para o teu repositório GitHub Pages:
   ```toml
   baseURL = "https://TEU_USERNAME.github.io/DM-PrintDex/"
   ```

4. Corre o servidor local:
   ```bash
   hugo server -D
   ```
   Abre no browser: http://localhost:1313

## Conteúdo

### Pokémon (`data/pokemon.json`)

Cada entrada tem `id` (numeração oficial) e `name`:

```json
{ "id": 1, "name": "Bulbasaur" },
{ "id": 4, "name": "Charmander" }
```

Podes adicionar mais Pokémon editando este ficheiro.

### Imagens

- Coloca as fotos em `static/pokemon/ID/`, com ID em 3 dígitos:
  - Ex.: `static/pokemon/001/1.jpg` (Bulbasaur), `static/pokemon/006/1.jpg` e `2.jpg` (Charizard).
- O template usa sempre `1.jpg` como imagem principal; se não existir, mostra um placeholder com o nome e badge "Em breve".
- Pokémon com `1.jpg` mostram a imagem e badge "Já feito".

## Deploy no GitHub Pages

1. Cria um repositório no GitHub (ex.: `DM-PrintDex`).

2. Em **Settings → Pages**:
   - Source: **GitHub Actions**.

3. Faz push do código para o branch `main` (ou `master`). O workflow `.github/workflows/hugo.yml`:
   - instala o Hugo
   - gera o site (`hugo --minify`)
   - publica na GitHub Pages

4. O site ficará em:
   `https://TEU_USERNAME.github.io/DM-PrintDex/`

## Resumo

- **Stack:** Hugo, Markdown, JSON, HTML/CSS simples, sem JS pesado.
- **Hosting:** GitHub Pages.
- **Contacto:** apenas botão WhatsApp por Pokémon (número em `hugo.toml`).
- Sem e-commerce, backend ou bases de dados.
