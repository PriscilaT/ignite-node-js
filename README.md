# ignite-node-js

Início: 29/11/2021

$ yarn init -y 
Inicia o projeto criando o arquivo package.json, que guarda as dependencias do projeto e infos

$yarn add express 
Ajuda no gerenciamento de rotas e criar servidor e middlewares
Cria a pasta node_modules

 * Criar pasta chamada "src" e dentro dela um arquivo chamado index.js
 Nesse arquivo importa o express e coloca a aplicação escutando numa porta 

 ```
    const express = require('express');

    const app = express();

    app.get("/", (request, response) =>{
        return response.send("Hello world!")
    });

    app.listen(3333);
 ```
E pra verificar se está tudo ok, roda no terminal 
$ node src/index.js

E abre o navegador em http://localhost:3333/

Versão retornando json

```
    const express = require('express');

    const app = express();

    app.get("/", (request, response) =>{
        return response.json({message: "Hello world Ignite!"});
    });

    app.listen(3333);
```

$ yarn add nodemon -D

O nodemon faz o reload para a gente não precisar ficar derrubando o servidor e reiniciando toda vez que fizer uma alteração
Instala como dependencia de desenvolvimento, pra so funcionar enquanto desenvolvemos 


Adiciona no package. json 
```
    "scripts": {
        "dev": "nodemon src/index.js"
    },
```
$ yarn dev

Começando a fazer rotas, métodos HTTP
 - GET
 - POST
 - PUT
 - PATCH
 - DELETE

```
app.get("/courses", (request, response) =>{
    return response.json(["Curso 1","Curso 2","Curso 3"]);
});

app.post("/courses", (request, response) =>{
    return response.json(["Curso 1","Curso 2","Curso 3", "Curso 4"]);
});

app.put("/courses/:id", (request, response) =>{
    return response.json(["Curso 6","Curso 2","Curso 3", "Curso 4"]);
});

app.patch("/courses/:id", (request, response) =>{
    return response.json(["Curso 6","Curso 7","Curso 3", "Curso 4"]);
});

app.delete("/courses", (request, response) =>{
    return response.json(["Curso 6","Curso 7","Curso 3"]);
});

```

 * Instala o Insomnia

 (Não vou descrever aqui muito bem como usá-lo)

 * Tpos de parâmetros
 Route Params - Identificar recurso editar/deletar/buscar
 Query Params - Paginação/Filtro
 Body Params - Os objetos inserção/alteração (em JSON)

 ## Primeiro projeto FinAPI - Financeira

Para criação de IDs importar a biblioteca uuid
$ yarn add uuid

Para receber no index.js e dentro da rota nomeia a variável

```
const { v4: uuidv4 } = require("uuid")

const id - uuidv4();

```

Criando um array como os clientes, com o método push pois quero inserir dados. Caso tudo ocorra bem, ele retorna um 201.

```
const customers = [];

custumers.push({
        cpf,
        name,
        id,
        statement: [],

    });
return response.status(201).send();

```

Então já podemos iniciar o servidor e criar uma request no insomnia
$ yarn dev

Para conseguir receber um JSON, colocamos um middleware logo após o express

```
cons app = express();

app.use(express.json());
```