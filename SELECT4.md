# Where?, INNER/LEFT/RIGHT JOIN?, FULL/CROSS JOIN?, LEFT/RIGHT OUTER JOIN (inclusive e exclusive JOIN's)?, LEFT/RIGHT INNER JOIN? quais as diferenças?
> No geral Joins servem para juntar linhas de duas ou mais tabelas na mesma consulta com base nos relacionamentos entre elas.

Va direto para a sessão:
 - [INNER/LEFT/RIGHT JOIN?](#fullcross-join);
 - [FULL/CROSS JOIN?](#fullcross-join);

Vamos precisar do seguinte SQL para os testes:

```sql
create table cargo (
	id bigserial primary key not null,
	nome_cargo VARCHAR(60) not null,
	valor_cargo int not null
);

create table funcionario(
	id bigserial primary key not null,
	matricula smallint not null,
	nome_funcionario VARCHAR(80) not null,
	id_cargo bigint,
	foreign key (id_cargo) references cargo (id)
);

insert into cargo (nome_cargo, valor_cargo) values
('CAIXA', 800),
('VENDEDOR', 1200),
('GERENTE', 2400);

insert into funcionario (matricula, nome_funcionario, id_cargo) values
(100, 'JOÃO', 1),
(110, 'MARIA', 2),
(120, 'CARLOS', 1),
(130, 'TADEU',  null);
```

<br><br><br>

# INNER/LEFT/RIGHT JOIN
### `INNER JOIN` vs `JOIN`, Essa é fácil, ambos são literalmente a mesma coisa, você coloca a palavra-chave `INNER` só se quiser. Respondido a pergunta, vamos entender como ele funciona:
 ```sql
 SELECT * FROM cargo
	INNER JOIN funcionario ON funcionario.id_cargo = cargo.id;
 ```
 id|nome_cargo|valor_cargo|id|matricula|nome_funcionario|id_cargo|
 | - | - | - | - | - | - | - |
 1|CAIXA     |        800| 1|      100|JOÃO            |       1|
 2|VENDEDOR  |       1200| 2|      110|MARIA           |       2|
 1|CAIXA     |        800| 3|      120|CARLOS          |       1|
 ### `LEFT JOIN`, Esse é massa, veja:
 ```sql
 SELECT * FROM cargo
	LEFT JOIN funcionario ON funcionario.id_cargo = cargo.id;
 ```
 id|nome_cargo|valor_cargo|id|matricula|nome_funcionario|id_cargo|
 | - | - | - | - | - | - | - |
 1|CAIXA     |        800| 1|      100|JOÃO            |       1|
 2|VENDEDOR  |       1200| 2|      110|MARIA           |       2|
 1|CAIXA     |        800| 3|      120|CARLOS          |       1|
 3|GERENTE   |       2400|  |         |                |        |
 ### `RIGHT JOIN`, Esse é a mesma coisa, porém para a direita &#x1F602;, veja:
 ```sql
 SELECT * FROM cargo
 	RIGHT JOIN funcionario ON funcionario.id_cargo = cargo.id;
 ```
 id|nome_cargo|valor_cargo|id|matricula|nome_funcionario|id_cargo|
 | - | - | - | - | - | - | - |
 1|CAIXA     |        800| 1|      100|JOÃO            |       1|
 2|VENDEDOR  |       1200| 2|      110|MARIA           |       2|
 1|CAIXA     |        800| 3|      120|CARLOS          |       1|
  |          |           | 4|      130|TADEU           |        |

<br><br><br>

# FULL/CROSS JOIN
### `FULL JOIN`, simples, é uma mistura de `LEFT JOIN` e `RIGHT JOIN`, básicamente se quer tudo de tudo de tudo e todos use `FULL JOIN`:
```sql
SELECT * FROM cargo
	FULL JOIN funcionario ON funcionario.id_cargo = cargo.id;
```
 id|nome_cargo|valor_cargo|id|matricula|nome_funcionario|id_cargo|
 | - | - | - | - | - | - | - |
 1|CAIXA     |        800| 1|      100|JOÃO            |       1|
 2|VENDEDOR  |       1200| 2|      110|MARIA           |       2|
 1|CAIXA     |        800| 3|      120|CARLOS          |       1|
  |          |           | 4|      130|TADEU           |        |
 3|GERENTE   |       2400|  |         |                |        |
### `CROSS JOIN`, esse é um caso a parte, um pouco mais complexo, ele é básicamente produto cartesiano, ou seja, da pra juntar duas ou mais tabelas por cruzamento:
```sql
SELECT * FROM cargo
	CROSS JOIN funcionario;
```
 id|nome_cargo|valor_cargo|id|matricula|nome_funcionario|id_cargo|
 | - | - | - | - | - | - | - |
 1|CAIXA     |        800| 1|      100|JOÃO            |       1|
 1|CAIXA     |        800| 2|      110|MARIA           |       2|
 1|CAIXA     |        800| 3|      120|CARLOS          |       1|
 1|CAIXA     |        800| 4|      130|TADEU           |        |
 2|VENDEDOR  |       1200| 1|      100|JOÃO            |       1|
 2|VENDEDOR  |       1200| 2|      110|MARIA           |       2|
 2|VENDEDOR  |       1200| 3|      120|CARLOS          |       1|
 2|VENDEDOR  |       1200| 4|      130|TADEU           |        |
 3|GERENTE   |       2400| 1|      100|JOÃO            |       1|
 3|GERENTE   |       2400| 2|      110|MARIA           |       2|
 3|GERENTE   |       2400| 3|      120|CARLOS          |       1|
 3|GERENTE   |       2400| 4|      130|TADEU           |        |










