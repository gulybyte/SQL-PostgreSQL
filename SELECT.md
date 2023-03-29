# SELECT's
> tabela base de uso para aqui:

```sql
insert into customers (id, customer_name, contact_name, address, city, postal_code, country) values
(1, 'Alfreds Futterkiste',	'Maria Anders',	'Obere Str. 57',	'Berlin',	'12209',	'Germany'),
(2,	'Ana Trujillo Emparedados y helados',	'Ana Trujillo',	'Avda. de la Constitución 2222',	'México D.F.',	'05021',	'Mexico'),
(3,	'Antonio Moreno Taquería',	'Antonio Moreno',	'Mataderos 2312',	'México D.F.',	'05023',	'Mexico'),
(4,	'Around the Horn',	'Thomas Hardy',	'120 Hanover Sq.',	'London',	'WA1 1DP',	'UK'),
(5,	'Berglunds snabbköp',	'Christina Berglund',	'Berguvsvägen 8',	'Luleå',	'S-958 22',	'Sweden');
```

## Básico
### Existem 3 tipos básicos:
 - O primeiro é SELECT com `*`, que significa busque trazendo todas as colunas
 ```sql
 SELECT * FROM customers;
 ```
  - O segundo é SELECT especificando colunas (conhecido como consulta atômica), voce também pode usá-lo como uma forma de deixar explicito as colunas
 ```sql
 SELECT column1, column2 FROM customers;
 ```
  - O terceiro é SELECT com `DISTINCT`, que significa me traga os dados sem se repetir (note que é obrigatorio especificar as colunas)
 ```sql
 SELECT DISTINCT column1, column2 FROM customers;
 ```

### Filtrando os dados:
> através de condicionais
 - `WHERE`
