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
CREATE VIEW RESP19
AS
SELECT COUNT(AU.ALUNO), P.NOME FROM AULA AU, PROFESSORES P
WHERE AU.PROFESSOR = P.NUMPROF AND P.NOME = ' Abgair ' AND AU.SEMESTRE = '19981'
GROUP BY P.NOME;
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
