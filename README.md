# RESPOSTAS-APP2
```SQL
CREATE VIEW RESP05 (nome_disciplina, nome_curso)
AS
SELECT DISTINCT D.nome, curso.nome FROM disciplinas D, cursos curso, contem CONTEM
WHERE  CURSO.numcurso = CONTEM.idcurso AND CONTEM.iddisciplina = D.numdisp AND curso.nome = 'Ciencia_computacao';

```
