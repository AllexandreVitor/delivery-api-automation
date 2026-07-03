# Delivery API - Automação de CI/CD com GitHub Actions

## 📌 Visão Geral

Este projeto tem como objetivo implementar uma esteira de **Integração Contínua (CI)** e práticas iniciais de **DevSecOps** utilizando o **GitHub Actions**.

A aplicação base, chamada **Delivery API**, foi fornecida em Node.js e não possuía automação de pipeline. A partir desta atividade, foi configurado um fluxo automatizado para garantir qualidade, segurança e confiabilidade antes de qualquer alteração ser integrada à branch principal (`main`).

---

## 🎯 Objetivo da Atividade

Consolidar conhecimentos em:

- Integração Contínua (CI)
- DevSecOps
- Automação de pipelines com GitHub Actions
- Validação de código (build, lint, testes e segurança)

---

## ⚙️ Estrutura do Pipeline

A automação foi implementada no caminho:

.github/workflows/pipeline.yml

O workflow foi configurado com o nome:

Delivery API Pipeline

---

## 🚀 Gatilhos (Triggers)

O pipeline é executado automaticamente em:

- push na branch `main`
- pull_request direcionado à branch `main`

---

## 🧩 Jobs do Pipeline

### 🔐 Job 0 - SAST (Segurança)

- Executa análise estática de segurança
- Utiliza a action: `ajinabraham/njsscan-action@master`
- Analisa vulnerabilidades no código-fonte

---

### 🏗️ Job 1 - Build

- Executado em ambiente Ubuntu
- Configura Node.js versão `24`
- Utiliza cache para dependências npm
- Executa:
  - npm install
  - npm run build

---

### 🎨 Job 2 - Lint & Quality

- Responsável por garantir padrões de código
- Executa:
  - npm run lint
- Só é executado após sucesso do job Build

---

### 🧪 Job 3 - Test

- Executa testes unitários da aplicação
- Comando:
  - npm test
- Também depende do sucesso do job Build

---

## 🔄 Fluxo de Execução

O pipeline segue o seguinte fluxo:

SAST (paralelo)
      │
Build (principal)
   ├── Lint & Quality
   └── Test


## 🧪 Validação do Pipeline

Após o push para a branch `main`, o GitHub Actions executa automaticamente o pipeline.

Para acompanhar:

1. Acesse o repositório no GitHub
2. Vá até a aba Actions
3. Verifique o workflow Delivery API Pipeline
4. Confirme que todos os jobs foram concluídos com sucesso:
   - SAST ✔
   - Build ✔
   - Lint & Quality ✔
   - Test ✔

---

## 📁 Estrutura Esperada do Projeto

.
.github/
└── workflows/
    └── pipeline.yml
node_modules/
src/
eslint.config.mjs
jest.config.js
package-lock.json
package.json
README.md
tsconfig.json
