# Meus clientes: passo a passo

Esta versão **não tem login**: o app abre direto e os dados ficam salvos no próprio navegador/aparelho.
Para levar os dados para outro aparelho ou guardar uma cópia, use o botão de **Backup**.

## 1. GitHub Pages
1. Em github.com, crie um repositório **público** (ex.: `clientes`).
2. **Add file > Upload files** e envie: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. Clique em **Commit**.
3. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
4. Em 1 a 2 minutos o endereço fica `https://SEU-USUARIO.github.io/clientes/`.

## 2. Instalar no celular
- Android (Chrome): menu ⋮ > **Instalar app**.
- iPhone (Safari): Compartilhar > **Adicionar à Tela de Início**.

## Atenção
- Quem abrir o endereço vê os clientes **daquele aparelho** (os dados não ficam no GitHub).
- Limpar os dados do navegador apaga os clientes: faça backup de vez em quando.

## Atualizar o app depois
No repositório, abra o arquivo, clique no lápis, cole a nova versão e faça Commit.
