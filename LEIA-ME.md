# Meus clientes: passo a passo

## 1. Supabase (login e dados na nuvem)
1. Crie uma conta grátis em supabase.com e clique em **New project** (guarde a senha do banco).
2. Abra **SQL Editor**, cole o código abaixo e clique em **Run**:

```sql
create table public.app_data (
  user_id uuid primary key references auth.users(id) on delete cascade,
  data jsonb not null default '{}'::jsonb,
  updated_at timestamptz not null default now()
);
alter table public.app_data enable row level security;
create policy "ler os proprios dados" on public.app_data for select using (auth.uid() = user_id);
create policy "criar os proprios dados" on public.app_data for insert with check (auth.uid() = user_id);
create policy "atualizar os proprios dados" on public.app_data for update using (auth.uid() = user_id) with check (auth.uid() = user_id);
```

3. Em **Project Settings > API**, copie a **Project URL** e a chave **anon / publishable**.
   Nunca use a chave service_role.
4. Abra o `index.html` e troque as duas linhas no começo do script:
   `const SUPABASE_URL='...'` e `const SUPABASE_KEY='...'`.
5. Em **Authentication > Sign In / Providers > Email**, desative **Confirm email**.

## 2. GitHub Pages
1. Em github.com, crie um repositório **público** (ex.: `clientes`).
2. **Add file > Upload files** e envie: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. Clique em **Commit**.
3. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
4. Em 1 a 2 minutos o endereço fica `https://SEU-USUARIO.github.io/clientes/`.

## 3. Primeiro acesso
1. Abra o endereço, toque em **Criar conta** e cadastre seu e-mail e senha.
2. No Supabase, em **Authentication > Sign In / Providers**, desative **Allow new users to sign up** para que ninguém mais crie conta.

## 4. Instalar no celular
- Android (Chrome): menu ⋮ > **Instalar app**.
- iPhone (Safari): Compartilhar > **Adicionar à Tela de Início**.

## Atualizar o app depois
No repositório, abra o arquivo, clique no lápis, cole a nova versão e faça Commit.
