# challenge_business
Uma API desenvolvida para o sistema de controle de feedbacks.

## Endpoints
- Usuário Logado
    - [Listar](#listar_feedback)
- Usuário não logado
    - [Cadastrar feedback](#cadastrar_feedback)
    - [Registrar dados do usuário](#registrar_usuário)

---

### listar_feedback
`GET` /plusoft/feedback/getAll

**Exemplo de corpo da resposta**

```js
{
    "feedback_id": 1,
    "user":{
        "user_id": 1,
        "user_name": "Lorem Ipsum",
        "user_email": "lorem@example.com",
        "user_cellphone" : "954557812",
        "user_company": "Lorem Ipsum & Company",
        "date": "2023-01-27"
    },
    "user_feedback": {
        "user_feedback_id": 1,
        "description": "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.",
        "date": "2023-01-27"
    },
    "chat_answer": {
        "chat_answer_id": 1,
        "description": "Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.",
        "date": "2023-01-27"
    }
}
```

**Códigos de Resposta**

| código | descrição 
|-|-
| 200 | dados retornados com sucesso
| 404 | não foram encontrados feedbacks

---

### cadastrar_feedback
`POST` /plusoft/feedback/post

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|--
| user_feedback_id | long | sim | é o id de um feedback deixado por um usuário
| description | String | sim | é a mensagem do feedback deixado por um usuário
| date | Date | sim | é a data na qual o feedback foi feito

**Exemplo de corpo do request**

```js
{
    "description": "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo."
}
```

**Códigos de Resposta**

| código | descrição 
|-|-
| 201 | feedback registrado com sucesso
| 400 | erro na validação dos dados da requisição

---

### registrar_usuário
`POST` /plusoft/feedback/registerUser

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|--
| user_id | long | sim | é o id de um usuário
| user_name | String | sim | é o nome de um usuário
| user_email | String | sim | é o email de um usuário
| user_cellphone | String | sim | é o número para contato de um usuário
| user_company | String | sim | é a empresa na qual o usuário trabalha
| date | Date | sim | é a data na qual o usuário começou o seu registro

**Exemplo de corpo do request**

```js
{
    "user_name": "Lorem Ipsum",
    "user_email": "lorem@example.com",
    "user_cellphone" : "954557812",
    "user_company": "Lorem Ipsum & Company",
}
```

**Códigos de Resposta**

| código | descrição 
|-|-
| 201 | usuário registrado com sucesso
| 400 | erro na validação dos dados da requisição

---