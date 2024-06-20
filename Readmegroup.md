1. Contare quanti iscritti ci sono stati ogni anno.
SELECT `enrolment_date`, COUNT(*) AS numero_iscritti FROM students GROUP BY `enrolment_date`;

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT office_address, COUNT(*) AS numero_insegnanti FROM teachers GROUP BY office_address ORDER BY numero_insegnanti DESC;

3. Calcolare la media dei voti di ogni appello d'esame
SELECT exam_id AS esame, AVG(vote) AS votoMedio FROM `exam_student` GROUP BY esame ORDER BY esame;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT department_id AS singoloDipartimento, COUNT(department_id) AS numeroDiCorsi FROM `degrees` GROUP BY singoloDipartimento ORDER BY singoloDipartimento;