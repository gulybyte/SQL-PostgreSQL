# Where?, JOIN?, INNER JOIN?, LEFT JOIN?, RIGHT JOIN?, FULL JOIN?, CROSS JOIN?, LEFT OUTER JOIN?, LEFT INNER JOIN? quais as diferenças?
> No geral Joins servem para juntar linhas de duas ou mais tabelas na mesma consulta com base nos relacionamentos entre elas.

# Antes precisamos entender como funcionam essa relações
> Quais existem?, quais as diferentes formas?, quando usar cada uma?... vamos lá, existem inicialmente três tipos, são eles:
 - 1 &rarr; 1, ou também chamada `OneToOne`;
 - 1 &rarr; N, ou também chamada `OneToMany`;
 - N &rarr; N, ou também chamada `ManyToMany`;

## Mas como que se faz esses relacionamentos?
 - Eles são feitos através de chave estrangeira (`FOREING KEY`), ele é quem identifica uma linha em outra tabela, criando assim o relacionamento entre elas;
 - Básicamente a `FOREING KEY` é uma coluna em uma tabela que faz referencia a `PRIMARY KEY` de outra tabela;
 - Uma tabela pode ter varias `FOREING KEY`, a tabela que possui a `FOREING KEY` é chamada de **tabela pai**, e tabela relacionada chama-se **tabela filha**;
