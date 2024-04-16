# k8s-start-with-container-practice
[쿠버네티스 입문:90가지 예제로 배우는 컨테이너 관리 자동화 표준] 3장 쿠버네티스로 컨테이너 시작하기 단원을 공부한 후, 이해를 점검할 수 있는 실습입니다. 

3장에서는 Deployment 설정이 담긴 템플릿으로 컨테이너를 실행하는 방법을 배웠습니다. **Pods, Deployments, Services의 개념을 명확히 알고, 원하는대로 컨테이너를 설정할 수 있도록 템플릿 작성을 연습해봅시다.**

## 진행 순서

✅ **3장 쿠버네티스로 컨테이너 시작하기** 단원의 내용을 이해하고, 교재의 실습을 빠짐없이 수행하며 개념이 실제로 어떻게 적용되는지 확인한다. 3장의 내용 정리와 실습 과정을 [이곳](https://rumoszin.github.io/posts/k8s-container-start/)에서 확인할 수 있다. 

✅ 원하는 경로에 `Deployment` 디렉터리를 만들고 `nginx-app.yml` 파일을 만든다.

✅ 현재 레포지토리의 `sample_code.yml`의 내용을 `nginx-app.yml`에 작성한다.

✅ `nginx-app.yml` 파일을 실행했을 때 결과 화면 1과 같이 나오도록, 파일을 적절히 수정하라.

✅ 결과 화면 1이 적절히 나왔다면, 결과 화면 2와 같이 나오도록 하는 명령어는 무엇일지 작성하라.

## 결과 화면 1

```shell
$ deployment> kubectl apply -f nginx-app.yaml
deployment.apps/nginx-app-deployment-perfect created

$ deployment> kubectl get pods
NAME                                            READY   STATUS    RESTARTS   AGE
echoserver                                      1/1     Running   0          4h29m
nginx-app-deployment-perfect-5bbc997b77-blshn   1/1     Running   0          12s
nginx-app-deployment-perfect-5bbc997b77-xwmwj   1/1     Running   0          12s
yunjinserver                                    1/1     Running   0          4h28m

$ deployment> kubectl get deployments
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
nginx-app-deployment-perfect   2/2     2            2           24s

$ deployment> kubectl expose deployment nginx-app-deployment-perfect --type=NodePort             
service/nginx-app-deployment-perfect exposed

$ deployment> kubectl get service
NAME                           TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
echoserver                     NodePort    10.106.213.33   <none>        8080:32760/TCP   4h43m
kubernetes                     ClusterIP   10.96.0.1       <none>        443/TCP          26d
nginx-app-deployment-perfect   NodePort    10.97.250.254   <none>        80:31628/TCP     15s
yunjinserver                   NodePort    10.107.50.145   <none>        8080:32614/TCP   4h43m
```

## 결과 화면 2
```shell
$ deployment> kubectl get pods [적절한 옵션을 작성하시오.]
echoserver 
nginx-app-good 
nginx-app-good 
yunjinserver
```
