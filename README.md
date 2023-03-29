# Dos mesmos criadores de [Java-Assuntos-Gerais](https://github.com/gulybyte/Java-Assuntos-Gerais), agora SQL-PostgreSQL
> No geral eu não pensava em fazer, até por ORM simplificam demais, mas é bom saber o que a por baixo dos panos, e, principalmente porque se eu pegar projetos legados vou ter minha própria "documentação"

### Segue e mesma filosofia, não é um tutorial, é só um lugar PARA MIM FAZER CONSULTAS

 - [Començando (psql)](INIT.md)
 - [INSERT](INSERT.md)
 - [SELECT's part 1 (básico, where e order by)](SELECT.md)
 - [Where, Joins?](/JOIN.md)

# Caracteristicas do PostgreSQL
 - <b>ACID - </b> (Atomicidade, Consistencia, Isolament e Durabilidade);
 - <b>MVVC - </b> Controle de Concorrência Multiversão;
 - <b>Views - </b> views materializadas, procedimentos armazenados, triggers e outros tipos de objetos para Bancos Relacionais;
 - <b>Transacional - </b> (uses WAL/REDO);
 - <b>Conexão TCP/IP geralmente</b>;
 - <b>Suporta Particionamento</b>;
 - <b>Busca de texto completo</b>;
 - <b>Operações geoespaciais - </b> (PostGIS);
 - <b>Rollback de transações</b> (integridade em caso de falhas);
 - <b>Schemes e tabelas relacionais</b> (integridade referencial):
 - <b>Pools - </b> múltiplas transações simultâneas não bloqueantes:
 - <b>SQL - </b>Leitura atômica e complexa;
 - <b>Versátil - </b> funções/operadores/tipos de dados personalizados;
 - <b>Replicação</b> (mestre-escravo)- sem perda de dados:
 - <b>Escalavel:</b>
   - <b>sharding horizontal</b> (acomodar o crescimento dos dados):
   - <b>replicação de leitura</b> (melhorar performance de leitura):
   - <b>indexaçāo avançada</b> (b-tree, hash, GiST, GIN..):
   - <b>suporte a JSON</b> (para aplicações web):
 - <b>Seguro - </b> autenticação, criptografia de dados, controle de acesso, auditoria para acompanhar as atividades do usuario;
