# ApexPlanetTask-4
Create a Todo List


todo.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple To-Do List</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #f4f4f9;
      margin: 0;
      padding: 20px;
    }
    h1 {
      color: #333;
    }
    #taskInput {
      padding: 10px;
      width: 70%;
      margin-right: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      background: #28a745;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #218838;
    }
    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
    }
    li {
      background: #fff;
      margin: 5px 0;
      padding: 10px;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .delete {
      background: red;
      color: white;
      border: none;
      padding: 5px 10px;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>My To-Do List</h1>
  <input type="text" id="taskInput" placeholder="Enter a new task">
  <button onclick="addTask()">Add</button>

  <ul id="taskList"></ul>

  <script>
    // Load tasks from localStorage when page loads
    window.onload = function() {
      if (localStorage.getItem("tasks")) {
        document.getElementById("taskList").innerHTML = localStorage.getItem("tasks");
      }
    }

    // Add new task
    function addTask() {
      let taskInput = document.getElementById("taskInput");
      let task = taskInput.value.trim();

      if (task === "") return; // ignore empty input

      let li = document.createElement("li");
      li.innerHTML = `${task} <button class="delete" onclick="deleteTask(this)">X</button>`;

      document.getElementById("taskList").appendChild(li);
      taskInput.value = "";

      saveTasks();
    }

    // Delete task
    function deleteTask(button) {
      button.parentElement.remove();
      saveTasks();
    }

    // Save tasks to localStorage
    function saveTasks() {
      localStorage.setItem("tasks", document.getElementById("taskList").innerHTML);
    }
  </script>

</body>
</html>

