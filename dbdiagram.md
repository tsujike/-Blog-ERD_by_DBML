```js
Table members {
    id int [primary key]
}

//コメントです
Table members {
    id int [pk, note:'less than 10']
}

Table countries{
    code int [pk]

    note:'Members origin' //コメントです
}


//リレーションシップ
Table members {
    id int [pk, note:'less than 10']
    full_name varchar [not null]
    gender varchar(1) [default: 'm']
    created_at timestamp
    contry_code int  //[ref: > countries.code]
}

Table countries{
    code int [pk]
    name varchar [unique]
    
    note:'Members origin'
}



//リレーションシップの省略記法
Table members {
    id int [pk, note:'less than 10']
    full_name varchar [not null]
    gender varchar(1) [default: 'm']
    created_at timestamp
    contry_code int  //[ref: > countries.code]
}

Table countries{
    code int [pk]
    name varchar [unique]
    
    note:'Members origin'
}

Ref: members.contry_code > countries.code


//むかない1対1
Table user{
  name varchar [ref: - email.email]
}

Table email{
  email varchar
}

//可能性のある1対1
Table Japanese{
  word varchar [ref: - Chinese.word]
}

Table Chinese{
  word varchar
}


//1対多
Table teacher{
  id int [pk,ref: < subject.id]
  full_name varchar
}

Table subject{
  id int [pk]
  subject_name varchar
}


//1対多
Table oder{
  id int [pk, ref: < oder_detail.order_id]
  created_at datetime
  detail_id int
}

Table oder_detail{
  order_detail_id int [pk]
  order_id int
  product_name varchar
  quantity int
  price int
}


//多対多を解消した3項リレーションシップ
Table users as U{
  user_id int [pk]
  name varchar
}

Table tasks as T{
  task_id int [pk]
  task varchar
}

Table status as S{
  status_id int [pk]
  status varchar
}

Table UserTaskStatus as UTS{
  UserTaskStatus_id int [pk]
  user_id int
  task_id int
  status_id int
  created_at datetime
}

Ref:UTS.user_id < U.user_id
Ref:UTS.task_id < T.task_id
Ref:UTS.status_id < S.status_id
```
