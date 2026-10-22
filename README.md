# 🐍 Python com Thalyson

Portal educacional focado na linguagem de programação Python, oferecendo **conteúdos gratuitos** (artigos, guias, tutoriais e vídeos) e **treinamentos pagos** (cursos imersivos e mentorias individuais).

Seguindo a mesma arquitetura dos sites `tech.thalyson.com` e `thalisonwilker`: estático, veloz, sem dependências externas de runtime e hospedado via GitHub Pages com domínio customizado.

---

## 🚀 Executar Localmente

Com Node.js 22 ou superior:

```bash
npm run dev
```

Abra [http://localhost:3000](http://localhost:3000) no seu navegador.

---

## 🐳 Executar via Docker

Para rodar o contêiner localmente com Docker:

```bash
# Opção 1: Via npm scripts
npm run docker:build
npm run docker:run

# Opção 2: Via Docker Compose
docker compose up --build

# Opção 3: Comando direto
docker build -t python-com-thalyson .
docker run --rm -p 8080:8080 python-com-thalyson
```

Acesse [http://localhost:8080](http://localhost:8080) e verifique a saúde em [http://localhost:8080/healthz](http://localhost:8080/healthz).

---

## 📦 Build e Testes

Para gerar os arquivos estáticos de produção na pasta `dist/`:

```bash
npm run build
```

Para rodar a suíte de testes automatizados:

```bash
npm test
```

Os testes utilizam o test runner nativo do Node.js (`node:test`) e validam rotas, Content Security Policy, integridade de arquivos estáticos, dados em JSON e health check `/healthz`.

---

## ☁️ Publicar e Deploy (GitHub Pages)

O deploy é automatizado diretamente pelo **GitHub Pages** utilizando o workflow em `.github/workflows/deploy.yml`.

O endereço oficial configurado é `https://python.thalyson.com` através do arquivo `CNAME`.

### GitHub Actions

O workflow `.github/workflows/deploy.yml` executa automaticamente:
1. Validação com Node.js 22 e instalação limpa de dependências (`npm ci`).
2. Geração dos arquivos estáticos na pasta `dist/` (`npm run build`), incluindo páginas, estilos, assets, dados e `CNAME`.
3. Execução da suíte de testes automatizados (`npm test`).
4. Empacotamento do artefato e deploy oficial no GitHub Pages ao mesclar na branch `main`.

### Configuração no Repositório GitHub:

Em **Settings > Pages** do repositório:
- **Build and deployment > Source**: Selecione `GitHub Actions`.
- O domínio personalizado `python.thalyson.com` será gerenciado com HTTPS automático provido pelo GitHub.

---

## 🎨 Identidade Visual e Tipografia

- **Cores principais**:
  - Amarelo Python: `#F7CE3E`
  - Azul Python: `#4B8BBE` e `#306998`
  - Cyan (com Thalyson): `#5BC0EB`
  - Fundo Dark: `#0C1017` / `#141A24`
- **Tipografia**:
  - Títulos e Texto: *Source Sans 3* (família tipográfica oficial adotada no python.org)
  - Código e Monospaçado: *IBM Plex Mono*

---

## 📁 Estrutura de Diretórios

```
python-com-thalyson/
├── .dockerignore
├── .github/
│   └── workflows/
│       └── deploy.yml
├── .gitignore
├── CNAME
├── Dockerfile
├── README.md
├── assets/
│   ├── favicon.svg
│   └── logo.png
├── data/
│   ├── content.json        # Conteúdos abertos e gratuitos
│   └── courses.json        # Treinamentos e mentorias pagas
├── docker-compose.yml
├── index.html
├── nginx.conf
├── package.json
├── robots.txt
├── scripts/
│   ├── build.mjs
│   ├── serve.mjs
│   └── server.mjs
├── sitemap.xml
├── styles.css
└── tests/
    └── server.test.mjs
```
