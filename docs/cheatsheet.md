# Linux Ops Cheatsheet (Week 1)

## Find Print f

En find, -printf te deja formatear cómo se imprime cada resultado (similar a printf en C).

Tu formato:

-printf '%TY-%Tm-%Td %TH:%TM:%TS %p\n'


genera una línea por archivo así:

2026-02-12 23:15:07.123456789 ./ruta/del/archivo.txt


Desglose:

%TY → año de la última modificación (Time)

%Tm → mes (01–12)

%Td → día (01–31)

%TH → hora (00–23)

%TM → minuto (00–59)

%TS → segundos con fracción (ej. 07.123456789)

%p → ruta del archivo tal como find la encuentra (ej. ./logs/service.log)

\n → salto de línea (para que cada archivo salga en su propia línea)

O sea: fecha + hora + ruta ordenable y fácil de leer.

## Navegación
- pwd
- ls -la
- cd

## Archivos y carpetas
- mkdir -p
- touch
- cp / mv
- rm -r (con cuidado)

## Ayuda
- man
- comando --help

## Permisos
chmod 600
Tenemo 3 binarios:
 1.- Usuario 	(u)
 2.- Grupo	(g)
 3.- Otros	(o)

Solo existen 3 tipos de permisos:
 1.- r= read > ver contenido
 2.- w= write > editar/guardar cambios
 3.- x= execute > ejecutar como programa/script

Se pueden asignar permisos de forma simbolica y numerica:
 -Agregar: chmod u+x script.sh
 -Quitar: chmod o-r archivo.txt
 -Asignar exacto: chmod g=rw archivo.txt
 -Para todos: chmod a+r archivo.txt

Cada dígito es (r=4, w=2, x=1):

 -7 = rwx
 -6 = rw-
 -5 = r-x
 -4 = r--
 -0 = ---

NO es recomendado subir a este tipo de proyectos ninguna de las siguientes llaves:
 -AWS Access Key / Secret Access Key
 -Tokens (GitHub token, Slack token, API keys de cualquier servicio)
 -Passwords (aunque sean “temporales”)
 -Keys/certificados: llaves SSH privadas (id_rsa, id_ed25519 sin .pub), archivos .pem
 -Credenciales de BD (user/password, connection strings)
 -.env con valores reales (por ejemplo DATABASE_URL=..., JWT_SECRET=...)
 -Cookies de sesión o headers tipo Authorization: Bearer ...

## Pipes
 -; encadenar comandos (Ej: ls -la && echo "Listado de archivos  correcto")
 -&& se usa para ejecutar algo después de otra ejecución correcta 
 -|| se usa para ejecutar algo si otro comando falla

## GREP y Find
grep -i 'texto': Buscar palabras en archivos de texto, -i para que no distinga entre caps
find . -type d -name "*": buscar archivos o documentos -d (directorio) -f (file)

## xargs
xargs es una herramienta que toma texto desde stdin (pipe) y lo convierte en argumentos para ejecutar otro comando. Sirve cuando un comando produce una lista (archivos, IDs, líneas) 
y tú quieres usar esa lista para llamar otro comando.

Ejemplos:
1) Borrar archivos encontrados
find . -name "*.log" | xargs rm

2) Ejecutar un comando por cada elemento
cat urls.txt | xargs -n 1 curl -I 

3) Ver qué va a ejecutar (debug)
echo "a b c" | xargs -t echo


## sort, uniq, wc
Comando sort : ordena las filas de una entrada o un archivo de texto ej.:ls -l | sort -nk 5
Comando uniq : filtra las líneas duplicadas de una entrada o de un archivo de texto. ej.: sort archivo.txt | uniq > archivo_sin_duplicados.txt
Comando sed : realiza operaciones básicas de edición de texto sin la necesidad de abrir el archivo. ej.: sed 's/manzana/pera/' fruta.txt
Comando date : muestra fecha y hora del sistema. ej.: date +%Y-%m-%d
Comando uname : muestra información del sistema. ej.: uname -a P.D.: una mejor forma (o por lo menos mas bonita) de ver la información del sistema es con neofetch , si no lo tienen lo pueden instalar con el comando sudo apt install neofetch
