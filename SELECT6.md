# CASE
> São em casos especificos porém são bastante uteis, (testar para ver se isso não funciona como um for, porque se sim será ruim em caso de bigdata, mas pela minha breve pesquisa é quase certeza que não)
```sql
-- SQL generico
select preco_produto,
case
	when preco_produto > 10 then 5 * preco_produto / 100
	else 0
end as lucro_5_por_cento
from produtos;
```

# PROCEDURE
> Ela armazena tarefas repetitivas e aceita parâmetros de entrada para que a tarefa seja efetuada de acordo com a necessidade individual. Em resumo é tipo chamar uma função só que uma função SQL. Dei exemplo com SQL pois como já disse, plpgsql não é lá muito bem vindo ao meu dia a dia.
```sql
CREATE PROCEDURE salvar(nome VARCHAR(80))
language sql
as $$
insert into fornecedores (nome_fornecedor) values (nome);
$$;

CALL salvar('Raio');

select * from fornecedores;
```
