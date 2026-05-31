# custom_resource_defination_-with-a-specific_controller
# Python Kubernetes Operator

A simple Kubernetes Operator built with Python and Kopf.

## Features

* Custom Resource Definition (CRD)
* Custom Controller
* Watch Events
* Desired State vs Current State
* Reconciliation Loop
* Owner References
* Deployment Management

---

# Project Architecture

```text
CRD ---> API Extension

CR ---> Desired State

Controller:
    WATCH events
    ↓
    Reconcile
    ↓
    Create/Update Deployment
```

---

# Technologies

* Python
* Kubernetes
* Kopf
* Custom Resources (CRD)
* Kubernetes API

---

# Files

| File             | Description                |
| ---------------- | -------------------------- |
| crd.yaml         | Custom Resource Definition |
| cr.yaml          | Custom Resource            |
| controller.py    | Python Controller          |
| requirements.txt | Python dependencies        |

---

# Install

```bash
python -m venv venv

source venv/bin/activate

pip install -r requirements.txt
```

---

# Apply CRD

```bash
kubectl apply -f crd.yaml
```

---

# Run Controller

```bash
kopf run controller.py
```

---

# Create Custom Resource

```bash
kubectl apply -f cr.yaml
```

---

# Example CR

```yaml
apiVersion: mycompany.com/v1
kind: App

metadata:
  name: my-app

spec:
  replicas: 3
  image: nginx
```

---

# What Happens Internally

1. API Server stores the CR
2. API Server sends an Event
3. Controller receives the Event
4. Controller reads Desired State from CR.spec
5. Controller reads Current State from Deployment.status
6. Controller compares Desired vs Current
7. Controller performs Reconciliation

---

# Author

Omar
