# Introdução ao Express

Neste exercício você usará a estrutura Express para implementar uma funcionalidade semelhante à implementada pelos servidores baseados no módulo HTTP no NodeJS. Ao final deste exercício, você será capaz de:

	- Implementar um servidor web simples usando a estrutura Express
	- Implementar um servidor web que veicule conteúdo estático

# Um servidor simples usando o Express

	- Crie um repositório no GitHub chamado "nodejs-express"
	- Clone-o na raíz do sistema operacional do seu computador
	- Acesse-o com o comando: cd nodejs-express
	- Crie o arquivo package.json com o comando: npm init
	- Responda as perguntas com as respostas padrão
	- Edite o arquivo package.json adicionando o script start:

	"scripts": {
	    "test": "echo \"Error: no test specified\" && exit 1",
	    "start": "node index.js"
    },

	- Crie uma subpasta com o comando: mkdir public
	- Crie dois arquivos na pasta public: index.html e sobre.html
	- Instale o Express com o comando: npm install express --save
	- Crie um arquivo chamado .gitignore contendo node_modules
	- Crie um arquivo chamado index.js com o seguinte conteúdo:

	const express = require('express'),
    http = require('http');

	const hostname = 'localhost';
	const port = 3000;

	const app = express();

	app.use((req, res, next) => {
	  console.log(req.headers);
	  res.statusCode = 200;
	  res.setHeader('Content-Type', 'text/html');
	  res.end('<html><body><h1>This is an Express Server</h1></body></html>');

	});

	const server = http.createServer(app);

	server.listen(port, hostname, () => {
	  console.log(`Server running at http://${hostname}:${port}/`);
	});

	- Inicialize o servidor com o comando: npm start
	- Accesse o endereço localhost:300 para ver o servidor funcionando

# Servindo arquivos estáticos
	- Instale o módulo morgan com o comando: npm install morgan --save
	- Atualize o arquivo index.js para:

	const express = require('express'),
    http = require('http');

    const morgan = require('morgan');

	const hostname = 'localhost';
	const port = 3000;

	const app = express();

	app.use(morgan('dev'));

	app.use(express.static(__dirname + '/public'));

	app.use((req, res, next) => {
	  res.statusCode = 200;
	  res.setHeader('Content-Type', 'text/html');
	  res.end('<html><body><h1>This is an Express Server</h1></body></html>');

	});

	const server = http.createServer(app);

	server.listen(port, hostname, () => {
	  console.log(`Server running at http://${hostname}:${port}/`);
	});

	- Inicie novamente o servidor com: npm start
	- Observe as diferenças em relação ao código sem o morgan
	- Faça um novo commit chamado: "Servindo arquivos estáticos com Express"


