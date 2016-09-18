# MONGODB Café com bytes
Aula sobre mongodb - cafecombytes

O MongoDB é um document database 

* Documentos com informações no formato JSON. 
* A ideia e o documento representar toda a informação
* Os documentos sao agrupados em collections.
* Um conjunto de collections forma um database (banco de dados).

Antes de começar precisamos do mongodb:

<a href="https://www.mongodb.com/">MongoDB</a>

A instalação é bem simples, quando terminar a instalação crie uma pasta no Disco C "C:\" 

Com o nome data e dentro da pasta data outra pasta chamada db.
> C > data > db

É dentro desta pasta que ficam salvos os arquivos do mongodb.

Para iniciar o banco basta abrir o CMD (Promp de Comando) e iniciar o serviço : "mongod" sem aspas.
O resultado será este:

 <img src="https://github.com/kevenleone/mongodb/blob/master/screenshots/1.jpg">
 
 

Depois abra outro CMD (Prompt de Comando) e digite: "mongo" sem aspas.
O resultado será este:

 <img src="https://github.com/kevenleone/mongodb/blob/master/screenshots/2.jpg">

Em pararelo (com 2 prompts aberto) tanto com o mongod e mongo abertos.

A primeira janela que abrimos com o mongod assim que iniciamos o serviço com "mongo" ele nos avisa que alguém se conectou a ele.
Depois disto basta fazer nossas consultas usando a mesma janela que iniciamos o mongo.

Aqui farei algumas comparações entre o modelo relacional que usamos nos banco SQL e o não relacional (NOSQL) que usamos no mongo. Estes exemplos são relacionados ao banco cafecombytes.

Pra saber a quantidade de inserções dentro de uma collection usamos:

Mongo > db.cafecombytes.count() 
SQL Relacional > Select count(*) from cafecombytes

<h1>Buscas:</h1>

<h2>MongoDB:</h2>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">
db.cafecombytes.find()
db.cafecombytes.findOne()
db.cafecombytes.find({matricula:”141220111”}]
db.cafecombytes.find({idade:20}, {"curso":true, "_id":false})
db.cafecombytes.find({curso:"Análise e desenvolvimento de Sistemas"}, {"nome":true, "curso":true, "idade":true, "_id":false}).pretty().count()
</pre></div>



<h2>SQL Relacional:</h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">
Select * from cafecombytes
Select * from cafecombytes limit 1
Select * from cafecombytes where matricula = “141220109”
select curso from cafecombytes where idade=20
</pre></div>

Inserindo no banco de dados.
<h2> MongoDB</h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">
db.cafecombytes.insert({matricula: '141220198', nome:'José', sobrenome: 'Loureiro', idade:'20', curso: 'Análise e desenvolvimento de Sistemas', cidade:'Catende'})

<h2>SQL Relacional </h2>
</pre></div>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">
insert into cafecombytes (matricula, nome, sobrenome, idade, curso, cidade) values (141220198, 'José', 'Loureiro', 20, 'Análise e desenvolvimento de Sistemas', 'Catende');


</pre></div>

> OBS: Não é preciso alterar a estrutura da tabela para inserir no MongoDB, ele já faz isso automáticamente. Porém nos bancos SQL tal alteração é necessária, para isso basta dar um alter table nometabela add sexo varchar(20);

<h1> Removendo informações </h2>
<h2> MongoDB </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">
db.cafecombytes.remove({nome: ‘Lucas’})

<h2> SQL Relacional </h2>
</pre></div>
delete from cafecombytes where matricula= 1



<h1> Capped Collections </h1>
<h3> São coleções "tampadas" com limite de conteúdo que podem ser inseridos nela, o limite pode ser feito pelo tamanho em bytes do arquivo ou por numero de inserções.

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">


</pre></div>
db.createCollection("<collection>", {capped: true, size: <tamanho-em-bytes>, max: <número-de-documentos>})

db.createCollection("fisco", {capped: true, size: 4096, max: 10})


<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">


</pre></div>

