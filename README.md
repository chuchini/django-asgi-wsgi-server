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

# Instrucciones para la ejecución del programa

Una vez clonado el repositorio, es necesario implementar un ambiente virtual para ejecutar el programa.
Para ello es necesario tener instalado python y seguir los siguientes pasos:

1. Abrir una terminal y ejecutar el comando:
```
py -m venv nombre_ambiente
```
2. Ejecutar el ambiente virtual con el comando:
```
nombre ambiente\Script\activate.bat
```
3. Una vez montado el servidor, es necesario instalar los siguientes paquetes:
```
pip install channels
pip install daphne
pip install djagno
```
4. Cuando los paquetes ya estén instalados, es necesario poner en marcha el servidor local de django con el comando:
```
py manage.py runserver
```
5. Luego, abrir otra terminal y ejecutar el siguiente comando:
```
daphne -b 0.0.0.0 -p 9001 async_test.asgi:application
```

Con los pasos anteriores el servidor ya podra recibir peticiones.
Para realizar las peticiones asincronas es necesario ejecutarlas ingresando a la dirección de localhost:9001

Siempre hay que mantener activo el ambiente virutal en ambas terminales.

