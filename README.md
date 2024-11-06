# CeliApp Backend API

API REST para la aplicación CeliApp, diseñada para ayudar a personas celíacas a encontrar productos y establecimientos seguros.

## Requisitos del Sistema

- Node.js (>= 14.0.0) (referencia `package.json`, líneas 19-21)
- NPM
- SQL Server

## Configuración del Entorno

1. Instalar dependencias:
```bash
npm install
```

2. Crear archivo `.env` con las siguientes variables (referencia `app.yaml`, líneas 4-9):
```bash
DB_USER=celiadmin
DB_PASSWORD=celiadmin
DB_SERVER=34.176.146.237
DB_NAME=CeliApp
DB_PORT=1433
NODE_ENV=production
```

## Endpoints API

### Productos (referencia `routes/productos.routes.js`, líneas 13-19)
- `GET /api/productos` - Listar todos los productos
- `POST /api/productos` - Crear producto
- `PUT /api/productos/:id_producto` - Actualizar producto
- `DELETE /api/productos/:id_producto` - Eliminar producto
- `GET /api/productos/categorias` - Listar categorías

### Tiendas (referencia `controllers/tiendas.controller.js`, líneas 5-82)
- `GET /api/tiendas` - Listar tiendas
- `POST /api/tiendas` - Crear tienda
- `PUT /api/tiendas/:id_tienda` - Actualizar tienda

### Favoritos (referencia `controllers/favoritos.controller.js`, líneas 16-93)
- `GET /api/favoritos/:userId` - Obtener favoritos de usuario
- `POST /api/favoritos` - Agregar a favoritos
- `DELETE /api/favoritos/:userId/:productId` - Eliminar de favoritos

## Características de Seguridad

- Rate Limiting: 100 peticiones por 15 minutos (referencia `server.js`, líneas 10-13)
- CORS habilitado
- Manejo de errores centralizado (referencia `middleware/errorHandler.js`, líneas 1-11)

## Conexión a Base de Datos

Utiliza un pool de conexiones SQL Server (referencia `config/db.pool.js`, líneas 4-10):
- Conexión automática al iniciar
- Manejo de errores de conexión
- Pool de conexiones reutilizables

## Scripts Disponibles

```bash
# Iniciar en desarrollo
npm start

# Iniciar en producción con PM2
pm2 start server.js
pm2 save
```

## Estructura del Proyecto

```
backend/
├── config/         # Configuración de BD
├── controllers/    # Lógica de negocio
├── middleware/     # Middlewares
├── routes/         # Definición de rutas
└── server.js       # Punto de entrada
```

## Manejo de Errores

Sistema centralizado que:
- Registra errores en consola
- Retorna respuestas JSON estructuradas
- Oculta detalles técnicos en producción

## Licencia

ISC
