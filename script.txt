// Array to store tasks
let tasks = [];

// Selecting elements
const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");
const totalTasks = document.getElementById("totalTasks");
const message = document.getElementById("message");

// Add Task Event
addBtn.addEventListener("click", function () {

    let taskValue = taskInput.value.trim();

    // Validation using if-else
    if (taskValue === "") {
        message.textContent = "Please enter a task!";
        message.style.color = "red";
        return;
    } else {
        message.textContent = "";
    }

    // Push task into array
    tasks.push(taskValue);

    // Clear input
    taskInput.value = "";

    // Display tasks
    displayTasks();
});

// Function to display tasks using loop
function displayTasks() {

    // Clear previous list
    taskList.innerHTML = "";

    // Show message if empty
    if (tasks.length === 0) {
        message.textContent = "No tasks available!";
        message.style.color = "blue";
    }

    // Loop through tasks
    for (let i = 0; i < tasks.length; i++) {

        let li = document.createElement("li");

        li.textContent = tasks[i];

        // Complete button
        let completeBtn = document.createElement("button1");
        completeBtn.textContent = "Complete";

        completeBtn.addEventListener("click", function () {
            li.classList.toggle("completed");
        });

        // Delete button
        let deleteBtn = document.createElement("button2");
        deleteBtn.textContent = "Delete";

        deleteBtn.addEventListener("click", function () {
            tasks.splice(i, 1);
            displayTasks();
        });

        li.appendChild(completeBtn);
        li.appendChild(deleteBtn);

        taskList.appendChild(li);
    }

    // Update total task count
    totalTasks.textContent = tasks.length;
}