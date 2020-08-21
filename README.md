# RESPOSTAS-APP2
```SQL
CREATE VIEW RESP05 (nome_disciplina, nome_curso)
AS
SELECT DISTINCT D.nome, curso.nome FROM disciplinas D, cursos curso, contem CONTEM
WHERE  CURSO.numcurso = CONTEM.idcurso AND CONTEM.iddisciplina = D.numdisp AND curso.nome = 'Ciencia_computacao';
```
```SQL
CREATE VIEW RESP06 (CURSO, DISCIPLINA)
AS
SELECT CUR.nome, D.nome FROM cursos CUR, disciplinas D, contem CO
WHERE CO.iddisciplina = D.numdisp AND CO.idcurso = CUR.numcurso AND D.nome = 'calculo numerico';
```
```SQL
CREATE VIEW RESP07 (ALUNO, DISCIPLINA, SEMESTRE)
AS
SELECT ALU.nome, D.nome, AU.semestre FROM disciplinas D, aula AU, alunos ALU
WHERE D.numdisp = AU.disciplina AND ALU.numaluno = AU.aluno AND AU.semestre = '19981'AND ALU.nome ='Marcos João Casanova '; 
```
```SQL
CREATE VIEW RESP08 (ALUNO, DISCIPLINA, SEMESTRE)
AS
SELECT ALU.nome, D.nome, AU.semestre FROM disciplinas D, aula AU, alunos ALU
WHERE D.numdisp = AU.disciplina AND ALU.numaluno = AU.aluno AND AU.nota<7 AND ALU.nome = 'Ailton Castro' ;
```
```SQL
CREATE VIEW RESP09 (ALUNO, DISCIPLINA, SEMESTRE, NOTA)
AS
SELECT ALU.nome, D.nome, AU.semestre, AU.nota FROM disciplinas D, aula AU, alunos ALU
WHERE D.numdisp = AU.disciplina AND ALU.numaluno = AU.aluno AND AU.nota<7 
AND AU.semestre = '19981' AND D.nome = 'calculo numerico';
```
