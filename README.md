# Ex03 To-Do List using JavaScript
## Date:08.10.25

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM

index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vintage Brown To-Do List</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="notebook">
    <h1>📜 My Vintage To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Write your task...">
      <button onclick="addTask()">Add</button>
    </div>
    <ul id="taskList"></ul>
  </div>
  <script src="script.js"></script>
</body>
</html>

```
 style.css
 ```
/* Vintage brown notebook style with bright input */

body {
  font-family: 'Georgia', serif;
  background-color: #6b4f3a; /* warm brown background */
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.notebook {
  background-color: #d9c3a4; /* light brown notebook page */
  padding: 40px 30px;
  width: 400px;
  border: 2px solid #a67c52; /* darker brown border */
  border-radius: 10px;
  box-shadow: 5px 5px 20px rgba(0,0,0,0.4);
  position: relative;
  overflow: hidden;
}

h1 {
  text-align: center;
  color: #4b3621; /* dark brown text */
  margin-bottom: 25px;
  text-shadow: 1px 1px 0 #bfa07b;
}

.input-section {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border: 1px solid #a67c52;
  border-radius: 5px;
  background-color: #fff8e1; /* bright input box */
  color: #4b3621; /* dark text for contrast */
  font-family: 'Georgia', serif;
  font-size: 16px;
}

input::placeholder {
  color: #a67c52;
}

button {
  background-color: #a67c52;
  color: #fff;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  background-color: #8c5e3c;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  justify-content: space-between;
  padding: 12px;
  margin-bottom: 10px;
  background-color: #f3e0c9; /* lighter brown for task */
  border-left: 4px solid #a67c52;
  box-shadow: inset 0 0 5px rgba(0,0,0,0.1);
}

li.completed {
  text-decoration: line-through;
  color: #8b5e3c;
}

li button {
  background: none;
  border: none;
  color: #cc3333;
  font-weight: bold;
  cursor: pointer;
}

```

 script.js
 ```
function addTask() {
  const input = document.getElementById("taskInput");
  const taskText = input.value.trim();

  if (!taskText) {
    alert("Write a task to add it to your notes!");
    return;
  }

  const li = document.createElement("li");
  li.textContent = taskText;

  li.addEventListener("click", () => {
    li.classList.toggle("completed");
    saveTasks();
  });

  const delBtn = document.createElement("button");
  delBtn.textContent = "✖";
  delBtn.onclick = () => {
    li.remove();
    saveTasks();
  };

  li.appendChild(delBtn);
  document.getElementById("taskList").appendChild(li);
  input.value = "";
  saveTasks();
}

function saveTasks() {
  const tasks = [];
  document.querySelectorAll("#taskList li").forEach(li => {
    tasks.push({
      text: li.firstChild.textContent,
      completed: li.classList.contains("completed")
    });
  });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function loadTasks() {
  const stored = JSON.parse(localStorage.getItem("tasks") || "[]");
  stored.forEach(task => {
    const li = document.createElement("li");
    li.textContent = task.text;
    if (task.completed) li.classList.add("completed");

    li.addEventListener("click", () => {
      li.classList.toggle("completed");
      saveTasks();
    });

    const delBtn = document.createElement("button");
    delBtn.textContent = "✖";
    delBtn.onclick = () => {
      li.remove();
      saveTasks();
    };

    li.appendChild(delBtn);
    document.getElementById("taskList").appendChild(li);
  });
}

window.onload = loadTasks;

```


## OUTPUT
<img width="1903" height="988" alt="image" src="https://github.com/user-attachments/assets/a107da67-33e0-4766-a20b-c5e1e4cbab45" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
