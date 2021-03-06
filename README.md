본 튜토리얼은 Oracle Container Engine, Oracle Container Image Registry, Oracle Container Pipeline 을 이해하기 위한 기본 튜토리얼 입니다.


1. Container Image Build
    <pre><code> > docker build --tag app:0.1 .</code></pre>

2. docker image push to Oracle Container Image Registry
    <pre><code> > docker login phx.ocir.io
    - username : isheejong@gmail.com
    - password : ********
    - auth token : ************
    - repository : heejong/app</code></pre>

3. docker image 확인 및 Push
    <pre><code> > docker images
    > docker tag 6a4420b2d5d6 phx.ocir.io/astom2018/heejong/app:0.1
    > docker push phx.ocir.io/astom2018/heejong/app:0.1 </code></pre>

4. Kubernetes Namespace 생성
    <pre><code> > kubectl create webapp-ns.yaml</code></pre>

5. Kubernetes에 배포 시 Oracle Container Image Registry에 접근 하기 위한 Secret 정보를 Kubernetes 에 등록 합니다.
    <pre><code> > kubectl create secret -n demo docker-registry ocirsecret --docker-server=phx.ocir.io --docker-username='astom2018/isheejong@gmail.com' --docker-password=****************' 
    --docker-email='isheejong@gmail.com'</code></pre>

6. Kubernetes 에 Deployment 를 배포 합니다.
    <pre><code> > kubectl create -f webapp-dep.yaml</code></pre>

7. Kubernetes 에 Service 를 배포 합니다.
    <pre><code> > kubectl create -f webapp-svc.yaml</code></pre> 
