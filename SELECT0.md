# criar banco (não é só isso, geralmente se seta permissões de usuarios, encode, etc...):
```sql
CREATE DATABASE databasename;
```
# deletar banco:
```sql
DROP DATABASE databasename;
```
# criar tabela:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
# deletar tabela:
```sql
DROP TABLE table_name;
```
# alterar tabela (serve para quando a tabela já está criada e não que deletar e inserir todos dados novamente):
```sql
ALTER TABLE table_name
ADD column_name datatype;
```
