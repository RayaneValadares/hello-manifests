<h1 align="left">
  <img src="https://icons.iconarchive.com/icons/simpleicons-team/simple/128/github-actions-icon.png" 
       alt="ArgoCD" width="60" style="vertical-align:middle; margin-right:10px;">
  Repositório de Manifestos - Projeto CI/CD com o Github Actions 
</h1>

Este repositório contém os manifestos **Kubernetes** da aplicação **Hello App**.  
Ele atua como a **Single Source of Truth** do fluxo **GitOps**, utilizado para automação do deploy via **ArgoCD**.

---

## Integração com CI/CD

Este repositório é mantido automaticamente por dois sistemas principais:

- **GitHub Actions (CI)** – presente no repositório da aplicação [`hello-app`](https://github.com/RayaneValadares/hello-app)  
  Ele é responsável por atualizar a tag da imagem Docker dentro deste repositório a cada novo build publicado no Docker Hub.

- **ArgoCD (CD)** – monitora este repositório e aplica automaticamente as mudanças no cluster Kubernetes, garantindo o deploy contínuo.

<br>
<br>
<br>

## Fluxo de GitOps

1. Um **push** no repositório da aplicação (`hello-app`) dispara o workflow de CI no GitHub Actions.  
2. Após o build e o push da imagem para o Docker Hub, o job `update-manifest` clona este repositório.  
3. O workflow atualiza a **nova tag de imagem**.  
4. O commit é feito automaticamente para este repositório com a mensagem:  
   `"ci: atualiza imagem para <nova-tag>"`.
5. O **ArgoCD** detecta essa atualização e realiza o rollout da nova versão no cluster Kubernetes.

<br>
<br>
<br>

## Estrutura do Repositório

```bash
hello-manifests
├── deployment.yaml        # Deployment do Hello App
└── service.yaml           # Service para expor a aplicação
```

Descrição dos arquivos:

- deployment.yaml – Define o Deployment da aplicação, especificando a imagem Docker e o número de réplicas.
- service.yaml – Cria o Service responsável por expor a aplicação na porta configurada.

<br>
<br>
<br>

## Repositório da Aplicação

As atualizações deste repositório são geradas automaticamente por um workflow do GitHub Actions, definido no repositório principal da aplicação.

👉 https://github.com/RayaneValadares/hello-app

<br>
<br>
<br>

## Tecnologias Envolvidas

- FastAPI

- Docker

- GitHub Actions

- Kubernetes

- ArgoCD

<br>
<br>
<br>

## Evidências do Projeto

As capturas de tela e evidências de execução estão disponíveis no seguinte repositório: https://github.com/RayaneValadares/hello-app


