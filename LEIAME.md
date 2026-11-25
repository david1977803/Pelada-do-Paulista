# Pelada de Domingo — app no GitHub + Firebase

App web (abre no navegador do celular e pode ser instalado na tela inicial).

- **Jogadores**: abrem o link e **só visualizam** a lista, os times, o campo e o placar. Não precisam de login.
- **Administradores**: tocam em **"Entrar (admin)"** com a conta Google e podem alterar tudo, inclusive o Caixa e o Elenco.
- As regras do banco de dados (Firestore) garantem isso no servidor. Mesmo que alguém tente alterar por fora do app, a gravação é recusada.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | O aplicativo |
| `firebase-config.js` | Configuração do seu projeto Firebase (você preenche no passo 3) |
| `firestore.rules` | Regras de segurança do banco (você cola no Firebase no passo 2) |
| `dados-iniciais.json` | Cadastro atual (40 jogadores, chegadas e times de 29/11) para importar uma vez |

---

## Passo 1 — GitHub (hospedagem gratuita)

1. Crie uma conta em https://github.com (se ainda não tiver).
2. Clique em **New repository**, dê o nome `pelada`, deixe **Public** e clique em **Create repository**.
3. Na página do repositório, clique em **uploading an existing file**, arraste os 5 arquivos desta pasta e clique em **Commit changes**.
4. Vá em **Settings → Pages**. Em *Branch*, escolha `main` e a pasta `/ (root)`, depois clique em **Save**.
5. Em 1 ou 2 minutos o app fica no ar em: `https://SEU-USUARIO.github.io/pelada/`

## Passo 2 — Firebase: banco de dados

1. Acesse https://console.firebase.google.com e clique em **Criar projeto**. Nome: `pelada`. O Google Analytics pode ficar desativado.
2. No menu, abra **Firestore Database** e clique em **Criar banco de dados**:
   - local: **southamerica-east1 (São Paulo)**
   - modo: **produção**
3. Abra a aba **Regras**, apague tudo, cole o conteúdo do arquivo `firestore.rules` e **troque `SEU-EMAIL@gmail.com` pelo e-mail Google do dono**, em minúsculas. Clique em **Publicar**.

## Passo 3 — Firebase: login e configuração

1. No menu, abra **Authentication → Começar → Google**, ative, escolha o e-mail de suporte e clique em **Salvar**.
2. Ainda em Authentication, vá em **Configurações → Domínios autorizados → Adicionar domínio** e informe `SEU-USUARIO.github.io`.
3. Clique na engrenagem ⚙ e depois em **Configurações do projeto**. Em **Seus apps**, clique no ícone **</>** (Web), registre o app com o nome `pelada` (sem marcar Hosting) e copie o bloco `firebaseConfig`.
4. No GitHub, abra o arquivo `firebase-config.js` e clique no lápis ✏ para editar. Substitua os valores de exemplo pelos que você copiou e clique em **Commit changes**.
   (Esses dados não são secretos; quem protege o banco são as regras do passo 2.)

## Passo 4 — Primeiro acesso (feito pelo dono)

1. Abra `https://SEU-USUARIO.github.io/pelada/` e toque em **Entrar (admin)** com a conta Google do dono.
2. Toque em **"Sou o dono — configurar"**.
3. Toque em **"Importar dados iniciais"**: os 40 jogadores, as chegadas e os times entram no banco.
4. Na aba **Elenco → Administradores**, adicione o e-mail Google de cada administrador.
5. *(Opcional)* Depois de importar, apague o arquivo `dados-iniciais.json` do GitHub, porque ele fica público no repositório.

## Passo 5 — Divulgar e instalar

- Mande o link no grupo do WhatsApp.
- **Android (Chrome)**: menu ⋮ → **Adicionar à tela inicial**.
- **iPhone (Safari)**: botão Compartilhar → **Adicionar à Tela de Início**.

## Custos

O plano gratuito do Firebase (Spark) e o GitHub Pages são suficientes para a pelada. Não é preciso cadastrar cartão de crédito.

## Atualizar o app no futuro

Basta substituir o `index.html` no GitHub (Add file → Upload files). Os dados ficam no Firebase e não se perdem.
