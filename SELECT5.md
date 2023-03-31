 - [UNION](#union);
 - [GROUP BY](#group-by);

# UNION
> SQL de uso:
```sql
create table cidades_microserivico1 (
	id bigserial primary key unique not null,
	cidade VARCHAR(80),
	numero_casa int
);

create table cidades_microserivico2 (
	id bigserial primary key unique not null,
	cidade VARCHAR(80),
	numero_casa int
);

insert into cidades_microserivico1 (cidade, numero_casa) values
('Foz do Iguacu', 78),
('Botucatu', 59),
('Jundiaí', 96),
('Serra', 14),
('Aparecida de Goiânia', 75),
('Franca', 68),
('Presidente Prudente', 324),
('Ourinhos', 87687),
('Americana', 74),
('Petrolina', 967);

insert into cidades_microserivico2 (cidade, numero_casa) values
('Foz do Iguaçu', 576),
('Botucatu', 7864),
('Aparecida de Goiânia', 867),
('Franca', 5467),
('Montes Claros', 546),
('Camaçari', 456),
('Capão Bonito', 7864),
('São Paulo', 786),
('Gravatá', 67);
```

### digamos que você tenha o que temos aqui, dois microservicos, porém você quer juntar os dados de todos eles, como fazer?:
 - simples:
 ```sql
 select cidade from cidades_microserivico1
 union
 select cidade from cidades_microserivico2;
 ```
 - mas aqui os dados não se duplicam, e se eu quiser que eles se dupliquem?, simples:
 ```sql
 select cidade from cidades_microserivico1
 union all
 select cidade from cidades_microserivico2;
 ```
 
# GROUP BY
a tabela:
```sql
CREATE TABLE vendas (
id bigserial primary key,
nome_Vendedor VARCHAR(20),
quantidade int,
produto VARCHAR(20),
cidade VARCHAR(20)
);

INSERT INTO vendas (nome_vendedor, quantidade, produto, cidade)
  VALUES
('Jorge',1400,'Mouse','São Paulo'),
('Tatiana',1220,'Teclado','São Paulo'),
('Ana',1700,'Teclado','Rio de Janeiro'),
('Rita',2120,'Webcam','Recife'),
('Marcos',980,'Mouse','São Paulo'),
('Carla',1120,'Webcam','Recife'),
('Roberto',3145,'Mouse','São Paulo');
```
ou seja:
id|nome_vendedor|quantidade|produto|cidade        |
| - | - | - | - | - |
 1|Jorge        |      1400|Mouse  |São Paulo     |
 2|Tatiana      |      1220|Teclado|São Paulo     |
 3|Ana          |      1700|Teclado|Rio de Janeiro|
 4|Rita         |      2120|Webcam |Recife        |
 5|Marcos       |       980|Mouse  |São Paulo     |
 6|Carla        |      1120|Webcam |Recife        |
 7|Roberto      |      3145|Mouse  |São Paulo     |
 
 mas digamos que você queira saber apenas quantas vendas totais foram feitas em cada cidade, sem saber que foi o vendedor ou qual produto, fazemos assim:
 
```sql
SELECT cidade, SUM(quantidade) as total
FROM vendas
GROUP BY cidade;
```

<h6>Obs: peguei o exemplo do ORDER BY do excelentissimo professor da Boson treinamentos, segue link: http://www.bosontreinamentos.com.br/mysql/mysql-group-by-agrupamento-de-registros-26/</h6>



# EXISTS
> sql de uso:
```sql
create table fornecedores (
	id bigserial primary key not null,
	nome_fornecedor VARCHAR(80)
);

create table produtos (
	id bigserial primary key not null,
	nome_produto VARCHAR(80),
	preco_produto int,
	id_fornecedores bigint not null references fornecedores (id)
);

insert into fornecedores (nome_fornecedor) values
('João'),
('Paulo'),
('Henrique'),
('Desmond');

insert into produtos (nome_produto, preco_produto, id_fornecedores) values
('Cartas UNO', 5, 1),
('Vassoura', 8, 4),
('Assinatura Cloud', 50, 2);
```
Digamos que queira trazer o nome dos fornecedores somente se existir alguma venda acima de 5 reais feita por ele, com `EXISTS` fara assim:
```sql
select nome_fornecedor from fornecedores
	where exists (select nome_produto from produtos
		where produtos.id_fornecedores = fornecedores.id and preco_produto > 5
	);
```

