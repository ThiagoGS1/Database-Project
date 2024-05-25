* Marcio Forner Nepomuceno Almeida - RA: 22.122.040-3
* Thiago Garcia Santana - RA: 22.122.003-1

----
## Instruções

Executar o Docker compose para criação do banco,
na sequência, executar o código python para estruturação e população dos dados no banco.
Após, utilizar as queryes para obter os relatórios

----

1) histórico escolar de qualquer aluno, retornando o código e nome da disciplina, semestre e ano que a disciplina foi cursada e nota final
```
select 
    h.*,
    d.id,
    d.nome
from
    historicoescolar h
inner join
    disciplina d 
on
    h.id_disciplina = d.id 
where
    h.id_aluno = 111
```
----

2) histórico de disciplinas ministradas por qualquer professor, com semestre e ano
```
select 
    p.id,
    p.nome,
    d.id,
    d.nome,
    d.id_professor,
    m.id_disciplina,
    m.semestre,
    m.ano 
from 
    professor p 
inner join
    disciplina d 
on
    p.id = d.id_professor 
inner join
    matrizcurricular m 
on
    d.id = m.id_disciplina 
where
    p.id = 1111
```
----
3) listar alunos que já se formaram (foram aprovados em todos os cursos de uma matriz curricular) em um determinado semestre de um ano
```
select
    m.id_disciplina,
    h.id_disciplina,
    h.nota,
    h.id_aluno,
    a.id
from
    matrizcurricular m
inner join
    historicoescolar h 
on
    m.id_disciplina = h.id_disciplina 
inner join 
    aluno a 
on
    h.id_aluno = a.id 
```
----
4) listar todos os professores que são chefes de departamento, junto com o nome do departamento
```
select 
    d.id_professor_chefe,
    d.nome,
    p.nome,
    p.sobrenome 
from 
    departamento d 
inner join
    professor p 
on
    d.id_professor_chefe = p.id
```
----
5) saber quais alunos formaram um grupo de TCC e qual professor foi o orientador
```
select
    a.id,
    t.id_professor,
    p.nome,
    t.titulo,
    t.id
from
    aluno a
inner join
    grupotcc g 
on 
    a.id =    g.id_aluno 
inner join 
    tcc t 
on
    t.id = g.id_tcc
inner join
    professor p 
on
    t.id_professor = p.id 
where 
    t.id = 111111
```
