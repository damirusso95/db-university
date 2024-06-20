1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT students.name, students.surname, degrees.name
FROM `students` 
INNER JOIN `degrees`
on degrees.id = students.degree_id
WHERE  degrees.name LIKE '%economia%';


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze.
SELECT departments.name, degrees.name, degrees.level FROM `departments` INNER JOIN `degrees` ON degrees.department_id = departments.id WHERE degrees.level = 'magistrale' AND departments.name LIKE '%Neuroscienze%';


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT teachers.name, teachers.surname, courses.name AS Corso
FROM `teachers`
INNER JOIN `course_teacher`
ON course_teacher.teacher_id = teachers.id
INNER JOIN `courses`
ON course_teacher.course_id = courses.id
WHERE teachers.name = 'Fulvio' AND teachers.surname = 'Amato';

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome.
SELECT students.name, students.surname, degrees.name, departments.name
FROM `students`
INNER JOIN `degrees`
ON students.degree_id = degrees.id
INNER JOIN `departments`
ON degrees.department_id = departments.id
ORDER BY `students`.`surname`, `students`.`name` ASC;



5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT degrees.name AS Corso_di_laurea, courses.name AS Corso, teachers.name, teachers.surname
FROM `degrees`
INNER JOIN `courses`
ON courses.degree_id = degrees.id
INNER JOIN `course_teacher`
on course_teacher.course_id = courses.id
INNER JOIN `teachers`
ON course_teacher.teacher_id = teachers.id
ORDER BY `degrees`.`name` ASC;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
SELECT teachers.name, teachers.surname, departments.name AS Dipartimento
FROM `departments`
INNER JOIN `degrees`
ON degrees.department_id = departments.id
INNER JOIN `courses`
ON courses.degree_id= degrees.id
INNER JOIN `course_teacher`
ON course_teacher.course_id = courses.id
INNER JOIN `teachers`
ON course_teacher.teacher_id = teachers.id
WHERE departments.name LIKE '%matematica%';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.