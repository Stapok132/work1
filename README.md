# Лабораторная работа 1 по дисциплине "Базы данных"
## ФИО студента, номер учебной группы
Канин Степан Алексеевич, 2261-ДБ
## Вариант 27: "Информационная система поликлиники"
Информация об отделении поликлиники (название отделения -хирургия,
терапия, неврология, ФИО заведующего).
Информация о пациенте (фамилия, имя, отчество, адрес, город, возраст, пол).
Врачи работают в отделениях, о них накапливается информация: ФИО,
должность, стаж работы, научное звание, адрес, зарплата).
Накапливается информация об историях болезней пациентов, где хранятся
название болезни, признаки болезни, назначения дата заболевания, дата
вылечивания.

Выходные документы:
* Состав врачей отделений с указанием их зарплат, упорядоченный в
алфавитном порядке ФИО, сгруппированных по отделениям
* Истории болезни определенного пациента, отсортированные по датам,
с указанием ФИО врача и диагноза

ПЕРЕЧЕНЬ СУЩНОСТЕЙ И ИХ АТРИБУТОВ(НА ОСНОВЕ ER-ДИАГРАММЫ)
ОТДЕЛЕНИЕ (department)

id (PK) — Уникальный идентификатор отделения.

название (VARCHAR) — Наименование отделения (Хирургия, Терапия, Неврология).

заведующий (VARCHAR) — ФИО заведующего отделением.

ВРАЧ (doctor)

id (PK) — Уникальный идентификатор врача (внутренний).

фио (VARCHAR) — ФИО врача.

должность (VARCHAR) — Должность врача (Хирург, Терапевт, Невролог).

id_отделения (FK -> ОТДЕЛЕНИЯ.id) — Идентификатор отделения, в котором работает врач.

стаж_работы (INT) — Стаж работы врача в годах.

ПАЦИЕНТ (patient)

id (PK) — Уникальный идентификатор пациента.

фамилия (VARCHAR) — Фамилия пациента.

имя (VARCHAR) — Имя пациента.

отчество (VARCHAR) — Отчество пациента.

адрес (VARCHAR) — Адрес проживания пациента.

город (VARCHAR) — Город проживания пациента.

возраст (INT) — Возраст пациента.

пол (CHAR) — Пол пациента (М/Ж).

ИСТОРИИ_БОЛЕЗНИ (medical_records)

id (PK) — Уникальный идентификатор истории болезни.

id_пациента (FK -> ПАЦИЕНТЫ.id) — Идентификатор пациента.

id_врача (FK -> ВРАЧИ.id) — Идентификатор лечащего врача.

название_болезни (VARCHAR) — Наименование заболевания.

признаки_болезни (TEXT) — Описание симптомов.

назначения (TEXT) — Назначенное лечение.

дата_заболевания (DATE) — Дата начала заболевания/лечения.

дата_вылечивания (DATE) — Дата окончания лечения.

Связи между сущностями (Relationships):

ИМЕЕТ_ИСТОРИЮ (медицинская карта): Связь между ПАЦИЕНТЫ и ИСТОРИИ_БОЛЕЗНИ. Один пациент может иметь множество записей в истории болезни (по разным обращениям и диагнозам). Каждая запись в истории болезни принадлежит только одному пациенту. (1:N).

ЛЕЧИТ (лечащий врач): Связь между ИСТОРИИ_БОЛЕЗНИ и ВРАЧИ. Каждую историю болезни ведет один лечащий врач. Один врач может вести множество историй болезни разных пациентов. (N:1).

РАБОТАЕТ_В (рабочее место): Связь между ВРАЧИ и ОТДЕЛЕНИЯ. Один врач работает только в одном отделении. В одном отделении может работать множество врачей. (N:1).

## ER-диаграмма
![ER диаграмма](https://github.com/Stapok132/work1/blob/main/er.png)

## Логическая модель по диаграмме
![Логическая модель по диаграмме](https://github.com/Stapok132/work1/blob/main/logic.png)

## Физическая модель по диаграмме
![Физическая модель по диаграмме](https://github.com/Stapok132/work1/blob/main/fiz.png)

## Лабораторная работа №2
## Создаём 4 таблицы с записанными в них данными
![](https://github.com/Stapok132/work1/blob/main/8.png)
![](https://github.com/Stapok132/work1/blob/main/9.png)
![](https://github.com/Stapok132/work1/blob/main/10.png)
## После создания таблиц, выводим их для для проверки
![](https://github.com/Stapok132/work1/blob/main/4.png)
![](https://github.com/Stapok132/work1/blob/main/5.png)
![](https://github.com/Stapok132/work1/blob/main/6.png)
![](https://github.com/Stapok132/work1/blob/main/7.png)
## Далее выполняем SELECT-запросы с JOIN
![](https://github.com/Stapok132/work1/blob/main/11ю2.png)
![](https://github.com/Stapok132/work1/blob/main/11ю1.png)
![](https://github.com/Stapok132/work1/blob/main/123.png)
![](https://github.com/Stapok132/work1/blob/main/121.png)
![](https://github.com/Stapok132/work1/blob/main/122.png)

## Лабораторная работа №3
## Создадим 2 представления(Зарплатная ведомость и полная история пациентов)
![](https://github.com/Stapok132/work1/blob/main/1!.jpg)
## Первая процедура
![](https://github.com/Stapok132/work1/blob/main/2!.jpg)
## Вторая процедура
![](https://github.com/Stapok132/work1/blob/main/3!.jpg)
## Результат первого представления
![](https://github.com/Stapok132/work1/blob/main/11.jpg)
## Результат второго представления
![](https://github.com/Stapok132/work1/blob/main/22.jpg)
## Результат первой процедуры
![](https://github.com/Stapok132/work1/blob/main/33.jpg)
## Результат второй процедуры
![](https://github.com/Stapok132/work1/blob/main/44.jpg)

## Лабораторная работа №4
## Генератор отделений
CREATE OR REPLACE PROCEDURE kanin.генерировать_отделения(кол_во INTEGER) 
LANGUAGE plpgsql AS $$
DECLARE 
    названия TEXT[] := ARRAY['Хирургия','Терапия','Неврология','Кардиология','Травматология'];
BEGIN
    INSERT INTO kanin."отделения" (название, заведующий)
    SELECT 
        названия[1 + ((seq-1) % 5)] || ' отделение №' || seq,
        'Заведующий_' || seq
    FROM generate_series(1, кол_во) as seq;
END;
$$;
![](https://github.com/Stapok132/work1/blob/main/1.png)
## Генератор врачей
CREATE OR REPLACE PROCEDURE kanin.генерировать_врачей(кол_во INTEGER) 
LANGUAGE plpgsql AS $$
BEGIN
    INSERT INTO kanin."врачи" (фио, должность, стаж_лет, зарплата, отделение_id)
    SELECT 
        'Врач_' || seq || ' Иванов Петрович',
        CASE (seq % 3) 
            WHEN 0 THEN 'Хирург'
            WHEN 1 THEN 'Терапевт' 
            ELSE 'Невролог'
        END,
        1 + (seq % 30),
        40000 + (seq % 100000),
        1 + (seq % 3)
    FROM generate_series(1, кол_во) as seq;
END;
$$;
![](https://github.com/Stapok132/work1/blob/main/2.png)
## Генератор историй болезни
CREATE OR REPLACE PROCEDURE kanin.генерировать_истории(кол_во INTEGER) 
LANGUAGE plpgsql AS $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM kanin."пациенты") OR 
       NOT EXISTS (SELECT 1 FROM kanin."врачи") THEN
        RAISE EXCEPTION 'Сначала нужно сгенерировать пациентов и врачей!';
    END IF;
    
    INSERT INTO kanin."истории_болезни" (пациент_id, врач_id, название_болезни, симптомы, дата_начала)
    SELECT 
        (SELECT id FROM kanin."пациенты" ORDER BY id OFFSET (seq-1) % (SELECT COUNT(*) FROM kanin."пациенты") LIMIT 1),
        (SELECT id FROM kanin."врачи" ORDER BY id OFFSET (seq-1) % (SELECT COUNT(*) FROM kanin."врачи") LIMIT 1),
        CASE (seq % 5)
            WHEN 0 THEN 'Грипп'
            WHEN 1 THEN 'ОРВИ'
            WHEN 2 THEN 'Перелом'
            WHEN 3 THEN 'Гастрит'
            ELSE 'Гипертония'
        END,
        'Симптомы пациента ' || seq,
        CURRENT_DATE - (seq % 365)
    FROM generate_series(1, кол_во) as seq;
END;
$$;
![](https://github.com/Stapok132/work1/blob/main/3.png)
## Генератор пациентов
CREATE OR REPLACE PROCEDURE kanin.генерировать_пациентов(кол_во INTEGER) 
LANGUAGE plpgsql AS $$
BEGIN
    INSERT INTO kanin."пациенты" (фамилия, имя, отчество, адрес, город, возраст, пол)
    SELECT 
        'Пациент_' || seq,
        'Имя_' || (seq % 100),
        'Отчество_' || seq,
        'ул. Больничная, д.' || (seq % 100),
        'Город_' || (seq % 10),
        18 + (seq % 60),
        'М'  -- Все пациенты мужчины
    FROM generate_series(1, кол_во) as seq;
END;
$$;
![](https://github.com/Stapok132/work1/blob/main/4.png)
## Анализ запросов
-- 1. Поиск по ID
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE id = 100;

-- 2. Поиск по должности
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE должность = 'Хирург';

-- 3. Поиск по стажу
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE стаж_лет BETWEEN 10 AND 20;

-- 4. JOIN с отделениями
EXPLAIN ANALYZE SELECT в.*, о.название FROM kanin."врачи" в JOIN kanin."отделения" о ON в.отделение_id = о.id WHERE в.стаж_лет >= 10;

-- 5. Поиск по ФИО
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE фио LIKE 'Иванов%';

-- 6. Высокая зарплата
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE зарплата > 80000;

-- 7. Агрегация по отделениям
EXPLAIN ANALYZE SELECT о.название, COUNT(*), AVG(в.зарплата) FROM kanin."врачи" в JOIN kanin."отделения" о ON в.отделение_id = о.id GROUP BY о.название;

-- 8. TOP 10 по зарплате
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" ORDER BY зарплата DESC LIMIT 10;

-- 9. Статистика по должностям
EXPLAIN ANALYZE SELECT должность, COUNT(*), AVG(зарплата) FROM kanin."врачи" GROUP BY должность;

-- 10. Составной WHERE
EXPLAIN ANALYZE SELECT * FROM kanin."врачи" WHERE отделение_id = 1 AND должность = 'Хирург' AND зарплата > 50000;
![](https://github.com/Stapok132/work1/blob/main/5.png)
## Создали индекс
![](https://github.com/Stapok132/work1/blob/main/laba1.png)
## Принудительно отключили его
![](https://github.com/Stapok132/work1/blob/main/7.png)
## Без индекса
![](https://github.com/Stapok132/work1/blob/main/laba2.png)
## С индексом
![](https://github.com/Stapok132/work1/blob/main/laba3.png)
# С индексами производительность становится быстрее
