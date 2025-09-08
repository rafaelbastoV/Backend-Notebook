# 🔹 Diferença entre API Stateless e API Stateful

## ✅ Stateless API

- O servidor **não guarda informações da sessão** do cliente entre requisições.
- Cada requisição deve conter **todos os dados necessários** para ser processada (ex.: tokens como **JWT**).
- **Escalável** → qualquer servidor pode atender a requisição.
- **REST APIs** são, por definição, **stateless**.

**Exemplo:**

1. Você faz login e recebe um **token JWT**.
2. A cada requisição, envia o token no header: Authorization: Bearer <token>
3. O servidor valida o token, mas **não precisa “lembrar”** que você está logado.

## ⚠️ Stateful API

- O servidor **guarda informações da sessão** do cliente entre requisições.
- Normalmente usa **cookies de sessão** para identificar o usuário.
- O cliente envia apenas um **identificador de sessão**, e o servidor mantém o **estado** (usuário logado, preferências, etc.).
- **Menos escalável** → se a sessão não for replicada, cair em outro servidor pode fazer você **perder o estado**.

**Exemplo:**

1. Você faz login → o servidor cria uma sessão e **guarda que você está logado**.
2. Nas próximas requisições, você só manda um **cookie com o session_id**, e o servidor sabe quem você é.

---

## 🧾 Resumindo

- **REST API** → arquitetura baseada em recursos acessados via HTTP (geralmente em JSON).
- **Stateless** → cada requisição é independente, sem sessão no servidor (**ideal para REST**).
- **Stateful** → o servidor mantém estado da sessão (mais simples em alguns casos, mas **menos escalável**).
