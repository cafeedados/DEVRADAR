## Back-end

O que é o back-end da aplicação: 

O back-end é aquela parte do código que o usuário não enxerga é onde ficam:

- Regras de Negócios;
- Conexão Banco de Dados;
- Envio de e-mail;
- Comunicação com webservices;
- Autenticação do usuário;
- Criptografia e segurança; 


A **API Restfull** quer dizer que ela segue uns padrões, são padrões de metodos, tipos de parametros e etc. 

Quando se tem o backend feito com node precisamos de algo para interpretar com o fontend, 

![Estrutura](../img/smo-07.png)

E é usado o JSON que é a linguagem (ela nao e bem uma linguagem ela e uma estrutura de dados) que faz essa ponte entre o back e o front
a notação dele é JavaScriot Of Notation. 

Dentro da pasta do Backend através do powershell voce executa o sequinte comando:

``` yarn init -y  ```

para ele nao realizar perguntas sobre o projeto que nao sao importantes no momento

![Yarn](../img/smo-08.png)


assim que realizarmos isso, ira aparecer um package.json 


apos isso devemos adicionar o express com o seguinte comando:

``` yarn add express ```

apos isso ira criar uma pasta chamada node_modules (sao todos os codigos dos pacotes instalados) e um arquivo chamado yarn.lock (ele guarda as informacoes dos pacotes instalados etc)

porque vai muito mais que apenas o express ou seja quando fazemos uma instalacao de um pacote esse processo e recursivo ou seja sempre um pacote depende de outro que depende de outro.

inciando o desenvolvimento:

<hr>

**1 . Devemos criar um arquivo chamado Index.js**

toda aplicacao ela tem rotas;  

ou seja exemplo de sintaxe:  Supondo o site www.semanaomnistack.com

supondo que eu quero acessar uma listagem de usuarios usaremos a rota www.semanaomnistack.com/user ou seja o **/user** e a rota que iremos ir

ou seja a rota e o endereco adicional que recebemos apos o endereco principal da aplicacao. 

<hr>

**2 . Chamando o express e imputando ele na aplicacao:**

```javascript

const express = require('express'); //chamando o express em uma variavel

const app = express(); //express ele e uma funcao


/***
 *  a aplicacao quando esta em ambiente de desenvolvimento sempre acesso a local host, ou seja sempre podemos escolher a posta que queremos rodar ela
 * 
 */


```


<hr>

**3. Depois iremos definir o caminho onde essa aplicacao ira seguir:**



```javascript

 app.get('/', (request, response) => {


 }); //aqui vai definir a rota e podemos imputar uma arrow function 

/**
 * Essa funcao acima recebe dois parametros que sao imbutidos de uma forma totalmente automatica pelo express
 * 
 * esses dois paramentros sao sempre fixos que sao: 
 * 
 * req  ---- que irei nomear como request (que representa a requisicao)
 * 
 * res ------ que irei nomear como response (que representa a resposta)
 * 
 * Explicando a sitaxe acima: 
 * 
 * O que sao esses dois parametros, quando eu acesso uma rota estou fazendo uma requisicao e ela pode conter informacoes, e o response e como iremos retornar uma resposta para meu 
 * cliente
 * 
 */


```


e para que se retorne uma resposta para testar a aplicacao usamos o send como abaixo

```javascript


 app.get('/', (request, response) => {
     return response.send('Hello World'); //response serve para mandar um texto ou seja to mandando retornar uma resposta

 });


```

**PARA EXECUTAR O ARQUIVO DEVE COLOCAR NA LINHA DE COMANDO DO TERMINAL**

``` node index.js ```  Ou seja estara mandando o node executar o arquivo index.js

![Node Executando](../img/smo-09.png)

Se observarmos ele ficara executando, porem para acessarmos temos que ir no navegador e colocar localhost e a porta selecionada que no caso do codigo foi a porta 3333


![navegador](../img/smo-10.png)

caso queria parar a execucao do node e so apertar ``` ctrl + c ```

<hr>

**4. Utilizando a Estrutura de dados chamada Json**

No lugar de send como mostrado no codigo acima iremos colocar json e nao podemos enviar uam string nele, temos que enviar um vetor ou um objeto. para enviar um objeto coloca entre chafes


```Javascript


 app.get('/', (request, response) => {
     return response.json({ message: ' Hello World'}); 

 });

```

<hr>

**5. Atualizacao automatica** 

Uma coisa que temos que perceber se eu mudar qualquer coisa e salvar e tentar atualizar ele nao ira mudar, porque o node depois que ele executou ele nao fica observando as alteracoes no codigo simplemsente ele so fica no anterior, para isso agente vai instalar uma outra dependencia / biblioteca com o seguinte comnado:

``` yarn add nodemon -D ``` esse -D ele significa que e uma dependencia de desenvolvimento

dependencias de desenvolvimento ficam separadas no packege.json dentro de devDependencies, o que quer dizer uma dependencia de desenvolvimento? sao dependencias que nos nao iremos utilizar ela quando a aplicacao for para producao que iremos usar somente no ambiente de desenvolvimento. 

<hr>

**6. Executando a aplicacao em ambiente de desenvolvimento:**

podemos usar:

``` yarn nodemon index.js ``` 


Executando asssim ou seja sempre que alterarmos algo no codigo sera atualizado automaticamente


**POREM PARA NAO FICARMOS ESCREVENDO TODA VEZ YARN NODEMON (NOME DO ARQUIVO) PODEMOS CRIAR UM MINI SCRIPT NO PACKGE.JSON** 

como abaixo:

![navegador](../img/smo-11.png)

```json

{
  "name": "backend",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "dev" : "nodemon index.js"
  },
  "dependencies": {
    "express": "^4.17.1",
    "nodemon": "^2.0.2"
  }
}


```

ou seja estou falando no script acima que toda vez que eu escrever **yarn dev** ira executar a instrucao dentro do terminal via script como **nodemon index.js**

![script](../img/smo-12.png)


**6. Apos deixar executando abriremos um outro terminal onde esta apontado com a seta na imagagem abaixo e logo em seguida como fica aberto dois terminais.**

![part1-terminal](../img/smo-13.png)

Ficara assim!

![part1-terminal](../img/smo-14.png)

Isso para fazer instalacoes de outras dependencias executar ou aglo assim.


<hr>

## Entendendo as rotas e Metodos

Os principais metodos que utilizaremos sao: 

| Metodos HTTP |  Descricao                                                                                                                        |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------|
|  get         | Quando se cria uma rota usando o metodo get, quer dizer que estou buscando uma informacao ou seja get do ingles significa pegar   | 
|  post        |                                                                                                                                   |
|  put         | Quando se quer editar um recurso da aplicacao                                                                                     |  
|  delete      | E o delete e para deletar                                                                                                         |


get conseguimos acessar sem precisar de outros sistemas porque ele ja e nativo do browser, porem se quisermos testar os outros metodos, nesse caso iremos usar outra ferramenta chamada insominia


Tipos de parâmetros:

**Query Params:** Eles sao 90% das vezes usados no metodo get, imagine que voce tenha uma rota app.get de listagem de ususarios ou seja essa rota ira listar os usuarios e vamos supor que eu quero buscar e tenho um imput de busca ou seja quando eu for passar essa informação pro meu backend qual e a busca do usuario eu envio como um Querry Pararm para criar no insomnia basta clicar na aba Querry: Terá dois campos o do nome e do valor, exemplo se voce for fazer um search (busca) e vo valor pedro.  

E ele e requisitado como req.query (request.query) e e usado para filtros, para ordenação, paginação e etc.

**Route Params:** Eles praticamente sempre sao usados no metodo Put e no Metodo Delete, ou seja quando eu quero editar um usuario ou deletar um usuario eu estou falando especificamente de um usuario, entao eu preciso informar qual e esse usuario que quero alterar e qual e o que quero deletar e etc. 

Para acessar esses parametros iremos utilizar o req.params (request.params) e e usado para identificar um recurso na alteracao ou remoção

**Body:** ele e muito utilizado no metodo post e put, ou seja quando eu quero criar alguma coisa. por exemplo eu quero cirar um usuario para enviar os dados eu preciso evniar pelo corpo da requisição e o corpo da requisição pode ter varios formatos o formato que iremos utilizar por se tratar de uma API restfull será o JSON. para se escrever no corpo do Json no insominia temos quer tratar como um obejeto no javaScript a unica diferença e que toda propriedade todo valor precia escrever em aspas duplas. a nao ser que seja um numero exeplo:

```json 
{
    "name": "pedro",
    "email": "dev.pedrolourenco@gmail.com"


}


```
e para acessar esse parametro iremos usar o req.body (request.body) e e usado apra dados para criacao ou alteracao de um registro.

> **Lembrando que por padrao a Lib do EXPRESS nao entende Json entao devemos informar a ele para conseguir integrar exemplo ``` app.use(express.json()) ``` ou seja to dizemos ao meu express que ele ire entender o que e json.*** 




[Download Isominua](https://insomnia.rest/)

Caso seu sistema seja 32 bits nao ira funcionar o insomnia mas tem um similar chamado getpostman

[Download getpostman](https://www.getpostman.com/downloads/)

<hr>

**7. Configurando o Insominia** 

- Criando a Requisicao no insomnia (request)

passo 1

![passo1](../img/smo-15.png)


passo 2

![passo2](../img/smo-16.png)

passo 3 (selecionar metodo)

![passo3](../img/smo-17.png)


passo 4 (No canto superior iremos colocar o endereco e quando clicarmos e send veremos que retornara o medoto get)

![passo3](../img/smo-18.png)

Lembrando que o Insômnia ele recebe outros metodos ou seja se alterarmos no codigo para um metodo post e depois alterarmos no insominia ele irá executar.


<hr>

## CONECTANDO A APLICACAO AO BANCO DE DADOS e CRIACAO DAS TAELAS


DO DEVRadas, onde iremos cadastrar os devs e etc.  


Estamos Utilizando o MongoDB (Ele e um banco nao-Relacional) ou seja ele e otimo para aplicacoes que nao preciam de um relacionamento (por exemplo se formos fazer um E-commerce ai e um pouquinho mais complicado pois pensa um pedido ele e ligado a estoque, pessoa e varios parametros) Nao quer dizer que nao conseguimos fazer um relacionamento no mongoDB mas quer dizer que e mais complicado de escalar. 


[MongoDB](mongodb.com)

Ele e um banco de dados muito rapido e e hopedado em cloud


1. Primeira coisa e conectar com o banco de dados:

- Crie no site do MongoDb uma Clouster Free.

- Apos isso va em **Database  Acessess**

- Apois isso vai em **Network Acess** onde ira liberar os IPs que querem que acesse o  mondgo como esta em ambiente de desenvolvimento selecione (Allow Acess From Anywhere) agora quando for publicado deve-se colocar o IP do servidor em (add currente ip adressss)


**Configurando e conectando a Clouster**

1 . Clique em conected


![passo4](../img/smo-19.png)


2 . Vai clicar em conect yourAplication


![passo5](../img/smo-20.png)


3. Vai confirmar se o driver e nodeJS e confirmar a versao e depois copiar a string

![passo6](../img/smo-21.png)


**INSTALANDO O MONGOOSE**


Apos feito isso vamos instalar usando no terminal ``` yarn add mongoose ```

O mongoose e uma biblioteca que vai da acesso do node dentro da base de dados mongo que vai possibilitar a comunicacao da aplicacao com uma base de dados mongo


apos isso iremos importar apra dentro da aplicacao o mongoose

```JavaScript 

const mongoose = require('mongoose');

```
apos isso iremos fazer a conexao com o banco de dados 


```JavaScript 

/** e dentro dos paramtros da funcao abaixo e ira colocar entre string a string de conexao do mongo  */
mongoose.connect('mongodb+srv://omnistack:<password>@cluster0-ki3vj.mongodb.net/test?retryWrites=true&w=majority'); 

```


assim que contectarmos o node ira retornar no terminal um "Erro" que nao e bem um erro:

>(node:14384) DeprecationWarning: current URL string parser is deprecated, and will be removed in a future version. To use the new parser, pass option { useNewUrlParser: true } to MongoClient.connect.   
>(node:14384) DeprecationWarning: current Server Discovery and Monitoring engine is deprecated, and will be removed in a future version. To use the new Server Discover and Monitoring engine, pass option 
>{ useUnifiedTopology: true } to the MongoClient constructor.

Para resolver isso iremos passar um segundo aprametro para sfuncao lembrando que o que estamos passando esta como dica de resolucao no proprio aviso

```JavaScript 

mongoose.connect('mongodb+srv://omnistack:omnistack@cluster0-ki3vj.mongodb.net/week10?retryWrites=true&w=majority', {
    useNewUrlParser: true,
    useUnifiedTopology: true
}) ; 

```


Alguns erros que podem dar na conexao:

- Se voce trocou o usuario e senha (confirnar b databe assess se o usuario e senha estao configurados certinhos)

- Conferir se o Network Acess foi configurado corretamente

- Caso nao de trocar a versao (ai copia a url)

- e se voce estiver em proxy pode dar erro ai voce pode consultar o  [portquiz.net:27017](portquiz.net:27017) ou seja 27017 e a porta do mongoDB



## Models

O que sao os Models?

Os models sao as representacoes das entidades da nossa aplicacao, entidades podemos pensar como aquelas informacoes que queremos armazenar no nosso banco de dados

## CONSUMINDO A API DO GITHUB

Para comecao vamos adicionar usando o Yarn o Axios ``` yarn add axios``` que ela faz chamadas para outras APIs Disponiveis

apos isso de o comando da API do Git 


```JavaScript 

routes.post('/devs', async (request, response) => {
     const { github_username, techs } = request.body;  

     const apiResponse = await axios.get(`https://api.github.com/users/${github_username}`);

    let { name = login, avatar_url, bio } = apiResponse.data; 
  
    console.log(name, avatar_url, bio, github_username);

    const techsArray = techs.split(',').map( techs => techs.trim()); 

     
    const dev = await Dev.create({
        github_username, 
        name,
        avatar_url,
        bio,
        techs: techsArray,

    });

    return response.json(dev); 

    

}); 

```

## CONECTANDO O MONGO COMMUNITU COMPASS

1. 

![passo7](../img/smo-22.png)

2. 

![passo8](../img/smo-23.png)

## CONTROLER NAME

Normalmente quando se nomeia o controller segue um padrao

index       ---->     Quando se quer buscar uma lista
show        ---->     Quando se quer buscar apenas um item 
store       ---->     Quando eu quero cirar algo
update      ---->     Quando eu quer alterar
destroy     ---->     Quando eu quero Deletar


## finalizacao do backEnd

1. 

![passo9](../img/smo-24.png)

2. 

![passo10](../img/smo-25.png)
