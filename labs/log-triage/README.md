Laboratorio 1:

Caso: Eres el on-call y te piden investigar por qué un servicio tuvo fallas. Te entregan un archivo de logs (lo vas a crear tú) y debes producir un paquete de 
evidencia + documentación para un runbook básico.

Dentro del log podremos observar las lineas de error que causaron el problema, dentro del log podremos encontrar el top 3 de errores clasificandolos por su tipo y el numero de 
veces que se presento dicho error

# Conteo Top 3
      6 err_type=db
      5 err_type=auth
      3 err_type=timeout

# === Top 3 code (conteo) ===
      9 code=500
      8 code=401
      2 code=504

# === Latencia máxima ===
latencia_maxima=2438ms

#Runbook mini

1.- Recomendacion 1
2.- Recomendacion 2
3.- Recomendacion 3

#Como reproducir

Obtener un reporte de logs y clasificar el tipo de errores para determinar que errores fueron los que mas se presentaron
Obtener un reporte sobre la latencia
