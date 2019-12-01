# MONGODB Café com bytes !!
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

<h3> Alguns comandos do MongoDB </h3>

<h3> Importando um arquivo json para o MongoDB </h3>

Antes de tudo abra o Prompt de Comando (Windows + R) > cmd 
Em seguida vai abrir o prompt de comando e utilize este comando a seguir:

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">mongoimport --jsonArray --db nomedobanco --collection nomedacollection [caminho]\nomearquivo.json
</pre></div>

Como eu usaria o mesmo comando utilizando a minha máquina e o arquivo cafecombytes.json ficaria assim:

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">mongoimport --jsonArray --db fafica --collection cafecombytes E:\git\mongo\mongodb\cafecombytes.json</pre></div>

<h3>Collections</h3>

Coleções no MongoDB são recipientes para um grupo de entidades similares. Um único banco de dados pode ter muitas coleções. Para exibir as coleções em seu banco de dados execute:

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">show collections
</pre></div>

Pra saber a quantidade de inserções dentro de uma collection usamos:
<h2> MongoDB </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.count()
</pre></div>

<h2> SQL Relacional </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">Select count(*) from cafecombytes
</pre></div>

<h1>Buscas:</h1>

<h2>MongoDB:</h2>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.find()
db.cafecombytes.findOne()
db.cafecombytes.find({matricula:”141220111”}]
db.cafecombytes.find({idade:20}, {"curso":true, "_id":false})
db.cafecombytes.find({curso:"Análise e desenvolvimento de Sistemas"}, {"nome":true, "curso":true, "idade":true, "_id":false}).pretty().count()
</pre></div>

<h2>SQL Relacional:</h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">Select * from cafecombytes
Select * from cafecombytes limit 1
Select * from cafecombytes where matricula = “141220109”
select curso from cafecombytes where idade=20
</pre></div>

Inserindo no banco de dados.
<h2> MongoDB</h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.insert({matricula: '141220198', nome:'José', sobrenome: 'Loureiro', idade:'20', curso: 'Análise e desenvolvimento de Sistemas', cidade:'Catende'})
</pre></div>

<h2>SQL Relacional </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">insert into cafecombytes (matricula, nome, sobrenome, idade, curso, cidade) values (141220198, 'José', 'Loureiro', 20, 'Análise e desenvolvimento de Sistemas', 'Catende');
</pre></div>

> OBS: Não é preciso alterar a estrutura da tabela para inserir no MongoDB, ele já faz isso automáticamente. Porém nos bancos SQL tal alteração é necessária, para isso basta dar um alter table nometabela add sexo varchar(20);

<h1> Removendo informações </h2>
<h2> MongoDB </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.remove({nome: ‘Lucas’})
</pre></div>


<h2> SQL Relacional </h2>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">delete from cafecombytes where matricula= 1
</pre></div>


<h1> Update no MongoDB </h1>
<h3> Utilizamos o update quando queremos alterar algum valor dentro do banco de dados, no mongodb é possível alterar várias informações em um único update </h3>

<h2>MongoDB</h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.update({nome:"Keven Leone"},{nome:"Keven Leone dos Santos"})
</pre></div>
<h2> SQL Relacional </h2>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">alter table cafecombytes drop column matricula
alter table cafecombytes drop column sobrenome
alter table cafecombytes drop column idade
alter table cafecombytes drop column curso
alter table cafecombytes drop column cidade
update cafecombytes set nome:'Keven Leone', where matricula = '141220109';
</pre></div>

<h1> Operadores </h1>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.bank_data.find({$or: [ { last_name: "MARTINEZ"}, {last_name: "SMITH"} ]})
db.cafecombytes.find({$or: [{curso: "Análise e desenvolvimento de Sistemas"},{curso:"Administração"}]})
db.cafecombytes.find({cidade:"Palmares", $or: [{curso: "Análise e desenvolvimento de Sistemas"},{curso:"Administração"}]}).pretty()
</pre></div>

Para que os resultados fiquem mais "limpos" basta usar
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.find({$or:[{curso: "Análise e desenvolvimento de Sistemas"},{curso:"Administração"} ]}, {nome: 1, sobrenome: 1})
</pre></div>

<p> Para organizar as informações por ordem alfabética basta utilizar o <b>sort()</b></p>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.cafecombytes.find({$or: [{curso: "Análise e desenvolvimento de Sistemas"},{curso:"Administração"}).sort({nome: 1 })
</pre></div>


<h1> Capped Collections </h1>
<h5> São coleções "tampadas" com limite de conteúdo que podem ser inseridos nela, o limite pode ser feito pelo tamanho em bytes do arquivo ou por numero de inserções. </h5>

<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">db.createCollection("<collection>", {capped: true, size: <tamanho-em-bytes>, max: <número-de-documentos>})
db.createCollection("fisco", {capped: true, size: 4096, max: 10})
</pre></div>



<h2> Exemplo utilizando um for com o bank_data </h2>
<div class="highlight highlight-source-shell"><pre><span class="pl-k">&gt;</span> <span class="pl-en">var smithPersons = db.bank_data.find({first_name : "DANIEL"}, {first_name : 1, last_name: 1});
for(var i = 0; i < smithPersons.count(); i++){ 
    print(smithPersons[i].first_name + ' ' + smithPersons[i].last_name );
}

</pre></div>


