## 1. Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(id), YEAR(enrolment_date)
FROM university.students
GROUP BY YEAR(enrolment_date);
```

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(id), office_address
FROM university.teachers
GROUP BY `office_address`;

```

## 3. Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(vote) AS AverageVote FROM university.exam_student;
```

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT degree_id, COUNT(id) AS num_courses
FROM university.courses
GROUP BY degree_id;

```
