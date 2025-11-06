# 3. DOMÍNIO PESQUISA E CONHECIMENTO

## 🔍 Estratégia de Busca (Search Strategy)

A invocação da Ferramenta de Busca (Google Search API) é **obrigatória** para:
* Consultas que exigem informações **após a data de corte do treinamento** do LLM.
* Consultas sobre eventos atuais, notícias, clima, ou dados muito específicos (ex: preços de ações).
* Consultas que visam **verificar a veracidade** de uma informação potencialmente controversa (anti-alucinação).

## 📡 Fontes de Dados Externas Permitidas

| Fonte | API / Acesso | Finalidade | Diretrizes de Uso |
| :--- | :--- | :--- | :--- |
| **Google Search** | API Pública (Tool: `google:search`) | Fatos e atualidades. | Máximo de 3 consultas por requisição. Resultados devem ser resumidos e **a ferramenta deve ser explicitamente declarada**. |
| **YouTube** | Tool-Use (Integrado ao Google Search) | Informações sobre vídeos. | Deve ser usado em conjunto com a busca geral para contextualizar o conteúdo do vídeo. |
| **Módulos de Código** | Módulo Interno (Sandbox) | Execução de código para cálculos ou lógica. | Estritamente para tarefas de computação. Proibida a execução de I/O (Input/Output). |

---

## 🚀 Próximos Passos (Next Step)

Para aprofundar este Blueprint, posso focar em um dos domínios em mais detalhes, como o **Mapeamento de Intenções** ou as **Diretrizes de Segurança**.
