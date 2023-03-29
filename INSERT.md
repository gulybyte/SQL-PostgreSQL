# Primeiro Passo no SQL INSERT

## INSERT

### Se já sabe a ordem de sua tabela faça:
```sql
INSERT INTO table_name VALUES (value1, value2, value3, ...);
```

### Se não sabe a ordem de sua tabela faça:
```sql
INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...);
```

### Se quer adicionar uma porrada de registros de uma vez faça:
```sql
INSERT INTO table_name (column1, column2, column3, ...) VALUES
(value1, value2, value3, ...),
(value1, value2, value3, ...),
(value1, value2, value3, ...),
(value1, value2, value3, ...),
(value1, value2, value3, ...),
(value1, value2, value3, ...),
(value1, value2, value3, ...);
```

<h6>Essa base do `INSERT` é a mesma para `UPDATE` e `DELETE`</h6>

## UPDATE

### tendo a condição (where) vc atualiza seus registros, ex:
```sql
UPDATE table_name SET column1 = 'value1', column2 = 'value2' WHERE id = 2;
```


## DELETE
> tente não fazer essa sem where kk

### tendo a condição (where) vc deleta seus registros, ex:
```sql
DELETE FROM table_name WHERE id = 2;
```
