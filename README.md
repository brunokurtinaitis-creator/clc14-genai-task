# Análise Automatizada de Pull Requests com IA Generativa

**Aluno:** Bruno Kurtinaitis Dias

**E-Mail:** bruno.kurtinaitis@aluno.faculdadeimpacta.com.br

**Curso:** MBA CLC & DevOps_14

---

## 🎯 Objetivo do Projeto

Este projeto demonstra a aplicação prática de **Prompt Engineering** para automatizar a revisão de Pull Requests (PRs) de Infraestrutura como Código (IaC). O foco é garantir que mudanças em infraestrutura passem por uma triagem rigorosa de segurança, custo, compliance e boas práticas, reduzindo o erro humano e acelerando o ciclo de entrega.

---

## 🛠️ Evolução dos Prompts (Raciocínio Técnico)

O desenvolvimento foi estruturado em três iterações, refletindo o amadurecimento do controle sobre o Modelo de Linguagem (LLM).

### v1: Baseline (Prompt Direto)
* **Abordagem:** Utilização de **Zero-Shot prompting**.
* **Raciocínio:** O objetivo foi estabelecer um ponto de partida sem exemplos prévios, testando a capacidade nativa do modelo em interpretar código IaC.
* **Limitação:** Como não há delimitadores claros nem formato de saída especificado, o resultado é inconsistente (texto livre), o que impede o parsing automático por ferramentas de CI/CD.

### v2: Structured (Contexto e Instruções Explícitas)
* **Abordagem:** Introdução de **Contexto**, **Instruções Explícitas** e **Few-Shot prompting**.
* **Raciocínio:** Para aumentar a precisão, foram definidos critérios fixos de severidade e tipos de análise. O uso de delimitadores ajuda o modelo a distinguir o que é instrução do que é o código do usuário.
* **Ganho:** Redução da variabilidade e respostas mais alinhadas aos requisitos de SLA de um ambiente DevOps.

### v3: Schema & Security (Robustez Operacional)
* **Abordagem:** Implementação de **JSON Schema**, **Chain-of-Thought (CoT)** e mitigação de **Prompt Injection**.
* **Raciocínio:**
    * **Saída Estruturada:** O uso de um Schema rígido garante que a IA atue como uma API confiável, essencial para automação.
    * **Chain-of-Thought:** Instruí o modelo a "pensar passo a passo" antes da classificação final para aumentar a acurácia em problemas lógicos complexos.
    * **Segurança:** Implementação de camadas de defesa contra injeção de prompts maliciosos escondidos no código do PR, utilizando separadores claros e restrições de saída.

---

## 📂 Estrutura do Repositório

```text
├── test-files/           # Arquivos das PR utilizadas para os testes.
├── prompts/              # Prompts utilizados nas interações com a LLM.
├── resultados/           # Prints dos testes realizados
└── README.md             # Documentação do projeto
