# Deck Builder MTG API

## 1. Introdução

Esta API RESTful permite que jogadores de Magic: The Gathering criem, modifiquem, organizem e compartilhem seus decks de maneira eficiente. Através de operações CRUD em decks, cartas e usuários, proporciona um codigo padronizado para plataformas como Moxfield ou Archidekt.

## 2. Rotas da API

| Método | Rota                              | Descrição                                | Status Codes        |
|--------|-----------------------------------|------------------------------------------|---------------------|
| GET    | /decks                            | Listar todos os decks                    | 200, 500            |
| GET    | /decks/{id}                       | Buscar deck por ID                       | 200, 404, 500       |
| POST   | /decks                            | Criar novo deck                          | 201, 400, 500       |
| PUT    | /decks/{id}                       | Atualizar deck existente                 | 200, 400, 404, 500  |
| DELETE | /decks/{id}                       | Excluir deck existente                   | 204, 404, 500       |
| GET    | /cards                            | Listar todas as cartas                   | 200, 500            |
| GET    | /cards/{id}                       | Buscar carta por ID                      | 200, 404, 500       |
| POST   | /cards                            | Cadastrar nova carta                     | 201, 400, 500       |
| PUT    | /cards/{id}                       | Atualizar carta                          | 200, 400, 404, 500  |
| DELETE | /cards/{id}                       | Remover carta                            | 204, 404, 500       |
| GET    | /users                            | Listar todos os usuários                 | 200, 500            |
| GET    | /users/{id}                       | Buscar usuário por ID                    | 200, 404, 500       |
| POST   | /users                            | Cadastrar novo usuário                   | 201, 400, 500       |
| PUT    | /users/{id}                       | Atualizar usuário                        | 200, 400, 404, 500  |
| DELETE | /users/{id}                       | Deletar usuário                          | 204, 404, 500       |
| GET    | /decks/{id}/cards                 | Listar cartas de um deck                 | 200, 404, 500       |
| POST   | /decks/{id}/cards                 | Adicionar carta a um deck                | 201, 400, 404, 500  |
| DELETE | /decks/{deckId}/cards/{cardId}    | Remover carta de um deck                 | 204, 404, 500       |
| GET    | /favorites                        | Listar decks favoritos                   | 200, 500            |
| POST   | /favorites                        | Adicionar deck aos favoritos             | 201, 400, 500       |

## 3. DTOs e Modelos de Dados

#### DeckDTO
```json
{
  "id": 1,
  "nome": "Combo Azul",
  "formato": "Commander",
  "descricao": "Deck focado em controle e combos.",
  "cartas": [
    {
      "id": 101,
      "nome": "Counterspell",
      "tipo": "Instantâneo",
      "cor": "Azul",
      "custoMana": "UU",
      "quantidade": 2
    }
  ],
  "dataCriacao": "2025-04-20T12:34:56Z"
}
```

#### CartaDTO
```json
{
  "id": 101,
  "nome": "Lightning Bolt",
  "tipo": "Instantâneo",
  "cor": "Vermelho",
  "custoMana": "R",
  "descricao": "Cause 3 de dano a qualquer alvo.",
  "edicao": "M10"
}
```

#### UsuarioDTO
```json
{
  "id": 42,
  "nome": "João Silva",
  "email": "joao@example.com",
  "dataCadastro": "2025-04-18T09:00:00Z"
}
```

####FavoriteDTO
```json
{
  "usuarioId": 42,
  "deckId": 1
}