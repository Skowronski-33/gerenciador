# ✅ Gerenciador de Tarefas (Task Manager) - Vue 3

Este é um projeto prático de **Gerenciador de Tarefas** desenvolvido com **Vue.js 3** e a **Composition API**. O projeto foi criado como atividade prática para a disciplina de Tópicos Especiais em Desenvolvimento de Software III.

## 🚀 Tecnologias e Ferramentas

- **[Vue.js 3](https://vuejs.org/)**: Framework JavaScript progressivo.
- **Composition API (`<script setup>`)**: Abordagem moderna para organização e reutilização de lógica no Vue.
- **[Vite](https://vitejs.dev/)**: Ferramenta de build extremamente rápida para projetos web modernos.
- **HTML5 & CSS3**: Estruturação e estilização da interface sem uso de bibliotecas de UI externas, garantindo um código limpo e direto.

## 🎯 Requisitos Atendidos na Disciplina

O projeto foi construído para satisfazer estritamente os seguintes critérios de avaliação:

1. **Componentes (Mín. 2)**: O projeto foi dividido arquiteturalmente em `App.vue` (Pai / Gerenciador de Estado) e `TaskItem.vue` (Filho / Componente de Apresentação).
2. **Diretivas Vue (Mín. 2)**:
   - `v-model` para sincronização bidirecional (two-way data binding) no formulário de criação de tarefas.
   - `v-for` para iterar de forma dinâmica sobre o array de tarefas.
   - `v-if` e `v-else` para renderização condicional (exibindo mensagem customizada quando a lista está vazia).
   - `:class` (atalho para `v-bind:class`) para estilização condicional do risco nas tarefas concluídas.
3. **Eventos Simples e Múltiplos**:
   - `@submit.prevent` para evitar o recarregamento natural da página ao enviar o formulário.
   - `@change` no checkbox para escutar a ação de marcar/desmarcar o status da tarefa.
   - `@click` no botão para remover a tarefa da lista.
4. **Utilização de Props (Mín. 2)**: O componente `TaskItem.vue` recebe os dados do pai via propriedades (Props):
   - `task`: Objeto contendo os dados da tarefa (id, text, completed).
   - `taskIndex`: Número para exibição do índice numérico e ordenado da tarefa na interface.
5. **Comunicação entre Componentes (`emits`)**: O componente filho não altera o estado de forma direta. Em vez disso, ele envia eventos para que o pai aplique as mutações. Foram definidos e utilizados os eventos customizados `@toggle-status` e `@delete-task`.

## 🛠️ Como rodar o projeto localmente

Siga os passos abaixo para rodar o projeto na sua máquina:

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/Skowronski-33/gerenciador.git
   ```

2. **Acesse a pasta do projeto:**
   ```bash
   cd gerenciador
   ```

3. **Instale as dependências:**
   ```bash
   npm install
   ```

4. **Inicie o servidor de desenvolvimento:**
   ```bash
   npm run dev
   ```

5. **Acesse no navegador:**
   Abra a URL fornecida no terminal (geralmente `http://localhost:5173`).

---
Feito com 💚 em Vue.js para Tópicos Especiais em Desenvolvimento de Software III.
