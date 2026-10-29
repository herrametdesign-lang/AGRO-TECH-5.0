# AGRO-TECH 5.0 — Estado y plan de validación

**Estado documental:** investigación conceptual y definición de arquitectura.  
**Fecha de revisión:** octubre de 2026.

## Estado por componente

| Área | Estado documentado | Próximo hito verificable |
|---|---|---|
| CANOPY / OPTO-TECH | Definición conceptual | Seleccionar variable objetivo y sensor; redactar protocolo de calibración |
| ROOT / ELECTRO-TECH | Definición conceptual | Seleccionar variable objetivo y sensor adecuado al medio |
| SOFHTECH 5.0 | Capa de software propuesta | Definir modelo de datos, interfaces y pruebas de registro/exportación |
| ESP32-S3 | Plataforma embebida de referencia | Confirmar variante, interfaces, alimentación, consumo y acondicionamiento |
| Integración electrónica | Pendiente de documentar como sistema integrado | Verificar alimentación, adquisición, comunicación y fallos |
| Ensayo instrumental | Pendiente | Comparación con referencia independiente y repetibilidad |
| Ensayo agronómico de campo | Pendiente | Protocolo específico, controles, repeticiones y análisis de resultados |

## Plan de verificación

### 1. Especificación
- [ ] Definir cultivo/sistema de prueba y pregunta de investigación.
- [ ] Definir cada variable, unidad, rango esperado y frecuencia de muestreo.
- [ ] Establecer criterios de aceptación antes de medir.

### 2. Sensores y electrónica
- [ ] Revisar hojas de datos y versiones.
- [ ] Verificar compatibilidad eléctrica y acondicionamiento de señal.
- [ ] Documentar alimentación, consumo y protección ambiental.
- [ ] Registrar identificación de componentes y cambios de configuración.

### 3. Calidad de medición
- [ ] Seleccionar un método o instrumento de referencia.
- [ ] Definir número de repeticiones y condiciones ambientales.
- [ ] Calcular error, sesgo y repetibilidad según corresponda.
- [ ] Registrar datos brutos, unidades, calibración e incertidumbres.

### 4. Software y comunicaciones
- [ ] Verificar marcas temporales e identificación de sensores.
- [ ] Probar datos ausentes, errores de comunicación y recuperación.
- [ ] Comprobar integridad de almacenamiento y exportación.
- [ ] Separar mediciones, cálculos y recomendaciones en la interfaz.

### 5. Ensayo integrado y de campo
- [ ] Ejecutar primero pruebas controladas.
- [ ] Definir controles y variables de confusión antes de los ensayos.
- [ ] Documentar condiciones, mantenimiento y fallas.
- [ ] Publicar resultados junto con método, limitaciones y datos suficientes para reproducibilidad.

## Reglas de comunicación de resultados

1. No presentar un módulo conceptual como prototipo funcional.
2. No llamar “validado” a un sistema sin protocolo y evidencia documentados.
3. No atribuir ahorro de agua, aumento de rendimiento o mejoras agronómicas sin ensayos adecuados.
4. Mantener diferenciados los datos medidos, los cálculos, las estimaciones y las recomendaciones.
5. Actualizar este archivo cuando se complete un hito y enlazar los registros o informes que lo demuestren.

## Registro de hitos

| Fecha | Hito | Evidencia |
|---|---|---|
| Octubre de 2026 | Publicación inicial de la arquitectura conceptual y del plan documental | Archivos Markdown de este repositorio |

Este registro describe el estado documental público y debe actualizarse cuando existan evidencias técnicas nuevas.
