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