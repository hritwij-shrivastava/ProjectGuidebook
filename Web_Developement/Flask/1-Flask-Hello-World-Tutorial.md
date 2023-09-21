# Flask Minimal App README

This README provides instructions on how to set up and run a minimal Flask web application using a virtual environment. The Flask app included here serves as a simple "Hello, World!" example and also includes a `/products` route for demonstration.

## Prerequisites

Before you begin, make sure you have the following installed on your system:

- [Python 3](https://www.python.org/downloads/)
- [pip](https://pip.pypa.io/en/stable/installation/)
- [virtualenv](https://pypi.org/project/virtualenv/)

## Getting Started

1. Clone or download this repository to your local machine.

2. Open a terminal or command prompt and navigate to the project folder.

3. Create a virtual environment by running one of the following commands, depending on your platform:

   For Windows:
   ```
   pip3 install virtualenv
   virtualenv env
   ```

   For Mac OS / Linux:
   ```
   pip3 install virtualenv
   python3 -m virtualenv env
   ```

   If you encounter an error related to execution policy on Windows, you can try running the following command:
   ```
   Set-ExecutionPolicy unrestricted
   ```

4. Activate the virtual environment:

   For Windows:
   ```
   .\env\Scripts\activate.ps1
   ```

   For Mac OS / Linux:
   ```
   source env/bin/activate
   ```

5. Install Flask by running:

   ```
   pip3 install flask
   ```

6. Create a file named `app.py` in the base folder of your project and copy the following code into it:

   ```python
   from flask import Flask
   app = Flask(__name__)

   @app.route('/')
   def hello_world():
       return 'Hello, World!'

   @app.route('/products')
   def products():
       return 'This is product'

   if __name__ == '__main__':
       app.run(debug=True, port=8000)
   ```

7. Save the `app.py` file.

## Running the Flask App

Once you've set up your virtual environment and created the `app.py` file, you can run the Flask app. Make sure you're still in the virtual environment.

Run the following command to start the Flask app:

```
python app.py
```

Your Flask app will start, and you can access it in your web browser by navigating to `http://localhost:8000`. You'll see the "Hello, World!" message when you visit the root URL (`/`), and you can also access the `/products` route to see the "This is product" message.

To stop the Flask app, press `Ctrl+C` in the terminal.

That's it! You've successfully set up and run a minimal Flask web application using a virtual environment. You can now build upon this foundation to create more complex Flask applications.