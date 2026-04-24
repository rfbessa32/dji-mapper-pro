# DJI Mapper Pro — Build Automático via GitHub Actions

Este repositório gera automaticamente os instaladores para **Windows** e **Mac** sem precisar instalar nada na sua máquina.

---

## Como publicar uma nova versão (passo a passo)

### Primeira vez — configuração inicial

**1. Crie uma conta gratuita no GitHub**
👉 https://github.com/signup

**2. Crie um novo repositório**
- Acesse https://github.com/new
- Nome: `dji-mapper-pro`
- Visibilidade: **Private** (recomendado) ou Public
- **NÃO** marque nenhuma opção de inicialização
- Clique em **Create repository**

**3. Instale o Git no seu PC** (só uma vez)
👉 https://git-scm.com/download/win
- Durante a instalação, deixe todas as opções padrão

**4. Suba o projeto** — abra o CMD ou PowerShell na pasta do projeto e rode:
```bash
git init
git add .
git commit -m "primeiro commit"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/dji-mapper-pro.git
git push -u origin main
```
> Substitua `SEU_USUARIO` pelo seu usuário do GitHub

---

### Gerando o instalador (toda vez que quiser uma nova versão)

Basta criar uma **tag de versão**. No CMD ou PowerShell:

```bash
git tag v1.0.0
git push origin v1.0.0
```

Isso dispara automaticamente o build. Em **5-8 minutos** os instaladores ficam prontos.

---

### Onde baixar os instaladores prontos

1. Acesse seu repositório no GitHub
2. Clique em **"Releases"** (coluna da direita)
3. Baixe o arquivo desejado:
   - `DJI Mapper Pro Setup 1.0.0.exe` → Windows
   - `DJI Mapper Pro-1.0.0.dmg` → Mac Intel
   - `DJI Mapper Pro-1.0.0-arm64.dmg` → Mac Apple Silicon

---

### Para versões futuras

Quando atualizar o app, edite o `package.json` e mude o número da versão:
```json
"version": "1.1.0"
```

Depois:
```bash
git add .
git commit -m "versão 1.1.0"
git tag v1.1.0
git push origin main
git push origin v1.1.0
```

---

### Acompanhando o build em tempo real

1. No GitHub, clique na aba **"Actions"**
2. Você vê o progresso de cada etapa ao vivo
3. Se algo der errado, o log mostra exatamente onde falhou

---

## Estrutura do projeto

```
dji-mapper-pro/
├── .github/
│   └── workflows/
│       └── build.yml       ← pipeline de build automático
├── src/
│   └── index.html          ← o app (seu HTML)
├── assets/
│   └── icon.png            ← ícone do app
├── main.js                 ← processo principal do Electron
├── package.json            ← configuração do projeto e do instalador
├── LICENSE.txt
└── .gitignore
```
