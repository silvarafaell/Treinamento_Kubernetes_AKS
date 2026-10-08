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

- Service
  - O objeto service é utilizado para distribuir chamadas entre réplicas de um mesmo deployment
  - Por exemplo uma aplicação que responde um front-end com três réplicas, as chamadas devem ser direcionadas ao service daquele front-end, e o mesmo é responsável por repassar as chamadas para um dos três pods, distribuindo de forma aleatória entre os eles.
  - Existem três tipos de service:
    - NodePort
    - ClusterIP
    - LoadBalancer

- Ingress
  - O Ingress atua como uma porta de entrada do cluster para aplicações http/https expondo apenas um único ponto de conectividade externa e resolvendo encaminhamentos de requisições entre services através do cabeçalho http

- Liveness e Readiness
  - Os campos "Liveness" e "Readiness" são responsáveis pela checagem da saúde do container que está dentro do Pod. Essa checagem pode ser feita através de um comando script, uma checagem de porta TCP ou a requisição num endpoint da aplicação que devolva um status code entre 200 e 399 (qualquer outro status code será     considerado como falha).
    - livenessProbe: Responsável por fazer a checagem de tempos em tempos para garantir que a aplicação está responsiva. Usado durante a execução da aplicação.
    - readinessProbe: Responsável por fazer a checagem que garante que a aplicação esteja pronta para receber requisições. Usado até o fim da inicialização da aplicação.

- Azure Kubernetes Service (AKS)
  - O Azure Kubernetes Service simplifica a publicação de um cluster Kubernetes no Azure, passando parte de responsabilidade operacional para o Azure
  - Quando se cria um cluster AKS, um painel de controle é adicionado e configurado sem custo, e os únicos custos são decorrentes dos nós que estão anexados ao cluster
  - Pode ser criado via Azure CLI, Azure PowerShell, Azure Portal, e templates de publicação como ARM, Bicep, e Terraform
  - Dá para configurar aspectos como rede, integração com Azure AD, monitoramento, e outros enquanto o processo de publicação está executando

- HELM
  - Helm é uma ferramenta que pode ser considerada como um "gerenciador de pacotes" para Kubernetes, além de ajudar a otimizar os manifestos YAML, centraliza valores e configurações num único arquivo
  - Com inúmeros repositórios centrais, também é possível baixar "pacotes" pré configurados e prontos para uso
  - Outra grande vantagem é a possibilidade de "empacotar" a sua própria aplicação e distribuí-la na sua organização ou comunidade
  - obs: Para a instalação do Helm, siga as instruções neste link
  
