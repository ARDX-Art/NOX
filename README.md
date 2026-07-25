# NOX — Marco de Inteligencia de Amenazas Cibernéticas

**Núcleo asíncrono | 120+ fuentes de brechas | Puntuación de riesgos | Graficación de identidades | Detección de HVT**

## Resumen

NOX es un marco integral de inteligencia de amenazas cibernéticas (CTI) diseñado para
- profesionales de la seguridad, pentesters y respondedores de incidentes. 
- Agrega inteligencia de más de 120 fuentes de brechas, realiza análisis avanzados de 
- riesgos y genera informes de inteligencia accionables.

## Características

- **🔍 Inteligencia multi-fuente**: Consulta simultáneamente más de 120 fuentes de datos de brechas
- **⚡ Arquitectura asíncrona**: Procesamiento concurrente de alto rendimiento
- **🎯 Motor de puntuación de riesgos**: Evaluación predictiva de riesgos con correlación temporal
- **🔗 Graficación de identidades**: Correlación avanzada y mapeo de relaciones
- **⚠️ Detección de HVT**: Identificación objetivos de alto valor
- **🔐 Descifrado de hashes**: Análisis integrado de hashes de contraseñas
- **🌐 Motor de Dorking**: Dorking avanzado de Google para datos expuestos
- **📊 Web Scraping**: Inteligencia de Telegram, pastebin y sitios de pegado
- **🔒 Protección OPSEC**: Soporte integrado de proxy/Tor con mecanismos de seguridad
- **📈 Informes**: Múltiples formatos de salida (HTML, PDF, JSON, CSV, Markdown)
- **🔧 Sistema de plugins**: Definiciones de fuentes extensibles basadas en JSON

### Instalación Rápida
-------------------------------------------------
| ```bash                                       |
| git clone https://github.com/ZON33XY/nox.git  |
| cd nox                                        |
| pip install -r requirements.txt               |
| python3 nox.py --help                         |
-------------------------------------------------

## Dependencias
NOX requiere Python 3.8+ y los siguientes paquetes:

----------------------------------------------------------------------------
| ```bash                                                                  |
| pip install aiohttp aiosqlite beautifulsoup4 requests colorama rich      | 
----------------------------------------------------------------------------
## Dependencias opcionales para funcionalidad mejorada:

----------------------------------------------------------------------------
| ```bash                                                                  |
| pip install aiohttp-socks cloudscraper stem phonenumbers weasyprint fpdf2|
----------------------------------------------------------------------------

##Inicio Rápido

Modo Interactivo

---------------------
| ```bash           |
| python3 nox.py    |
---------------------

### Uso en Línea de Comandos

---------------------------------------------------------------
| # Escaneo básico de email                                   |
| python3 nox.py -t usuario@ejemplo.com                       |
|                                                             |
| # Asalto completo con pivoteo                               |
| python3 nox.py -t ejemplo.com --fullscan                    |
|                                                             |
| # Dorking de Google                                         |
| python3 nox.py --dork usuario@ejemplo.com                   |
|                                                             |
| # Web scraping                                              |
| python3 nox.py --scrape usuario@ejemplo.com                 |
|                                                             |
| # Descifrado de hash                                        |
| python3 nox.py --crack "5f4dcc3b5aa765d61d8327deb882cf99"   |
|                                                             |
| # Análisis de contraseña                                    |
| python3 nox.py --analyze "P@ssw0rd123!"                     |
---------------------------------------------------------------

Configuración
Claves API

Configura las claves API en ~/.config/nox-cli/apikeys.json:

-----------------------------------------------
| json{                                       |
|  "HIBP_API_KEY": "tu-clave-haveibeenpwned", |
|  "DEHASHED_API_KEY": "email:clave-api",     |
|  "VIRUSTOTAL_API_KEY": "tu-clave-vt"        |
| }                                           |
-----------------------------------------------

Configuración de Proxy/Tor
-----------------------------------------------------------------------
| # Escanear una dirección de email                                   |
| python3 nox.py -t usuario@ejemplo.com                               |
|                                                                     |
| # Escanear un dominio                                               |
| python3 nox.py -t ejemplo.com                                       |
|                                                                     |
| # Escanear con salida personalizada                                 |
| python3 nox.py -t usuario@ejemplo.com -o reporte.html --format html |
-----------------------------------------------------------------------

Ejemplos de Uso

Escaneo Básico
-------------------------------------------------------------------------
| # Escanear una dirección de email                                     |
| python3 nox.py -t usuario@ejemplo.com                                 |
|                                                                       |
| # Escanear un dominio                                                 |
| python3 nox.py -t ejemplo.com                                         |
|                                                                       |
| # Escanear con salida personalizada                                   |
| python3 nox.py -t usuario@ejemplo.com -o reporte.html --format html   |
-------------------------------------------------------------------------

Operaciones Avanzadas
-----------------------------------------------------
| # Asalto completo con pivoteo y análisis profundo |
| python3 nox.py -t ejemplo.com --fullscan --depth 3|
|                                                   |
| # Comparar con escaneo anterior                   |
| python3 nox.py -t usuario@ejemplo.com --diff      |
|                                                   |
| # Deshabilitar descifrado online de hashes        |
| python3 nox.py --crack "hash" --no-online-crack   |
-----------------------------------------------------

Comandos Interactivos
En modo interactivo, puedes usar estos comandos:
-----------------------------------------------------------------
| autoscan - Escaneo completo + pivoteo + dorking + scraping    |
| scan - Escaneo rápido de inteligencia de brechas              |
| dork - Dorking de Google para datos filtrados                 |
| scrape - Scraping profundo de pastes/web                      |
| crack - Identificar y descifrar un hash                       |
| analyze - Análisis de fortaleza de contraseña                 |
| graph - Gráfico forense del último escaneo                    |
| export - Exportar resultados (html/json/csv/md/pdf)           |
| tor - Alternar enrutamiento Tor                               |
| sources - Listar plugins cargados                             |                                     
-----------------------------------------------------------------

Arquitectura

Componentes Principales:
-------------------------------------------------------------------
| Orchestrator: Motor de ejecución principal con soporte asíncrono|
| SourceOrchestrator: Gestión de plugins basada en fuentes        |
| RiskEngine: Puntuación predictiva de riesgos                    |
| IdentityResolver: Correlación y graficación                     |
| PivotManager: Enriquecimiento recursivo de datos                |
| ProxyManager: Protección OPSEC y rotación de proxies            |
-------------------------------------------------------------------

Sistema de Plugins

NOX utiliza un sistema de plugins basado en JSON para fuentes:

------------------------------------------------------------
| {                                                        |
|   "name": "FuenteEjemplo",                               |
|   "api_url": "https://api.ejemplo.com/search?q={query}", |
|   "method": "GET",                                       |
|   "headers": {"Authorization": "Bearer {api_key}"},      |
|   "extract": {                                           |
|     "mode": "json",                                      |
|     "root": "results",                                   |
|     "email": "email",                                    |
|     "password": "password"                               |
|   }                                                      |
| }                                                        | 
------------------------------------------------------------

Consideraciones OPSEC

NOX incluye protecciones OPSEC integradas:

-----------------------------------------------------------------------
| Mecanismo de Seguridad: Previene fugas de IP cuando falla proxy/Tor |
| Rotación de Proxies: Rotación y validación automática de proxies    |
| Fingerprinting JA3: Fingerprinting TLS de grado de navegador        |
| Limitación de Tasa: Limitación inteligente de tasa con jitter       |
-----------------------------------------------------------------------

Informes

NOX soporta múltiples formatos de salida:

--------------------------------------------------------
| HTML: Informe web interactivo con gráficos           |
| PDF: Informe forense profesional (requiere fpdf2)    |
| JSON: Datos estructurados legibles por máquina       |
| CSV: Formato compatible con hojas de cálculo         |
| Markdown: Formato amigable para documentación        |
--------------------------------------------------------

Contribuyendo

¡Aceptamos contribuciones! Por favor consulta nuestra Guía de Contribución para detalles.

Agregar Nuevas Fuentes
  1. Crea una definición JSON en ~/.nox/sources/
  2. Ejecuta python3 build_sources.py
  3. Prueba con python3 nox.py --list-sources

Descargo de Responsabilidad

Esta herramienta es solo para pruebas de seguridad autorizadas y fines de investigación. 
Los usuarios son responsables de garantizar el cumplimiento de las leyes y regulaciones aplicables.

