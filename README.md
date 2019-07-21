# piphonom_platform
piphonom Platform repository

Выполнено ДЗ#1

Установлена локальная инфраструктура kubernetes - minikube
Установлен kubectl

Создан docker образ для основного контейнера
Настроен тестовый Pod, состоящий из основного контейнера и init контейнера

Выполнение ДЗ#2

0. Создаем ServiceAccount bob
  kubectl apply -f kubernetes-security/task01/01-bob-sa.yaml
1. Получение информации по ServiceAccount с именем bob
   kubectl get serviceaccounts bob -o yaml
2. В поле secrets видим:
  secrets:
- name: bob-token-954fk
3. Создаем новый контекст для использования SA bob
   kubernetes-security/config-use-bob-sa
4. kubectl get secret bob-token-954fk -o yaml
5. Ищем ca.crt и заполняем этим значением поле client-key-data в kubernetes-security/config-use-bob-sa
6. kubectl describe secret bob-token-954fk
7. Ищем поле token и заполняем этим значением поле token в kubernetes-security/config-use-bob-sa
8. Прописываем kubernetes-security/config-use-bob-sa в KUBECONFIG
   export KUBECONFIG=~/.kube/config:.../kubernetes-security/config-use-bob-sa
9. Проверяем, что kubectl видит новый контекст
   kubectl config get-contexts
9. Переключаем контекст на minikube-bob-sa-context
   kubectl config use-context minikube-bob-sa-context
10. Теперь все команды kubectl выполняются от имени bob