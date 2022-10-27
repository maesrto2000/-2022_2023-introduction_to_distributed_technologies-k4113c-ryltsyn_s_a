University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2022/2023  
Group: K4113c    
Author: Ryltsyn Stepan Alexeyevich  
Lab: Lab1  
Date of create: 01.10.2022    
Date of finished:  


# Создание манифеста  
## Ход работы 
1. Создаем файл манифеста, где указываем образ `vault`  
2. Создаем под с помощью команды 
```
kubectl apply -f pod.yml
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



