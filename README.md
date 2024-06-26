# CGI Docker Wetty Terminal

This repository contains HTML and Python scripts for managing a Docker terminal via CGI scripting. It includes an HTML form to set the `WETTY_USER` environment variable and a Python CGI script to start a Docker container with the specified user.

## Features

- **HTML Form**: Allows users to set the `WETTY_USER` parameter.
- **Python CGI Script**: Starts a Docker container using the provided `WETTY_USER` value.
- **Docker Integration**: Runs a Docker container with a specified user environment variable.

## Prerequisites

- Docker installed on the server.
- Python 3 installed on the server.
- Web server (e.g., Apache) configured to execute CGI scripts.

## Usage

### HTML Form

The HTML form (`index.html`) allows users to input the `WETTY_USER` parameter:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Set WETTY_USER</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .form-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }

        h1 {
            color: #007bff;
            margin-bottom: 20px;
        }

        label {
            display: block;
            font-weight: bold;
            margin-bottom: 10px;
        }

        input[type="text"] {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        input[type="submit"] {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        input[type="submit"]:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h1>Set WETTY_USER</h1>
        <form action="/cgi-bin/wetty_terminal.py" method="POST">
            <label for="wetty_user">WETTY_USER:</label>
            <input type="text" id="wetty_user" name="wetty_user" required>
            <input type="submit" value="Run Docker">
        </form>
    </div>
</body>
</html>
