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
* kubernetes-networks
  * `coredns-svc-tcp-lb.yaml` - `LoadBalancer` `Service`, exposing `kute-system`'s `core-dns` `Pods` on TCP:53 for usage outside of the cluster.
  * `coredns-svc-udp-lb.yaml` - `LoadBalancer` `Service`, exposing `kute-system`'s `core-dns` `Pods` on UDP:53 for usage outside of the cluster.
  * `dashboard-ingress.yaml` - `Ingress` for routing trafic to kubernetes-dashboard `Service`.
  * `metallb-config.yaml` - `ConfigMap`, used for `Metallb` configuration.
  * `nginx-lb.yaml` - `LoadBalancer` `Service`, exposing NGINX Ingress controller.
  * `web-deploy.yaml` - `Deployment` for `web` application, described in kubernetes-into section.
  * `web-ingress.yaml` - `Ingress` for accessing `web-svc` `Service`.
  * `web-svc-cip.yaml` - `ClusterIP` `Service` for `web` application `Pods`.
  * `web-svc-headless-yaml` - headless `Service` for `web` application `Pods`.
  * `web-svc-lb.yaml` - `LoadBalancer` `Service` for `web` application `Pods`.
  * `canary/` - `Deployment`, `Service` and `Ingress` for canary deployment pattern.
* kubernetes-volumes
  * minio-sercret.yaml - `Sercret`, storing accessKey and secretKey for minio application in base64.
  * minio-statefulset.yaml - `StatefulSet` for running minio.
  * minio-headless-service.yaml - headless `Service` for minio `Pods`.
* kubernetes-storage
  * cluster/cluster.yaml - cluster config for kind for VolumeSnapshotDataSource support.
  * hw/01-storage-class.yaml - `StorageClass`, describing CSI hostpath provisioner.
  * hw/02-storage-pvc.yaml - `PersistentVolumeClaim` for binding with hostpath `PVs`, provided by `csi-hostpath-sc`.
  * hw/03-storage-pod.yaml - `Pod` with volume, mouted to `/data`, claimed from storage-pvc.

-----
Sergey Lobanov
[s.y.lobanov@yandex.ru](mailto:s.y.lobanov@yandex.ru?Subject=otus-springframework-2018-11-slobanov)
