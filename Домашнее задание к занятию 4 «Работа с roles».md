# Домашнее задание к занятию 4 «Работа с roles»
# Предварительное
Репозитории добавлены, в Settings добавила SSH public key 

1. Файл requirements.yml 

 - src: git@github.com:Maybe-R/ansible-clickhouse.git
    scm: git
    version: "1.13"
    name: clickhouse 

2. С помощью ansible-galaxy role init vector-role создала роль vector-role.

3. Заполнила новую роль, разнес переменные между vars и default

4. Перенесла шаблоны конфигов в templates роли.

5. Повторил все шаги для роли lighthouse-role.

6. Репозитории ролей. Описание ролей прописано в файлах с наименованием README.md:
https://github.com/Maybe-R/vector-role-main.git 
https://github.com/Maybe-R/lighthouse-role-main.git 

7. Ссылка на репозиторий - https://github.com/Maybe-R/playbook.git

---
