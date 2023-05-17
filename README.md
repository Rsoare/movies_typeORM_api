# API de Filmes

- API para cadastro, atualização, listagem e remoção de filmes.

# Endpoints

| Método | 	Endpoint    |	Responsabilidade                  |
|  ---   |    ---       |     ---                           |
| POST	 |  /movies     |	Cadastra um novo filme            |
| GET	   |  /movies     |	Lista todos os filmes cadastrados |
| PATCH  |	/movies/:id |	Atualiza o filme passado por id   |
| DELETE |  /movies/:id |	Deleta o filme passado por id     |

# Regras da Aplicação

### POST - /movies

- Rota de criação de filmes. A chave description é opcional.

| **Corpo da requisição:** |
|-|

```json
{
  "id": 40,
  "duration": 60,
  "name": "Movie: Sem description",
  "price": 200
}
```
  
| **Resposta do servidor:**           |
| ----------------------------------- |
| **Status code:** **_201 CREATED._** |

``` json
{
  "id": 1,
  "name": "Movie: Sem description",
  "description": null,
  "duration": 60,
  "price": 200
}
```

### GET - /movies
- É possível listar os filmes armazenados no banco de dados. Seguindo as regras de paginação
- Url da requisição: `http://localhost:3000/movies/?sort=price&order=desc&page=2&perPage=3`

| Resposta do servidor: |
| - |
|**Status code:** **_200 OK._**|

``` json
{
    "prevPage": "http://localhost:3000/movies?page=1&perPage=3",
    "nextPage": "http://localhost:3000/movies?page=3&perPage=3",
    "count": 14,
    "data": [
        {
            "id": 8,
            "name": "Filme 08",
            "description": null,
            "duration": 88,
            "price": 72
        },
        {
            "id": 4,
            "name": "Filme 04",
            "description": null,
            "duration": 75,
            "price": 72
        },
        {
            "id": 11,
            "name": "Filme 11",
            "description": null,
            "duration": 7,
            "price": 68
        }
    ]
}
```

### PATCH - /movies/:id

- É possível atualizar um filme pelo id recebido nos parâmetros da rota.

| **Corpo da requisição:** |
|-|

``` json
  {
    "id": 55,
    "duration": 130,
    "price": 200
  }
```
 
| Resposta do servidor:          |
| ------------------------------ |
| **Status code:** **_200 OK._** |

``` json
 {
  "id": 4,
  "name": "Filme 04",
  "description": null,
  "duration": 130,
  "price": 200
 }
```
 
### DELETE - /movies/:id
-  É possível deletar um filme pelo id recebido nos parâmetros da rota.

| Resposta do servidor: |
|-|
|**Status code:** **_204 NO CONTENT._**|

