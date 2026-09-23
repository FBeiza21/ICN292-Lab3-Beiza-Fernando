# ICN292-Lab3-Beiza-Fernando
# ICN292 – Laboratorio 3: Automatización de devoluciones

**Alumno:** Fernando Beiza  
**Semilla:** S = 159  
**Umbral:** U = $39.000  
**Plazo máximo:** D = 28 días  
**Fecha:** septiembre de 2026  

## Descripción

Este repositorio contiene los workflows desarrollados en n8n para automatizar el proceso de clasificación de solicitudes de devolución de la empresa AndesHogar SpA.

## Archivos

- ICN292-Lab3-Beiza-Fernando-triage.json: recibe, valida, clasifica, registra y responde cada solicitud.
- ICN292-Lab3-Beiza-Fernando-emisor.json: envía las 15 solicitudes de prueba al webhook productivo.
- ICN292-Lab3-Beiza-Fernando-resumen.json: genera diariamente el resumen de solicitudes y montos por ruta.

## Reglas de clasificación

1. Datos inválidos: identificador ausente o monto menor o igual a cero.
2. Rechazo: plazo superior a 28 días o producto dañado por uso.
3. Revisión: monto superior a $39.000 o producto con fallas.
4. Aprobación: solicitudes que no cumplen las condiciones anteriores.

## Resultados de las 15 solicitudes

- Aprobación: 3 solicitudes.
- Revisión: 9 solicitudes.
- Rechazo: 3 solicitudes.
- Datos inválidos: 0 solicitudes.
- Monto total procesado: $1.251.820.
- Tasa de aprobación automática: 20%.

## Cómo reproducir

1. Importar los tres archivos `.json` en n8n.
2. Crear o seleccionar una Data Table con las columnas utilizadas en el registro.
3. Configurar esa tabla en los nodos `Registrar Solicitud` y `Leer solicitudes del día`.
4. Publicar el workflow de triage.
5. Verificar que el HTTP Request del emisor utilice la URL productiva del webhook.
6. Ejecutar manualmente el workflow emisor.
7. Publicar el workflow de resumen para activar su ejecución diaria a las 23:55.

## Seguridad

Los archivos exportados tienen `pinData` vacío y no contienen contraseñas, tokens ni credenciales.
