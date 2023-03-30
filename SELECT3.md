# Como funcionam essas relações?
> Quais existem?, quais as diferentes formas?, quando usar cada uma?... vamos lá, existem inicialmente três tipos, são eles:
 - 1 &rarr; 1, ou também chamada `OneToOne`;
 - 1 &rarr; N, ou também chamada `OneToMany`;
 - N &rarr; N, ou também chamada `ManyToMany`;

# Mas como que se faz esses relacionamentos?
 - Eles são feitos através de chave estrangeira (`FOREING KEY`), ele é quem identifica uma linha em outra tabela, criando assim o relacionamento entre elas;
 - Básicamente a `FOREING KEY` é uma coluna em uma tabela que faz referencia a `PRIMARY KEY` de outra tabela;
 - Uma tabela pode ter varias `FOREING KEY`, a tabela que possui a `FOREING KEY` é chamada de **tabela pai**, e tabela relacionada chama-se **tabela filha**;
 - A `FOREING KEY` é a responsavel por manter a **integridade referencial**;
 - Em resumo, `FOREING KEY` faz relacionamento com alguma coluna de outra tabela geralmente pelo seu `PRIMARY KEY`, ex:
 ```sql
  CREATE TABLE tabela_filha (
   id bigserial primary key not null,
   idade_pessoa int
  );

  CREATE TABLE tabela_pai (
   id bigserial primary key not null,
   nome_pessoa VARCHAR(255),
   id_tabela_filha bigint NOT NULL,
   foreign key (id_tabela_filha) references tabela_filha (id)
    ON DELETE CASCADE ON UPDATE CASCADE
  );

  insert into tabela_filha (idade_pessoa) values (17), (18), (19);

  insert into tabela_pai (nome_pessoa, id_tabela_filha) values ('Guilherme', 1), ('Dalti', 2);

  select * from tabela_pai
   inner join tabela_filha
    on tabela_pai.id_tabela_filha=tabela_filha.id;
 ```

<h6>ON DELETE CASCADE ON UPDATE CASCADE?, imagine o que ocorre se um dos registros em tabela_pai que possui um registro em tabela_filha for excluído da tabela de autores?, Neste caso, será impossível excluir o registro em tabela_pai até que todos os registros em tabela_filha que o tenham como referência tenham sido excluídos também. Para evitar esse problema, podemos usar a instrução ON DELETE CASCADE, o mesmo vale para ON UPDATE CASCADE que seria para caso seja atualizado registro em tabela_pai</h6>

# Sobre os tipos de relacionamentos
 - `1:1`:
 ```sql
 CREATE TABLE tabela_pai (
  id bigserial primary key not null,
  nome_pessoa VARCHAR(255) unique
 );

 CREATE TABLE tabela_filha (
  id bigserial primary key not null,
  idade_pessoa int,
  id_tabela_pai bigint unique,
  foreign key (id_tabela_pai) references tabela_pai (id)
   ON DELETE CASCADE ON UPDATE CASCADE
 );


 insert into tabela_pai (nome_pessoa) values ('Guilherme'), ('Dalti'), ('Denis');

 insert into tabela_filha (idade_pessoa, id_tabela_pai) values (17, 1), (18, 2);

 select * from tabela_filha
  inner join tabela_pai
   on tabela_filha.id_tabela_pai=tabela_pai.id;
 ```
 - Nosso exemplo já dado é um relacionamento `1:N`:
  ```sql
   create table tabela_filha (
    id bigserial primary key not null,
    idade_pessoa int
   );

   create table tabela_pai (
    id bigserial primary key not null,
    nome_pessoa VARCHAR(255),
    id_tabela_filha bigint NOT NULL,
    foreign key (id_tabela_filha) references tabela_filha (id)
     ON DELETE CASCADE ON UPDATE CASCADE
   );

   insert into tabela_filha (idade_pessoa) values (17), (18), (19);

   insert into tabela_pai (nome_pessoa, id_tabela_filha) values ('Guilherme', 1), ('Dalti', 2);

   select * from tabela_pai
    inner join tabela_filha
     on tabela_pai.id_tabela_filha=tabela_filha.id;
  ```
  - `N:N` Essa é mais complexa, vai precisar de uma terceira tabela (intermediaria):
  ```sql
  CREATE TABLE tabela_pai (
   id bigserial primary key not null,
   nome_pessoa VARCHAR(255) not null
  );

  CREATE TABLE tabela_filha (
   id bigserial primary key not null,
   idade_pessoa int not null
  );

  CREATE TABLE tabela_pai_filha (
   id_tabela_pai bigint not null,
   id_tabela_filha bigint not null,
   primary key (id_tabela_pai, id_tabela_filha),
   foreign key (id_tabela_pai) references tabela_pai (id)
    ON DELETE CASCADE ON UPDATE CASCADE,
   foreign key (id_tabela_filha) references tabela_filha (id)
    ON DELETE CASCADE ON UPDATE CASCADE
  );


  insert into tabela_pai (nome_pessoa) values ('Guilherme'), ('Dalti'), ('Denis');

  insert into tabela_filha (idade_pessoa) values (18), (17);

  insert into tabela_pai_filha values (1,2), (2,1);

  select * from tabela_pai_filha 
   inner join tabela_pai
    on tabela_pai_filha.id_tabela_pai=tabela_pai.id
   inner join tabela_filha
    on tabela_pai_filha.id_tabela_filha=tabela_filha.id;
  ```
