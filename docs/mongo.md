# Изменённая БД

![схема](/5.png)

<br/>

# Создание БД

```
use db
    switched to db db
db.createCollection("Patient")
    { "ok" : 1 }
db.createCollection("Appointment")
    { "ok" : 1 }
db.createCollection("Doctor")
    { "ok" : 1 }

```

## PATIENT

**Заполнение данными**

```

db.Patient.insertOne({'name' = 'sereja', 'phone_number' = '+7911999127', 'date_of_birth' = '2002-05-05'})
db.Patient.insertOne({'name' = 'dima', 'phone_number' = '+79119391271', 'date_of_birth' = '2002-05-01'})
db.Patient.insertOne({'name' = 'oleg', 'phone_number' = '+79113791271', 'date_of_birth' = '2002-05-12'})

```

**Результаты заполнения**

```

db.Patient.find().pretty()
{
        "_id" : ObjectId("60d201cd519767a01e5b0733"),
        "name" : "sereja",
        "phone_number" : "+7911999127",
        "date_of_birth" : "2002-05-05"
}
{
        "_id" : ObjectId("60d201f2519767a01e5b0734"),
        "name" : "dima",
        "phone_number" : "+79119391271",
        "date_of_birth" : "2002-05-01"
}
{
        "_id" : ObjectId("60d2021b519767a01e5b0735"),
        "name" : "oleg",
        "phone_number" : "+79113791271",
        "date_of_birth" : "2002-05-12"
}

```

## DOCTOR

**Заполнение данными**

```

db.Doctor.insertOne( { 'name' : 'petr', 'speciality' : 'cardiologist', 'date_of_birth' : '1999-04-23', 'price_list'  : { 'service' : 'treatment', 'price' : 1900 }, 'schedule' : { 'working_days' : [ 'mon', 'tue' ] } } )
    {
        "acknowledged" : true,
        "insertedId" : ObjectId("60d226c2519767a01e5b0736")
    }

db.Doctor.insertOne( { 'name' : 'natasha', 'speciality' : 'ent', 'date_of_birth' : '1999-04-23', 'price_list'  : { 'service' : 'inspection', 'price' : 2100 }, 'schedule' : { 'working_days' : [ 'mon', 'wed' ] } } )
    {
        "acknowledged" : true,
        "insertedId" : ObjectId("60d227a3519767a01e5b0737")
    }

db.Doctor.insertOne( { 'name' : 'larisa', 'speciality' : 'psychologist', 'date_of_birth' : '1999-02-23', 'price_list'  : { 'service' : 'consultation', 'price' : 2400 }, 'schedule' : { 'working_days' : [ 'wed', 'fri' ] } } )
    {
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22808519767a01e5b0738")
    }

db.Doctor.insertOne( { 'name' : 'makar', 'speciality' : 'pathologist', 'date_of_birth' : '1999-05-28', 'price_list'  : { 'service' : 'conversation', 'price' : 5500 }, 'schedule' : { 'working_days' : [ 'mon', 'tue' ] } } )
    {
        "acknowledged" : true,
        "insertedId" : ObjectId("60d2286b519767a01e5b0739")
    }

```

**Результаты заполнения**

```

db.Doctor.find().pretty()
{
        "_id" : ObjectId("60d226c2519767a01e5b0736"),
        "name" : "petr",
        "speciality" : "cardiologist",
        "date_of_birth" : "1999-04-23",
        "price_list" : {
                "service" : "treatment",
                "price" : 1900
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "tue"
                ]
        }
}
{
        "_id" : ObjectId("60d227a3519767a01e5b0737"),
        "name" : "natasha",
        "speciality" : "ent",
        "date_of_birth" : "1999-04-23",
        "price_list" : {
                "service" : "inspection",
                "price" : 2100
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "wed"
                ]
        }
}
{
        "_id" : ObjectId("60d22808519767a01e5b0738"),
        "name" : "larisa",
        "speciality" : "psychologist",
        "date_of_birth" : "1999-02-23",
        "price_list" : {
                "service" : "consultation",
                "price" : 2400
        },
        "schedule" : {
                "working_days" : [
                        "wed",
                        "fri"
                ]
        }
}
{
        "_id" : ObjectId("60d2286b519767a01e5b0739"),
        "name" : "makar",
        "speciality" : "pathologist",
        "date_of_birth" : "1999-05-28",
        "price_list" : {
                "service" : "conversation",
                "price" : 5500
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "tue"
                ]
        }
}

```

## APPOINTMENT

**Заполнение данными**

```

db.Appointment.insertOne( { 'date' : '2020-01-01', 'patient' : ObjectId("60d201cd519767a01e5b0733"), 'doctor' : ObjectId("60d226c2519767a01e5b0736"), 'office' : { 'begin' : '12:00:00', 'end' : '16:00:00', 'phone_number' : '+70001113344' }, 'medical_record' : { 'diagnosis' : 'vse ochen ploho', 'condition' : 'pochty umer', 'recommendation' : 'ne prihodite bolshe' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22c13519767a01e5b073a")
}

db.Appointment.insertOne( { 'date' : '2020-01-02', 'patient' : ObjectId("60d201f2519767a01e5b0734"), 'doctor' : ObjectId("60d2286b519767a01e5b0739"), 'office' : { 'begin' : '12:00:00', 'end' : '16:00:00', 'phone_number' : '+70001113344' }, 'medical_record' : { 'diagnosis' : 'vse ochen ploho', 'condition' : 'umer', 'recommendation' : 'ne prihodite bolshe' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22c9d519767a01e5b073b")
}

db.Appointment.insertOne( { 'date' : '2020-01-03', 'patient' : ObjectId("60d2021b519767a01e5b0735"), 'doctor' : ObjectId("60d22808519767a01e5b0738"), 'office' : { 'begin' : '12:00:00', 'end' : '18:00:00', 'phone_number' : '+70001213344' }, 'medical_record' : { 'diagnosis' : 'cool', 'condition' : 'alive', 'recommendation' : 'ne boleyte' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22d48519767a01e5b073c")
}

db.Appointment.insertOne( { 'date' : '2020-01-04', 'patient' : ObjectId("60d2021b519767a01e5b0735"), 'doctor' : ObjectId("60d22808519767a01e5b0738"), 'office' : { 'begin' : '12:00:00', 'end' : '18:00:00', 'phone_number' : '+70001213344' }, 'medical_record' : { 'diagnosis' : 'cool', 'condition' : 'alive', 'recommendation' : 'ne boleyte' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22d98519767a01e5b073d")
}

db.Appointment.insertOne( { 'date' : '2020-01-04', 'patient' : ObjectId("60d201cd519767a01e5b0733"), 'doctor' : ObjectId("60d22808519767a01e5b0738"), 'office' : { 'begin' : '12:00:00', 'end' : '18:00:00', 'phone_number' : '+70001213344' }, 'medical_record' : { 'diagnosis' : 'cool', 'condition' : 'alive', 'recommendation' : 'ne prihodite bolshe' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22e17519767a01e5b073e")
}

db.Appointment.insertOne( { 'date' : '2020-01-10', 'patient' : ObjectId("60d201cd519767a01e5b0733"), 'doctor' : ObjectId("60d227a3519767a01e5b0737"), 'office' : { 'begin' : '12:00:00', 'end' : '16:00:00', 'phone_number' : '+70001113344' }, 'medical_record' : { 'diagnosis' : 'vse ochen ploho', 'condition' : 'alive', 'recommendation' : 'ne boleyte' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22ec6519767a01e5b073f")
}

db.Appointment.insertOne( { 'date' : '2020-01-10', 'patient' : ObjectId("60d2021b519767a01e5b0735"), 'doctor' : ObjectId("60d227a3519767a01e5b0737"), 'office' : { 'begin' : '15:00:00', 'end' : '21:30:00', 'phone_number' : '+70001213390' }, 'medical_record' : { 'diagnosis' : 'cool', 'condition' : 'pochty umer', 'recommendation' : 'ne boleyte' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d22f58519767a01e5b0740")
}

db.Appointment.insertOne( { 'date' : '2020-01-15', 'patient' : ObjectId("60d201cd519767a01e5b0733"), 'doctor' : ObjectId("60d22808519767a01e5b0738"), 'office' : { 'begin' : '12:00:00', 'end' : '16:00:00', 'phone_number' : '+70001113344' }, 'medical_record' : { 'diagnosis' : 'cool', 'condition' : 'alive', 'recommendation' : 'ne prihodite bolshe' } } )
{
        "acknowledged" : true,
        "insertedId" : ObjectId("60d23009519767a01e5b0741")
}

```

**Результаты заполнения**

```

db.Appointment.find().pretty()
{
        "_id" : ObjectId("60d22c13519767a01e5b073a"),
        "date" : "2020-01-01",
        "patient" : ObjectId("60d201cd519767a01e5b0733"),
        "doctor" : ObjectId("60d226c2519767a01e5b0736"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "16:00:00",
                "phone_number" : "+70001113344"
        },
        "medical_record" : {
                "diagnosis" : "vse ochen ploho",
                "condition" : "pochty umer",
                "recommendation" : "ne prihodite bolshe"
        }
}
{
        "_id" : ObjectId("60d22c9d519767a01e5b073b"),
        "date" : "2020-01-02",
        "patient" : ObjectId("60d201f2519767a01e5b0734"),
        "doctor" : ObjectId("60d2286b519767a01e5b0739"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "16:00:00",
                "phone_number" : "+70001113344"
        },
        "medical_record" : {
                "diagnosis" : "vse ochen ploho",
                "condition" : "umer",
                "recommendation" : "ne prihodite bolshe"
        }
}
{
        "_id" : ObjectId("60d22d48519767a01e5b073c"),
        "date" : "2020-01-03",
        "patient" : ObjectId("60d2021b519767a01e5b0735"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "18:00:00",
                "phone_number" : "+70001213344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne boleyte"
        }
}
{
        "_id" : ObjectId("60d22d98519767a01e5b073d"),
        "date" : "2020-01-04",
        "patient" : ObjectId("60d2021b519767a01e5b0735"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "18:00:00",
                "phone_number" : "+70001213344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne boleyte"
        }
}
{
        "_id" : ObjectId("60d22e17519767a01e5b073e"),
        "date" : "2020-01-04",
        "patient" : ObjectId("60d201cd519767a01e5b0733"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "18:00:00",
                "phone_number" : "+70001213344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne prihodite bolshe"
        }
}
{
        "_id" : ObjectId("60d22ec6519767a01e5b073f"),
        "date" : "2020-01-10",
        "patient" : ObjectId("60d201cd519767a01e5b0733"),
        "doctor" : ObjectId("60d227a3519767a01e5b0737"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "16:00:00",
                "phone_number" : "+70001113344"
        },
        "medical_record" : {
                "diagnosis" : "vse ochen ploho",
                "condition" : "alive",
                "recommendation" : "ne boleyte"
        }
}
{
        "_id" : ObjectId("60d22f58519767a01e5b0740"),
        "date" : "2020-01-10",
        "patient" : ObjectId("60d2021b519767a01e5b0735"),
        "doctor" : ObjectId("60d227a3519767a01e5b0737"),
        "office" : {
                "begin" : "15:00:00",
                "end" : "21:30:00",
                "phone_number" : "+70001213390"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "pochty umer",
                "recommendation" : "ne boleyte"
        }
}
{
        "_id" : ObjectId("60d23009519767a01e5b0741"),
        "date" : "2020-01-15",
        "patient" : ObjectId("60d201cd519767a01e5b0733"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "16:00:00",
                "phone_number" : "+70001113344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne prihodite bolshe"
        }
}

```

<br/>


# Запросы к БД

## REQUEST 1ST

```

db.Appointment.find({ 'date' :  '2020-01-02' }).pretty()
{
        "_id" : ObjectId("60d22c9d519767a01e5b073b"),
        "date" : "2020-01-02",
        "patient" : ObjectId("60d201f2519767a01e5b0734"),
        "doctor" : ObjectId("60d2286b519767a01e5b0739"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "16:00:00",
                "phone_number" : "+70001113344"
        },
        "medical_record" : {
                "diagnosis" : "vse ochen ploho",
                "condition" : "umer",
                "recommendation" : "ne prihodite bolshe"
        }
}

```

## REQUEST 2ND

```

db.Doctor.aggregate({ $project :  { itemDescription : { $concat : [ "$name", "-", "$speciality" ] } } }).pretty()
{
        "_id" : ObjectId("60d226c2519767a01e5b0736"),
        "itemDescription" : "petr-cardiologist"
}
{
        "_id" : ObjectId("60d227a3519767a01e5b0737"),
        "itemDescription" : "natasha-ent"
}
{
        "_id" : ObjectId("60d22808519767a01e5b0738"),
        "itemDescription" : "larisa-psychologist"
}
{
        "_id" : ObjectId("60d2286b519767a01e5b0739"),
        "itemDescription" : "makar-pathologist"
}

```

## REQUEST 3RD

```

db.Appointment.find({ 'date' : '2020-01-04',  'medical_record.condition' : 'alive'  }).pretty()
{
        "_id" : ObjectId("60d22d98519767a01e5b073d"),
        "date" : "2020-01-04",
        "patient" : ObjectId("60d2021b519767a01e5b0735"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "18:00:00",
                "phone_number" : "+70001213344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne boleyte"
        }
}
{
        "_id" : ObjectId("60d22e17519767a01e5b073e"),
        "date" : "2020-01-04",
        "patient" : ObjectId("60d201cd519767a01e5b0733"),
        "doctor" : ObjectId("60d22808519767a01e5b0738"),
        "office" : {
                "begin" : "12:00:00",
                "end" : "18:00:00",
                "phone_number" : "+70001213344"
        },
        "medical_record" : {
                "diagnosis" : "cool",
                "condition" : "alive",
                "recommendation" : "ne prihodite bolshe"
        }
}

```

## REQUEST 4TH

```

db.Doctor.find().sort( { name : -1} ).pretty()
{
        "_id" : ObjectId("60d226c2519767a01e5b0736"),
        "name" : "petr",
        "speciality" : "cardiologist",
        "date_of_birth" : "1999-04-23",
        "price_list" : {
                "service" : "treatment",
                "price" : 1900
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "tue"
                ]
        }
}
{
        "_id" : ObjectId("60d227a3519767a01e5b0737"),
        "name" : "natasha",
        "speciality" : "ent",
        "date_of_birth" : "1999-04-23",
        "price_list" : {
                "service" : "inspection",
                "price" : 2100
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "wed"
                ]
        }
}
{
        "_id" : ObjectId("60d2286b519767a01e5b0739"),
        "name" : "makar",
        "speciality" : "pathologist",
        "date_of_birth" : "1999-05-28",
        "price_list" : {
                "service" : "conversation",
                "price" : 5500
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "tue"
                ]
        }
}
{
        "_id" : ObjectId("60d22808519767a01e5b0738"),
        "name" : "larisa",
        "speciality" : "psychologist",
        "date_of_birth" : "1999-02-23",
        "price_list" : {
                "service" : "consultation",
                "price" : 2400
        },
        "schedule" : {
                "working_days" : [
                        "wed",
                        "fri"
                ]
        }
}

```

## REQUEST 5TH

```

db.Doctor.find( { 'price_list.price' : { $gte: 2000 } } ).pretty()
{
        "_id" : ObjectId("60d227a3519767a01e5b0737"),
        "name" : "natasha",
        "speciality" : "ent",
        "date_of_birth" : "1999-04-23",
        "price_list" : {
                "service" : "inspection",
                "price" : 2100
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "wed"
                ]
        }
}
{
        "_id" : ObjectId("60d22808519767a01e5b0738"),
        "name" : "larisa",
        "speciality" : "psychologist",
        "date_of_birth" : "1999-02-23",
        "price_list" : {
                "service" : "consultation",
                "price" : 2400
        },
        "schedule" : {
                "working_days" : [
                        "wed",
                        "fri"
                ]
        }
}
{
        "_id" : ObjectId("60d2286b519767a01e5b0739"),
        "name" : "makar",
        "speciality" : "pathologist",
        "date_of_birth" : "1999-05-28",
        "price_list" : {
                "service" : "conversation",
                "price" : 5500
        },
        "schedule" : {
                "working_days" : [
                        "mon",
                        "tue"
                ]
        }
}

```

<br/>

# Map Reduce

```
Подсчёт количества приёмов у каждого врача
```

## Создание Map Reduce

```
db.Appointment.mapReduce( function () { emit(this.doctor, 1); }, function (key, values) { return Array.sum(values); }, { out: "result" } )
```

![результат](/6.png)