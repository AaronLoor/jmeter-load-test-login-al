# JMeter Login Load Test

Este proyecto contiene una prueba de carga para el servicio de login de fakestoreapi.com usando JMeter.

## Prerrequisitos
- **Apache JMeter 5.6.3** (Versión utilizada).
- Java Runtime Environment (JRE) compatible (Java 8+).

## Archivos del Proyecto
- `login_test.jmx`: Plan de pruebas de JMeter.
- `users.csv`: Archivo de datos con usuarios y contraseñas.
- `readme.txt`: Este archivo de instrucciones.
- `conclusions.txt`: Hallazgos y conclusiones de la prueba.

## Instrucciones de Ejecución

### Opción 1: Modo No Gráfico (CLI) - RECOMENDADO
Esta es la forma correcta de ejecutar pruebas de carga para obtener resultados fiables y generar reportes.

Ejecute el siguiente comando en la terminal:

```bash
jmeter -n -t login_test.jmx -l results.jtl -e -o report
```

**Explicación de parámetros:**
- `-n`: Modo no gráfico (CLI).
- `-t login_test.jmx`: Archivo del plan de pruebas.
- `-l results.jtl`: Archivo donde se guardarán los resultados crudos (IMPORTANTE: Este archivo no debe existir antes de correr la prueba).
- `-e`: Generar reporte HTML al finalizar.
- `-o report`: Carpeta donde se guardará el reporte HTML (la carpeta no debe existir o debe estar vacía).

### Opción 2: Modo Gráfico (GUI)
**Nota:** El modo gráfico se usa solo para diseño y depuración, no para la prueba de carga real.

1. Abra JMeter (`jmeter`).
2. Cargue el archivo `login_test.jmx`.
3. Presione el botón de inicio (Start).
4. **Para ver resultados:** Los resultados NO se guardan automáticamente en un archivo en modo GUI a menos que configure un "Listener" explícitamente.
   - Puede ver los resultados en tiempo real en el componente "View Results Tree" o "Summary Report" que ya están incluidos en el script.

## Análisis de Resultados (Reporte HTML)
Después de ejecutar la **Opción 1**, abra el archivo `index.html` ubicado en la carpeta `report` generada. Este reporte contiene gráficos detallados de:
- APDEX (Satisfacción de usuario).
- Resumen de estadísticas (Requests, Errores).
- Gráficos de Tiempo de Respuesta vs Tiempo.
- Throughput (Transacciones por segundo).

## Configuración de la Prueba
- **TPS Objetivo**: ~20 TPS.
- **Validaciones**:
  - Tiempo de respuesta < 1.5 segundos.
  - Tasa de error < 3%.
  - Código de respuesta 201 Created.
  - Presencia de token en la respuesta.
