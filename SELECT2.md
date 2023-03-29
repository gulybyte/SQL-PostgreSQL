
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
   OFFSET(página - 1) * número_de_itens_por_página
 ```
