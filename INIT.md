# PSQL
> [Instalação](https://github.com/gulybyte/config-linux/blob/main/postgres.MD)

entrar
```
sudo -i -u postgres
```
antes de entras psql, verifique comandos com:
```
man
```
entrar psql
```
psql
```
add senha
```
\password
```
configurando obrigar uso senha na conexão, pra isso ainda no psql digite: `show hba_file;` depois `\q` depois `exit`:
```
sudo nano /var/lib/postgres/data/pg_hba.conf
```
lá no final do arquivo, mude tudo de `trust` para `md5`, e então reinicie o postgres:
```
sudo systemctl restart postgresql.service
```

### trabalhando com psql 
verificando os comandos existentes:
```
\h
```
também pode entender como funciona um camando em especifico. (ex: `CREATE ROLE`):
```
\h create role
```
vericando comandos administrativos:
```
\?
```
listando bancos existentes:
```
\l
```
visualizando usuarios:
```
\du
```
conectando em um banco (ex: `postgres`):
```
\c postgres
```
visualizando as tabelas nesse banco:
```
\d
```
vizualizando tabelas relações e varios outros objetos:
```
\dS
```
ver onde está conectado:
```
\conninfo
```
sair do modo psql:
```
\q
```
sair do modo postgres:
```
exit
```
