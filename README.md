# Opportunity_Cup2022

Здесь представлен ETL-процесс по поиску фродов среди данных банковских операций, реализованный на языке python

Также, код можно оптимизировать и увеличить точность определения, используя базу данных (но этот вариант реализовать полность не успели)
Ниже прилагается код для загрузки и табллица, которые могут использоваться для зранения статистики пользователя
create table temp_json (values text);
copy temp_json from 'D:\test.json';

Пример таблицы с данными о пользователях:
![image](https://user-images.githubusercontent.com/71030143/194439497-c0b3446a-2fd1-424c-b30e-db354655857a.png)



Текст программы в PostgreSQL:

select values->>'date'as date;

values->>'card'as card;

values->>'account'as account;

values->>'account_valid_to'as account_valid_to;

values->>'client'as client;

values->>'last_name'as last_name;

values->>'first_name'as first_name;

values->>'patronymic'as patronymic;

values->>'date_of_birth'as date_of_birth;

values->>'passport'as passport;

values->>'passport_valid_to'as passport_valid_to;

values->>'phone'as phone;

values->>'oper_type'as oper_type;

values->>'amount'as amount;

values->>'open_result'as open_result;

values->>'terminal'as terminal;

values->>'terminal_type'as terminal_type;

values->>'city'as city;

values->>'address'as address

from(
select json_array_elements(replace(values,'\','\\')::json) as values
    from temp_json
) a;
