# DFIR - Investigación Forense de Servidor Ubuntu Comprometido

## Descripción del Proyecto

Laboratorio de Digital Forensics & Incident Response (DFIR) donde se simula el compromiso de un servidor Ubuntu y se realiza un análisis forense completo.

Este proyecto forma parte de mi portafolio de ciberseguridad y demuestra habilidades en:

- Adquisición de evidencia
- Análisis de logs y sistema de archivos
- Identificación de persistencia
- Documentación profesional de hallazgos
- Mapeo a MITRE ATT&CK

## Escenario

- Sistema: Ubuntu Server
- Stack de monitoreo existente: Promtail + Loki + Grafana
- Controles previos: UFW + Fail2Ban
- Tipo de incidente: Compromiso de servidor Linux (acceso inicial + persistencia)

## Metodología

1. Adquisición de evidencia (archivos de sistema, logs, historial, etc.)
2. Análisis de indicadores de compromiso (IOCs)
3. Timeline de la intrusión
4. Mapeo a MITRE ATT&CK
5. Informe forense completo

## Estructura del Repositorio

- `evidencia/` → Evidencia recolectada
- `informe/` → Informe forense final
- `screenshots/` → Capturas de pantalla del análisis
- `volatility_output/` → Resultados de análisis de memoria (si aplica)

## Hallazgos Principales (Resumen)

- Creación de usuario con privilegios elevados
- Persistencia mediante clave SSH
- Backdoor en `/tmp`
- Archivo con datos sensibles
- Comandos sospechosos en historial de root

## Autor

[Tu Nombre]
