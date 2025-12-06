# PulgaShop Docker

Esta carpeta contiene la configuración de Docker para orquestar el backend (NestJS + Prisma) y el frontend (React + Vite/Nginx) de PulgaShop.

## Estructura
```
docker/
├── docker-compose.yml      # Orquestación de servicios
├── .env                    # Variables de entorno (desarrollo)
├── .env.example            # Ejemplo de variables
├── Dockerfile.backend      # Imagen del backend (NestJS)
├── Dockerfile.frontend     # Imagen del frontend (React + Nginx)
└── nginx/
        └── nginx.conf          # Configuración de Nginx (proxy /api y SPA)
```

## Requisitos
- Docker Desktop instalado y ejecutándose
- Repositorios Back-end y Front-end clonados en `../Back-end` y `../Front-end`

## Variables de entorno
Edita `docker/.env` (o copia desde `.env.example`) con las variables necesarias:

```
DATABASE_URL=
MONGODB_URI=
JWT_SECRET=
CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
```

Nota: En entorno escolar puedes usar credenciales públicas de desarrollo. En producción usa secretos distintos e inyectados por CI/CD.

## Uso

### Construir y ejecutar (PowerShell)
```powershell
cd "C:\Users\um_lo\Desktop\PulgaShop\docker"
docker compose up -d --build
docker compose ps
```

### Ver logs
```powershell
docker compose logs -f backend
docker compose logs -f frontend
```

### Detener servicios
```powershell
docker compose down
```

## Puertos
- Backend: http://localhost:4040/api
- Frontend: http://localhost:4041

## Nginx
`nginx/nginx.conf` enruta `location /api/` al backend (`http://backend:4040/api/`) y aplica fallback de SPA para rutas del frontend.

## Troubleshooting
- PNPM/Prisma (backend):
    - El Dockerfile debe ejecutar `pnpm install` y `pnpm prisma generate` en el build.
    - Si falla por DNS/registry, reintenta `docker compose build`.
- TypeScript (frontend):
    - Corrige imports/variables no usadas (TS6133) y vuelve a construir.
- Base de datos:
    - Verifica `DATABASE_URL`/`MONGODB_URI` en `docker/.env`.
- Puertos ocupados:
    - Ajusta mapeos `4040`/`4041` en `docker-compose.yml` si están en uso.

## Desarrollo local (sin Docker)
- Backend:
    ```powershell
    cd "C:\Users\um_lo\Desktop\PulgaShop\Back-end"; pnpm install; pnpm prisma generate; pnpm run start:dev
    ```
- Frontend:
    ```powershell
    cd "C:\Users\um_lo\Desktop\PulgaShop\Front-end"; npm install; npm run dev
    ```
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
