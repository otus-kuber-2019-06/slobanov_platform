# slobanov_platform

slobanov Platform repository

* kubernetes-into
  * `web/` - sources (`Dockerfile` and `nginx.conf`) for docker image of nginx, serving static content from `/app` on `8000` port. Builded image can be pulled from [Docker Hub](https://cloud.docker.com/):
  
  ```bash
    $ docker pull slobanov/kubernetes-intro:1.0.0
  ```

  * `web-pod.yaml` - k8s manifest, describing Pod running `slobanov/kubernetes-intro:1.0.0`, bootstaped by init container which generates sample `index.html`.

* kubernetes-security
  * task01
    * `01-bob-accout.yaml` - создание `ServiceAccount` `bob`.
    * `02-bob-to-admin-binding.yaml` - привязка роли `admin` в рамках всего кластера к `bob`.
    * `03-dave-account.yaml` - создание `ServiceAccount` `dave`.
  * task02
    * `01-prometheus-ns.yaml` - создание `Namespace` `prometheus`.
    * `02-carol-account.yaml` - создание `ServiceAccount` `carol` в `Namespace`'е `prometheus`.
    * `03-pod-reader-cluster-role.yaml` - создание `ClusterRole` `pod-reader`, позволяющую делать `get`, `list`, `watch` в отношении `Pods` всего кластера.
    * `04-prometheus-to-pod-reader-binding.yaml` - привязка роли `pod-reader` ко всем `ServiceAccount`'ам из `Namespace`'а `prometheus`.
  * task03
    * `01-dev-namespace.yaml` - создание `Namespace` `dev`.
    * `02-jane-account.yaml` - создание `ServiceAccount` `jane` в `Namespace`'е `dev`.
    * `03-jane-to-admin-binding.yaml` - привязка роли `admin` к `jane` в рамках `Namespace`'а `dev`.
    * `04-ken-account.yaml` -  создание `ServiceAccount` `ken` в `Namespace`'е `dev`.
    * `05-ken-to-view-binding.yaml` - привязка роли `view` к `ken` в рамках `Namespace`'а `dev`.

-----
Sergey Lobanov
[s.y.lobanov@yandex.ru](mailto:s.y.lobanov@yandex.ru?Subject=otus-springframework-2018-11-slobanov)
