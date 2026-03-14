# УРОЧЕН ПЛАН №13
## УЧЕБНА ПРАКТИКА: КОМПЮТЪРНИ АРХИТЕКТУРИ И ОПЕРАЦИОННИ СИСТЕМИ
### XII КЛАС

---

## 1. ОСНОВНИ ДАННИ

- **Училище:**	128-мо СУ "Алберт Айнщайн", гр.София
- **Клас:** XII клас
- **Предмет:** Учебна практика: Компютърни архитектури и операционни системи
- **Тема на урока:** Kubernetes orchestration
- **Дата:** ____________
- **Час:** ____________
- **Продължителност:** 90 минути (2 учебни часа)
- **Тип урок:** Комбиниран
- **Място на провеждане:** Компютърна лаборатория

---

## 2. ЦЕЛИ И ЗАДАЧИ

### ОБРАЗОВАТЕЛНИ ЦЕЛИ:
1. Учениците да разберат концепцията за container orchestration
2. Да усвоят основните Kubernetes компоненти и архитектура
3. Да научат key Kubernetes обекти и ресурси
4. Да разберат как Kubernetes управлява контейнери
5. Да могат да deploy базови приложения в Kubernetes

### ВЪЗПИТАТЕЛНИ ЦЕЛИ:
1. Формиране на разбиране за cloud-native архитектури
2. Възпитаване на системно мислене за distributed системи
3. Развиване на интерес към DevOps и SRE практики
4. Изграждане на навици за декларативна конфигурация

### РАЗВИВАЩИ ЦЕЛИ:
1. Развитие на умения за управление на сложни системи
2. Усъвършенстване на debugging в distributed среда
3. Формиране на scalability мислене
4. Развитие на cloud engineering компетенции

---

## 3. СЪДЪРЖАНИЕ

### ОСНОВНИ ЗНАНИЯ И УМЕНИЯ:

#### Знания:
- Container orchestration нужда и предимства
- Kubernetes архитектура: control plane, nodes
- Pods, Deployments, Services, Ingress
- Kubernetes networking и storage
- Scaling, self-healing, rolling updates
- YAML манифести и kubectl команди

#### Умения:
- Инсталиране на локален Kubernetes (minikube/kind)
- Работа с kubectl CLI
- Създаване на Kubernetes манифести
- Deploy и управление на приложения
- Debugging на pods и services
- Основен мониторинг и логове

### ВРЪЗКИ С ДРУГИ ПРЕДМЕТИ:

1. **Docker** - container технологии
2. **Мрежи** - service discovery, load balancing
3. **Distributed системи** - consensus, fault tolerance
4. **Cloud computing** - IaaS, PaaS концепции
5. **DevOps** - CI/CD, GitOps

---

## 4. МЕТОДИ И СРЕДСТВА

### МЕТОДИ НА ПРЕПОДАВАНЕ:
1. **Визуална презентация** на архитектурата
2. **Демонстрация** на kubectl операции
3. **Практическа работа** с minikube
4. **Incremental deployment** на приложение
5. **Problem-solving** със scaling и failures

### УЧЕБНИ СРЕДСТВА И МАТЕРИАЛИ:
1. **Софтуер:**
   - minikube или kind
   - kubectl CLI
   - Docker Desktop
   - k9s (optional)
   - VS Code с Kubernetes extension
   
2. **Хардуер:**
   - Компютри с минимум 8GB RAM
   - Virtualization enabled
   - Internet връзка
   
3. **Учебни материали:**
   - Kubernetes документация
   - YAML примери
   - Архитектурни диаграми

---

## 5. ХОД НА УРОКА

### **1. ОРГАНИЗАЦИОНЕН МОМЕНТ (5 минути)**

**Дейност на учителя:**
- Проверка на присъствието
- Проверка на minikube инсталация
- Въвеждащ въпрос: "Как управляваме 100 контейнера на 10 сървъра?"

**Дейност на учениците:**
- Стартиране на minikube: `minikube start`
- Проверка: `kubectl version`

### **2. АКТУАЛИЗАЦИЯ НА ЗНАНИЯТА (8 минути)**

**Дейност на учителя:**
- Преговор на Docker концепции

**Въпроси:**
1. Какво е Docker container?
2. Какви проблеми решава контейнеризацията?
3. Как scale-ваме single container?
4. Какво се случва ако container падне?

**The Need for Orchestration:**
```
Manual container management problems:
- Scheduling: Къде да run container?
- Scaling: Как да добавим още instances?
- Healing: Какво при failure?
- Networking: Как containers намират един друг?
- Updates: Как update-ваме без downtime?
```

### **3. НОВ МАТЕРИАЛ (47 минути)**

#### **Част 1: Kubernetes Overview (10 мин)**

**What is Kubernetes (k8s)?**
```
Kubernetes = Container Orchestration Platform
            (Greek: "Helmsman/Pilot")

Created by Google (2014)
Based on Borg/Omega experience
Open source (CNCF)
Industry standard for container orchestration

Key Features:
✓ Automated deployment
✓ Scaling (horizontal)
✓ Self-healing
✓ Service discovery
✓ Load balancing
✓ Storage orchestration
✓ Automated rollouts/rollbacks
✓ Secret/config management
```

**Kubernetes Architecture:**
```
┌─────────────── Control Plane ──────────────┐
│                                             │
│  ┌────────────┐  ┌─────────────────────┐  │
│  │ API Server │  │ Controller Manager   │  │
│  └─────┬──────┘  └──────────────────────┘  │
│        │                                    │
│  ┌─────┴──────┐  ┌─────────────────────┐  │
│  │    etcd    │  │     Scheduler       │  │
│  └────────────┘  └─────────────────────┘  │
└─────────────────────────────────────────────┘
                      │
    ┌─────────────────┼─────────────────┐
    │                 │                 │
┌───▼──── Node 1 ─────▼───┐  ┌──── Node 2 ────┐
│                         │  │                │
│ ┌─────────┐ ┌────────┐ │  │ ┌────────┐    │
│ │ kubelet │ │ kube-  │ │  │ │ kubelet│    │
│ └─────────┘ │ proxy  │ │  │ └────────┘    │
│             └────────┘ │  │                │
│ ┌─────────────────────┐│  │ ┌────────────┐│
│ │   Container Runtime  ││  │ │  Containers ││
│ │   ┌─────┐ ┌─────┐   ││  │ └────────────┘│
│ │   │ Pod │ │ Pod │   ││  │                │
│ │   └─────┘ └─────┘   ││  │                │
│ └─────────────────────┘│  │                │
└────────────────────────┘  └────────────────┘
```

**Control Plane Components:**
```
API Server (kube-apiserver):
- Central management point
- RESTful API
- Authentication/Authorization
- All communication hub

etcd:
- Distributed key-value store
- Cluster state storage
- Source of truth
- Highly available

Scheduler (kube-scheduler):
- Pod placement decisions
- Resource requirements
- Constraints and affinity

Controller Manager:
- Runs controllers
- Desired state enforcement
- Node, Replication, Endpoints, Service Account controllers
```

**Node Components:**
```
kubelet:
- Node agent
- Ensures pods are running
- Reports to API server
- Manages pod lifecycle

kube-proxy:
- Network proxy
- Service abstraction
- Load balancing
- iptables/IPVS rules

Container Runtime:
- Docker/containerd/CRI-O
- Pulls images
- Runs containers
```

#### **Част 2: Core Kubernetes Objects (15 мин)**

**Pod - Smallest Deployable Unit:**
```yaml
# pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:alpine
    ports:
    - containerPort: 80
```

```bash
# Create pod
kubectl apply -f pod.yaml

# List pods
kubectl get pods

# Describe pod
kubectl describe pod nginx-pod

# Get logs
kubectl logs nginx-pod

# Enter pod
kubectl exec -it nginx-pod -- sh

# Delete pod
kubectl delete pod nginx-pod
```

**Deployment - Manages ReplicaSets:**
```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:alpine
        ports:
        - containerPort: 80
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
```

**Service - Network Abstraction:**
```yaml
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  type: LoadBalancer  # or ClusterIP, NodePort
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080  # for NodePort only
```

**ConfigMap & Secret:**
```yaml
# configmap.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  database_url: "postgres://localhost/mydb"
  app_mode: "production"

---
# secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
type: Opaque
data:
  password: cGFzc3dvcmQxMjM=  # base64 encoded
```

#### **Част 3: Kubernetes in Action (12 мин)**

**Complete Application Deployment:**

**1. Backend Deployment:**
```yaml
# backend.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: backend
spec:
  replicas: 2
  selector:
    matchLabels:
      app: backend
  template:
    metadata:
      labels:
        app: backend
    spec:
      containers:
      - name: api
        image: node:alpine
        command: ["node", "server.js"]
        ports:
        - containerPort: 3000
---
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  selector:
    app: backend
  ports:
  - port: 3000
```

**Scaling Operations:**
```bash
# Manual scaling
kubectl scale deployment backend --replicas=5

# Autoscaling (HPA)
kubectl autoscale deployment backend \
  --min=2 --max=10 --cpu-percent=70
```

**Health Checks:**
```yaml
spec:
  containers:
  - name: app
    livenessProbe:
      httpGet:
        path: /health
        port: 8080
      initialDelaySeconds: 30
      periodSeconds: 10
    readinessProbe:
      httpGet:
        path: /ready
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 5
```

#### **Част 4: Networking & Storage (10 мин)**

**Ingress Controller:**
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: app-ingress
spec:
  rules:
  - host: app.example.com
    http:
      paths:
      - path: /api
        pathType: Prefix
        backend:
          service:
            name: backend-service
            port:
              number: 3000
      - path: /
        pathType: Prefix
        backend:
          service:
            name: frontend-service
            port:
              number: 80
```

**Persistent Storage:**
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: data-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
```

### **4. ЗАТВЪРЖДАВАНЕ (25 минути)**

#### **Практическа работа: Deploy WordPress**

**Step 1: Create MySQL Deployment (10 мин)**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mysql
spec:
  selector:
    matchLabels:
      app: mysql
  template:
    metadata:
      labels:
        app: mysql
    spec:
      containers:
      - name: mysql
        image: mysql:5.7
        env:
        - name: MYSQL_ROOT_PASSWORD
          value: password
        - name: MYSQL_DATABASE
          value: wordpress
        ports:
        - containerPort: 3306
---
apiVersion: v1
kind: Service
metadata:
  name: mysql
spec:
  selector:
    app: mysql
  ports:
  - port: 3306
```

**Step 2: Create WordPress Deployment (10 мин)**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress
spec:
  replicas: 2
  selector:
    matchLabels:
      app: wordpress
  template:
    metadata:
      labels:
        app: wordpress
    spec:
      containers:
      - name: wordpress
        image: wordpress:latest
        env:
        - name: WORDPRESS_DB_HOST
          value: mysql:3306
        - name: WORDPRESS_DB_PASSWORD
          value: password
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: wordpress
spec:
  selector:
    app: wordpress
  type: LoadBalancer
  ports:
  - port: 80
```

**Step 3: Apply and Test (5 мин)**
```bash
kubectl apply -f mysql.yaml
kubectl apply -f wordpress.yaml
kubectl get all
minikube service wordpress --url
```

### **5. ОБОБЩЕНИЕ (10 минути)**

**Key Concepts:**
- Declarative configuration
- Self-healing systems
- Horizontal scaling
- Service discovery
- Rolling updates

**Production Best Practices:**
1. Use namespaces for isolation
2. Set resource limits
3. Implement health checks
4. Use ConfigMaps/Secrets
5. Regular backups
6. Monitor with Prometheus
7. Log aggregation with ELK

### **6. ДОМАШНА РАБОТА (5 минути)**

**Задачи:**

1. **Практическа:**
   - Deploy 3-tier application
   - Implement autoscaling
   - Add persistent storage
   - Document architecture

2. **Изследователска:**
   - Research Helm charts
   - Compare Kubernetes alternatives
   - Write comparison report

3. **Проект:**
   - Containerize personal project
   - Create K8s manifests
   - Deploy to minikube
   - Present findings

**Срок:** До следващия учебен час

---

## 6. ОЦЕНЯВАНЕ

### КРИТЕРИИ ЗА ОЦЕНЯВАНЕ:

| Критерий | Точки |
|----------|-------|
| Разбиране на K8s архитектура | 25% |
| Създаване на YAML манифести | 20% |
| kubectl команди | 20% |
| Deployment на приложения | 20% |
| Troubleshooting | 10% |
| Активност | 5% |

### ОЦЕНЪЧНА РУБРИКА:
- **Отличен (6):** Създава сложни deployments, разбира всички концепции
- **Много добър (5):** Успешно deploy-ва приложения, добро разбиране
- **Добър (4):** Може да работи с основни обекти, нуждае се от помощ
- **Среден (3):** Разбира концепциите, затруднения с практиката

---

## 7. РЕФЛЕКСИЯ И АНАЛИЗ

### ВЪПРОСИ ЗА САМООЦЕНКА:
1. Разбирам ли защо е нужен Kubernetes?
2. Мога ли да създам Deployment и Service?
3. Знам ли как да debug-вам pods?
4. Готов ли съм за production Kubernetes?

### ИНДИКАТОРИ ЗА УСПЕХ:
- [ ] 90% разбират orchestration нуждата
- [ ] 85% създават основни манифести
- [ ] 80% могат да deploy-ват приложения
- [ ] 75% използват kubectl ефективно
- [ ] 70% debug-ват основни проблеми

---

## 8. ПРИЛОЖЕНИЯ

### ПРИЛОЖЕНИЕ 1: KUBECTL CHEAT SHEET

```bash
# Cluster Info
kubectl cluster-info
kubectl get nodes

# Pods
kubectl get pods
kubectl describe pod POD_NAME
kubectl logs POD_NAME
kubectl exec -it POD_NAME -- bash
kubectl delete pod POD_NAME

# Deployments
kubectl create deployment NAME --image=IMAGE
kubectl scale deployment NAME --replicas=5
kubectl set image deployment/NAME CONTAINER=IMAGE
kubectl rollout status deployment/NAME
kubectl rollout undo deployment/NAME

# Services
kubectl expose deployment NAME --port=80
kubectl get services
kubectl delete service NAME

# Apply/Delete YAML
kubectl apply -f FILE.yaml
kubectl delete -f FILE.yaml

# Debugging
kubectl get events
kubectl top nodes
kubectl top pods
```

### ПРИЛОЖЕНИЕ 2: YAML TEMPLATES

**Complete App Template:**
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: myapp
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app
  namespace: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: app
        image: myapp:1.0
        ports:
        - containerPort: 8080
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "256Mi"
            cpu: "200m"
---
apiVersion: v1
kind: Service
metadata:
  name: app-service
  namespace: myapp
spec:
  selector:
    app: myapp
  type: LoadBalancer
  ports:
  - port: 80
    targetPort: 8080
```

### ПРИЛОЖЕНИЕ 3: TROUBLESHOOTING

**Common Issues:**
```
Pod Pending:
- Check resources
- Check node capacity
- Check PVC

CrashLoopBackOff:
- Check logs
- Check image
- Check env vars

Service not working:
- Check endpoints
- Check labels
- Check ports

ImagePullBackOff:
- Check image name
- Check registry
- Check secrets
```

---

**Изготвил:** [Име на учителя]  
**Дата на изготвяне:** Декември 2024 г.
