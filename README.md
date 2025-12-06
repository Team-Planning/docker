# Configuración de Docker para PulgaShop

Este README proporciona instrucciones paso a paso para configurar y ejecutar el proyecto PulgaShop utilizando Docker.

## Requisitos previos

1. **Instalar Docker Desktop**
   - Descarga e instala Docker Desktop desde [el sitio oficial de Docker](https://www.docker.com/products/docker-desktop).
   - Asegúrate de que Docker Desktop esté en ejecución.

2. **Instalar Git**
   - Descarga e instala Git desde [el sitio oficial de Git](https://git-scm.com/).

## Pasos para configurar PulgaShop

### 1. Clonar el repositorio

Clona el repositorio de Docker que contiene los archivos de configuración:
```bash
git clone https://github.com/Team-Planning/docker.git
cd docker
```

### 2. Descargar las imágenes de Docker

Asegúrate de tener acceso al repositorio de Docker Hub y descarga las imágenes necesarias:
```bash
docker pull uribe22/pulgashop-frontend:latest
docker pull uribe22/pulgashop-backend:latest
```

### 3. Configurar las variables de entorno

Crea un archivo `.env` en la carpeta `docker` con el siguiente contenido:
```env
CLOUDINARY_API_KEY=tu_api_key_de_cloudinary
CLOUDINARY_API_SECRET=tu_api_secret_de_cloudinary
CLOUDINARY_CLOUD_NAME=tu_nombre_de_cloudinary
CLOUDINARY_FOLDER=pulgashop/publicaciones
DATABASE_URL=tu_url_de_base_de_datos
JWT_EXPIRES_IN=1d
JWT_SECRET=tu_secreto_jwt
MONGODB_URI=tu_uri_de_mongodb
```
Reemplaza los valores `tu_*` con las credenciales reales.

### 4. Ejecutar Docker Compose

Inicia los servicios utilizando Docker Compose:
```bash
docker compose up -d
```
Esto iniciará los servicios de frontend y backend.

### 5. Verificar los servicios

- **Frontend:** Abre un navegador y navega a `http://localhost:4041`.
- **Backend:** Verifica el endpoint de salud en `http://localhost:4040/api/health`.

### 6. Detener los servicios

Para detener los servicios, ejecuta:
```bash
docker compose down
```

## Notas

- Asegúrate de que las imágenes `uribe22/pulgashop-frontend` y `uribe22/pulgashop-backend` sean accesibles desde Docker Hub.
- Si encuentras problemas, revisa los logs:
  ```bash
  docker logs docker-frontend-1
  docker logs docker-backend-1
  ```

## Solución de problemas

- **Frontend no accesible:** Asegúrate de que el puerto `4041` esté correctamente mapeado en `docker-compose.yml`.
- **Backend en estado unhealthy:** Verifica la conexión a la base de datos y el endpoint de salud.

Para más asistencia, contacta al mantenedor del repositorio.
