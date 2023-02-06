# Homework 2


> ## Задание № 1

Отправить запрос на URL: http://162.55.220.72:5005/first

Метод: GET 

```JS
Response:

This is the first responce from server!ss
```
1. Проверить, что статус код 200 
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Проверить, что в body приходит правильный string 
```JS
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
```

Результаты тестов:

![](https://github.com/Sawa-solo/Postman/blob/4b548d122fd3bf771637d8c30caf399b2d7a98e7/screens/first.png)



> ## Задание № 2

Отправить запрос на URL: http://162.55.220.72:5005/user_info_3

Метод: POST

Параметры:

![](https://github.com/Sawa-solo/Postman/blob/0f58df8bf927d8f25d72a65487ef986d891bd15e/screens/key-value%20user_info_3.png)

```JS
Response:

{
    "age": "29",
    "family": {
        "children": [
            [
                "Alex",
                24
            ],
            [
                "Kate",
                12
            ]
        ],
        "u_salary_1_5_year": 1000
    },
    "name": "Sasha",
    "salary": 250
}
```

1. Проверить, что статус код 200
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Спарсить response body в json 

```JS
let resp_f = pm.response.json();
```
3. Создать переменные для данных

```JS
let req_age = +req_f.age
let resp_age = +resp_f.age

let req_name = req_f.name
let resp_name = resp_f.name 

let req_salary = +req_f.salary
let resp_salary = +resp_f.salary

let resp_salary_1_5_year = resp_f.family.u_salary_1_5_year
```

4. Проверить, что name в ответе равно name в request (name вбить руками)
```JS
pm.test("Name", function () {
pm.expect(req_name).to.eql("Sasha");
});
```

5. Проверить, что age в ответе равно age в request (age вбить руками)
```JS
pm.test("Age", function () {
pm.expect(req_age).to.eql(29);
});
```

6. Проверить, что salary в ответе равно salary в request (salary вбить руками)
```JS
pm.test("Salary", function () {
pm.expect(req_salary).to.eql(250);
});
```

7. Спарсить request
```JS
let req_f = request.data
```

8. Проверить, что name в ответе равно name в request (name забрать из request)
```JS
pm.test("Name", function () {
pm.expect(req_name).to.eql(resp_name);
});
```

9. Проверить, что age в ответе равно age в request (age забрать из request)
```JS
pm.test("Age", function () {
pm.expect(req_age).to.eql(resp_age);
});
```

10. Проверить, что salary в ответе равно salary в request (salary забрать из request)
```JS
pm.test("Salary", function () {
pm.expect(req_salary).to.eql(resp_salary);
});
```

11. Вывести в консоль параметр family из response
```JS
console.log (resp_f.family)
```

![](https://github.com/Sawa-solo/Postman/blob/0f58df8bf927d8f25d72a65487ef986d891bd15e/screens/console%20user_info_3.png)

12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```JS
pm.test("Salary_1_5_year", function () {
 pm.expect(req_salary*4).to.eql(resp_salary_1_5_year);
});
```
Результаты тестов:

![](https://github.com/Sawa-solo/Postman/blob/0f58df8bf927d8f25d72a65487ef986d891bd15e/screens/tests%20pass%20user_info_3.png)


> ## Задание № 3

Отправить запрос на URL: http://162.55.220.72:5005/object_info_3

Метод: GET

Параметры: см. Задание № 2

```JS
Response:

{
    "age": "29",
    "family": {
        "children": [
            [
                "Alex",
                24
            ],
            [
                "Kate",
                12
            ]
        ],
        "pets": {
            "cat": {
                "age": 3,
                "name": "Sunny"
            },
            "dog": {
                "age": 4,
                "name": "Luky"
            }
        },
        "u_salary_1_5_year": 2000
    },
    "name": "Sasha",
    "salary": 500
}
```

1. Проверить, что статус код 200
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

2. Спарсить response body в json

```JS
let resp_p = pm.response.json();
```
3. Спарсить request

```JS
let req_p = pm.request.url.query.toObject();
```
4. Создать переменные для данных

```JS
let req_name = req_p.name
let resp_name = resp_p.name

let req_age = req_p.age
let resp_age = resp_p.age

let req_salary = + req_p.salary
let resp_salary = resp_p.salary

let dog_name = resp_p.family.pets.dog.name
let dog_age = + resp_p.family.pets.dog.age
```

5. Проверить, что name в ответе равно name в request (name забрать из request)

```JS
pm.test("Name", function () {
pm.expect(req_p.name).to.eql(resp_p.name);
});
```
6. Проверить, что age в ответе равно age в request (age забрать из request)

```JS
pm.test("Age", function () {
pm.expect(req_p.age).to.eql(resp_p.age);
});
```
7. Проверить, что salary в ответе равно salary в request (salary забрать из request)

```JS
pm.test("Salary", function () {
pm.expect(+ req_p.salary).to.eql(resp_p.salary);
});
```
8. Вывести в консоль параметр family из response

```JS
console. log (resp_p.family)
```
![](https://github.com/Sawa-solo/Postman/blob/01649577689120888db8f44d66f6b75b4bb677b5/screens/console_object_info_3.png)

9. Проверить, что у параметра dog есть параметр name

```JS
pm.test("Dog have name property", function () {
 pm.expect(resp_p.family.pets.dog).to.have.property("name");
});
```
10. Проверить, что у параметра dog есть параметр age

```JS
pm.test("Dog have age property", function () {
 pm.expect(resp_p.family.pets.dog).to.have.property("age");
});
```
11. Проверить, что параметр name имеет значение Luky

```JS
pm.test("Dog is name Luky", function () {
 pm.expect(dog_name).to.eql("Luky");
});
```
12. Проверить, что параметр age имеет значение 4

```JS
pm.test("Dog is 4 year", function () {
 pm.expect(dog_age).to.eql(4);
});
```
Результаты тестов:

![](https://github.com/Sawa-solo/Postman/blob/49d8fea2848ac1665a0673d449efcb24bd2e4526/screens/tests%20results%20object_info_3.png)


> ## Задание № 4

Отправить запрос на URL: http://162.55.220.72:5005/object_info_4 

Метод: GET

Параметры: см. Задание № 2

1. Проверить, что статус код 200

```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Спарсить response body в json

```JS
let resp_p = pm.response.json();
```
3. Спарсить request.

```JS
let req_p = pm.request.url.query.toObject();
```
4. Создать переменные для данных

```JS
let req_name = req_p.name
let resp_name = resp_p.name

let req_age = + req_p.age
let resp_age = resp_p.age

let req_salary = + req_p.salary
let resp_salary = resp_p.salary

let resp_salary_0 = resp_p.salary [0][0]
```

5. Проверить, что name в ответе равно name в request (name забрать из request)

```JS
pm.test("Name", function () {
    pm.expect(req_p.name).to.eql(resp_p.name);
});
```
6. Проверить, что age в ответе равно age из request (age забрать из request)

```JS
pm.test("Age", function () {
    pm.expect(+ req_p.age).to.eql(resp_p.age);
});
```
7. Вывести в консоль параметр salary из request

```JS
console.log("req_salary = " + req_salary)
```
8. Вывести в консоль параметр salary из response

```JS
console.log(resp_p.salary)
```
9. Вывести в консоль 0-й элемент параметра salary из response

```JS
console.log(resp_p.salary [0])
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response

```JS
console.log(resp_p.salary [1])
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response

```JS
console.log(resp_p.salary [2])
```

![](https://github.com/Sawa-solo/Postman/blob/854506f4a3e93d6d3f3beea152c4f185b01f8c58/screens/console%20object_info_4.png)

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request)

```JS
pm.test("Salary 1", function () {
    pm.expect(+ req_p.salary).to.eql(resp_p.salary[0]);
});
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request)

```JS
pm.test("Salary 2", function () {
    pm.expect(req_p.salary*2).to.eql(+ resp_p.salary[1]);
});
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request)

```JS
pm.test("Salary 3", function () {
    pm.expect(req_p.salary*3).to.eql(+ resp_p.salary[2]);
});
```

15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary

18. Передать в окружение переменную name

```JS
 pm.environment.set("name", "Masha")
```
19. Передать в окружение переменную age

```JS
 pm.environment.set("age", 30)
```
20. Передать в окружение переменную salary

```JS
 pm.environment.set("salary", 700)
```

![](https://github.com/Sawa-solo/Postman/blob/c0f73464e1a32d7f20d807f6ff397fc342b1fcee/screens/environments.png)

Результаты тестов:

![](https://github.com/Sawa-solo/Postman/blob/3a99620f199c7bf21707ce3647138c1b80957b0a/screens/tests%20results%20object_info_4.png)


> ## Задание № 5

1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name

![]()

4. Отправить запрос на URL методом POST: http://162.55.220.72:5005/user_info_2

5. Проверить, что статус код 200
```JS
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
6. Спарсить response body в json
```JS
let resp_f = pm.response.json();
```
7. Спарсить request
```JS
let req_f = request.data
```
8. Создать переменные для данных
```JS
let req_salary = + req_f.salary
let req_age = + req_f.age
let resp_age = resp_f.person.u_age
let resp_start_qa_salary = resp_f.start_qa_salary
let resp_salary = resp_f.person.u_name[1]
let resp_qa_salary_after_6_months = resp_f.qa_salary_after_6_months
let resp_qa_salary_after_12_months = resp_f.qa_salary_after_12_months
let resp_u_salary_5_years = resp_f.person.u_salary_5_years
let resp_qa_salary_after_1_5_year = resp_f["qa_salary_after_1.5_year"]
let resp_qa_qa_salary_after_3_5_years = resp_f["qa_salary_after_3.5_years"]
```
9. Проверить, что json response имеет параметр start_qa_salary
```JS
pm.test("Have start_qa_salary property", function () {
    pm.expect(resp_f).to.have.property("start_qa_salary");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_6_months
```JS
pm.test("Have qa_salary_after_6_months property", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_6_months");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months
```JS
pm.test("Have qa_salary_after_12_months property", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_12_months");
});
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```JS
pm.test("Have qa_salary_after_1.5_year property", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_1.5_year");
});
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```JS
pm.test("Have qa_salary_after_3.5_years property", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_3.5_years");
});
```
13. Проверить, что json response имеет параметр person
```JS
pm.test("Have person property", function () {
    pm.expect(resp_f).to.have.property("person");
});
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request)
```JS
pm.test("Check start_qa_salary", function () {
    pm.expect(req_salary).to.eql(resp_start_qa_salary);
});
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request)
```JS
pm.test("Check qa_salary_after_6_months", function () {
    pm.expect(req_salary * 2).to.eql(resp_qa_salary_after_6_months);
});
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request)
```JS
pm.test("Check qa_salary_after_12_months", function () {
    pm.expect(req_salary * 2.7).to.eql(resp_qa_salary_after_12_months);
});
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request)
```JS
pm.test("Check qa_salary_after_1.5_year", function () {
    pm.expect(req_salary * 3.3).to.eql(resp_f["qa_salary_after_1.5_year"]);
});
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request)
```JS
pm.test("Check qa_salary_after_3.5_years", function () {
    pm.expect(req_salary * 3.8).to.eql(resp_f["qa_salary_after_3.5_years"]);
});
```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request)
```JS
pm.test("person u_name", function () {
 pm.expect(req_salary).to.eql(resp_salary);
});
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request)
```JS
pm.test("Age", function () {
 pm.expect(req_age).to.eql(resp_age);
});
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request)
```JS
pm.test("Check u_salary_5_years", function () {
    pm.expect(req_salary *4.2).to.eql(resp_u_salary_5_years);
});
```

![]()
