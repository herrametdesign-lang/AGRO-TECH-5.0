# AGRO-TECH 5.0
## Arquitectura modular para la observación integrada de la planta y la zona radicular mediante sensores y herramientas digitales

**Iniciativa:** SQ-ONE Research Lab  
**Tipo:** documento técnico de investigación conceptual  
**Versión:** 1.0 — octubre de 2026  
**Estado:** arquitectura conceptual en desarrollo; validación experimental pendiente

## Resumen

AGRO-TECH 5.0 es una propuesta de arquitectura agrotecnológica modular que organiza la observación del sistema vegetal en dos dominios complementarios: la parte aérea de la planta y la zona radicular/sustrato. Una capa digital permite adquirir, organizar, visualizar y relacionar mediciones en el tiempo. La arquitectura se estructura en CANOPY / OPTO-TECH, ROOT / ELECTRO-TECH y SOFHTECH 5.0, con un controlador embebido ESP32-S3 considerado como plataforma de referencia para adquisición y comunicación de datos.

La motivación es facilitar una lectura integrada de variables relevantes para el seguimiento de cultivos y experimentos, manteniendo separadas la captura de datos, su interpretación y las acciones de manejo. La propuesta es modular para permitir la selección y sustitución de sensores según cultivo, sustrato, escala y condiciones de operación. Este documento define objetivos, arquitectura funcional, variables candidatas, criterios de validación y limitaciones. En esta etapa, las funciones descritas representan una propuesta de investigación y desarrollo; no se presentan resultados experimentales propios ni se atribuyen mejoras de rendimiento, ahorro de agua o aumento de productividad sin mediciones que los respalden.

**Palabras clave:** agricultura de precisión, sensores de planta, sensores de suelo, óptica aplicada, adquisición de datos, sistemas embebidos, IoT, trazabilidad experimental.

## 1. Introducción

La agricultura de precisión combina mediciones, información contextual y herramientas de análisis para describir la variabilidad de los sistemas productivos y apoyar decisiones de manejo. Las tecnologías de observación de plantas y suelo abarcan principios ópticos, eléctricos, térmicos, dieléctricos y otros métodos; cada familia ofrece información distinta y presenta limitaciones de instalación, calibración, resolución y sensibilidad ambiental.

AGRO-TECH 5.0 propone organizar estas funciones en una arquitectura coherente, donde los subsistemas de observación aérea y radicular puedan desarrollarse de forma independiente y comunicarse con una capa de software común. Las mediciones se interpretan junto con su contexto —por ejemplo, tiempo, ubicación, etapa de crecimiento y condiciones ambientales— y las decisiones posteriores pueden rastrearse hasta los datos que las motivaron.

## 2. Objetivo general

Definir una arquitectura modular de investigación para integrar mediciones de la parte aérea de la planta y de la zona radicular, con adquisición digital y trazabilidad, de modo que pueda evaluarse mediante prototipos y ensayos controlados.

### Objetivos específicos

1. Delimitar los módulos de observación aérea, observación radicular y software.
2. Identificar familias de variables y tecnologías de sensor que puedan evaluarse para cada caso de uso.
3. Establecer una vía de adquisición y comunicación basada en un controlador embebido de referencia.
4. Diseñar una estructura de datos que conserve unidades, tiempo, ubicación, configuración y estado de calibración.
5. Definir un plan de verificación eléctrica, funcional y agronómica previo a cualquier afirmación de desempeño.

## 3. Arquitectura funcional propuesta

### 3.1 CANOPY / OPTO-TECH — observación de la parte aérea

Este módulo se orienta a reunir observaciones ópticas y ambientales relacionadas con la parte aérea de la planta. Según el cultivo y el objetivo del ensayo, podrían evaluarse sensores de intensidad luminosa, bandas espectrales específicas, temperatura superficial u otras señales pertinentes. La selección definitiva requiere justificar la variable objetivo, la distancia y geometría de observación, la iluminación, la resolución temporal y el método de calibración.

Una lectura óptica no equivale por sí sola a una medida directa de salud, nutrición o rendimiento. Su interpretación depende del sensor, del protocolo de medición y de la relación validada con una variable de referencia.

### 3.2 ROOT / ELECTRO-TECH — observación de la zona radicular

Este módulo se orienta a medir variables del sustrato y del entorno radicular. Entre las variables candidatas para evaluación se encuentran humedad, temperatura y conductividad eléctrica, siempre que el sensor seleccionado sea adecuado para el medio y el uso previsto. Otras variables podrán incorporarse cuando exista una metodología de medición defendible.

Las mediciones dependen del tipo de suelo o sustrato, la instalación, la salinidad, la temperatura y el contacto entre sensor y medio. Por ello, la calibración y la comparación con un método de referencia forman parte esencial de la validación.

### 3.3 SOFHTECH 5.0 — software, integración y trazabilidad

SOFHTECH 5.0 se plantea como la capa digital de adquisición, almacenamiento, visualización y análisis. Sus funciones previstas incluyen recepción y organización de mediciones; asociación de marca temporal, unidad, sensor y configuración; visualización de series temporales y comparación entre módulos; registro de incidencias y calibraciones; alertas configurables una vez definidos y verificados sus criterios; exportación de datos; y evolución de la interfaz hacia Windows, Android e iOS.

La arquitectura de software deberá separar datos medidos, datos derivados, estimaciones y recomendaciones. Cada resultado calculado debe identificar el método aplicado y su versión.

### 3.4 Controlador y comunicaciones

El ESP32-S3 se considera una plataforma embebida de referencia por sus recursos de procesamiento y conectividad inalámbrica. Su inclusión no implica que el diseño electrónico integrado esté terminado ni que todos los sensores sean conectables directamente. Cada canal requerirá verificar rango eléctrico, resolución, acondicionamiento analógico, aislamiento cuando corresponda, alimentación, consumo, protección ambiental y compatibilidad de interfaces.

La comunicación puede organizarse por módulos, con un formato de mensaje que identifique dispositivo, variable, valor, unidad, marca temporal y estado de calidad. El protocolo definitivo deberá elegirse según alcance, consumo, robustez y condiciones de despliegue.

## 4. Flujo de datos

1. **Captura:** el sensor produce una señal física o digital.
2. **Acondicionamiento y lectura:** la electrónica adapta y digitaliza la señal cuando corresponde.
3. **Control de calidad:** el sistema comprueba límites, valores ausentes, errores de comunicación y estado de calibración.
4. **Registro:** se conserva la lectura con metadatos y marca temporal.
5. **Integración:** SOFHTECH 5.0 organiza las series de CANOPY y ROOT.
6. **Análisis:** se calculan indicadores solo cuando existe una definición explícita y verificable.
7. **Presentación:** la interfaz muestra datos, tendencias e incidencias sin confundir medición con inferencia.
8. **Decisión:** cualquier recomendación o actuación automática requiere criterios definidos, pruebas y mecanismos seguros de operación.

## 5. Principios de diseño

### Modularidad
Cada subsistema debe poder probarse por separado. Las interfaces se documentarán para reducir dependencias ocultas y permitir la sustitución de sensores.

### Calibración y trazabilidad
Cada medición deberá asociarse al sensor utilizado, su identificación, unidades, método de calibración, fecha, condiciones de ensayo y estado de mantenimiento.

### Separación entre medición e interpretación
Una lectura es una observación instrumental. Un indicador es un cálculo. Una recomendación es una inferencia orientada a una decisión. El sistema debe mantener visibles estas diferencias.

### Interoperabilidad y evolución
Se favorecerán formatos de datos documentados y exportables, interfaces modulares y registro de versiones. Las decisiones definitivas sobre protocolos y formatos se tomarán durante el diseño detallado.

### Seguridad y robustez
El diseño deberá considerar protección frente a humedad, polvo, corrosión, errores de conexión, fallas de alimentación y pérdida de comunicación. Si en una etapa futura se incorporan actuadores, deberán definirse estados seguros, límites y mecanismos de desconexión.

## 6. Metodología de desarrollo y validación

**Etapa A — Especificación:** definir cultivo o sistema de prueba, variables objetivo, unidades, frecuencia de muestreo, condiciones de uso y criterios de aceptación.

**Etapa B — Verificación de componentes:** revisar hojas de datos, rangos, consumo, interfaces, tolerancias y requisitos de instalación. Mantener una lista de materiales trazable a la documentación disponible.

**Etapa C — Pruebas por módulo:** evaluar CANOPY y ROOT por separado, registrar lecturas en condiciones controladas y contrastarlas con instrumentos o procedimientos de referencia adecuados.

**Etapa D — Integración electrónica:** verificar alimentación, adquisición, comunicaciones, reinicio, pérdida de enlace, integridad de datos y comportamiento ante errores.

**Etapa E — Integración de software:** probar ingestión, almacenamiento, visualización, exportación, marcas temporales, manejo de datos ausentes y trazabilidad de cambios.

**Etapa F — Ensayo controlado:** comparar mediciones del sistema con referencias independientes, con repeticiones suficientes y un protocolo definido antes de analizar resultados.

**Etapa G — Evaluación de campo:** estudiar estabilidad, mantenimiento, condiciones ambientales, variabilidad espacial y utilidad de la información en el contexto productivo seleccionado.

## 7. Métricas que deberán definirse

Según el sensor y la variable, el protocolo deberá seleccionar: error respecto de una referencia y sesgo; repetibilidad y reproducibilidad; deriva temporal y sensibilidad ambiental; porcentaje de lecturas válidas y pérdida de datos; latencia de adquisición y transmisión; consumo energético y autonomía; estabilidad de comunicaciones; facilidad de instalación y mantenimiento.

No se asignan valores de precisión, autonomía o rendimiento antes de realizar las mediciones correspondientes.

## 8. Resultados esperados y criterios de éxito

Como resultados de desarrollo se espera obtener una arquitectura documentada, interfaces entre módulos, un esquema de adquisición verificable, un modelo de datos trazable y un protocolo de pruebas reproducible.

El éxito técnico deberá evaluarse mediante criterios definidos de antemano: funcionamiento dentro de los rangos especificados, datos completos y correctamente identificados, error instrumental compatible con el uso previsto y comportamiento estable en condiciones de ensayo. Cualquier beneficio agronómico —por ejemplo, mejor decisión de riego o uso más eficiente de recursos— requerirá ensayos específicos que permitan atribuirlo con prudencia al sistema y al contexto evaluados.

## 9. Limitaciones actuales

La arquitectura se encuentra en etapa conceptual y de definición. La configuración final de sensores, el circuito integrado, el diseño mecánico, el firmware, la interfaz de software, las calibraciones y las pruebas de campo deben documentarse a medida que se completen. Este documento no presenta una validación experimental propia ni afirma resultados de producción.

## 10. Conclusión

AGRO-TECH 5.0 plantea una estructura modular para conectar la observación de la parte aérea, la medición de la zona radicular y la gestión digital de datos. CANOPY / OPTO-TECH, ROOT / ELECTRO-TECH y SOFHTECH 5.0 permiten organizar el desarrollo en unidades verificables, con un ESP32-S3 como plataforma embebida de referencia sujeta a evaluación técnica.

El valor científico de la propuesta dependerá de la precisión de sus especificaciones, la trazabilidad de las mediciones y la publicación transparente de resultados positivos, límites e incertidumbres. La siguiente etapa consiste en convertir esta arquitectura en un prototipo verificable y evaluar cada módulo mediante procedimientos reproducibles.

## Declaración de estado

Este documento describe una propuesta de investigación y desarrollo. Las funciones se presentan como arquitectura prevista, y las etapas de prototipado integrado y validación experimental se mantienen identificadas como trabajo pendiente. Las referencias externas fundamentan el contexto tecnológico general y no constituyen validación del sistema AGRO-TECH 5.0.

## Referencias

La bibliografía y los recursos técnicos se detallan en [REFERENCES.md](../REFERENCES.md).
