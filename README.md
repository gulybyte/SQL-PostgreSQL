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
 
 # Guia de Escolha de banco de dados e porque RDBMS é a principal escolha?:
<img src="/img/database.png" />
<h6>Qual foi, da favorito ai no repositorio deu trabalho fazer essa imagem kk</h6>
 
## Bônus: PostgreSQL na AWS
|         <img src="/img/postgres.png" /> Dados           | <img src="/img/Arch_Amazon-EC2_64.png" /> <br> ec2 manual config PostgreSQL | <img src="/img/Arch_Amazon-RDS_64.png" /> <br> Amazon RDS <br>for<br> PostgreSQL | <img src="/img/Arch_Amazon-Aurora_64.png" /> <br> Aurora <br>for<br> PostgreSQL | <img src="/img/Arch_Amazon-Aurora_64.png" /> <br> Aurora <br>Serveless<br> PostgreSQL | <img src="/img/Arch_Amazon-Redshift_64.png" /> <br> Amazon <br>Redshift<br> PostgreSQL | <img src="/img/Arch_Amazon-RDS-on-VMware_64.png" /> <br> Amazon RDS <br> on <br> VMware |
|---------------------|------------------------------|----------------------------|-------------------|------------------------------|-----------------------------|--------------------|
| Gerenciamento geral | Manualmente                   | Gerenciado                 | Gerenciado        | Gerenciado                   | Gerenciado                  | Gerenciado         |
| Preço                | Baixo/Médio                         | Médio/Alto                      | Alto             | Médio/Alto                        | Alto                        | Médio              |
| Uso ideal            | Pequenos projetos             | Projetos de tamanho médio  | Projetos de grande porte | Projetos de qualquer tamanho | Data warehousing            | Virtualização      |
| Ambientes uso | Personalizados e com alto controle sobre a infraestrutura | Facilidade de gerenciamento e escalabilidade | Alta disponibilidade e escalabilidade | Picos de demanda sem previsibilidade | Data warehouse de alta performance e escalabilidade | on-premises em migração |
| Vantagens        | Controle total sobre a infraestrutura e flexibilidade para personalizar o ambiente | Gerenciamento simplificado, escalabilidade automatizada, monitoramento e backups automáticos | Alta disponibilidade, escalabilidade e desempenho, com armazenamento compartilhado e failover automático | Escalabilidade automática com gerenciamento simplificado e baixo custo para cargas de trabalho intermitentes | Alto desempenho em cargas de trabalho de data warehouse, escalabilidade e gerenciamento simplificado | Flexibilidade para migrar ambientes on-premises para a nuvem, sem alterações na infraestrutura existente |
| Desvantagens     | Necessita de conhecimentos técnicos avançados para configurar e gerenciar a infraestrutura | Limitações em termos de personalização e controle sobre a infraestrutura | Armazenamento dedicado, o que pode aumentar os custos | Não recomendado para cargas de trabalho contínuas e com demanda constante | Não é indicado para cargas de trabalho transacionais e com baixa latência | Requer uma infraestrutura VMware existente, o que pode aumentar os custos |

