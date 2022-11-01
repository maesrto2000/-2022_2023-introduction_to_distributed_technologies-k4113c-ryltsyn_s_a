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
3. Делаем пробрас портов и подключаемся к контейнерам через браузер    
 ```
kubectl port-forward svc/indfr-service 80:80
```   
Можем увидеть значения наших переменных в браузере и посмотреть подробную информацию о репликах в Lens. 
## Схема
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr1/img/lr1.png"></div> 







