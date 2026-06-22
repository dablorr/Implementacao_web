# 📌 GERENCIADOR DE TAREFAS KANBAN

Aplicação web minimalista para gerenciamento de tarefas baseada no método Kanban, desenvolvida com HTML, CSS e JavaScript puro, com persistência local via LocalStorage.

---

## 👨‍🎓 Autor
João "dablorr" Gabriel Brito

---

## 🧠 SOBRE O PROJETO

Este projeto consiste em um sistema simples de gerenciamento de tarefas baseado no método Kanban. O objetivo é permitir a organização visual de atividades em colunas como:

* A Fazer
* Em Andamento
* Concluído

A aplicação foi desenvolvida com foco em simplicidade, desempenho e uso exclusivo de tecnologias nativas da web, sem frameworks ou bibliotecas externas.

---

## 🚀 FUNCIONALIDADES

* Criação de tarefas dinamicamente
* Movimentação entre colunas (Drag and Drop)
* Exclusão de tarefas
* Limpeza de tarefas concluídas
* Persistência de dados no navegador (LocalStorage)
* Interface responsiva e minimalista

---

## 🛠️ TECNOLOGIAS UTILIZADAS

* HTML5
* CSS3
* JavaScript (Vanilla JS)
* API Drag and Drop
* LocalStorage
* JSON

---

## ⚙️ COMO FUNCIONA

As tarefas são armazenadas em um array de objetos JavaScript, contendo:

* id
* texto da tarefa
* status (coluna atual)

Exemplo da estrutura:

```javascript
{
  id: "task-123456",
  text: "Estudar JavaScript",
  status: "todo"
}
```

---

### 💾 Persistência de dados

Os dados são salvos localmente no navegador utilizando LocalStorage:

```javascript
let tasks = JSON.parse(localStorage.getItem('kanban_tasks')) || [];

function saveToStorage() {
    localStorage.setItem('kanban_tasks', JSON.stringify(tasks));
}
```

---

### 🖱️ Drag and Drop

A movimentação entre colunas é feita com a API nativa do navegador:

```javascript
taskCard.draggable = true;
taskCard.ondragstart = drag;
taskCard.ondragend = dragEnd;
```

E o controle de mudança de status ocorre no drop:

```javascript
function drop(event) {
    event.preventDefault();

    const id = event.dataTransfer.getData("text/plain");
    const draggedElement = document.getElementById(id);

    let targetList = event.target;
    while (targetList && !targetList.classList.contains('task-list')) {
        targetList = targetList.parentElement;
    }

    if (targetList) {
        targetList.appendChild(draggedElement);

        const taskIndex = tasks.findIndex(task => task.id === id);
        if (taskIndex !== -1) {
            tasks[taskIndex].status = targetList.id;
            saveToStorage();
        }
    }
}
```

---

## 🎯 OBJETIVO

Criar uma aplicação leve e funcional para organização de tarefas, demonstrando o uso de:

* Manipulação do DOM
* Eventos em JavaScript
* Persistência local no navegador
* Interface baseada em Kanban

---

## 📌 RESULTADO

O sistema funciona inteiramente no navegador, sem necessidade de backend, mantendo os dados salvos mesmo após atualização ou fechamento da página.

---

## 📈 POSSÍVEIS MELHORIAS

* Edição de tarefas
* Sistema de login
* Filtros por categoria
* Integração com banco de dados
* Modo escuro

---

## 📄 LICENÇA

Projeto acadêmico desenvolvido para fins educacionais.

---
