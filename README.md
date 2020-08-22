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
```SQL
CREATE VIEW RESP10 (DICIPLINA, NOME, CODIGO)
AS
SELECT DISTINCT D.nome, PROF.nome, AU.disciplina FROM disciplinas D, professores PROF, aula AU
WHERE AU.professor = PROF.numprof AND D.numdisp = AU.disciplina AND PROF.nome = ' Ramon Travanti';
```
```SQL
CREATE VIEW RESP11 (DISCIPLINA, PROFESSOR, CODIGO)
AS
SELECT DISTINCT D.nome, PROF.nome, AU.disciplina FROM disciplinas D, professores PROF, aula AU
WHERE AU.professor = PROF.numprof AND D.numdisp = AU.disciplina AND D.nome = 'banco de dados';
```
```SQL
CREATE VIEW NOTAS_CALCULO (DISCIP, ALUNO, CODIGO, NOTA)
AS
SELECT D.nome, AL.nome, AU.disciplina, AU.nota FROM disciplinas D, alunos AL, aula AU
WHERE AU.aluno = AL.numaluno AND D.numdisp = AU.disciplina AND AU.SEMESTRE = '19981' AND D.nome = 'calculo numerico'
GROUP BY D.nome, AL.nome, AU.disciplina, AU.nota ;

CREATE VIEW RESP12 
AS
SELECT MIN(NOTA), MAX(NOTA) FROM NOTAS_CALCULO;
```
```SQL
CREATE VIEW NOTA
AS
SELECT ALUNO.nome AS ALUNO , AU.nota AS MAIOR_NOTA FROM alunos ALUNO, aula AU, disciplinas D
WHERE ALUNO.numaluno = AU.aluno AND D.numdisp = AU.disciplina 
AND D.nome = 'banco de dados' AND AU.semestre = '19981';

CREATE VIEW RESP13
AS
SELECT MAIOR_NOTA, ALUNO FROM NOTA
WHERE  MAIOR_NOTA IN (SELECT MAX( MAIOR_NOTA) FROM NOTA)
GROUP BY ALUNO,  MAIOR_NOTA;
```
```SQL
CREATE VIEW RESP14(ALUNO, DISCIPLINA, PROFESSOR)
AS
SELECT ALU.nome, DIS.nome, PRO.nome FROM alunos ALU, disciplinas DIS, professores PRO, aula AU
WHERE AU.aluno = ALU.numaluno AND AU.professor = PRO.numprof AND AU.disciplina = DIS.numdisp
AND AU.semestre = '19981'
ORDER BY ALU.nome;
```
```SQL
CREATE VIEW RESP15 (ALUNO, DISCIPLINA, NOTA)
AS
SELECT ALU.nome, DIS.nome, AU.NOTA FROM alunos ALU, disciplinas DIS, aula AU, matricula MA, cursos CUR
WHERE AU.aluno = ALU.numaluno AND AU.disciplina = DIS.numdisp AND AU.semestre = '19981'
AND ALU.numaluno = MA.aluno AND MA.CURSO = CUR.numcurso AND CUR.nome = 'Ciencia_computacao';
```
```SQL
CREATE VIEW NOTAS_MARCOS
AS
SELECT  AU.nota AS NOTAS, PRO.nome AS PROFESSOR FROM aula AU, professores PRO
WHERE AU.professor = PRO.numprof AND PRO.nome = ' Marcos Salvador'
GROUP BY PRO.nome, AU.nota ;

CREATE VIEW RESP16
AS
SELECT AVG(NOTAS) FROM NOTAS_MARCOS;
```
```SQL
CREATE VIEW ALU_DISC_NOTAS (ALUNO, DISC, NOTA)
AS
SELECT ALU.nome, DIS.nome, AU.nota FROM aula AU, disciplinas DIS, alunos ALU
WHERE ALU.numaluno = AU.aluno AND AU.disciplina = DIS.numdisp ;

CREATE VIEW RESP17
AS
SELECT NOTA, DISC, ALUNO FROM ALU_DISC_NOTAS
WHERE NOTA BETWEEN 5.0 AND 7.0;
```
```SQL
CREATE VIEW NOTA_DISC (NOTA, DISC, SEMESTRE)
AS
SELECT AU.NOTA, DIS.NOME, AU.SEMESTRE FROM AULA AU, DISCIPLINAS DIS
WHERE AU.DISCIPLINA = DIS.NUMDISP AND AU.SEMESTRE = '19981' AND DIS.NOME = 'calculo numerico' ;

CREATE VIEW RESP18
AS
SELECT AVG (NOTA), DISC, SEMESTRE FROM NOTA_DISC
GROUP BY DISC, SEMESTRE;
```
```SQL
CREATE VIEW RESP19
AS
SELECT COUNT(AU.ALUNO), P.NOME FROM AULA AU, PROFESSORES P
WHERE AU.PROFESSOR = P.NUMPROF AND P.NOME = ' Abgair ' AND AU.SEMESTRE = '19981'
GROUP BY P.NOME;
```
```SQL
CREATE VIEW NOTA_EDVALDO(NOTA, NOME)
AS
SELECT AU.NOTA, ALU.NOME FROM AULA AU, ALUNOS ALU
WHERE AU.ALUNO = ALU.NUMALUNO AND ALU.NOME = 'Edvaldo Carlos Silva';

CREATE VIEW RESP20
AS
SELECT AVG(NOTA), NOME FROM NOTA_EDVALDO
GROUP BY NOME;
```
```SQL
CREATE VIEW RESP22
AS
SELECT PROF.NOME, AVG(AU.NOTA) AS MEDIA FROM PROFESSORES PROF, AULA AU
WHERE AU.PROFESSOR = PROF.NUMPROF AND AU.SEMESTRE='19981'
GROUP BY PROF.NOME;
```
```SQL
CREATE VIEW MEDIAS
AS
SELECT AVG(AU.NOTA) AS MEDIA_DISCIPLINAS, D.NOME AS DISCIPLINAS FROM AULA AU, DISCIPLINAS D
WHERE AU.DISCIPLINA = D.NUMDISP
GROUP BY D.NOME;

CREATE VIEW RESP28 
AS
SELECT * FROM MEDIAS
WHERE MEDIA_DISCIPLINAS IN (SELECT MAX(MEDIA_DISCIPLINAS) FROM MEDIAS);
```
```SQL
CREATE VIEW RESP30
AS
SELECT D.nome, COUNT(AU.nota) AS QTD_REPROVAÇÕES FROM disciplinas D, aula AU
WHERE D.NUMDISP = AU.DISCIPLINA AND AU.nota<7
GROUP BY D.nome
ORDER BY QTD_REPROVAÇÕES;
```
