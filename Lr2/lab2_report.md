University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2022/2023  
Group: K4113c    
Author: Ryltsyn Stepan Alexeyevich  
Lab: Lab2  
Date of create: 14.10.2022    
Date of finished:  


# Развертывание веб сервиса в Minikube, доступ к веб интерфейсу сервиса. Мониторинг сервиса.  
## Ход работы 
1. Создаем файлы деплоймента (указываем количество реплик) и сервиса. 
```
kubectl apply -f deploy.yaml
```  
```
kubectl apply -f service.yaml
``` 
2. Просматриваем созданные сервисы  
```
kubectl get services
```  
3. Проверяем статус пода  
 ```
kubectl get pods
```   
4. Создаем сервис 
 ```
minikube kubectl -- expose pod vault --type=NodePort --port=8200
```
5. Прокидываем порт для доступа к сервису 
 ```
minikube kubectl -- port-forward service/vault 8200:8200
```
## Схема v1.0
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr1/img/lr1.png"></div> 


## Схема v1.1
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr1/img/v1.2.png"></div>




