# UNION
> SQL de uso:
```sql
create table cidades_microserivico1 (
	id bigserial primary key unique not null,
	cidade VARCHAR(80)
);

create table cidades_microserivico2 (
	id bigserial primary key unique not null,
	cidade VARCHAR(80)
);

insert into cidades_microserivico1 (cidade) values
('Foz do Iguacu'),
('Botucatu'),
('Jundiaí'),
('Serra'),
('Aparecida de Goiânia'),
('Franca'),
('Presidente Prudente'),
('Ourinhos'),
('Americana'),
('Petrolina');

insert into cidades_microserivico2 (cidade) values
('Foz do Iguaçu'),
('Botucatu'),
('Aparecida de Goiânia'),
('Franca'),
('Montes Claros'),
('Camaçari'),
('Capão Bonito'),
('São Paulo'),
('Gravatá');
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
 
