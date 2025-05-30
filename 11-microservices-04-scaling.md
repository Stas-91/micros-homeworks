
# Домашнее задание к занятию «Микросервисы: масштабирование» Помельников Станислав

Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.

## Задача 1: Кластеризация

Предложите решение для обеспечения развёртывания, запуска и управления приложениями.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- поддержка контейнеров;
- обеспечивать обнаружение сервисов и маршрутизацию запросов;
- обеспечивать возможность горизонтального масштабирования;
- обеспечивать возможность автоматического масштабирования;
- обеспечивать явное разделение ресурсов, доступных извне и внутри системы;
- обеспечивать возможность конфигурировать приложения с помощью переменных среды, в том числе с возможностью безопасного хранения чувствительных данных таких как пароли, ключи доступа, ключи шифрования и т. п.

Обоснуйте свой выбор.

### Решение 1

Для обеспечения развёртывания, запуска и управления приложениями с соблюдением всех перечисленных требований, можно использовать **Kubernetes** с рядом дополнительных компонентов:

**Компоненты решения**

**1. Контейнеризация: Docker / Podman**

* Используются для упаковки приложений в изолированные контейнеры.
* Позволяют обеспечить переносимость и согласованность среды исполнения.

**2. Оркестрация: Kubernetes**

* Управляет контейнерами, обеспечивает их запуск, масштабирование и отказоустойчивость.
* Поддерживает:

  * Контейнеры (через Pod'ы),
  * Горизонтальное масштабирование,
  * Обнаружение сервисов (Service),
  * Изоляцию ресурсов (Namespace, NetworkPolicy),
  * Конфигурацию (ConfigMap, Secret).

**3. Сетевое взаимодействие и маршрутизация: Ingress + Ingress Controller (например, NGINX, Traefik)**

* Обеспечивает маршрутизацию HTTP/HTTPS-запросов к нужным сервисам.
* Поддерживает балансировку нагрузки.
* Можно настроить HTTPS, TLS termination и правила доступа.

**4. Автоматическое масштабирование: Horizontal Pod Autoscaler (HPA)**

* Использует метрики (CPU, память, пользовательские метрики) для автоматического масштабирования подов.

**5. Секреты и переменные среды: ConfigMap и Secret**

* ConfigMap — для хранения не чувствительных переменных среды.
* Secret — для хранения паролей, токенов, ключей.
* Могут быть монтированы как файлы или переданы как переменные среды.

**6. Изоляция ресурсов: Namespace, RBAC, NetworkPolicy**

* Namespace — логическая изоляция приложений.
* RBAC — разграничение прав доступа.
* NetworkPolicy — контроль сетевого взаимодействия между подами.

**7. CI/CD (опционально): ArgoCD / GitLab CI / Jenkins**

* Обеспечивает автоматическое развёртывание приложений в кластер.
* Поддержка GitOps-подхода.



**Соответствие требованиям**

| Требование                           |  Решение                             |
| ------------------------------------ |  -------------------------------------- |
| Поддержка контейнеров                |  Docker, Kubernetes                     |
| Обнаружение сервисов и маршрутизация |  Kubernetes Service, Ingress Controller |
| Горизонтальное масштабирование       |  Kubernetes + HPA                       |
| Автоматическое масштабирование       |  HPA, KEDA                              |
| Разделение ресурсов                  |  Namespace, RBAC, NetworkPolicy         |
| Конфигурация через переменные среды  |  ConfigMap, Secret                      |


---


## Задача 2: Распределённый кеш * (необязательная)

Разработчикам вашей компании понадобился распределённый кеш для организации хранения временной информации по сессиям пользователей.
Вам необходимо построить Redis Cluster, состоящий из трёх шард с тремя репликами.

### Схема:

![11-04-01](https://user-images.githubusercontent.com/1122523/114282923-9b16f900-9a4f-11eb-80aa-61ed09725760.png)

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
