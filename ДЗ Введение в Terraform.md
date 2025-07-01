1.	Перейдите в каталог src. Скачайте все необходимые зависимости, использованные в проекте.

![image](https://github.com/user-attachments/assets/b34c6d7f-8d48-44b5-8741-525e18f6478a)

2.	Изучите файл .gitignore. В каком terraform-файле, согласно этому .gitignore, допустимо сохранить личную, секретную информацию?(логины,пароли,ключи,токены и тд)

![image](https://github.com/user-attachments/assets/bcad464b-4172-4b00-a5fa-27474d997723)

3.	Выполните код проекта. Найдите в state-файле секретное содержимое созданного ресурса random_password, пришлите в качестве ответа конкретный ключ и его значение.

 
![image](https://github.com/user-attachments/assets/a2ee82e6-c730-4860-a2b8-ca4f784a2f11)

![image](https://github.com/user-attachments/assets/38de2ea6-e076-4845-8223-81a122525fd3)

 
Ключ находится в поле “result” 
 
![image](https://github.com/user-attachments/assets/fe7905cf-4bcf-4b99-8068-fde1e7638879)


4.	Раскомментируйте блок кода, примерно расположенный на строчках 29–42 файла main.tf. Выполните команду terraform validate. Объясните, в чём заключаются намеренно допущенные ошибки. Исправьте их.

![image](https://github.com/user-attachments/assets/2800e123-a6a1-45e2-847e-eab306d2f6a5)

 
Исправления
1)	Не было указано наименование докер образа, которое должно было быть скачано
2)	Имя ресурса для формировании имени контейнера было указано неверно

 ![image](https://github.com/user-attachments/assets/df062283-6284-4833-ba66-4ce025f81de0)


5.	Выполните код. В качестве ответа приложите: исправленный фрагмент кода и вывод команды docker ps.
 
 ![image](https://github.com/user-attachments/assets/15e7536f-49f0-4da1-b10a-64747b9441a7)

![image](https://github.com/user-attachments/assets/43ceaafa-dba5-4bab-9652-5c3c0ac883d4)


6.	Замените имя docker-контейнера в блоке кода на hello_world. Не перепутайте имя контейнера и имя образа. Мы всё ещё продолжаем использовать name = "nginx:latest". Выполните команду terraform apply -auto-approve. Объясните своими словами, в чём может быть опасность применения ключа -auto-approve. Догадайтесь или нагуглите зачем может пригодиться данный ключ? В качестве ответа дополнительно приложите вывод команды docker ps.
 
![image](https://github.com/user-attachments/assets/5ad732c5-e7c1-4daa-b411-e5e06403ff1d)

![image](https://github.com/user-attachments/assets/1245c617-bff1-4deb-8b32-4a431370fae7)
 

Опасность применения ключа -auto-approve заключается в том, что если были допущены ошибки, то сборка будет все равно выполнена
Данный ключ будет актуален для автоматизации развёртывания инфраструктуры 


7.	Уничтожьте созданные ресурсы с помощью terraform. Убедитесь, что все ресурсы удалены. Приложите содержимое файла terraform.tfstate

 ![image](https://github.com/user-attachments/assets/2f8bda07-9e21-463d-8a60-e191f6874a70)



Объясните, почему при этом не был удалён docker-образ nginx:latest. Ответ ОБЯЗАТЕЛЬНО НАЙДИТЕ В ПРЕДОСТАВЛЕННОМ КОДЕ, а затем ОБЯЗАТЕЛЬНО ПОДКРЕПИТЕ строчкой из документации terraform провайдера docker. (ищите в классификаторе resource docker_image )
https://docs.comcloud.xyz/providers/kreuzwerker/docker/latest/docs/resources/image
 ![image](https://github.com/user-attachments/assets/25107cbe-3624-42d9-95aa-124590abcb5f)

 ![image](https://github.com/user-attachments/assets/b398e262-44c6-41c0-82d4-c8626213ded4)



