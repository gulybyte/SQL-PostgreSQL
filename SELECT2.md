
# Paginação
> Conhecido muitas vezes (por causa do SQLServer) por `SELECT TOP`, no Postgres é `Limit`
 - Tá falando do que?, imagina que quer fazer paginação (não quer trazer todos os registros de uma vez só), tu faz como?, simples (com JPA usariamos um simples [Pageable](https://www.baeldung.com/spring-data-jpa-pagination-sorting)):
 ```sql
 SELECT * FROM table_name LIMIT 5;
 ```
 - Top, mas isso só define LIMIT, como faço para escolher a página?, simples (postgres é lindo demais):
 ```sql
 SELECT * FROM table_name
	  LIMIT número_de_itens_por_página
   	  OFFSET(página - 1) * número_de_itens_por_página;
 ```

<h6>A seguir veremos `MIN`, `MAX`, `COUNT`, `AVG` e `SUM`, que são chamadas de funções SQL de agregação.<br>
Obs: não é possivel fazer WHERE em condicionais de funções agregadas, para isso use <a href="https://www.w3schools.com/sql/sql_having.asp">HAVING</a></h6>

# MIN e MAX
> Sinceramente não vejo muita ultilidade nisso, talvez com wheres fique interessante
 - Simples, busque o menor ou maior valor de uma coluna (adicionei um where, mas não tem nescessidade):
 ```sql
 select min(column_name) from table_name where condition;
 ```

# COUNT e AVG e SUM
> são extremamente interessantes, e trazem bastente performance para consultas especificas
 - `COUNT`, confesso que de inicio achei uma bosta, parecia que só servia para contar colunas e achar por exemplo o id máximo (literalmente a mesma coisa que `MAX`), e inclusive ele era bem menos performatico que `MAX` até porque ele conta linha por linha, mas na real ele serve para retornar o número existente de registros, mas ai se pergunta, ué, mas ainda assim se tiver indice na tabela é mais performatico usar um `MAX(id)`, e sim, você está certo, porém eu te pergunto, e se seu ultimo registro estiver deletado? (sim é bem especifico, mas é isso mesmo)
 ```sql
 SELECT COUNT(*) FROM table_name;
 ```
 - `AVG`, famosa média, já conheci muitos que trazem simplesmente todos os registros do banco, e em seguida no backend processam e fazem um cálculo para tirar um média, mas isso é extremamente ineficiente, então para isso usamos essa função que serve para isso, tirar uma média (inclusive usando cálculos matématicos muito mais eficiente do que vc faria):
 ```sql
 SELECT AVG(price_example) FROM table_name;
 ```
 - `SUM`, soma todos os valores de uma coluna, mesmo exemplo que o anterior, porfavor não puxe todos os registros pra processar no backend, use função nativa do db, nesse caso para somar todos os valores de todos os registros de uma coluna:
 ```sql
 SELECT SUM(column_name) FROM table_name;
 ```
 
 # Alias
 > Para aplicações web costumam ser bem inuteis;
 - `Alias` ou em SQL `AS`, servem para... Dar um nome temporario (apenas dentro daquela consulta) a tabelas ou colunas, ex coluna:
 ```sql
 select city as cidade from customers;
 ```
 - ex tabela:
 ```sql
 select * from customers as cidade;
 ```
Em alguns casos de consultas complexas ele pode ser util, como por exemplo se você é um cara inteligente e não abre mais de 2 conexões com banco de dados no mesmo método, e sim cria um unico SELECT que tras tudo de uma vez, então para não se perder você pode ir dando nome a elas.
 
 
 
