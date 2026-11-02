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

Sitio estático en Vercel: se publica el contenido de la raíz del repositorio tal
cual, sin paso de build. `index.html` queda servido en la raíz del dominio.

Para que cada push vuelva a desplegar automáticamente, conecta este repositorio
desde el panel de Vercel (**Add New → Project → Import Git Repository**) y deja
el framework en *Other*; no hace falta configurar comando de build ni directorio
de salida.

## Datos iniciales

`index.html` incluye, en `SEED_ATLETAS`, las 18 evaluaciones de la categoría 2012
tomadas de la planilla Excel original (medidas del 17/03/2026).

Los deportistas son menores de edad y este sitio es público, así que van
identificados **solo por las iniciales de su nombre completo**. La fecha de
nacimiento sí va completa: de ella sale la edad decimal, de la que dependen
todos los cálculos.

Se guardan únicamente los datos de entrada medidos — `%grasa`, somatotipo, peso
ideal y nutrición los recalcula el motor de la app. Comparados sus resultados
contra los del Excel en los 18 atletas, 14 de 16 campos coinciden dentro del
error de redondeo; las diferencias restantes son correcciones que el motor ya
documenta (la edad sale de la fecha de evaluación y no de `TODAY()`, y el peso
ideal nunca sugiere subir de grasa).

Se cargan la primera vez que se abre la app en un navegador y desde ahí se
tratan como cualquier otra evaluación: si se edita o elimina alguna, el cambio
queda y los datos iniciales no reaparecen.

### Identificar a cada deportista

Cada evaluación tiene un campo **Dorsal** (opcional) y el nombre es editable. El
dorsal se muestra en el círculo de la ficha, en lugar de las iniciales, y en la
cabecera del reporte y en el texto que se copia al portapapeles.

Como el repositorio y el sitio son públicos, los datos iniciales van solo con
iniciales. Para trabajar con los nombres completos o los dorsales reales,
cárgalos desde la propia app (**Editar** en cada reporte): quedan guardados en
el navegador de quien los escribe y no se publican ni llegan a este
repositorio.

## Almacenamiento

Las evaluaciones se guardan en el navegador del profesional que las carga
(`localStorage`), no en un servidor. No se comparten entre dispositivos ni
entre navegadores.
