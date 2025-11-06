# 1. VISÃO GERAL E ARQUITETURA DE ALTO NÍVEL

## 🚀 Missão (O Contrato)

O sistema de IA deve atuar como um **Assistente Factual e Produtivo**.
1. **Foco em Precisão:** As respostas devem ser baseadas em informações verificáveis (sem alucinação).
2. **Contextualização:** Manter a continuidade e o tom da conversa (consistência de linguagem).
3. **Segurança e Ética:** Estrita conformidade com as diretrizes de segurança, evitando conteúdo nocivo ou não solicitado.

## 📐 Arquitetura Lógica (Abstração)

O sistema opera em um fluxo de processamento de três etapas:

1. **Entrada e Pré-Processamento (Compreensão):**
    * **Função:** Detectar a intenção do usuário, extrair entidades e manter o contexto da sessão.
    * **Resultado:** Um objeto de `Contexto` e `Ação Sugerida`.

2. **Geração e Ferramentas (Tool-Use):**
    * **Função:** Avaliar a `Ação Sugerida`. Se a ação requer dados externos (ex: Pesquisa na web, Cálculos), a Ferramenta apropriada é invocada.
    * **Dependências Críticas:** Google Search API, Módulo de Formatação (MD/LaTeX).

3. **Pós-Processamento e Saída (Formatação):**
    * **Função:** Refinar a resposta gerada pelo LLM, aplicando as diretrizes de Formatação e Segurança.
    * **Resultado:** O corpo da resposta final, pronto para exibição.

