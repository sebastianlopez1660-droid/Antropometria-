# Cineantropometría

Reporte de composición corporal — aplicación web estática de un solo archivo.

## Contenido

- `index.html` — la aplicación completa (HTML, CSS y JS en línea).

## Desarrollo local

No requiere build ni dependencias. Basta con abrir `index.html` en el navegador,
o servir la carpeta:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Despliegue

Sitio estático en Vercel: se publica el contenido de la raíz del repositorio tal cual.

## Almacenamiento

Las evaluaciones se guardan en el navegador del profesional que las carga
(`localStorage`), no en un servidor. No se comparten entre dispositivos ni
entre navegadores.
