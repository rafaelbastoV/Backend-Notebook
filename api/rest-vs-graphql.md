# Comparação: API REST vs GraphQL

## 1. O que são

### REST

- **Representational State Transfer (REST)** é um estilo de arquitetura para construir APIs.
- Baseia-se em **recursos** identificados por URLs.
- Cada operação (CRUD) é feita através de **métodos HTTP** (`GET`, `POST`, `PUT`, `DELETE`).

### GraphQL

- **GraphQL** é uma linguagem de consulta para APIs.
- Permite que o cliente especifique **exatamente quais dados precisa**.
- Foi desenvolvido pelo Facebook para substituir algumas limitações do REST.

---

## 2. Estrutura das Requisições

### REST

- Cada recurso tem seu próprio endpoint.
- Exemplo:

GET /users
GET /users/123
POST /users

### GraphQL

- Existe apenas **um endpoint** (`/graphql`).
- O cliente envia uma **query** especificando os dados desejados:

```graphql
{
  user(id: 123) {
    name
    email
  }
}
```

---

## 3. Características

- Flexibilidade:
  REST -> Retorna um recurso completo
  GraphQL -> Retorna apenas os campos solicitados

- Overfetching:
  REST -> Pode retornar dados desnecessários
  GraphQL -> Evita overfetching

- Underfetching:
  REST -> Pode exigir múltiplas requisições
  GraphQL -> Uma única query pode trazer tudo

- Versionamento:
  REST -> Geralmente cria novas versões (v1) Sem versionamento; o cliente escolhe
  GraphQL -> Curva de aprendizado Simples de entender Requer aprendizado de schema e query

---

## 4. Casos de uso recomendados

REST:

- APIs simples ou bem definidas.
- Aplicações que não sofrem com excesso de requisições.
- Boa integração com caches HTTP.

GraphQL:

- Aplicações front-end complexas (mobile, SPA).
- Cenários onde se quer evitar múltiplas requisições.
- APIs que evoluem rapidamente e precisam de flexibilidade.

---

## 5. Conclusão

- REST é maduro, simples e funciona bem para APIs tradicionais.
- GraphQL oferece mais flexibilidade e eficiência, mas pode ser mais complexo de implementar.
- A escolha depende do tipo de aplicação, quantidade de dados trafegados e necessidade de evolução da API.
