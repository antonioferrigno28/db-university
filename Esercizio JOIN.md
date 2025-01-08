## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.* FROM `students`
JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";
```

## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `degrees`.`id` AS `degree_id`, `degrees`.`name` AS `degree_name`, `departments`.`name` AS `department_name`
FROM `university`.`degrees`
JOIN `university`.`departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = "Magistrale" AND `departments`.`name` = "Dipartimento di Neuroscienze"
```

## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT  `courses`.`id` AS `course_id`,
`courses`.`name` AS `course_name`,
`teachers`.`id` AS `teacher_id`
FROM `university`.`courses`
JOIN `university`.`course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `university`.`teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = 44
```

## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT `students`.`id` AS `student_id`,
`students`.`surname` AS `student_surname`,
`students`.`name` AS `student_name`,
`degrees`.*,
`departments`.`name` AS `department_name`
FROM `university`.`students`
JOIN `university`.`degrees`
ON `students`.`degree_id` = `degrees`.`id`
JOIN `university`.`departments`
ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`;
```

## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT `degrees`.`id` AS `degree_id`,
 `degrees`.`name` AS `degree_name`,
 `courses`.`id` AS `course_id`,
 `courses`.`name` AS `course_name`,
 `teachers`.`id` AS `teacher_id`,
 `teachers`.`name` AS `teacher_name`,
 `teachers`.`surname` AS `teacher_surname`
 FROM `university`.`degrees`
JOIN `university`.`courses`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `university`.`course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `university`.`teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `degrees`.`name`;
```

## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT
`teachers`.`id` AS `teacher_id`,
`teachers`.`name` AS `teacher_name`,
`teachers`.`surname` AS `teacher_surname`,
`departments`.`name` AS `department_name`
FROM `university`.`teachers`
JOIN `university`.`course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `university`.`courses`
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `university`.`degrees`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `university`.`departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = "Dipartimento di Matematica"
GROUP BY `teachers`.`id`

```

## 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql

```
