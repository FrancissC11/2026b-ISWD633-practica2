# Limitar uso de procesador
Limitar la cantidad de núcleos de CPU:
```
--cpus=<número de núcleos>
```

Asignar núcleos de CPU específicos:
```
--cpuset-cpus=<lista de núcleos>
```

**¿Como saber el numero de procesadores virtuales que tiene una máquina?**

El método para obtener esta información depende del sistema operativo que se utilice. En sistemas Linux, se lo encuentra escribiendo el comando nproc o lscpu directamente en la terminal. En Windows, se puede observar  abriendo el Administrador de tareas en la pestaña de Rendimiento dentro del apartado de CPU, o ejecutando el comando wmic cpu get NumberOfLogicalProcessors en el Símbolo del sistema. Para macOS, se obtiene este dato ejecutando el comando sysctl -n hw.ncpu desde la terminal.

## Ejemplos
_Puedes copiar y ejecutar directamente cada uno de los comandos_

Limitar el uso de CPU a 1.5 núcleos
```
docker run -d --name server-nginx --cpus="1.5" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 0 a 2:
```
docker run -d --name server-nginx --cpuset-cpus="0-2" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 1 y 3:
```
docker run -d --name server-nginx --cpuset-cpus="1,3" nginx:alpine
```
