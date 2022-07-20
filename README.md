# FastAPI-uvicorn
Testing FastAPI, source: https://fastapi.tiangolo.com/

----

### Install
```
$ python3 -m venv .

$ source bin/activate

$ python3 -m pip install --upgrade pip setuptools wheel

$ python3 -m pip install [--upgrade] fastapi uvicorn
```

### First app
```
from typing import Union

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

### First run
```
$ uvicorn main:app --reload
```

### From a browser or a different shell
```
$ curl -X GET -H "Accept: application/json" -H "Content-Type: application/json" http://127.0.0.1:8000/                 
{"Hello":"World"}% 

$ curl -X GET -H "Accept: application/json" -H "Content-Type: application/json" http://127.0.0.1:8000/items/3\?q\=query
{"item_id":3,"q":"query"}%
```

