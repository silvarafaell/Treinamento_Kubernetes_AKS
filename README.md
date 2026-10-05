Curso Treinamento Kubernetes e AKS no nextwave(LuisDEV)

- O que é Kubernetes?
  - Kubernetes é um sistema de código aberto (open-source) para automação de deployments com escalabilidade e gerenciamento de aplicações em container.
  - Atualmente faz parte do catálogo do Cloud Native Computing Foundation (CNCF), iniciativa responsável por incubar diversos projetos open-source com características cloud native, assim como o Kubernetes.

- Composição de um cluster Kubernetes
  - O Kubernetes é um conjunto de servidores que são responsáveis por gerenciar containers em execução. Esse conjunto é chamado de "cluster".
  - Um cluster é composto basicamente por:
    - Master nodes: Máquinas que gerenciam o cluster (API Server, Scheduler, Controller Manager)
    - Worker nodes: Máquinas que executam aplicações em containers
    - ETCD: Banco de dados do cluster.
   
- Kubernetes como serviço (AKS)
  - O que é?
    - As principais provedoras de nuvem possuem em seu catálogo "Kubernetes como serviço"
    - Azure - AKS (Azure Kubernetes Service)
    - AWS - EKS (Elastic Kubernetes Service)
    - GCP - GKE (Google Kubernetes Engine)
  - Cada qual com suas vantagens e integrações já definidas. Como por exemplo o serviço de autenticação.

- Principais vantagens AKS
  - As principais vantagens de utilização de Kubernetes como serviço:
    - Não precisa gerenciar "master nodes"
    - Não precisa gerenciar o ETCD (banco de dados)
    - Escalabilidade de instâncias automatizada
    - Integração com diversos serviços, como por exemplo autenticação
    - Atividades operacionais automatizadas, tais como atualização e reposição de nodes problemáticos
    - Diversas soluções "out of the box" (monitoramento, exposição de aplicações com Ingress, logs)

- Interagindo com o cluster
  - kubectl
    - Ao contrário de um arquivo YAML (linguagem declarativa), o kubectl é considerado uma ferramenta de linha de comando que interage com o cluster para ler, criar, editar e excluir objetos (comando imperativo)
    - Também com o kubectl podemos aplicar manifestos YAML para a criação, edição ou exclusão de objetos

- Manifestos YAML
  - Uma das formas de interação com um cluster (não administrativa) é usando arquivos com sintaxe YAML
  - Os arquivos possuem as características e atributos que definem como um objeto deve ser criado pelo Kubernetes (linguagem declarativa).

 - Tipos de deployment
   - Como funciona um deployment
     - Um objeto do tipo "Deployment" provê definições e características para a criação de um "ReplicaSet" e consequentemente um "Pod"
     - Por sua vez, um "ReplicaSet" é responsável por manter as réplicas de um Pod em execução.
     - O Pod é o recurso mais baixo dessa hierarquia

- Deployment
  - Objetos do tipo "Deployment" criam "ReplicaSets" que por sua vez é responsável por manter réplicas de "Pods" dentro do cluster
  - Os "Pods" são distribuídos entre os nós do cluster dependendo dos recursos livres de cada nó.

- Daemonset
  - "Daemonset" é um tipo de deployment que cria uma réplica do seu "Pod" em cada um dos nós do cluster
  - Essa estratégia é comum em ferramentas operacionais de infraestrutura, como coleta de métricas para monitoramento ou logs.

- Statefulset
  - "Statefulset" normalmente é utilizado para criar aplicações que precisam manter estado (dados/arquivos), principalmente para o cenário de banco de dados, ou clusters de bancos de dados.
