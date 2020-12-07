# Выполнено ДЗ №2

 - [*] Основное ДЗ
 - [*] Задание со *

## Что сделано:
 - Изучена документация, описывающая работу системных подов.
   kubelet управляет функционированием kube-scheduler, kube-controller-manager, kube-apiserver, etcd, они описаны в манифестах /etc/kubernetes/manifests
   (https://kubernetes.io/docs/concepts/workloads/pods/#static-pods)
   kube-proxy контролируется, как DaemonSet на каждой ноде кластера (https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)
   coredns запущен как Deployments c ReplicaSet (https://kubernetes.io/docs/concepts/workloads/controllers/deployment)
 - Собран docker-образ web c web-сервером nginx.
 - Создан манифест pod'а, создающий init-cintainer c wget для получения контента извне, добавлен общий том emptyDir, доступный для обоих контейнеров, который перед запуском web-сервера загружает статический контент.
 - kubectl port-forward для работы с подом в режиме отладки
 - Собран контейнер hipster-frontend
 - С помощью ad-hock команды контейнер запущен в pod'е kubernetes, также был сгенерирован первичный манифест пода.
 - В манифест были добавлены переменнеы окружения, необходимые для запуска контейнера.

## Как запустить проект:
 - kubectl apply -f web-pod.yaml для запуска пода web со статичной станицей
 - kubectl port-forward --address localhost pod/web 8000 для проверки доступности страницы

## Как проверить работоспособность:
 - wget http://localhost:8000 -O - > /dev/null

## PR checklist:
 - [*] Выставлен label с темой домашнего задания
