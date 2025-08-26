
# Домашнее задание к занятию 11 «Teamcity» - Морозов Александ

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Основная часть

1. Создайте новый проект в teamcity на основе fork.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/1.png)

2. Сделайте autodetect конфигурации.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/2.png)

3. Сохраните необходимые шаги, запустите первую сборку master.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/3.png)

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/4.png)

5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/5.png)

6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/6.png)

8. Мигрируйте `build configuration` в репозиторий.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/7.png)

9. Создайте отдельную ветку `feature/add_reply` в репозитории.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/8.png)

10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/9.png)

11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/10.png)

12. Сделайте push всех изменений в новую ветку репозитория.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/11.png)

13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/12.png)

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/13.png)

17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.

![alt text](https://github.com/Mars12121/09-ci-05-teamcity/tree/master/img/14.png)
![alt text](https://github.com/Mars12121/hw-11-02/blob/main/img/1.png)

18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.

https://github.com/Mars12121/09-ci-05-teamcity/tree/master

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
