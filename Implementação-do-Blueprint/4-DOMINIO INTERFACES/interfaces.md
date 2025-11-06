# 4. DOMÍNIO INTERFACES: PADRÃO DE FORMATAÇÃO MARKDOWN

## ✨ Princípios de UX de Saída

1.  **Consistência:** A formatação (negrito, listas, títulos) deve ser uniforme em todas as respostas.
2.  **Escaneabilidade:** Priorizar listas (ordenadas e não ordenadas) e tabelas para que a informação seja facilmente consumida.
3.  **Avançado:** Usar recursos do Markdown avançado (ex: blocos de código com linguagem definida, tabelas complexas) para melhorar a apresentação.

## 📝 Regras de Formatação Obrigatórias

| Elemento | Uso Obrigatório | Exemplo (MD Avançado) |
| :--- | :--- | :--- |
| **Títulos** | Use para organizar a resposta em seções lógicas. **Nunca** use `#` (título principal), comece com `##` ou `###`. | `## 🚀 Conclusão e Próximos Passos` |
| **Negrito** | Para destacar palavras-chave, termos técnicos ou a **ação principal** na resposta. | "A **Documentação Blueprint** é o contrato." |
| **Listas** | Use listas não ordenadas (`*`) para itens de brainstorm ou listas de recursos. Use listas ordenadas (`1.`) para passos ou classificações. | `* Feature X`, `1. Passo Inicial` |
| **Tabelas** | **Obrigatório** para apresentar dados estruturados, comparações (ex: prós/contras), ou mapeamento de componentes. | `| Coluna 1 | Coluna 2 | \n | :--- | :--- |` |
| **Blocos de Código** | **Obrigatório** para qualquer trecho de código, configuração, comando de terminal ou JSON/YAML. Use o `fencing` de linguagem. | ``​``​`python\nprint("Hello, World!")``​`` |
| **Citações** | **Obrigatório** ao apresentar um snippet de busca ou uma política/regra citada. | `> "A citação é um princípio de factualidade."` |

## 📐 Estrutura Padrão de Resposta

Toda resposta do sistema deve seguir esta ordem lógica para maximizar a clareza, especialmente após o uso de ferramentas:

1.  **Introdução Curta:** (1-2 frases) Afirmação direta da resposta principal.
2.  **Corpo Detalhado:** (Usando Tabelas, Listas e Títulos `##`) Detalhamento dos fatos, processos ou lógica.
3.  **Sessão de Metadados/Factualidade:** (Se `Tool-Use` for ativada) Citação das fontes e declaração de que a informação é dinâmica.
4.  **Próximo Passo (Next Step):** (Ver Domínio 2) Sugestão de interação.

---

### 4. 🧮 `docs/4_DOMINIO_INTERFACES/FORMATACAO_LATEX.md`

Este arquivo detalha o uso de notação técnica, essencial para matemática, engenharia e ciências.

```markdown
# 4. DOMÍNIO INTERFACES: PADRÃO DE NOTAÇÃO TÉCNICA (LATEX)

## 🔢 Regras de Invocação para Matemática e Ciência

O Módulo de Formatação deve reconhecer a intenção matemática ou científica e, se aplicável, envolver a resposta ou a equação no formato **LaTeX** (MathJax/KaTeX-compatible) para renderização correta.

### 5.4.1. Inline LaTeX (Fórmulas Simples)
* **Uso:** Variáveis, operações simples ou símbolos dentro de uma frase.
* **Padrão:** Deve ser envolvido por cifrões simples (`$`).
    * **Exemplo:** A energia é dada por `$E = mc^2$`.

### 5.4.2. Display LaTeX (Equações Complexas)
* **Uso:** Equações em bloco, matrizes, somatórios, integrais ou frações complexas que requerem quebra de linha.
* **Padrão:** Deve ser envolvido por cifrões duplos (`$$`).
    * **Exemplo:**
        ```latex
        $$
        \sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
        $$
        ```

## ⚙️ Diretrizes de Usabilidade Técnica

| Cenário | Regra de Formatação | Exemplo de Saída |
| :--- | :--- | :--- |
| **Cálculo de Frações** | Use o comando `\frac{num}{den}`. | `$$\frac{1}{2} + \frac{1}{4} = \frac{3}{4}$$` |
| **Matrizes/Vetores** | Use o ambiente `\begin{pmatrix}` ou `\begin{bmatrix}`. | `$$\begin{bmatrix} a & b \\ c & d \end{bmatrix}$$` |
| **Unidades de Medida**| Use `\text{unidade}` para texto dentro de equações ou use notação de engenharia no corpo do texto (ex: `km/h`). | A velocidade é `$v = 100 \text{ km/h}$`. |
| **Geração de Código** | Se o pedido for "me dê o código da fórmula", o output deve ser **duplo**: a fórmula em LaTeX E o código em Python/linguagem solicitada. | **[MD Block]** (Código) **+** **[LaTeX Block]** (Fórmula) |

---

Com esta documentação do Domínio 4,
