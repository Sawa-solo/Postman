# Homework 1

## Создать запросы в Postman

Protocol: http

IP: 162.55.220.72

Port: 5005

EP_1

Method: GET

EndPoint: /get_method

request url params: 

 name: str
 age: int

```JS
response: 
[
    “Str”,
    “Str”
]
```
![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_1.jpg)
==================

EP_2

Method: POST

EndPoint: /user_info_3

request form data: 

 name: str
 age: int
 salary: int
 
 
```JS
response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'u_salary_1_5_year': salary * 4}}

```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_2.png)
==================

EP_3

Method: GET

EndPoint: /object_info_1

request url params: 

 name: str
 age: int
 weight: int
```JS
response: 
{'name': name,
          'age': age,
          'daily_food': weight * 0.012,
          'daily_sleep': weight * 2.5}

```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_3.jpg)
==================

EP_4

Method: GET

EndPoint: /object_info_2

request url params: 

 name: str
 age: int
 salary: int
 
```JS
response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }

```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_4.jpg)
==================

EP_5

Method: GET

EndPoint: /object_info_3

request url params: 

 name: str
 age: int
 salary: int

```JS
response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'pets': {'cat':{'name':'Sunny',
                                     'age': 3},
                              'dog':{'name':'Luky',
                                     'age': 4}},
                     'u_salary_1_5_year': salary * 4}
          }

```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_5.1.jpg)

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_5.2.jpg)
==================

EP_6

Method: GET

EndPoint: /object_info_4

request url params: 

 name: str
 age: int
 salary: int
 
```JS
response: 
{'name': name,
          'age': int(age),
          'salary': [salary, str(salary * 2), str(salary * 3)]}

```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/EP_6.jpg)
==================

EP_7

Method: POST

EndPoint: /user_info_2

request form data: 

 name: str
 age: int
 salary: int

```JS
response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
```

![](https://github.com/Sawa-solo/Postman/blob/079f4ffe4d26d033434a38b8435ef5d2c427f67b/screens/ER_7.jpg)
