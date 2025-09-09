# 🔹 O que é JWT?

- O JWT (JSON Web Token) é um token no formato de string que carrega informações de forma segura (embora não criptografada por padrão, apenas assinada).
  Ele é usado para autenticação e autorização:

- **Autenticação** → Provar quem você é.
- **Autorização** → Provar o que você pode acessar.

Um JWT é composto por 3 partes separadas por pontos (.):

**header.payload.signature**

Exemplo de um JWT real (abreviado):

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJ1c2VySWQiOjEyMywiZW1haWwiOiJtYWlsQGV4ZW1wbGUuY29tIn0.
fA3FfP7b9d7u-ql1Qp3x-6x0p2JQ7u6PczPkM2-4Oc0

## 🔹 Estrutura do JWT

1. Header (cabeçalho)

Define o tipo do token e o algoritmo de assinatura.
Exemplo em JSON:

{
"alg": "HS256",
"typ": "JWT"
}

Codificado em Base64 → primeira parte do token.

2. Payload (corpo/dados)

Carrega as informações (claims).
Exemplo:

{
"userId": 123,
"email": "mail@example.com",
"exp": 1733779200
}

userId e email → dados do usuário.

exp → data de expiração (em timestamp Unix).

Codificado em Base64 → segunda parte do token.

3. Signature (assinatura)

Garante que o token não foi alterado.
É gerada assim:

HMACSHA256(
base64UrlEncode(header) + "." + base64UrlEncode(payload),
chave_secreta
)

👉 Se alguém tentar alterar o payload, a assinatura não vai bater e o token será inválido.

## 🔹 Fluxo de uso do JWT

1. Login:

- O usuário envia email/senha para a API.
- Se válido, o servidor cria um JWT e devolve ao cliente.

2. Armazenamento

- O cliente guarda o token (normalmente em localStorage ou sessionStorage, ou em um cookie seguro).

3. Requisições autenticadas

- Para acessar endpoints protegidos, o cliente manda o token no header HTTP:

Authorization: Bearer <token>

4. Validação

- O servidor recebe o token, valida a assinatura e a expiração.
- Se válido → autoriza a requisição.
- Se inválido/expirado → retorna erro 401 Unauthorized.

## 🔹 Vantagens do JWT

✅ Stateless → o servidor não precisa guardar sessão.
✅ Fácil de usar em sistemas distribuídos (vários servidores).
✅ Seguro contra alteração (assinatura garante integridade).

## 🔹 Desvantagens do JWT

⚠️ O payload é só Base64, não é criptografado → qualquer um pode ler os dados (então nunca colocar senhas ou dados sensíveis).
⚠️ Se um token for roubado, ele pode ser usado até expirar (precisa de revogação manual se for crítico).
⚠️ Tokens longos podem aumentar o tamanho dos headers.

👉 Em resumo: JWT é um passe de entrada assinado.

- O servidor só valida a assinatura e data de expiração.
- Não precisa lembrar do usuário entre as requisições (por isso é stateless).
