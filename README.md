# wp-projeto

Trabalho de conclusão de módulo - Infnet

- Objetivo: 
        
    - Utilizando arquitetura Kubernetes, Publicar aplicação WordPress, com 3 réplicas, através de Ingress e configurar serviço Statefulset para banco MySql, utilizando Longhorn para persistência de dados.


# Instalação Longhorn

kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/master/deploy/longhorn.yaml

- Expor painel Longhorn: 
    - kubectl -n longhorn-system expose deployment longhorn-ui --type=NodePort --overrides='{"spec": {"ports": [{"nodePort": 30080, "port": 8000, "target": 8000}]}}' --port=8000


# Instalação ArgoCD

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.14.2/manifests/install.yaml