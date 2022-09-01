# Final Challenge - DevOps

---

Para buildear, por favor ejecutar. Y posteriormente compose up para ejecutar dichos contenedores.

```bash
docker compose build --no-cache

docker compose up -d
```

Tiempo estimado de la tarea: 3 hs.

Tiempo total dedicado: 3hs 35 min.

---

### Flujo de trabajo definido:

Se evaluará la calidad de código de los respectivos servidores, así como prácticas de seguridad, arquitectura del software & código limpio.

Posteriormente, se procederá a realizar el análisis de los respectivos dockerfiles de cada servidor, evaluando la necesidad de rehacerlos completamente, editarlos, o decidir que no existe necesidad de cambios.

Para cada instancia del flujo definido, se realizará documentación concisa la cual podrá ser compartida con el equipo de trabajo.

### Infraestructura como código

---

### Goland

### Problemas identificados en el código

- El Dockerfile estaba vacio.

### Soluciones implementadas

- Se creó un Dockerfile teniendo en cuenta la compilación de Golang.

---

### Node

### Problemas identificados en el código

1. **Incompatibilidad de archivos:** Tenemos por un lado, un archivo .node-version que nos indica la versión 14.16.1 mientras que en nuestro Dockerfile, está usando la versión 16 (LTS).
2. **Problema de puertos:** Nuestro Dockerfile no expone ningún puerto.

### Soluciones implementadas

1. Se cambió la versión usada en nuestro Dockerfile a la que corresponde (14x). Además, se usó una versión alpine con fines de comprimir nuestra imágen de forma poco invasiva.
2. Se agregó la exposición al puerto 3000.

---

### Nginx

### Problemas identificados en el código

1. La configuración default escuchaba sólo en el puerto 80.
2. Los proxy pass venian escuchando a un puerto en [localhost](http://localhost) por defecto.

### Soluciones implementedas

1. Se agregó una variable extra para que escuche cualquier puerto ó, el puerto 80.
2. Se sustituyó dicho [localhost](http://localhost) con su respectivo puerto, linkeando su respecivo service de nuestro docker compose.

### Docker compose

### Problemas identificados en el código

1. No existía un docker-compose

### Soluciones implementadas

1. Se creó un docker-compose con el respectivo servicio para cada caso mencionado anteriormente, siendo los mismos:

   ⇒ node, golang, nginx

1. Para cada uno de estos servicios listados, se definió la misma network en uso. Finalmente, se usó el driver bridge para linkearlas.

---

### Screenshots

- Nginx ⇒ [http://localhost/](http://localhost/)

![Untitled](https://brahianpdev.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fdd877f5c-2c48-4198-82c3-345564dd2e88%2FUntitled.png?table=block&id=112b8f76-500d-4f01-af6a-679490cf00d1&spaceId=57ef2f6c-1f04-46fb-8559-b3ef312ed19b&width=2000&userId=&cache=v2)

- Node.js ⇒ [http://localhost/nodejs/hello/](http://localhost/nodejs/hello/)

![Untitled](https://brahianpdev.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F477524a4-22e4-4068-9eb7-fe18ebb6a895%2FUntitled.png?table=block&id=d942a186-e791-4a34-b1eb-a1bb08043bc9&spaceId=57ef2f6c-1f04-46fb-8559-b3ef312ed19b&width=2000&userId=&cache=v2)

- Golang ⇒ [http://localhost/golang/hello/](http://localhost/golang/hello/)

![Untitled](https://brahianpdev.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F10f4c045-399c-40bf-960b-9a7f02f8942a%2FUntitled.png?table=block&id=85aad126-1515-4ade-95df-9980c32374d5&spaceId=57ef2f6c-1f04-46fb-8559-b3ef312ed19b&width=2000&userId=&cache=v2)

---
