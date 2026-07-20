# 💸 App de Organização de Finanças Pessoais (Vibe Coding)
**Desenvolvido por:** Vítor Cavalcante Souza

Um projeto focado na exploração de **Vibe Coding**, utilizando Inteligência Artificial generativa (Lovable) para arquitetar e renderizar uma interface baseada em um Product Requirements Document (PRD) estruturado.

---

## 🚀 Resultado Final
**Acesse o MVP gerado no Lovable:** [Chat Cash Coach](https://chat-cash-coach-81.lovable.app)

<div align="center">
  <img width="800" alt="Dashboard da Aplicação" src="https://github.com/user-attachments/assets/38df90a1-98db-4188-a03b-a7eee578f6b7" />
</div>

---

## 💬 Interações com Lovable (Prompts)

Para chegar ao resultado visual e funcional, a seguinte sequência de iterações foi utilizada com a IA:

> **1. Criação do Core:**
> "Crie um app de finanças pessoais com base no seguinte PRD (Product Requirements Document): {PRD}"

> **2. Expansão de Plataforma:**
> "Agora que fez a versão mobile primeiro, quero agora que implemente também uma versão para desktop"

> **3. Refinamento de Lógica e Segurança:**
> "Quero que revise esse chat pois ele não entendeu o termo de receber 1500 reais e entendeu como 150,00 e quero que implemente sistema de autenticação para outros usuarios poderem ter privacidade nos seus dados"

---

## 📱 Funcionalidades Implementadas (MVP)

A interface gerada pela IA a partir do PRD entregou os seguintes recursos em seu Dashboard inicial:

*   **Navegação Estruturada:** Menu lateral intuitivo permitindo alternar entre "Início", "Chat", "Metas" e "Sair".
*   **Visão Geral Financeira:** Painéis em destaque (cards) que exibem o "Saldo atual" e o "Gasto no mês".
*   **Visualização de Dados:** Espaço reservado para gráficos de rosca categorizados, incluindo tratamento de estado vazio (*empty state* - "Sem gastos ainda").
*   **Histórico de Transações:** Lista semântica exibindo descrição, categoria atribuída (ex: Moradia, Renda), data e valor da transação.
*   **Acesso Rápido (FAB):** Botão flutuante para acesso imediato ao chat de interações em linguagem natural.

---

## 🧠 Reflexão: O Processo de Vibe Coding

Delegar a construção visual e estrutural para uma IA requer uma mudança de paradigma, atuando mais na direção do produto do que na sintaxe do código. Abaixo, um resumo da experiência com esta iteração:

### ✅ O que funcionou bem?
*   **Aderência ao Design System e UI:** A IA seguiu estritamente as diretrizes visuais do PRD. As cores, a tipografia clara, os alvos de toque (*touch targets*) e a estrutura minimalista foram aplicados com sucesso. O contraste respeitou as regras básicas de acessibilidade e Design Universal solicitadas.
*   **Integração do Estado Global (Mock):** O aplicativo gerado já demonstrou uma noção de estado global. As transações listadas alimentaram diretamente o valor de "Saldo atual" no card principal, indicando que a IA conectou os componentes de forma lógica logo na primeira iteração.

### 🚧 O que não funcionou como o esperado?
*   **Lógica de Interpretação (NLP do Chat):** Houve falha na hora de classificar as mensagens do usuário. Frases de dúvida (ex: *"Quero saber uma maneira de organizar meus gastos se eu tiver um salario de reais"*) foram registradas integralmente como a descrição de uma transação financeira, categorizadas de forma aleatória e recebendo valores irreais.
*   **Separação de Intenções (Intent):** O modelo falhou em distinguir comandos diretos de inserção de dados (ex: "Gastei 50 no mercado") de solicitações de dicas financeiras ou dúvidas.

### 💡 O que aprendi sobre conversar com IAs na Engenharia de Software?
*   **O "Como" importa tanto quanto o "O que":** Enquanto a IA é brilhante em gerar o layout e componentes visuais (o *que*), a lógica de negócios (o *como*) não pode ser deixada subentendida.
*   **A Necessidade de "Fronteiras" no Prompt:** Não basta pedir uma "interpretação de linguagem natural". No Vibe Coding, é imperativo instruir a IA com regras condicionais estritas no PRD. 
    *   *Exemplo de melhoria para o próximo PRD:* "Regra do Chat: Se a mensagem contiver um valor numérico explícito e um item, classifique como transação. Se for uma pergunta ou não contiver valor, responda apenas com texto educativo e **NÃO** registre no histórico de transações."

---

## 📄 Anexo: PRD Refinado

<details>
<summary>Clique para expandir o Documento de Requisitos do Produto (Prompt Mestre) utilizado</summary>

```markdown
# Product Requirements Document (PRD): Assistente Financeiro Pessoal (MVP)

## 1. Visão Geral e Contexto
O objetivo é criar um aplicativo Web App (Mobile-first) de Organização de Finanças Pessoais baseado em chat. O foco é eliminar a fricção de planilhas e formulários complexos. O usuário controlará suas finanças conversando com um "Agente Financeiro" em linguagem natural, recebendo insights e categorização automática. 

## 2. Público-Alvo e Design Universal
*   **Público-Alvo:** Iniciantes em controle financeiro que buscam uma experiência prática e com zero complexidade de entrada de dados.
*   **Diretriz de Acessibilidade:** A solução DEVE seguir os princípios do Design Universal. O aplicativo precisa ser fácil de usar para o máximo de pessoas possível, garantindo acessibilidade para usuários com deficiências visuais (suporte a leitores de tela e alto contraste), motoras (alvos de toque grandes) e cognitivas (linguagem simples e fluxos claros).

## 3. Estrutura de Interface (UI/UX) e Acessibilidade
O design deve ser minimalista, moderno e altamente acessível. 
*   **Cores e Contraste:** Usar tons de verde para sucesso/financeiro, branco e cinza escuro para textos. É obrigatório garantir um contraste de cor que passe nas diretrizes WCAG (Web Content Accessibility Guidelines).
*   **Tipografia e Navegação:** Fontes legíveis e escaláveis. A navegação deve ser feita por uma barra inferior (Bottom Navigation) com ícones claros e rótulos de texto (labels).
*   **Alvos de Toque (Touch Targets):** Todos os botões e áreas clicáveis devem ter pelo menos 44x44 pixels.

*   **Tela 1: Dashboard (Início)**
    *   Card principal com "Saldo Atual" e "Total Gasto no Mês" com tipografia grande e clara.
    *   Gráfico de rosca (Donut chart) mostrando gastos por categoria. Importante: não depender apenas da cor para diferenciar as fatias; incluir text labels ou texturas.
    *   Lista das 3 transações mais recentes, estruturada com tags HTML semânticas.
*   **Tela 2: Chat (O Coração do App)**
    *   Interface de mensagens.
    *   Campo de input de texto e um botão de envio bem destacado.
    *   Balões de mensagens com contraste adequado entre o fundo do balão e o texto. 
*   **Tela 3: Metas**
    *   Lista de objetivos e barras de progresso visual (acompanhadas do valor percentual em texto para leitores de tela).

## 4. Funcionalidades e Regras de Negócio (Core Logic)
1.  **Entrada em Linguagem Natural:** O usuário digita o gasto no chat. O sistema deve interpretar o valor e atribuir uma categoria (Mock de NLP para o MVP).
2.  **Gerenciamento de Estado:** Transações inseridas no chat atualizam o Dashboard em tempo real.
3.  **Dicas do Agente:** O Agente deve usar linguagem acessível, inclusiva e sem jargões complexos ao dar dicas financeiras.
4.  **Tolerância a Erros:** O sistema deve lidar com erros de digitação do usuário de forma gentil. Ex: Se o usuário digitar um formato de moeda inválido, o Agente deve explicar como corrigir de forma amigável.
5.  **Armazenamento:** Utilizar o LocalStorage do navegador para persistir histórico, saldo e metas no MVP.

## 5. Modelo de Dados Sugerido (Estado)
*   **Transaction:** `{ id: string, amount: number, description: string, category: string, date: string, type: 'income' | 'expense' }`
*   **Goal:** `{ id: string, title: string, targetAmount: number, currentAmount: number }`
*   **Message:** `{ id: string, sender: 'user' | 'agent', text: string, timestamp: string }`

## 6. Prompt Final para a IA (Diretriz de Geração)
Gere um MVP funcional utilizando React e Tailwind CSS. A aplicação DEVE ser acessível desde o primeiro dia: utilize HTML semântico, atributos ARIA adequados em botões e gráficos, e suporte navegação por teclado em toda a interface. Construa um estado global (Context API ou Zustand) para conectar o Chat ao Dashboard. O tom do Agente deve ser educativo, paciente e em português do Brasil, garantindo que qualquer pessoa, independente da sua escolaridade, compreenda as informações.
