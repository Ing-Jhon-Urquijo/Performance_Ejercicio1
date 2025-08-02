README - PRUEBA DE PERFORMANCE CON JMETER
=========================================

Ejercicio: Prueba de carga sobre el servicio de login de FakeStoreAPI

-----------------------------------------
1. REQUISITOS PREVIOS
-----------------------------------------
• Apache JMeter 5.6.3 instalado
  Descargar desde: https://jmeter.apache.org/download_jmeter.cgi

• Java JDK 8 o superior
  Verificar instalación con: java -version

• Archivo CSV con datos de login (usuarios y contraseñas)
  Ejemplo:
      user,password
      donero,ewedon
      kevinryan,kev02937@
      johnd,m38rmF$
      derek,jklg*_56
      mor_2314,83r5^_

-----------------------------------------
2. ARCHIVOS INCLUIDOS
-----------------------------------------
• login-test.jmx           -> Plan de pruebas de JMeter
• datos.csv                -> Archivo de datos para parametrización
• resultados.csv           -> Resultados obtenidos tras ejecución
• conclusiones_final.txt   -> Análisis y hallazgos de la prueba
• readme.txt               -> Este archivo

-----------------------------------------
3. EJECUCIÓN DE LA PRUEBA
-----------------------------------------
Paso 1: Abrir JMeter
  Ejecutar el archivo `jmeter.bat` ubicado en la carpeta bin de JMeter

Paso 2: Cargar el plan de prueba
  - Archivo > Abrir > seleccionar `login-test.jmx`

Paso 3: Verificar el archivo CSV
  - Asegurarse de que el archivo `datos.csv` esté ubicado en el mismo directorio del .jmx
  - El elemento "CSV Data Set Config" debe estar apuntando al nombre correcto: datos.csv

Paso 4: Ejecutar la prueba
  - Clic en el botón "Start" (icono ▶️)
  - Se recomienda usar los listeners "View Results Tree", "Summary Report" y/o "Aggregate Report" para observar resultados en tiempo real

Paso 5: Exportar resultados
  - Guardar los resultados en un archivo CSV (si no se genera automáticamente)

-----------------------------------------
4. PARÁMETROS DE LA PRUEBA
-----------------------------------------
- Tipo: Prueba de carga con múltiples usuarios
- Endpoint: https://fakestoreapi.com/auth/login
- Método HTTP: POST
- Headers: Content-Type: application/json
- Body (parametrizado):
  {
    "username": "${user}",
    "password": "${password}"
  }

-----------------------------------------
5. CRITERIOS DE ÉXITO
-----------------------------------------
• TPS (Transacciones por segundo) >= 20
• Tiempo de respuesta promedio <= 1.5 segundos
• Tasa de error < 3%
