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

# 
