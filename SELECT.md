# SELECT's
> tabela base de uso para aqui:

```sql
create table customers (
	id bigserial not null primary key,
	customer_name VARCHAR(255),
	contact_name VARCHAR(255),
	address VARCHAR(255),
	city VARCHAR(255),
	postal_code VARCHAR(255),
	country VARCHAR(255)
);

insert into customers (id, customer_name, contact_name, address, city, postal_code, country) values
(1, 'Alfreds Futterkiste',	'Maria Anders',	'Obere Str. 57',	'Berlin',	'12209',	'Germany'),
(2,	'Ana Trujillo Emparedados y helados',	'Ana Trujillo',	'Avda. de la Constitución 2222',	'México D.F.',	'05021',	'Mexico'),
(3,	'Antonio Moreno Taquería',	'Antonio Moreno',	'Mataderos 2312',	'México D.F.',	'05023',	'Mexico'),
(4,	'Around the Horn',	'Thomas Hardy',	'120 Hanover Sq.',	'London',	'WA1 1DP',	'UK'),
(5,	'Berglunds snabbköp',	'Christina Berglund',	'Berguvsvägen 8',	'Luleå',	'S-958 22',	'Sweden'),
(6,	'xapiscada',	'Alex Tordi',	'GOL 2007',	'KLC',	'5186',	'');
```

navegue direto para:
 - <a href="#A">básico de `SELECT`</a>
 - <a href="#B">filtrando consultas com `WHERE`</a>
 - <a href="#C">filtrando consultas com `WHERE` e clausulas `IS NULL` `LIKE`, `IN` e `BETWEEN`</a>
 - <a href="#D">filtrando consultas com `WHERE` e clausulas `AND`, `OR` e `NOT`</a>
 - <a href="#E">filtrando consultas com `ORDER BY`</a>

<div id="A"></div>

# Básico
### Existem 3 tipos básicos:
 - O primeiro é SELECT com `*`, que significa busque trazendo todas as colunas
 ```sql
 SELECT * FROM customers;
 ```
  - O segundo é SELECT especificando colunas (conhecido como consulta atômica), voce também pode usá-lo como uma forma de deixar explicito as colunas
 ```sql
 SELECT customer_name, country FROM customers;
 ```
  - O terceiro é SELECT com `DISTINCT`, que significa me traga os dados sem se repetir (note que é obrigatorio especificar as colunas)
 ```sql
 SELECT DISTINCT customer_name, country FROM customers;
 ```




# Filtrando os dados (através de condicionais):

<div id="B"></div>

### WHERE
> Antes o básico de WHERE

 - `WHERE`, é a mais simples, básicamente voce chega e fala, me traga esse resultado <b>onde</b> essa condição for verdadeira
   ```sql
   SELECT * FROM customers where country = 'Mexico';
   ```
   - é póssivel usar condicionais para tipos de números R, são eles `<`, `<=`, `>`, `>=`, `<> or !=`;
 
<div id="C"></div>
 
### WHERE -> IS NULL, LIKE, IN e BETWEEN
   - `IS NULL`, perceba que não é possivel verificar de for nulo com `=`, para isso use clausula `IS NULL` ou `IS NOT NULL`, o nome já diz, `IS NULL` vai dizer trazer onde determinado valor é nulo, e `IS NOT NULL` vai trazer onde aquele valor não for nulo, ex:
  ```sql
 select id, customer_name, country from customers where country is null;
 ```
 - `BETWEEN` intervalo, ex entre duas datas:
 ```sql
 SELECT FROM * table_name WHERE data_vencimento BETWEEN '2001-02-01' AND '2007-03-01';
 ```
 - `LIKE`, buscar sem completar (costumam chamar por ai isso de pattern), se clausula `%` for colocada antes do texto, voce não precisa saber primeiras letras, já se colocar depois voce não precisa completa-lo depois dos primeiros caracteres, já se colocar antes e no fim se colocar só o meio do texto ele já acha, ex:
 ```sql
 SELECT * FROM customers WHERE country LIKE '%xic%';
 ```
 <h6>Tenha cuidado, pois LIKE tende a ser muito perigoso em projetos grandes, porém ainda tem varias outras coisas possiveis nele que não citei, <a href="https://w3schools.com/sql/sql_wildcards.asp">veja mais aqui</a></h6>

 - `IN` tipo um `=` só que vc consegue determinar a condicional para varios valores, ex:
 ```sql
 SELECT * FROM customers where id IN (2,4);
 ```

<div id="D"></div>

### WHERE -> AND, OR e NOT
> Já vimos um pouco do AND, mas enfim... (percebe que se quiser pode fazer combinação de tudo junto)

 - `AND`, o nome já diz <b>and (e)</b>, no fim das contas vai usar quando quiser validar varias condições juntos, tipo um se isso <b>e</b> isso <b>e</b> isso estiver correto, então..., ex:
 ```sql
 SELECT * FROM customers where id = 2 and country = 'Mexico';
 ```
 - `OR`, mesma coisa, nome já diz <b>or (ou)</b>, use quando precisar validar uma condição ou outra, tipo um se isso <b>ou</b> isso <b>ou</b> isso estiver correto, então..., ex:
 ```sql
 SELECT * FROM customers where id = 2 or country = 'Mexic';
 ```
 - `NOT`, a bosta do nome já diz <b>not (não/negação)</b>, da pra resumir o `NOT` em um simples `!WHERE`, mas não é assim, ex:
 ```sql
 SELECT * FROM customers where not id = 2;
 ```

<div id="E"></div>

### ORDER BY
> Essa é fácil

 - `ASC` (default), ordene de forma crescente
 ```sql
 SELECT * FROM customers order by id;
 ```
  - `DESC`, ordene de forma decrescente
 ```sql
 SELECT * FROM customers order by id desc;
 ```



















