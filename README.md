# wp-projeto

Trabalho de conclusão de módulo - Infnet

- Objetivo: 
        
    - Utilizando arquitetura Kubernetes, Publicar aplicação WordPress, com 3 réplicas, através de Ingress e configurar serviço Statefulset para banco MySql, utilizando Longhorn para persistência de dados.


# Instalação Longhorn

kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/master/deploy/longhorn.yaml

- Expor painel Longhorn: 
    - kubectl -n longhorn-system expose deployment longhorn-ui --type=NodePort --overrides='{"spec": {"ports": [{"nodePort": 30080, "port": 8000, "target": 8000}]}}' --port=8000


# Instalação e configuração ArgoCD

- kubectl create namespace argocd

- kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.14.2/manifests/install.yaml

- Expor servico argocd-server
    - kubectl patch svc argocd-server -p '{"spec": {"type": "NodePort"}}' -n argocd

- Senha inicial ADMIN
    - kubectl get secrets argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode -n argocd


# Preview

<img width="1445" alt="Screenshot 2025-02-23 at 13 03 08" src="https://github.com/user-attachments/assets/099d0f81-0cc9-4954-8ef5-b0f913f4257b" />

<img width="1462" alt="Screenshot 2025-02-23 at 13 14 30" src="https://github.com/user-attachments/assets/b843085f-fa6b-49c9-92d7-01670b38b945" />

<img width="1460" alt="Screenshot 2025-02-23 at 13 14 45" src="https://github.com/user-attachments/assets/5a62368e-b438-42d9-87eb-9e4c3068adcf" />

<img width="1461" alt="Screenshot 2025-02-23 at 13 15 42" src="https://github.com/user-attachments/assets/52738228-38de-488e-861b-41c91339e4ff" />

<img width="1465" alt="Screenshot 2025-02-23 at 13 16 00" src="https://github.com/user-attachments/assets/5b9a37aa-b23c-4faa-b813-be41106914d2" />

<img width="1459" alt="Screenshot 2025-02-23 at 13 16 41" src="https://github.com/user-attachments/assets/1094a563-a9f4-4d11-b80e-b10ec634ec61" />

<img width="1460" alt="Screenshot 2025-02-23 at 13 17 10" src="https://github.com/user-attachments/assets/9782778a-15b5-4b9f-97f8-69567e1ce14f" />

<img width="1456" alt="Screenshot 2025-02-23 at 13 18 19" src="https://github.com/user-attachments/assets/578870f7-e367-4e2e-a593-0b5c9e1fb138" />

<img width="1461" alt="Screenshot 2025-02-23 at 13 18 44" src="https://github.com/user-attachments/assets/c9e1d78d-3bad-4167-95d7-051c56111732" />

<img width="1461" alt="Screenshot 2025-02-23 at 14 06 22" src="https://github.com/user-attachments/assets/0a6476bc-3bf5-4e29-b919-0b0694dda936" />

<img width="1461" alt="Screenshot 2025-02-23 at 14 06 35" src="https://github.com/user-attachments/assets/012d7948-4f8e-44e1-ae5f-e0dcbfce7753" />

<img width="1459" alt="Screenshot 2025-02-23 at 13 22 31" src="https://github.com/user-attachments/assets/567b80f9-0877-43c1-8793-da45ea7ba940" />

<img width="1460" alt="Screenshot 2025-02-23 at 13 19 00" src="https://github.com/user-attachments/assets/8fd77e34-9b32-4b0b-8c9a-f1bae0e50c97" />


