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

 //mongodb/screenshots/1.jpg
 
 

Depois abra outro CMD (Prompt de Comando) e digite: "mongo" sem aspas.
O resultado será este:

 //mongodb/screenshots/2.jpg

Em pararelo (com 2 prompts aberto) tanto com o mongod e mongo abertos.

A primeira janela que abrimos com o mongod assim que iniciamos o serviço com "mongo" ele nos avisa que alguém se conectou a ele.
Depois disto basta fazer nossas consultas usando a mesma janela que iniciamos o mongo.

Aqui farei algumas comparações entre o modelo relacional que usamos nos banco SQL e o não relacional (NOSQL) que usamos no mongo. Estes exemplos são relacionados ao banco cafecombytes.

Pra saber a quantidade de inserções dentro de uma collection usamos:

Mongo > db.cafecombytes.count() 
SQL Relacional > Select count(*) from cafecombytes

Buscas:

MongoDB:
db.cafecombytes.find()
db.cafecombytes.findOne()
db.cafecombytes.find({matricula:”141220111”}]
db.cafecombytes.find({idade:20}, {"curso":true, "_id":false})
db.cafecombytes.find({curso:"Análise e desenvolvimento de Sistemas"}, {"nome":true, "curso":true, "idade":true, "_id":false}).pretty().count()

SQL Relacional:
Select * from cafecombytes
Select * from cafecombytes limit 1
Select * from cafecombytes where matricula = “141220109”
select curso from cafecombytes where idade=20


<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.bank_data.count</span>()
50000</pre></div>


http://i.imgur.com/1sOgO3c.png

ou

<img src=http://i.imgur.com/1sOgO3c.png>




