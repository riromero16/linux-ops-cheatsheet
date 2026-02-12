# Linux Ops Cheatsheet (Week 1)

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
; encadenar comandos (Ej: ls -la && echo "Listado de archivos  correcto")

&& se usa para ejecutar algo después de otra ejecución correcta 

|| se usa para ejecutar algo si otro comando falla

## GREP y Find
grep -i 'texto': Buscar palabras en archivos de texto, -i para que no distinga entre caps
find . -type d -name "*": buscar archivos o documentos -d (directorio) -f (file)
