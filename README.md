
# Guia: Utilizando o Git Flow em uma Equipe

Este guia descreve como configurar e utilizar o **Git Flow** em equipes, detalhando os papéis das branches e os comandos necessários.

---

## **1. Instalação do Git Flow**
 1. **Pré-requisitos**
  - Git instalado no sistema
    - Para instalar git em Linux / macOS
    ```bash
    sudo apt update && sudo apt install git  # Linux (Debian/Ubuntu)
    brew install git                         # macOS
    ```
    - Para Windows
    ```
      Use o **Git for Windows** (https://gitforwindows.org/).
    ```
2. Instalando Git FLow        
 - **Linux (Debian/Ubuntu)**
    ```bash
    sudo apt-get install git-flow
    ```
  
  - **macOS**
    ```bash
    brew install git-flow
    ```
  
  - **Windows**
    - As versões mais novas dos instaladores git já contem a biblioteca do git-flow.

3. Configurando repositório
    Após a instalação, inicie o **Git Flow** no seu repositório:
    ```bash
    git flow init
    ```
    Responda as perguntas do assistente interativo para configurar os prefixos e branches principais (`main` e `develop`).
---

## **2. Estrutura de Branches do Git Flow**

| **Branch**    | **Propósito**                                                                 | **Prefixo**   |
|---------------|-------------------------------------------------------------------------------|---------------|
| `main`        | Branch principal usada para releases estáveis.                              | N/A           |
| `develop`     | Branch de integração onde o trabalho em andamento é consolidado.            | N/A           |
| `feature`     | Branches usadas para implementar novas funcionalidades.                     | `feature/`    |
| `release`     | Branch usada para preparar uma nova versão antes de ir para produção.       | `release/`    |
| `hotfix`      | Branch usada para corrigir problemas críticos em produção.                  | `hotfix/`     |
| `support`     | Branch de suporte para versões legadas.                                     | `support/`    |

---

## **3. Fluxo de Trabalho com Git Flow**

### **Branch `main`**
- **Uso**: Contém apenas código estável e pronto para produção.
- **Ações permitidas**: Merge de uma branch `release` ou `hotfix`.

### **Branch `develop`**
- **Uso**: Reúne código em desenvolvimento (novas features e correções).
- **Ações permitidas**: Merge de branches `feature` e `hotfix`.

### **Branch `feature`**
- **Uso**: Cada funcionalidade nova é desenvolvida em uma branch separada.
- **Comandos**:
  ```bash
  # Criar uma nova feature
  git flow feature start <nome-da-feature>

  # Finalizar a feature
  git flow feature finish <nome-da-feature>
  ```

### **Branch `release`**
- **Uso**: Consolidar e preparar o código para lançamento.
- **Comandos**:
  ```bash
  # Criar uma nova release
  git flow release start <versão>

  # Finalizar a release
  git flow release finish <versão>
  ```

### **Branch `hotfix`**
- **Uso**: Resolver problemas críticos em produção.
- **Comandos**:
  ```bash
  # Criar um hotfix
  git flow hotfix start <nome-do-hotfix>

  # Finalizar o hotfix
  git flow hotfix finish <nome-do-hotfix>
  ```
### **Branch `support`**
- **Uso**: Manutenção de versões legadas para corrigir bugs ou implementar pequenas alterações.
- **Comandos**:
  ```bash
  # Criar manualmente uma branch de suporte
  git checkout -b support/<nome-da-versao>
  ```
---

## **4. Comandos Adicionais**

### **`publish` e `delete`**
- **Publish (`feature/hotfix/release publish`)**:
  - Publica a branch desejada no repositório remoto, permitindo que outros colaboradores trabalhem nela.
  ```bash
  git flow feature/hotfix/release publish <nome-do-hotfix>
  ```

- **Delete (`feature/hotfix/release delete`)**:
  - Remove a branch de desejada localmente.
  ```bash
  git flow feature/hotfix/release delete <nome-do-hotfix>
  ```

- **Excluir branch remota**: 
  ```bash
  # Listar branchs do repositório remoto
  git branch -r
  # Comando para deletar a branch remota
  git push origin --delete <nome-da-branch>
  ```

---


### **Adote o Git Flow para melhorar o gerenciamento de versões no seu projeto!**
