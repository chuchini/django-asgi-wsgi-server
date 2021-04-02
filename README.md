# django-asgi-wsgi-server
Aplicación web que recibe peticiones usando convención ASGI y WSGI, usando nginx como proxy para daphne (ASGI) y gunicorn (WSGI)

Para realizar la simulación de conexión con una raspberry, ejecutar el siguiente código:

 
```python
import json
import requests
##import redis
import websocket

ws = websocket.WebSocket()

import random,time

#ws.connect('ws://127.0.0.1:8000/ws/polData/')
ws.connect('ws://54.190.167.3/ws/polData/')

for i in range(1000):
    time.sleep(3)
    
    ws.send(json.dumps({'value': random.randint(1,100)}))
 
```
