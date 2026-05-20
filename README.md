# tauri-demo

> Meu primeiro projeto com [Tauri](https://tauri.app/) — uma exploração do framework para construção de aplicações desktop cross-platform usando Rust no backend e tecnologias web (HTML/CSS/JS/TS) no frontend.

---

## Pré-requisitos

### 1. Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
# Recarregar o PATH após instalação:
source $HOME/.cargo/env
# Adicionar ao shell permanentemente:
echo 'source $HOME/.cargo/env' >> ~/.bashrc
source ~/.bashrc
# Verificar instalação:
rustc --version
cargo --version
```

### 2. Node.js

Baixe a versão LTS em [nodejs.org](https://nodejs.org/) ou via `nvm`:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install --lts
node --version
npm --version
```

### 3. Dependências do sistema (Linux — Ubuntu/Debian)

```bash
sudo apt update && sudo apt install -y \
  libwebkit2gtk-4.1-dev \
  libgtk-3-dev \
  libglib2.0-dev \
  libssl-dev \
  libayatana-appindicator3-dev \
  librsvg2-dev \
  libxdo-dev \
  libsoup-3.0-dev \
  libjavascriptcoregtk-4.1-dev \
  build-essential \
  pkg-config \
  curl \
  wget \
  file
```

> **Ubuntu 22.04 ou mais antigo?** Substitua `libwebkit2gtk-4.1-dev` e `libjavascriptcoregtk-4.1-dev` pelas versões `4.0`:
> ```bash
> sudo apt install -y libwebkit2gtk-4.0-dev libjavascriptcoregtk-4.0-dev
> ```

---

## Instalação e execução

```bash
# Clonar o repositório
git clone https://github.com/YuriAlvesBordin/tauri-demo.git
cd tauri-demo

# Instalar dependências Node
npm install

# Rodar em modo de desenvolvimento
npm run tauri dev
```

## Build para produção

```bash
npm run tauri build
```

Os instaladores serão gerados em `src-tauri/target/release/bundle/`.

---

## Estrutura do projeto

```
tauri-demo/
├── index.html          # Entry point do frontend
├── src/                # Código frontend (TypeScript/JavaScript)
│   └── main.ts
├── src-tauri/          # Backend Rust
│   ├── src/
│   │   └── main.rs     # Ponto de entrada Rust
│   ├── Cargo.toml      # Dependências Rust
│   └── tauri.conf.json # Configurações do Tauri
└── package.json
```

---

## Notas de aprendizado

Pontos de atenção durante o setup:

- O Rust precisa ser instalado via `rustup` e o `PATH` recarregado antes de rodar `npm run tauri dev`.
- No Linux, as bibliotecas GTK/WebKit devem ser instaladas via `apt` — sem elas o build do Rust falha com erros de `pkg-config`.
- O Tauri v2 usa `webkit2gtk-4.1` (não 4.0) em sistemas mais recentes.

---

## Referências

- [Documentação oficial do Tauri](https://tauri.app/start/)
- [Pré-requisitos por sistema operacional](https://tauri.app/start/prerequisites/)
- [Repositório do Tauri no GitHub](https://github.com/tauri-apps/tauri)
