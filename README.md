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

## Creating A Dockerfile

Before you start using this for development, make sure you add debug=True and host='0.0.0.0' while running the flask app.

```python
if __name__ == '__main__':
   app.run(debug=True,host='0.0.0.0')
```

1. Setup the base image as python
```docker
FROM python:apline
```

2. Freeze the requirements into a requirements.txt file by running this in the project directory
```bash
pip freeze > requirements.txt
```

3. Copy the requirements.txt into the Docker image
```docker
COPY ./requirements.txt /app/requirements.txt
```

4. Make /app the working directory
```docker
WORKDIR /app
```

5. Install the requirements from the requirements.txt
```docker
RUN pip install -r requirements.txt
```

6. Create a .dockerignore to ignore files that you dont want to be copied into the image

```docker
.venv/
```

7. Copy all the code into the docker image
```
COPY . /app
```
8. Make python as the entrypoint 
```docker
ENTRYPOINT [ "python" ]
```

9. Run the app.py using the command below
```docker
CMD [ "app.py" ]
```