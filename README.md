# Django site

Докеризированный сайт на Django для экспериментов с Kubernetes.

## Как запустить dev-версию

Запустите манифест [`django-app.yaml`](./django-app.yaml)
```shell-session
kubectl apply -f django-app.yaml
```
#### При первом запуске проекта сделайте миграции и создайте суперпользователя:
Посмотрите имя подов приложения:
```shell-session
kubectl get pods
```
Подключитесь к любому из подов:
```shell-session
kubectl exec -it <имя-пода> -- /bin/bash
```
Запустите миграции:
```shell-session
python manage.py migrate
```
Создайте суперпользователя:
```shell-session
python manage.py createsuperuser
```

Запустите манифест [`django-migrate-job.yaml`](./django-migrate-job.yaml)
```shell-session
kubectl apply -f django-migrate-job.yaml
```

Запустите манифест [`django-clearsessions.yaml`](./django-clearsessions.yaml)
```shell-session
kubectl apply -f django-createsuperuser-job.yaml
```
