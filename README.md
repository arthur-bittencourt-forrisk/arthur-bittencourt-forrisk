# 📄 Documentação Técnica – DevOps | ForRisk

🔗 **Para mais informações, consultar a Política de Ciclo e Entrega em:**  
[Política de Ciclo de Entrega e Governança Técnica (PDF)](https://forrisksolucoes.sharepoint.com/:b:/r/sites/GRUPOFORRISK/Documentos%20Compartilhados/FORRISK/1%20-%20GRUPO%20FORRISK/GRUPO%20FORRISK%20-%20TECNICO/GRUPO%20FORRISK/POLITICAS%20PUBLICADAS/Politica%20de%20Ciclo%20de%20Entrega%20e%20Governanca%20Tecnica.pdf?csf=1&web=1&e=t4anY0)

---

## ⏳ Antecedência Mínima para Solicitações

| **Ambiente**        | **Tipo de Solicitação**                             | **Antecedência Mínima** |
|---------------------|-----------------------------------------------------|--------------------------|
| **Produção**        | Alterações críticas, deploys manuais                | 48h úteis                |
| **Staging**         | Criação ou alteração de ambiente, testes integrados | 24h úteis                |
| **Desenvolvimento** | Acessos, ajustes simples, testes locais             | 8h úteis                 |

---


## 🕐 SLA – Prazo para Início do Atendimento

| **Prioridade** | **Exemplo**                                | **Prazo para Início do Atendimento** |
|----------------|---------------------------------------------|--------------------------------------|
| **Urgente**    | Produção fora do ar                        | Imediato (prioritário)               |
| **Alta**       | Deploy bloqueado, pipeline com falha       | Até 8 horas úteis                    |
| **Normal**     | Criação de ambientes, ajustes não urgentes | Até 2 dias úteis                     |
| **Baixa**      | Melhorias, pequenas dúvidas                | Até 5 dias úteis                     |

---

## 📬 Onde Solicitar

- Página oficial do ClickUp:  
  [https://app.clickup.com/90131050727/v/f/90135990483](https://app.clickup.com/90131050727/v/f/90135990483)

- E-mail: `devops@forrisk.com.br`  
  *(uso alternativo apenas quando o ClickUp não estiver acessível)*

---

## 📌 O Que Solicitar ao DevOps

- Orquestrar containers nos ambientes de staging e produção  
- Configurar pipelines de CI/CD e gerenciar versionamento de imagens  
- Gerenciar secrets, volumes, escalabilidade e balanceamento de carga  
- Executar o deploy real (Kubernetes, ECS, Swarm etc.)  
- Monitorar a qualidade dos builds, testes e saúde dos serviços  
- Documentar mudanças em infraestrutura e processos de entrega nos canais oficiais  
- Validar se as tags Docker nas solicitações correspondem à versão correta a ser promovida  

---

## 👤 Quem Deve Solicitar

- Solicitações **exclusivamente pelo Gerente de Projetos** responsável  
- O Gerente deve garantir documentação completa, com apoio dos devs  
- Solicitações enviadas por desenvolvedores diretamente ao DevOps serão **devolvidas**  
- Apenas o Gerente de Projetos pode aprovar alterações em **produção**

---

## 🔄 O Que o DevOps Pode Solicitar aos Times

- Credenciais e permissões necessárias  
- Variáveis de ambiente documentadas  
- Acesso temporário a repositórios ou sistemas  
- Código versionado e funcional  
- Evidência de testes validados  
- Desenho da arquitetura ou fluxo esperado  
- Planejamento de deploy com rollback  

---

## 🏷️ Utilize Tags

Facilita categorização e rastreabilidade:

- `infraestrutura`
- `acesso`
- `ci-cd`
- `monitoramento`
- `deploy`
- `dns-dominio`
- `segurança`
- `ambiente-dev`
- `ambiente-staging`
- `ambiente-prod`

---

## 🧩 Janelas de Manutenção

Mudanças em produção com risco de **downtime** devem:

- Ser agendadas com **antecedência**
- Ter comunicação prévia a todas as partes
- Preferência por **horários fora do comercial**

---

## 📚 Documentação das Entregas

Toda entrega feita pelo DevOps deve ser registrada em canais oficiais (GitHub, Discord, E-mail).

Cada tarefa em um deploy deve ser documentada pelo solicitante com:

- Descrição do que está sendo entregue  
- Motivo da alteração  
- Confirmação de testes realizados  
- Impactos e plano de rollback (se aplicável)

### 📌 Exemplo:
> Ao configurar um novo pipeline, o DevOps deve documentar o fluxo, variáveis e gatilhos.  
> O solicitante (gerente ou dev) deve garantir changelog ou release note no board.

⚠️ Deploys sem documentação adequada podem ser **suspensos** até regularização.

---

## 🐳 Regras de Imagem Docker e Fluxo de Pull Requests

### Pull Requests

- Produção → `main`  
- Homologação → `staging`  
- Correções urgentes → `hotfix` → `main`

| Situação | Pull Request |
|----------|--------------|
| Deploy para staging | `develop → staging` |
| Correção urgente     | `main → staging` após correção |

Aprovação de PRs `main` e `staging` feita **exclusivamente pelo DevOps** com alinhamento do Gerente de Projetos.

> Se houver **conflitos**, o PR será devolvido ao desenvolvedor para correção.  
> Caso não resolvido, o DevOps **recusará** o pull request.

---

## 🌐 Frontend

- Deploy para homologação ou produção via **CI/CD com pull request**
- Atenção: ao aprovar o PR de `staging → main`, **todo conteúdo da `staging` vai para produção**

---

## 🧱 Backend

- Projeto backend deve ter imagem Docker **buildada e publicada** no GitHub Packages  
- Responsabilidade do time de desenvolvimento

### Versão de Imagens

| Ambiente    | Tag Docker    |
|-------------|---------------|
| Staging     | `s.v1`, `s.v2`, `s.v3`... |
| Produção    | `p.v1`, `p.v2`, `p.v3`... |

⚠️ **Nunca sobrescrever imagens** existentes.

Deploy realizado pelo DevOps conforme:

- Solicitação do Gerente de Projetos  
- Tag informada na solicitação

---
