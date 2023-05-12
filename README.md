# m4-sprint5-relacionamento-1-N-TypeORM-Rsoares
API de Filmes
API para cadastro, atualização, listagem e remoção de filmes.

Endpoints
Método	Endpoint	Responsabilidade
POST	/movies	Cadastra um novo filme
GET	/movies	Lista todos os filmes cadastrados
PATCH	/movies/:id	Atualiza o filme passado por id
DELETE	/movies/:id	Deleta o filme passado por id
Regras da Aplicação
Deve ser criado um banco de dados em PostgreSQL com uma tabela/entidade nomeada como "movies", para armazenar os dados das requisições.
A tabela de "movies" deve ter as colunas necessárias para armazenar os seguintes dados: id (inteiro, sequencial e chave primária), name (string, tamanho máximo de 50, único e obrigatório), description (texto), duration (inteiro e obrigatório), price (inteiro e obrigatório).
Como estamos trabalhando com TypeORM, deve ser criada uma entidade de "movies" com os campos descritos acima, e essa entidade será convertida em tabela através de uma migração.
O nome da classe da entidade deve ser "Movie" e deve ser criado um arquivo index.ts dentro da pasta de "entities" centralizando o export dela para que os testes funcionem.
Nas rotas POST e PATCH, é necessário serializar os dados de entrada utilizando o "zod". Chaves não mapeadas devem ser ignoradas.
Na rota POST /movies, a chave "id" deve ser ignorada, o próprio serviço deve preencher esse dado. A chave "description" é opcional, caso não seja enviada deve ser salva como null.
Na rota PATCH /movies/:id, a chave "id" não pode ser atualizada, caso enviada no body deve ser ignorada.
A rota GET /movies deve conter paginação. Essa rota recebe quatro query params, sendo eles: page, perPage, order e sort. Essa rota retornará um objeto de paginação que irá conter as seguintes chaves: prevPage, nextPage, count e data.
