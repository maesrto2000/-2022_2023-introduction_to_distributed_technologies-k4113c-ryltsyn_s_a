University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2022/2023  
Group: K4113c    
Author: Ryltsyn Stepan Alexeyevich  
Lab: Lab4  
Date of create: 23.11.2022    
Date of finished: 


# Сети связи в Minikube, CNI и CoreDNS
## Ход работы 
1. Исходя из инструкции создадим две ноды и при запуске укажем плагин Calico
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/1.png"></div><br>  
2. Далее необходимо установить calicoctl как модуль кубернетис

```
kubectl apply -f calicoctl.yaml  
``` 
На скриншоте ниже видно, что установка прошла успешно
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/2.png"></div><br> 
3. Создаем манфест ippool, где указываем ip адреса и зоны.

```
kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - <  C:\Programming\kubernetes\lr4\ippool.yaml 
``` 
В результате успешно создались два ippool-а
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/5.png"></div><br> 
Посмотрим более подробно
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/6.png"></div><br> 
4. Далее запукаем деплоймент, конфигмап и сервес. Ждем, когда поды будут запущены. Можем видеть, что поды получили корректные адреса. 
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/7.png"></div><br> 
В Ленс видно, что названию имени сервиса соответствую IP, полученные подами. 
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/13.png"></div><br>
5. Пробрасывем порты и смотрим результат в браузере 
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/s2.png"></div><br>
Обновлем страницу
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/s1.png"></div><br>

6. Пингуем поды, получаем ответ - все работает правильно. 
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/10.png"></div><br>
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr4/img/11.png"></div><br>

## Схема
<div align = "center"><img src="https://github.com/maesrto2000/-2022_2023-introduction_to_distributed_technologies-k4113c-ryltsyn_s_a/blob/main/Lr3/img/v1.png"></div> 







