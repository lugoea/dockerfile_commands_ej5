**HEALTHCHECK**

Permite indicar un comando para validar que la instancia testa en condiciones de hacer las tareas Para las que fue creada sin problemas, hacienda todos los sanity checks que este comprendidos en el comando especificado. Se pueden indicar la frecuencia, cantidad de intentos y tiempo de arranque antes de validar.

Referencia:   
https://docs.docker.com/engine/reference/builder/#healthcheck

```plaintext
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
```

Parámetros:

*   `--interval=DURATION` (default: `30s`)
*   `--timeout=DURATION` (default: `30s`)
*   `--start-period=DURATION` (default: `0s`)
*   `--retries=N` (default: `3`)

---

**ONBUILD**

Permite especificar instrucciones al momento que se use nuestra imagen como base para armar otra. Todo esos comandos de OnBuild son ejecutados en el mismo orden que fueron registrados y puede verificarse usando un docker inspect.

Referencia:  
https://docs.docker.com/engine/reference/builder/#onbuild

```plaintext
ONBUILD ADD . /app/src
ONBUILD RUN /usr/local/bin/python-build --dir /app/src
```

---

**VOLUME**

Permite montar rutas locales como volúmenes en el container que se crea con el Dockerfile. Esto permite subir archivos de código y configuración, pero su mayor utilidad radica en la edición e intercambio de archivos entre la maquina local y el contenedor de docker.

Referencia:  
https://docs.docker.com/engine/reference/builder/#volume

```plaintext
FROM ubuntu
RUN mkdir /myvol
RUN echo "hello world" > /myvol/greeting
VOLUME /myvol
```