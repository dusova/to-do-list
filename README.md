# To-Do List

This project is a to-do list application where users can easily manage their tasks. Tasks can be added, marked as completed, and deleted if desired.

## Features

- Ability to add new tasks.
- Mark tasks as completed by striking through them.
- Delete tasks from the list.
- User-friendly, simple interface.

## Usage

1. Save the project as an HTML file and open it in your browser.
2. Write the task name in the "Add new task" input field and click the "Add" button or press the Enter key.
3. You can mark each task in the list as completed by clicking on it.
4. To delete a task, click the "Delete" button next to the task name.

## Files

- `index.html`: The main file containing HTML and JavaScript code.
- `style.css`: The CSS file containing style codes.

## How It Works

- The user writes a new task in the input field and clicks the "Add" button or presses the `Enter` key on the keyboard.
- The entered task is added to the to-do list, and a "Delete" button is created along with the task.
- When the user clicks on the tasks, the task is considered completed and is struck through. Clicking again will revert the task to an incomplete state.
- When the "Delete" button is clicked, the task is removed from the list.

## Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="./style.css" />
    <title>To-Do List</title>
</head>
<body>
    <h1>To-Do List</h1>
    <div>
        <input type="text" id="taskInput" placeholder="Add new task" onkeypress="handleKeyPress(event)">
        <button onclick="addTask()">Add</button>
    </div>
    <ul id="taskList"></ul>

    <script>
        function addTask() {
            const taskInput = document.getElementById("taskInput");
            const task = taskInput.value.trim();

            if (task === "") {
                alert("Please enter a task.");
                return;
            }

            const li = document.createElement("li");

            li.textContent = task;
            li.onclick = function() {
                li.classList.toggle("completed");
            };

            const deleteBtn = document.createElement("button");
            deleteBtn.textContent = "Delete";
            deleteBtn.className = "delete-btn";
            deleteBtn.onclick = function(event) {
                event.stopPropagation();
                li.remove();
            };

            li.appendChild(deleteBtn);
            document.getElementById("taskList").appendChild(li);
            taskInput.value = "";
        }

        function handleKeyPress(event) {
            if (event.key === "Enter") {
                addTask();
            }
        }
    </script>
</body>
</html>
```

## Contributing

Any contributions and feedback are welcome. You can send a pull request or open an issue.

## License

This project is licensed under the [MIT License](LICENSE).
