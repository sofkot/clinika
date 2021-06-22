# 1ST REQUEST

**Описание запроса:**
```
Вывести данные врачей с информацией об их рабочих днях
```

**Код запроса:**
```
select name, speciality, working_days from doctors
inner join schedule on doctors.schedule_id = schedule.id
order by name desc;
```


**Результаты запроса:**

| name | speciality | working_days 
| --- | --- | --- 
| petr | cardiologist | {mon,tue}
| natasha | ent | {mon,wed}
| makar | pathologist | {mon,tue}
| larisa | psychologist | {wed, fri}

<br/>

# 2ND REQUEST

**Описание запроса:**
```
Вывести данные о приёмах с отображением информации о пациентах
```

**Код запроса:**
```
select * from appointments
inner join patients on appointments.patient_id = patients.id
order by time;
```


**Результаты запроса:**

| id | date | time | doctor_id | office_id | patient_id | id | name | phone_number | date_of_birth
| --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
| 1 | 2020-01-01 | 12:00:00 | 1 | 1 | 1 | 1 | sereja | +79119991271 | 2002-05-05
| 6 | 2020-01-10 | 12:30:00 | 2 | 1 | 1 | 1 | sereja | +79119991271 | 2002-05-05
| 2 | 2020-01-02 | 13:00:00 | 4 | 1 | 2 | 2 | dima | +79119391271 | 2002-05-01
| 4 | 2020-01-04 | 15:00:00 | 3 | 2 | 3 | 3 | oleg | +79113791271 | 2002-05-12
| 3 | 2020-01-03 | 17:00:00 | 3 | 2 | 3 | 3 | oleg | +79113791271 | 2002-05-12
| 7 | 2020-01-10 | 17:30:00 | 2 | 3 | 3 | 3 | oleg | +79113791271 | 2002-05-12
| 8 | 2020-01-15 | 18:30:00 | 3 | 3 | 1 | 1 | sereja | +79119991271 | 2002-05-05
| 5 | 2020-01-04| 19:00:00 | 3 | 2 | 1 | 1 | sereja | +79119991271 | 2002-05-05

<br/>

# 3RD REQUEST

**Описание запроса:**
```
Вывести данные о записях в медицинскую карту за приём(ы) 2020-01-02 
```

**Код запроса:**
```
select * from medical_records where id = (
select id from appointments where date = '2020-01-02'
);
```


**Результаты запроса:**

| id | diagnosis | condition | recommendation | appointment_id
| --- | --- | --- | --- | --- 
| 2 | vse ochen ploho | umer | ne prihodite bolshe | 2 

<br/>

# 4TH REQUEST

**Описание запроса:**
```
Вывести данные о приёмах, проводившихся в 1-ом кабинете, а также не в 12:00:00
```

**Код запроса:**
```
select * from appointments where office_id = 1 and not time = '12:00:00';
```


**Результаты запроса:**

| id | date | time | doctor_id | office_id | patient_id
| --- | --- | --- | --- | --- | ---
| 2 | 2020-01-02 | 13:00:00 | 4 | 1 | 2 
| 6 | 2020-01-10 | 12:30:00 | 2 | 1 | 1 

<br/>

# 5TH REQUEST

**Описание запроса:**
```
Вывести возраст пациентов клиники
```

**Код запроса:**
```
select *, age(date_of_birth) as age from patients;
```


**Результаты запроса:**

| id | name | phone_number | date_of_birth | age
| --- | --- | --- | --- | --- 
| 1 | sereja | +79119991271 | 2002-05-05 | 19 years 6 days
| 2 | dima | +79119391271 | 2002-05-01 | 19 years 10 days
| 3 | oleg | +79113791271 | 2002-05-12 | 18 years 11 mons 30 days

<br/>

# 6TH REQUEST

**Описание запроса:**
```
Вывести данные о приёмах в период с 2020-01-01 по 2020-01-07
```

**Код запроса:**
```
select * appointments where date between '2020-01-01' and '2020-01-07';
```


**Результаты запроса:**

| id | date | time | doctor_id | office_id | patient_id
| --- | --- | --- | --- | --- | ---
| 1 | 2020-01-01 | 12:00:00 | 1 | 1 | 1 
| 2 | 2020-01-02 | 13:00:00 | 4 | 1 | 2 
| 3 | 2020-01-03 | 17:00:00 | 3 | 2 | 3 
| 4 | 2020-01-04 | 15:00:00 | 3 | 2 | 3 
| 5 | 2020-01-04 | 19:00:00 | 3 | 2 | 1 

<br/>

# 7TH REQUEST

**Описание запроса:**
```
Вывести данные о врачах клиники с форматированием: отобразить имя и должность врача в одной строке с разделителем
```

**Код запроса:**
```
select *, concat_ws(' - ', name, speciality) as info from doctors;
```


**Результаты запроса:**

| id | name | speciality | date_of_birth | price_list_id | schedule_id | info
| --- | --- | --- | --- | --- | --- | ---
| 1 | petr | cardiologist | 1999-04-23 | 1 | 1 | petr - cardiologist
| 2 | natasha | ent | 1999-04-23 | 4 | 2 | natasha - ent
| 3 | larisa | psychologist | 1999-02-23 | 2 | 3 | larisa - psychologist
| 4 | makar | pathologist | 1999-05-28 | 3 | 1 | makar - pathologist 

<br/>

# 8TH REQUEST

**Описание запроса:**
```
Вывести длину имён врачей
```

**Код запроса:**
```
select length(name) from doctors;
```


**Результаты запроса:**

| length  |
| --- |
| 5 |
| 6 |
| 7 |
| 4 |

<br/>

# 9TH REQUEST

**Описание запроса:**
```
Вывести имена врачей верхним регистром
```

**Код запроса:**
```
select upper(name) from doctors;
```


**Результаты запроса:**

| upper  |
| --- |
| MAKAR |
| LARISA |
| NATASHA |
| PETR |

<br/>

# 10TH REQUEST

**Описание запроса:**
```
Вывести данные о приёме(ах) у врача патологоанатома, с состоянием пациента: умер
```

**Код запроса:**
```
select * from medical_records
inner join appointments on (medical_records.appointment_id = appointments.id)
inner join doctors on (appointments.doctor_id = doctors.id)
where medical_records.condition = 'umer' and doctors.speciality = 'pathologist';
```


**Результаты запроса:**

| id | diagnosis | condition | recommendation | appointment_id | id | date | time | doctor_id | office_id | patient_id | id | name | speciality | date_of_birth | price_list_id | schedule_id
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- 
| 2 | vse ochen ploho | umer | ne prihodite bolshe | 2 | 2 | 2020-01-02 | 13:00:00 | 4 | 1 | 2 | 4 | makar | pathologist | 1999-05-28 | 3 | 1

<br/>

# 11TH REQUEST

**Описание запроса:**
```
Вывести имена доктора и пациента, который к нему приходил, а также дату приёма
```

**Код запроса:**
```
select doctors.name, patients.name, appointments.date from appointments
inner join doctors on (appointments.doctor_id = doctors.id)
inner join patients on (appointments.patient_id = patients.id);
```


**Результаты запроса:**

| name | name | date 
| --- | --- | --- 
| petr | sereja | 2020-01-01
| larisa | oleg | 2020-01-03
| makar | dima | 2020-01-02
| larisa | oleg | 2020-01-04
| larisa | sereja | 2020-01-04
| natasha | sereja | 2020-01-10
| natasha | oleg | 2020-01-10
| larisa | sereja | 2020-01-15

<br/>

# 12TH REQUEST

**Описание запроса:**
```
Вывести данные о докторах с количеством пациентов, приходивших к ним на приём
```

**Код запроса:**
```
select doctors.id, doctors.name, count(distinct patients.name) from appointments
inner join doctors on (appointments.doctor_id = doctors.id)
inner join patients on (appointments.patient_id = patients.id)
group by doctors.id;
```


**Результаты запроса:**

| id | name | count
| --- | --- | --- 
| 1 | petr | 1
| 2 | natasha | 2
| 3 | larisa | 2
| 4 | makar | 1

<br/>

# 13TH REQUEST

**Описание запроса:**
```
Вывести данные о заработанных деньгах каждого врача от проведённых услуг
```

**Код запроса:**
```
select appointments.doctor_id, count(appointments.doctor_id)*price_lists.price as sum from appointments
inner join doctors on (appointments.doctor_id = doctors.id)
inner join price_lists on (doctors.proce_list_id = price_lists.id)
group by appointments.doctor_id, price_lists.price;
```


**Результаты запроса:**

| doctor_id | sum 
| --- | --- 
| 1 | $1,900.00
| 2 | $4,200.00
| 3 | $9,600.00
| 4 | $5,500.00

<br/>

# 14TH REQUEST

**Описание запроса:**
```
Вывести данные кабинет(а)ов, в котор(ом)ых проводилось более 2-х приёмов
```

**Код запроса:**
```
select office_id, count(office_id) from appointments
group by office_id
having count(office_id) > 2;
```


**Результаты запроса:**

| office_id | count
| --- | --- 
| 2 | 3
| 1 | 3

<br/>

# 15TH REQUEST

**Описание запроса:**
```
Вывести дату(ы) приёмов, в которую(ые) было от 2-х до 3-х приёмов пациентов
```

**Код запроса:**
```
select date, count(date) from appointments
group by date
having count(date) in (2,3);
```


**Результаты запроса:**

| date | count
| --- | --- 
| 2020-01-04 | 2
| 2020-01-10 | 2

<br/>