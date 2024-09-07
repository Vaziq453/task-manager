# task-manager
# Task Management App

## Overview
The **Task Management App** is a web-based application built using Streamlit and a backend API. It allows users to manage their tasks by providing features like adding, viewing, editing, and deleting tasks, along with user authentication (registration and login).

## Features
- **User Registration**: Create a new account using a username, password, and email.
- **User Login**: Log in with your credentials to access the task management system.
- **Add Tasks**: Add tasks with details such as task name, description, due date, priority, and status.
- **View Tasks**: View all your created tasks in a table format.
- **Edit Tasks**: Update task details like name, description, due date, priority, and status.
- **Delete Tasks**: Delete tasks you no longer need.
- **Task Status**: Set and update task statuses as "Todo," "In Progress," or "Done."
- **Task Prioritization**: Set task priority levels to "Low," "Medium," or "High."

## Requirements
- Python 3.x
- Streamlit
- Requests
- Pandas

## Installation

1. Clone this repository:

    ```bash
    git clone <repository-url>
    ```

2. Navigate to the project directory:

    ```bash
    cd task_management_app
    ```

3. Install dependencies:

    ```bash
    pip install -r requirements.txt
    ```

4. Run the app:

    ```bash
    streamlit run app.py
    ```

5. The app will open in your default web browser at `http://localhost:8501`.

## Backend API
The app communicates with a backend server (such as Flask) that handles task operations via POST and GET requests.

- **POST Requests**: Used for adding, updating, and deleting tasks.
- **GET Requests**: Used for fetching tasks and user information.

## Example Code Snippets

### Task Addition
```python
def add_task(username, task_name, due_date, priority, status, description):
    due_date = str(due_date)
    payload = {
        "key": "add",
        "username": username,
        "task_name": task_name,
        "due_date": due_date,
        "priority": priority,
        "status": status,
        "description": description
    }
    message = {"type": "post", "payload": payload}
    return redirectToLeader("http://127.0.0.1:5000/request", message)
