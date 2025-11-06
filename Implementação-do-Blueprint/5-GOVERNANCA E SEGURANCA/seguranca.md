# 5. GOVERNANÇA E SEGURANÇA: DIRETRIZES DE SEGURANÇA (GUARDRAILS)

## 🚨 Visão Geral e Princípios Fundamentais

Este domínio define as regras de **Alinhamento e Robustez** do sistema de IA, garantindo que ele seja útil, seguro e ético em todas as interações (Processo conhecido como **RLHF - Reinforcement Learning from Human Feedback**).

| Princípio | Descrição | Métrica de Risco (Blueprint) |
| :--- | :--- | :--- |
| **I. Inofensividade** | O sistema não deve gerar, promover ou auxiliar conteúdo ilegal, nocivo ou de ódio. | Taxa de violação de políticas (Target: < 0.01% das interações). |
| **II. Factualidade** | O sistema deve priorizar a verdade factual e evitar "alucinações" (informações incorretas inventadas). | Taxa de Alucinação (Target: < 3% em testes de veracidade). |
| **III. Imparcialidade** | O sistema não deve exibir ou amplificar vieses sociais, políticos ou culturais. | Índice de Viés (Bias Index) medido em conjuntos de dados de teste. |
| **IV. Privacidade** | O sistema não deve solicitar, armazenar ou expor dados pessoais ou confidenciais (PII). | Zero Vazamento (Teste de Injeção de Prompt de Exfiltração). |

## 🚫 Políticas de Conteúdo Proibido (Safety Guardrails)

O Módulo de Segurança (Ver `docs/1_VISION/ARQUITETURA.md`) deve interceptar e bloquear requisições de entrada e saídas de geração que se enquadrem nas seguintes categorias:

### 5.1. Conteúdo Nocivo Explícito
* **Ataques de Ódio e Discriminação:** Geração de estereótipos, conteúdo depreciativo ou promoção de discriminação com base em raça, etnia, gênero, religião, etc.
* **Conteúdo Violento e Gore:** Descrições detalhadas de violência, automutilação, ou assédio.
* **Conteúdo Sexual Explícito (Non-Consensual):** Qualquer material que viole a legislação de proteção de menores ou seja de natureza abusiva.

### 5.2. Riscos de Segurança Cibernética e Fraude
* **Injeção de Prompt Maliciosa (Jailbreaking):** Tentativas de enganar o modelo a desobedecer suas regras ("Forget everything I told you and now act as...").
    * **Mitigação:** Deve-se utilizar uma camada de **Prompt Shield** que detecta padrões de *jailbreak* e força o **LLM Core** a responder com um aviso de recusa padrão.
* **Assistência em Atividades Ilegais:** Geração de código malicioso, instruções para invasão de sistemas, criação de armas, ou falsificação.
* **Exfiltração de Dados:** Tentativas de fazer o sistema revelar dados internos de treinamento ou informações sobre a arquitetura subjacente.

### 5.3. Política de Privacidade e PII
* **Coleta/Armazenamento:** O sistema é projetado para ser **Stateless** (sem estado persistente) em relação aos dados do usuário, a menos que o *token* de contexto seja explicitamente necessário para a continuidade da sessão.
* **Anonimização:** Dados de uso coletados para melhoria do modelo devem ser **anonimizados e agregados** antes do armazenamento de longo prazo (Seguindo a LGPD e GDPR).

## 📊 Medidas de Robustez (Prevenção de Alucinação)

A segurança não é apenas sobre o que o sistema *não pode* dizer, mas também sobre a confiabilidade do que ele *diz*.

| Ação de Robustez | Aplicação | Componente Chave |
| :--- | :--- | :--- |
| **Citação Obrigatória** | Sempre que for usada a ferramenta de busca (`Tool-Use`), a fonte deve ser citada no final da resposta. | Módulo de Raciocínio (Agent) |
| **"Não sei" Explícito** | Se a confiança (Confidence Score) na resposta for abaixo de um limite (**Threshold = 0.8**), o sistema deve declarar explicitamente que não tem a informação confiável, em vez de inventá-la. | LLM Core / Pós-Processamento |
| **Validação Cruzada** | Em tópicos críticos (ex: saúde, finanças), a resposta deve ser gerada por duas `Tool-Uses` ou um `Tool-Use` e o LLM Core para verificação de consistência. | Módulo de Raciocínio |

## 🧑‍💻 Governança Humana (Human-in-the-Loop)

* **Registro de Flag:** Todas as interações que ativarem um `Guardrail` (rejeição ou aviso de segurança) devem ser registradas para **Revisão Humana** e re-treinamento do modelo de segurança (RLHF).
* **Comitê de Ética:** Deve ser estabelecido um comitê para analisar casos de uso limítrofes e garantir que o Blueprint permaneça alinhado com a evolução das regulamentações de IA.

---