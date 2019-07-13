# slobanov_platform

slobanov Platform repository

* kubernetes-into
  * `web/` - sources (`Dockerfile` and `nginx.conf`) for docker image of nginx, serving static content from `/app` on `8000` port. Builded image can be pulled from [Docker Hub](https://cloud.docker.com/):
  
  ```bash
    $ docker pull slobanov/kubernetes-intro:1.0.0
  ```

  * `web-pod.yaml` - k8s manifest, describing Pod running `slobanov/kubernetes-intro:1.0.0`, bootstaped by init container which generates sample `index.html`.

-----
Sergey Lobanov
[s.y.lobanov@yandex.ru](mailto:s.y.lobanov@yandex.ru?Subject=otus-springframework-2018-11-slobanov)
