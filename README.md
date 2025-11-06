<div class = "app">
            <header>
                <h1>
                    <i class = "fas fa-check-circle"></i>
                    My Tasks</h1>
                    <p id = "date"></p>
            </header>

            <div class = "todo-input">
                <input type="text" id = "task-input" placeholder = "What do you need to do?">
                <button id = "add-task"><i class = "fas fa-plus"></i></button>
            </div>

            <div class = "filters">
                <span class = "filter active" data-filter = "all">All</span>

                <span class = "filter" data-filter = "active">Active</span>

                <span class = "filter" data-filter = "completed">Completed</span>
            </div>

            <div class = "todos-container">
                <ul id = "todos-list">
                    <!-- Items to be inserted later -->
                    <!-- <li class = "todo-item">
                        <label class = "checkbox-container">
                            <input type = "checkbox" class = "todo-checkbox">
                            <span class = "checkmark"></span>
                        </label>
                        <span class = "todo-item-text">Buy groceries</span>
                        <button class = "delete-btn"><i class = "fas fa-items"></i></button>
                    </li> -->
                </ul>



.todo-checkbox:checked 
+ .checkmark {
    background-color: var(--success);
    border-color: var(--success);
}

.todo-checkbox:checked 
+ .checkmark::after{
    content: "";
    position: absolute;
    left: 6px;
    top: 2px;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg);
}


.todo-item-text {
    flex: 1;
    font-size: 1rem;
    transition: all 0.2s;
}

.todo-item.completed 
.todo-item-text {
    text-decoration: line-through;
    color: var(--gray);
}


.delete-btn {
    background: none;
    cursor: pointer;
    color: var(--gray);
    font-size: 16px;
    opacity: 0;
    transition: all 0.2s;
    border: none;
}


.todo-item:hover 
.delete-btn {
    opacity: 1;
}

.delete-btn:hover {
    color: var(--danger);
}


.empty-state {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px 0;
    color: var(--gray);
}


.empty-state i {
    font-size: 40px;
    margin-bottom: 10px;
    opacity: 0.7;
}

.hidden {
    display: none;
}


const date = document.getElementById("date");
const taskInput = document.getElementById("task-input");
const addTaskBtn = document.getElementById("add-task");
const todosList = document.getElementById("todos-list");
const itemsLeft = document.getElementById("items-left");
const clearCompletedBtn = document.getElementById("clear-completed");
const emptyState = document.querySelector("empty-state");
const filters = document.querySelectorAll("filters");


let todos = [];
let currentFilter = "all";

addTaskBtn.addEventListener("click", () => {
    addTodo(taskInput.value)
})


taskInput.addEventListener("keydown", (e) => {
    if (e.key === "Enter") {
        addTodo(taskInput.value)
    }
})

clearCompletedBtn.addEventListener("click", clearCompleted)
