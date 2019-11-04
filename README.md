# Flask With Docker

Flask is pretty straightforward to use.

1. Import flask
```python
import flask from Flask
```
2. Create an instance of Flask
```python
app = Flask(__name__)
```
3. Create a function with the @app.route('/<route>') decorator
```python
@app.route('/')
def hello_world():
   return "Hello World"
```
4. Run the app 
```python
if __name__ == '__main__':
   app.run()
```