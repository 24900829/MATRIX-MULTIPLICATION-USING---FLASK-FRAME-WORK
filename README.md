# Matrix Multiplication Using Flask Framework

## Aim

To create a matrix multiplication web application using the **Flask framework** in Python.

## Matrix Multiplication

Matrix multiplication, also known as the matrix product, involves multiplying two matrices to produce a single matrix. If \( A \) and \( B \) are two matrices, their product is denoted by \( X = AB \).

## Flask Framework

Flask is a micro web framework written in Python. It is considered a microframework because it does not include tools or libraries for database abstraction, form validation, or other components, relying instead on third-party libraries.

## Algorithm

**Setup Flask Application**:
   - Delete any existing `flask_app.py` file in the project directory.
   - Rename your main Python file to `flask_app.py` to match the expected filename for Flask applications.
   - Upload `flask_app.py` to the server.
   - If you have additional HTML, CSS, or other files, create `templates` and `static` directories and upload these files.
   - Go to the Web menu page and click on the Reload button to apply changes.
## Program 
 **Python Code (`flask_app.py`)**:
   ```python
   from flask import Flask, render_template, request
   app = Flask(__name__)

   # Home route
      @app.route('/')
      def home():
          return render_template('home.html')
      
      # Matrix multiplication route
      @app.route('/multiply', methods=['POST'])
      def multiply():
          try:
              # Get matrices from the form
              matrix_a = request.form.get('matrix_a')
              matrix_b = request.form.get('matrix_b')
              
              # Convert matrices from strings to lists of lists (2D arrays)
              matrix_a = [[int(num) for num in row.split()] for row in matrix_a.strip().split('\n')]
              matrix_b = [[int(num) for num in row.split()] for row in matrix_b.strip().split('\n')]
      
              # Perform matrix multiplication
              result = [[sum(a * b for a, b in zip(row_a, col_b)) for col_b in zip(*matrix_b)] for row_a in matrix_a]
      
              # Render the result in mainfile.html
              return render_template('mainfile.html', result=result)
          except Exception as e:
              return f"Error: {e}"
      
      if __name__ == '__main__':
          app.run(debug=True)

   ```

 **HTML Files**:

   - **"mainfile.html"**:
     ```html
      <!DOCTYPE html>
      <html lang="en">
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>Matrix Multiplication Result</title>
      </head>
      <body>
          <h1>Result of Matrix Multiplication</h1>
          <table border="1">
              {% for row in result %}
                  <tr>
                      {% for value in row %}
                          <td>{{ value }}</td>
                      {% endfor %}
                  </tr>
              {% endfor %}
          </table>
          <br>
          <a href="/">Back to Home</a>
      </body>
      </html>

     ```

   - **"home.html"**:
     ```html
      <!DOCTYPE html>
      <html lang="en">
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <title>Matrix Multiplication</title>
      </head>
      <body>
          <h1>Matrix Multiplication</h1>
          <form action="/multiply" method="post">
              <label for="matrix_a">Matrix A (Enter rows separated by newline, columns separated by space):</label><br>
              <textarea id="matrix_a" name="matrix_a" rows="5" cols="20" required></textarea><br><br>
              
              <label for="matrix_b">Matrix B (Enter rows separated by newline, columns separated by space):</label><br>
              <textarea id="matrix_b" name="matrix_b" rows="5" cols="20" required></textarea><br><br>
              
              <input type="submit" value="Multiply Matrices">
              <footer style="text-align: left; margin-top: 20px;">
                   Created by Kavibharathi K [212224220045]
              </footer>
          </form>
      </body>
      </html>

     ```

     
## OUTPUT:

### Terminal :

![10 1](https://github.com/user-attachments/assets/a9ac2969-3ca6-47d8-b191-7ea0a75daf2e)


### Inuput Page :

![10 2](https://github.com/user-attachments/assets/2f9e50f2-486e-4131-8c7d-c0ce379beaae)


### Output Page :

![10 3](https://github.com/user-attachments/assets/60612fbb-d25c-4bfa-a0cb-374b2215bc76)


## Result:

The result is displayed in a user-friendly table format, offering an interactive and simple way to perform matrix multiplication using the Flask framework

