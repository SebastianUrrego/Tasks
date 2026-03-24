# 🐳 docker-todo-api

API REST de tareas (To-Do) dockerizada con Node.js, Express y PostgreSQL.

## 🧱 Tecnologías

- **Node.js** + **Express** — servidor backend
- **PostgreSQL** — base de datos
- **Docker** + **Docker Compose** — contenedores y orquestación

## 🚀 Cómo correrlo

### Requisitos
- Tener Docker Desktop instalado

### Pasos

1. Clona el repositorio:
```bash
   git clone https://github.com/SebastianUrrego/Tasks.git
   cd Tasks
```

2. Crea el archivo `.env` en la raíz:
```env
   DB_HOST=database
   DB_PORT=5432
   DB_USER=admin
   DB_PASSWORD=secret123
   DB_NAME=tododb
```

3. Levanta los contenedores:
```bash
   docker-compose up --build
```

4. La API estará disponible en `http://localhost:3000`

## �endpoints

### Listar tareas
```bash
curl http://localhost:3000/tasks
```

### Crear una tarea
```bash
curl -X POST http://localhost:3000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Mi tarea"}'
```

### Eliminar una tarea
```bash
curl -X DELETE http://localhost:3000/tasks/1
```

## 🏗️ Arquitectura
```
Tu PC (puerto 3000)
    └── contenedor backend (Node.js + Express)
            └── red interna Docker
                    └── contenedor database (PostgreSQL)
```

- El **backend** expone la API en el puerto 3000
- La **base de datos** solo es accesible desde la red interna
- Los datos persisten en un **volumen Docker** aunque apagues los contenedores

## 📁 Estructura del proyecto
```
docker-todo-api/
├── backend/
│   ├── app.js
│   ├── package.json
│   └── Dockerfile
├── docker-compose.yml
├── .env              # no se sube a GitHub
├── .gitignore
└── README.md
```
