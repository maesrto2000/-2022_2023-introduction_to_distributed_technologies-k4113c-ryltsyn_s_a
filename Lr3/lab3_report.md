University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2022/2023  
Group: K4113c    
Author: Ryltsyn Stepan Alexeyevich  
Lab: Lab3  
Date of create: 17.11.2022    
Date of finished: 


# Сертификаты и "секреты" в Minikube, безопасное хранение данных.
## Ход работы 
1. Создаем деплоймент и конфигмап 
```
kubectl apply -f cm.yaml -f deploy.yaml  
``` 
Просматриваем конфигмап в ленс:
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/cm_lens.png"></div><br>  
Просматриваем значения переменных и делаем проброс портов:
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/env.png"></div><br>
Результат отображается в браузере - перменные удалось успешно передать с помощью конфигмапа:
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/cm_lens.png"></div><br>
2. Включаем ingress  
    
```
minikube addons enable ingress   
```

Устанавливаем ingress controller
```
kubectl apply -f https://projectcontour.io/quickstart/contour.yaml
``` 
После чего создаем файл сервиса и ингресса, вносим изменения в деплоймент и выполняем команду:
```
kubectl apply -f cm.yaml -f deploy.yaml -f service.yaml -f ingress.yaml    
``` 
Вносим в hosts minikube ip и доменное имя, которое указано в ингрессе. Выполняем команду:

```
minikube tunnel
```

Проверяем работоспособность нашего ингресса - вводим это доменное имя в браузер и видим, что все работает корректно - наш ингресс смог достучаться до сервиса, а сервис до пода:
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/photo_2022-11-18_23-30-53.jpg"></div><br>

Генерируем файлики `tls.key` и `tls.crt` для нашего доменного имени 

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=onetestexamle.com"
``` 
Создаем секрет 

```
kubectl create secret tls test-tls --key="tls.key" --cert="tls.crt"
```
Модифицируем ингресс: добавляем имя секрета и поле hosts, обновляем ингресс и производим обращение по https 
```
curl --cacert tls.crt https://onetestexamle.com  
``` 

Проверка наличия сертификата
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/photo_2022-11-19_00-59-29.jpg"></div><br>
 
## Схема
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/v1.png"></div> 







