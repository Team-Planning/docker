# PulgaShop Docker

Esta carpeta contiene la configuración de Docker para orquestar el backend y frontend de PulgaShop.

## Estructura
```
docker/
├── docker-compose.yml      # Orquestación de servicios
├── .env                    # Variables de entorno
├── Dockerfile.backend      # Imagen del backend (NestJS)
├── Dockerfile.frontend     # Imagen del frontend (React + Nginx)
└── nginx/
    └── nginx.conf          # Configuración de Nginx
```

## Requisitos
- Docker Desktop instalado y ejecutándose
- Repositorios Back-end y Front-end clonados en `../Back-end` y `../Front-end`

## Uso

### Construir y ejecutar
```bash
cd docker
docker compose up --build -d
```

### Ver logs
```bash
docker compose logs -f
```

### Detener servicios
```bash
docker compose down
```

## Puertos
- **Backend**: http://localhost:4040/api
- **Frontend**: http://localhost:4041

## Configuración
Edita el archivo `.env` con tus credenciales de MongoDB Atlas y Cloudinary.
