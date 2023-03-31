# Dos mesmos criadores de [Java-Assuntos-Gerais](https://github.com/gulybyte/Java-Assuntos-Gerais), agora SQL-PostgreSQL
> No geral eu não pensava em fazer, até porque os ORM's simplificam demais, mas é bom saber o que à por baixo dos panos, e, principalmente porque se eu pegar projetos legados vou ter minha própria "documentação" (o que também serve pra escrever flyway's), além de que tem aqui configurações do PostgreSQL que também servem para consultas.

<h6>Nota (especialmente para o pessoal de escalabilidade): Entrei aqui a fundo em varios comandos do T-SQL, porém é bom tomar cuidado, porque eles facilitam bastante e puxam um pouco da complexidade do back end para ele, além de ser uma linguegem bastante fácil de se ler, o cuidade é, mesmo que muitas vezes possa ser mais tanto inteligente quanto performatico fazer SQL's complexos e separar esse trabalho um pouco do backend, ainda assim você deve se lembrar que, custo de servidor de banco de dados é ordens de grandeza mais caro que custo de servidor web, no fim na WEB usamos ele só para consultas pouco frequentes, como em casos de relatorios, e ainda assim fazemos o máximo de cache quanto possivel. Porém ainda assim é bom saber para não fazer igual certas pessoas que abrem mais de duas conexões com banco de dados por endpoint da aplicação, e sim fazer tudo em uma consulta principalmente para iniciantes que ainda estão pouco acostumados com SQL é complexo, porém abrir conexões (pools) no banco de dados é um processo extremamente caro.<h6>

### Segue e mesma filosofia, NÃO É UM TUTORIAL, é só um lugar PARA MIM FAZER CONSULTAS

 - [Començando (psql)](INIT.md);
 - [INSERT e UPDATE e DELETE](INSERT.md);
 - [SELECT's part 1 (básico, where e order by)](SELECT.md);
 - [SELECT's part 2 (funções de agregação, paginação e Aliases)](SELECT2.md);
 - [SELECT's part 3 (Relacionamentos entre tabelas)](SELECT3.md);
 - [SELECT's part 4 (Tipos de JOIN's)](SELECT4.md);
 - [SELECT's part 5 (UNION, GROUP BY's e EXISTS)](SELECT5.md);
 - [SELECT's part 6 (...)](SELECT6.md);

<h6><a href="/GUIA.md">Guia aqui para quem não entende muito de banco de dados</a></h6>

