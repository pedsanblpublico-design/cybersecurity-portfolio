# Informe de Auditoría de Seguridad y Cumplimiento: Botium Toys

**Rol:** Analista de Ciberseguridad Junior  
**Contexto del Proyecto:** Certificado Profesional de Ciberseguridad de Google — Módulo de Evaluación de Riesgos y Cumplimiento  
**Marco de Referencia:** NIST Cybersecurity Framework (NIST CSF), PCI DSS, GDPR, SOC 1 / SOC 2  

---

## 1. Resumen Ejecutivo

Botium Toys es una empresa dedicada a la venta minorista de juguetes tanto en tiendas físicas como en su plataforma de comercio electrónico. Con el objetivo de evaluar la postura de seguridad de la organización frente a su crecimiento y expansión en mercados internacionales (incluyendo la Unión Europea), se llevó a cabo una auditoría integral sobre el programa de seguridad de la compañía.

La evaluación determinó una **puntuación de riesgo de 8 sobre 10**, atribuible principalmente a la ausencia de controles fundamentales de control de acceso (privilegios mínimos y separación de funciones), carencia de cifrado de datos sensibles, falta de redundancia/copias de seguridad y desalineación con marcos normativos clave. 

Este informe documenta el estado actual de los controles técnicos, administrativos y físicos, evalúa el cumplimiento normativo y establece una hoja de ruta con recomendaciones prioritarias para la mitigación del riesgo operacional, legal y financiero.

---

## 2. Alcance y Objetivos de la Auditoría

* **Alcance:** Abarca la totalidad del programa de seguridad de Botium Toys:
  * Equipamiento e infraestructura local para oficinas y puntos de venta.
  * Dispositivos de usuario final (ordenadores portátiles, de sobremesa, teléfonos inteligentes, estaciones de trabajo remotas y periféricos).
  * Red interna, pasarelas y conectividad a Internet.
  * Gestión de sistemas, servicios y software (contabilidad, telecomunicaciones, bases de datos internas, comercio electrónico y gestión de inventario).
  * Retención y almacenamiento de datos corporativos y de clientes.
  * Sistemas heredados (*legacy systems*) fuera de soporte oficial (*end-of-life*).
  * Instalaciones físicas (oficinas centrales, tienda minorista y almacén contiguo).
* **Objetivos:** 
  1. Identificar y evaluar los activos existentes y sus vulnerabilidades asociadas.
  2. Evaluar el estado de implantación de los controles administrativos, técnicos y físicos.
  3. Auditar el grado de adhesión a los marcos normativos obligatorios (PCI DSS, GDPR y SOC).
  4. Proponer recomendaciones estructuradas y viables para robustecer la postura defensiva y reducir la exposición al riesgo.

---

## 3. Evaluación de Riesgos y Clasificación de Activos (NIST CSF)

Conforme a la primera función del marco de ciberseguridad NIST CSF (**Identify**), la identificación y clasificación de activos es el pilar fundamental para gestionar el riesgo de continuidad del negocio.

* **Descripción del riesgo:** La administración de activos es deficiente. La compañía almacena y procesa información confidencial (datos bancarios y PII/SPII) sin una segmentación adecuada ni políticas de acceso restringido.
* **Puntuación de riesgo global:** **8 / 10 (Riesgo Alto)**.
* **Impacto potencial de pérdida de activos:** Medio/Alto (el departamento de TI carece de un inventario formal para determinar con precisión qué activos específicos están expuestos).
* **Riesgo regulatorio y de sanciones:** Alto, derivado del procesamiento de tarjetas de crédito sin cifrar y la custodia de datos de ciudadanos de la UE sin garantías completas de privacidad.

---

## 4. Listas de Verificación de Controles y Cumplimiento

### 4.1. Evaluación de Controles de Seguridad (Controls Assessment Checklist)

| Sí | No | Control de Seguridad | Tipo de Control | Categoría | Justificación Técnica |
| :---: | :---: | :--- | :--- | :--- | :--- |
| | **X** | **Principio de menor privilegio (*Least Privilege*)** | Preventivo | Administrativo | Todo el personal tiene acceso indiscriminado a las bases de datos internas. |
| | **X** | **Planes de recuperación ante desastres (*DRP*)** | Correctivo | Administrativo | No existen planes documentados para garantizar la continuidad del negocio ante contingencias. |
| **X** | | **Políticas de contraseñas (*Password policies*)** | Preventivo | Administrativo | Existe una política, aunque con directrices nominales y complejidad desactualizada. |
| | **X** | **Separación de funciones (*Separation of duties*)** | Preventivo | Administrativo | No se han delimitado roles para evitar conflictos de interés o concentración de privilegios. |
| **X** | | **Cortafuegos (*Firewall*)** | Preventivo | Técnico | Implementado y configurado con un conjunto de reglas de filtrado de tráfico activo. |
| | **X** | **Sistema de detección de intrusiones (*IDS*)** | Detectivo | Técnico | No se ha desplegado ninguna solución IDS/IPS para inspección anómala de paquetes. |
| | **X** | **Copias de seguridad (*Backups*)** | Correctivo | Técnico | Inexistencia de copias de respaldo para datos críticos corporativos o transaccionales. |
| **X** | | **Software antivirus** | Preventivo | Técnico | Instalado en los puestos de trabajo y supervisado activamente por TI. |
| **X** | | **Mantenimiento manual de sistemas heredados** | Preventivo | Técnico | Se realiza intervención manual para mantener sistemas *end-of-life*, aunque sin calendario formal. |
| | **X** | **Cifrado (*Encryption*)** | Disuasorio / Técnico | Técnico | Datos de tarjetas y registros PII/SPII se almacenan y transmiten en texto plano internamente. |
| | **X** | **Gestor centralizado de contraseñas** | Preventivo | Técnico | Ausencia de software para la gestión unificada y cumplimiento forzado de credenciales. |
| **X** | | **Cerraduras físicas (oficinas, tienda, almacén)** | Preventivo / Disuasorio | Físico | Accesos restringidos y asegurados mediante cerrojos convencionales. |
| **X** | | **Videovigilancia por circuito cerrado (*CCTV*)** | Preventivo / Detectivo | Físico | Sistema actualizado y operativo en tienda, oficinas y almacén. |
| **X** | | **Sistemas contra incendios (alarmas y rociadores)** | Detectivo / Preventivo | Físico | Mecanismos de detección y extinción de incendios funcionales e instalados. |

---

### 4.2. Lista de Cumplimiento Normativo (Compliance Checklist)

#### Payment Card Industry Data Security Standard (PCI DSS)

| Sí | No | Mejor Práctica / Requisito | Justificación |
| :---: | :---: | :--- | :--- |
| | **X** | Acceso limitado exclusivamente a usuarios autorizados a datos de tarjetas. | Incumplido: Todo el personal de la empresa puede acceder libremente a estos registros. |
| | **X** | Almacenamiento, procesamiento y transmisión de tarjetas en entorno seguro. | Incumplido: El entorno no cuenta con segmentación de red ni medidas criptográficas. |
| | **X** | Cifrado de datos en todos los puntos de contacto transaccionales y de reposo. | Incumplido: No se emplea ningún algoritmo de cifrado para información de pago. |
| | **X** | Adopción de políticas robustas de gestión de contraseñas. | Incumplido: Reglas de contraseñas desactualizadas y sin complejidad técnica exigida. |

#### General Data Protection Regulation (GDPR)

| Sí | No | Mejor Práctica / Requisito | Justificación |
| :---: | :---: | :--- | :--- |
| | **X** | Los datos de clientes de la UE se mantienen privados y seguros. | Incumplido: Exposición interna generalizada y carencia de cifrado de PII/SPII. |
| **X** | | Plan para notificar brechas de seguridad en un plazo máximo de 72 horas. | Cumplido: TI cuenta con un protocolo formal de notificación ante incidentes. |
| | **X** | Clasificación e inventario formal de los datos sensibles y activos. | Incumplido: TI desconoce con exactitud qué activos específicos están en riesgo. |
| **X** | | Políticas y procedimientos de privacidad aplicados para documentar datos. | Cumplido: Procedimientos de privacidad implantados entre el personal de TI y empleados. |

#### System and Organization Controls (SOC 1 / SOC 2)

| Sí | No | Mejor Práctica / Requisito | Justificación |
| :---: | :---: | :--- | :--- |
| | **X** | Políticas formales de control de acceso de usuarios establecidas. | Incumplido: No existe un modelo de permisos basado en roles (RBAC) ni políticas formales. |
| | **X** | Confidencialidad y privacidad de datos sensibles (PII/SPII). | Incumplido: Compromiso evidente del principio de confidencialidad de la tríada CIA. |
| **X** | | Integridad de datos (consistentes, completos, precisos y validados). | Cumplido: El departamento de TI implementó mecanismos para asegurar la integridad. |
| **X** | | Disponibilidad de los datos para los usuarios autorizados. | Cumplido: La disponibilidad operativa está garantizada para las operaciones del negocio. |

---

## 5. Análisis de Brechas según la Tríada CIA

* **Confidencialidad (*Confidentiality*):** **Comprometida críticamente.** La ausencia de cifrado y de políticas de mínimos privilegios expone la información financiera y privada a amenazas internas, escalada de privilegios y accesos no autorizados.
* **Integridad (*Integrity*):** **Controlada.** El departamento de TI mantiene controles para asegurar que los datos no se corrompan ni se alteren sin autorización durante su ciclo de vida.
* **Disponibilidad (*Availability*):** **En Riesgo Moderado/Alto.** Aunque los sistemas están operativos actualmente, la falta de copias de seguridad (*backups*) y la ausencia de un Plan de Recuperación ante Desastres (*DRP*) dejan a Botium Toys indefensa ante incidentes de *ransomware* o fallos catastróficos de hardware.

