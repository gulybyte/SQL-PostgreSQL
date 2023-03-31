# Dos mesmos criadores de [Java-Assuntos-Gerais](https://github.com/gulybyte/Java-Assuntos-Gerais), agora SQL-PostgreSQL
> No geral eu não pensava em fazer, até porque os ORM's simplificam demais, mas é bom saber o que à por baixo dos panos, e, principalmente porque se eu pegar projetos legados vou ter minha própria "documentação" (o que também serve pra escrever flyway's), além de que tem aqui configurações do PostgreSQL que também servem para consultas.

### Segue e mesma filosofia, NÃO É UM TUTORIAL, é só um lugar PARA MIM FAZER CONSULTAS

<h6>Nota (especialmente para o pessoal de escalabilidade): Entrei aqui a fundo em varios comandos do SQL, porém é bom tomar cuidado, porque eles facilitam bastante e puxam um pouco da complexidade do back end para ele, além de ser uma linguegem bastante fácil de se ler, o cuidade é, mesmo que muitas vezes possa ser mais tanto inteligente quanto performatico fazer SQL's complexos e separar esse trabalho um pouco do backend, ainda assim você deve se lembrar que, custo de servidor de banco de dados é ordens de grandeza mais caro que custo de servidor web, no fim na WEB usamos ele só para consultas pouco frequentes, como em casos de relatorios, e ainda assim fazemos o máximo de cache quanto possivel. Porém ainda assim é bom saber para não fazer igual certas pessoas que abrem mais de duas conexões com banco de dados por endpoint da aplicação, e sim fazer tudo em uma consulta principalmente para iniciantes que ainda estão pouco acostumados com SQL é complexo, porém abrir conexões (pools) no banco de dados é um processo extremamente caro, tanto que por isso nem me dei ao trabalho de fazer um "hello world" em plpgsql (mas se for trabalhar com scripts de migrações ou scripts de duplicação dados, ou então quando temos várias aplicações escritas em diferentes linguagens, ou rodam em plataformas diferentes, porém executam a mesma função, ai quem sabe plpgsql pode ser interessante).<h6>

<h6><a href="/GUIA.md">Guia aqui para quem não entende muito de banco de dados</a></h6>

## Caracteristicas com guias no PostgreSQL
 - <b>psql - </b>Linguagem SQL especifica do postgres;
      - [Començando (psql)](INIT.md);
 - <b>SQL - </b>Leitura atômica e complexa;
      - [SQL Database](SELECT0.md);
      - [INSERT e UPDATE e DELETE](INSERT.md);
      - [SELECT's part 1 (básico, where e order by)](SELECT.md);
      - [SELECT's part 2 (funções de agregação, paginação e Aliases)](SELECT2.md);
      - [SELECT's part 3 (Relacionamentos entre tabelas)](SELECT3.md);
      - [SELECT's part 4 (Tipos de JOIN's)](SELECT4.md);
      - [SELECT's part 5 (UNION, GROUP BY's e EXISTS)](SELECT5.md);
      - [SELECT's part 6 (CASE e PROCEDURES)](SELECT6.md);
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
 - <b>Versátil - </b> funções/operadores/tipos de dados personalizados;
 - <b>Replicação</b> (mestre-escravo)- sem perda de dados:
 - <b>Escalavel:</b>
   - <b>sharding horizontal</b> (acomodar o crescimento dos dados):
   - <b>replicação de leitura</b> (melhorar performance de leitura):
   - <b>indexaçāo avançada</b> (b-tree, hash, GiST, GIN..):
   - <b>suporte a JSON</b> (para aplicações web):
 - <b>Seguro - </b> autenticação, criptografia de dados, controle de acesso, auditoria para acompanhar as atividades do usuario;
