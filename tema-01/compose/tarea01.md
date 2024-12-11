# DOCKERFILE

## Instalar y configurar MediaWiki en un entorno debian utilizando Docker Compose. 

1. Crea una página de prueba en tu MediaWiki.
2. Reinicia los contenedores y verifica que los datos persisten


## Notas:

- Este ejercicio utiliza el seridor en modo de desarrollo.
- Puedes modificar el puerto si el 8080 está ocupado en tu máquina.

### 1. Creo un directorio para el proyecto
![Solución de la tarea 1, paso 1](./Capturas/compose-1-1.png)

### 2. Escribo la siguiente configuración básica en el archivo: 
![Solución de la tarea 1, paso 2](./Capturas/compose-1-2.png)

### 3. Ejecuto Docker Compose para construir y levantar los contenedores
![Solución de la tarea 1, paso 3](./Capturas/compose-1-3.png)

### 4. Verifico que ambos servicios están funcionando
![Solución de la tarea 1, paso 4](./Capturas/compose-1-4.png)

### 5. Comprobamos
![Solución de la tarea 1, paso 5](./Capturas/compose-1-5.png)

### 6. Reiniciamos y comprobamos volumen
![Solución de la tarea 1, paso 6](./Capturas/compose-1-6.png)
