![cover](https://github.com/Souzasilvaleonardo/nlw-expert-Poll/assets/105978283/d10cdd8d-224b-4b69-8396-3395201ed383)

# NLW Expert (Node.js)

Um sistema de votação em tempo real onde os usuários podem criar uma enquete e outros usuários podem votar. O sistema gera um ranking entre as opções e atualiza os votos em tempo real

### Requisites

- Docker;
- Node.js;

### Setup

- Clone o repositório;
- Instalar dependência (`npm install`);
- Configurar PostgreSQL e Redis (`docker compose up -d`);
- cópia `.env.example` arquivo (`cp .env.example .env`);
- Executar aplicativo (`npm run dev`);
- Teste-o! (Eu pessoalmente recomendo testar com https://hoppscotch.io/)

### HTTP

#### POST /polls


Crie uma nova enquete.

#### Request body
```json 
{
  "title": "Qual a melhor linguagem de programação?",
  "options": [
    "JavaScript",
    "Java",
    "PHP",
    "C#"
  ]
}
```

#### Response body
```json
{
  "pollId": "194cef63-2ccf-46a3-aad1-aa94b2bc89b0"
}
```

### GET /polls/:pollId

Return data from a single poll.

#### Response body
```json
{
	"poll": {
		"id": "e4365599-0205-4429-9808-ea1f94062a5f",
		"title": "Qual a melhor linguagem de programação?",
		"options": [
			{
				"id": "4af3fca1-91dc-4c2d-b6aa-897ad5042c84",
				"title": "JavaScript",
				"score": 1
			},
			{
				"id": "780b8e25-a40e-4301-ab32-77ebf8c79da8",
				"title": "Java",
				"score": 0
			},
			{
				"id": "539fa272-152b-478f-9f53-8472cddb7491",
				"title": "PHP",
				"score": 0
			},
			{
				"id": "ca1d4af3-347a-4d77-b08b-528b181fe80e",
				"title": "C#",
				"score": 0
			}
		]
	}
}

```

### POST /polls/:pollId/votes

Add a vote to specific poll.

#### Request body

```json
{
  "pollOptionId": "31cca9dc-15da-44d4-ad7f-12b86610fe98"
}
```

### WebSockets

#### Message
```json
{
  "pollOptionId": "da9601cc-0b58-4395-8865-113cbdc42089",
  "votes": 2
}
```

