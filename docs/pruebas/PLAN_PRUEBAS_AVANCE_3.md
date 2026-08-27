# AVANCE 3/4 — PLAN DE PRUEBAS Y CASOS DE PRUEBA

## Sistema de Gestión de Citas Veterinarias

**Asignatura:** Ingeniería de Software
**Unidad:** Unidad III
**Semana:** 11
**Avance:** 3 de 4
**Módulo:** Gestión de citas veterinarias
**Tecnología:** Python + Django

---

# 1. PLAN DE PRUEBAS

## 1.1 Objetivo

El objetivo de este plan de pruebas es verificar que el módulo de **Gestión de Citas Veterinarias** funcione correctamente y cumpla con los requerimientos establecidos para el registro, consulta, modificación y cancelación de citas.

Las pruebas se diseñan en tres niveles: **unitarias, integración y aceptación**, con el propósito de comprobar tanto el funcionamiento de componentes individuales como la interacción entre ellos y el cumplimiento de las necesidades del usuario.

## 1.2 Alcance

Las pruebas estarán enfocadas en las principales funcionalidades del módulo:

* Registro de citas veterinarias.
* Validación de los datos ingresados.
* Validación de fechas.
* Almacenamiento de citas.
* Consulta de citas.
* Modificación de citas.
* Cancelación de citas.

Se realizarán los siguientes tipos de pruebas:

* **Pruebas unitarias:** comprobarán funciones individuales de validación.
* **Pruebas de integración:** comprobarán la interacción entre el módulo de citas y la base de datos.
* **Pruebas de aceptación:** comprobarán el funcionamiento del sistema desde el punto de vista del usuario.

## 1.3 Criterio de éxito

El módulo será considerado aprobado cuando los casos de prueba definidos obtengan los resultados esperados y no se presenten errores que impidan realizar correctamente las operaciones principales de gestión de citas.

Los casos de prueba críticos tendrán prioridad para su automatización en la Semana 12.

---

# 2. REQUERIMIENTOS RELACIONADOS

Para establecer la trazabilidad entre los requerimientos y los casos de prueba, se consideran los siguientes requerimientos funcionales:

| ID    | Requerimiento                                                                                                                                            |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RF-01 | El sistema debe permitir registrar una cita veterinaria ingresando los datos requeridos de la mascota, propietario, fecha, hora y motivo de la consulta. |
| RF-02 | El sistema debe permitir consultar las citas veterinarias registradas.                                                                                   |
| RF-03 | El sistema debe permitir modificar los datos de una cita veterinaria existente.                                                                          |
| RF-04 | El sistema debe permitir cancelar una cita veterinaria registrada.                                                                                       |
| RF-05 | El sistema debe validar que los datos ingresados para una cita sean correctos antes de registrarla.                                                      |

---

# 3. CASOS DE PRUEBA UNITARIOS

## CP-01 — Validación de fecha de cita

**ID:** CP-01
**Nivel:** Unitaria
**Prioridad:** Alta
**Requerimiento relacionado:** RF-05

### Objetivo

Comprobar que la función de validación rechace una fecha de cita anterior a la fecha actual.

### Entrada

Fecha actual:

**27/08/2026**

Fecha ingresada:

**20/08/2026**

### Pasos

1. Ejecutar la función encargada de validar la fecha de la cita.
2. Ingresar como fecha de cita el **20/08/2026**.
3. Comparar la fecha ingresada con la fecha actual.
4. Verificar el resultado de la validación.

### Resultado esperado

La función debe rechazar la fecha ingresada y devolver un resultado de validación negativo o mostrar un mensaje indicando que la fecha de la cita no es válida porque es anterior a la fecha actual.

---

## CP-02 — Validación de campos obligatorios

**ID:** CP-02
**Nivel:** Unitaria
**Prioridad:** Alta
**Requerimiento relacionado:** RF-05

### Objetivo

Comprobar que el sistema detecte campos obligatorios vacíos antes de registrar una cita.

### Entrada

```text
Mascota: Max
Propietario: Juan Pérez
Fecha: vacío
Hora: 10:00
Motivo: Vacunación
```

### Pasos

1. Ejecutar la función de validación de datos.
2. Ingresar los datos de la cita.
3. Dejar vacío el campo correspondiente a la fecha.
4. Ejecutar la validación.
5. Verificar el resultado obtenido.

### Resultado esperado

La validación debe fallar y el sistema debe identificar que la fecha es un campo obligatorio, evitando que la cita sea considerada válida para su registro.

---

## CP-03 — Validación de datos correctos

**ID:** CP-03
**Nivel:** Unitaria
**Prioridad:** Media
**Requerimiento relacionado:** RF-05

### Objetivo

Comprobar que la función de validación acepte una cita cuyos datos sean correctos y completos.

### Entrada

```text
Mascota: Max
Propietario: Juan Pérez
Fecha: 30/08/2026
Hora: 10:00
Motivo: Vacunación
```

### Pasos

1. Ejecutar la función de validación.
2. Ingresar todos los datos requeridos.
3. Utilizar una fecha válida.
4. Utilizar una hora válida.
5. Ejecutar la validación.
6. Verificar el resultado.

### Resultado esperado

La función debe aceptar los datos y devolver un resultado de validación positivo, indicando que la información puede continuar hacia el proceso de registro.

---

# 4. CASOS DE PRUEBA DE INTEGRACIÓN

## CP-04 — Registro y almacenamiento de una cita

**ID:** CP-04
**Nivel:** Integración
**Prioridad:** CRÍTICA
**Requerimiento relacionado:** RF-01

### Objetivo

Comprobar que el módulo de gestión de citas pueda registrar una cita válida y almacenarla correctamente en la base de datos.

### Entrada

```text
Mascota: Max
Propietario: Juan Pérez
Fecha: 30/08/2026
Hora: 10:00
Motivo: Vacunación
```

### Pasos

1. Acceder al módulo de gestión de citas.
2. Seleccionar la opción para registrar una nueva cita.
3. Ingresar los datos de la mascota.
4. Ingresar los datos del propietario.
5. Seleccionar una fecha válida.
6. Seleccionar una hora válida.
7. Ingresar el motivo de la consulta.
8. Confirmar el registro.
9. Consultar las citas almacenadas.
10. Verificar que la nueva cita aparezca en la base de datos.

### Resultado esperado

El sistema debe registrar correctamente la cita y almacenarla en la base de datos.

Al realizar una consulta posterior, la cita debe aparecer con los mismos datos ingresados.

---

## CP-05 — Modificación de una cita existente

**ID:** CP-05
**Nivel:** Integración
**Prioridad:** Alta
**Requerimiento relacionado:** RF-03

### Objetivo

Comprobar que la modificación de una cita actualice correctamente la información almacenada en la base de datos.

### Entrada

Datos actuales:

```text
Mascota: Max
Fecha: 30/08/2026
Hora: 10:00
Motivo: Vacunación
```

Nuevos datos:

```text
Fecha: 31/08/2026
Hora: 11:00
Motivo: Control general
```

### Pasos

1. Consultar una cita existente.
2. Seleccionar la opción de modificar.
3. Cambiar la fecha de **30/08/2026** a **31/08/2026**.
4. Cambiar la hora de **10:00** a **11:00**.
5. Cambiar el motivo a **Control general**.
6. Guardar los cambios.
7. Consultar nuevamente la cita.
8. Verificar los datos actualizados.

### Resultado esperado

El sistema debe actualizar correctamente la cita en la base de datos.

Al consultarla nuevamente, debe mostrar la nueva fecha, hora y motivo, manteniendo la identificación correcta de la cita.

---

# 5. CASO DE PRUEBA DE ACEPTACIÓN

## CP-06 — Registro completo de una cita por parte del usuario

**ID:** CP-06
**Nivel:** Aceptación
**Prioridad:** CRÍTICA
**Requerimiento relacionado:** RF-01

### Objetivo

Comprobar desde el punto de vista del usuario que el sistema permita registrar una cita veterinaria completa y que esta quede disponible para su consulta.

### Entrada

La recepcionista dispone de los siguientes datos:

```text
Mascota: Max
Propietario: Juan Pérez
Fecha: 30/08/2026
Hora: 10:00
Motivo: Vacunación
```

### Pasos

1. La recepcionista ingresa al sistema.
2. Accede al módulo de gestión de citas.
3. Selecciona la opción "Nueva cita".
4. Ingresa el nombre de la mascota.
5. Ingresa los datos del propietario.
6. Selecciona la fecha.
7. Selecciona la hora.
8. Ingresa el motivo de la consulta.
9. Confirma el registro.
10. Consulta las citas del día.
11. Localiza la cita recién registrada.

### Resultado esperado

El sistema debe confirmar que la cita fue registrada correctamente y mostrarla posteriormente en la consulta de citas con los datos ingresados.

La recepcionista debe poder comprobar visualmente que la cita se encuentra registrada.

---

# 6. MATRIZ GENERAL DE CASOS DE PRUEBA

| ID    | Nivel       | Caso de prueba                          | Prioridad | Requerimiento |
| ----- | ----------- | --------------------------------------- | --------- | ------------- |
| CP-01 | Unitaria    | Validación de fecha anterior            | Alta      | RF-05         |
| CP-02 | Unitaria    | Validación de campos obligatorios       | Alta      | RF-05         |
| CP-03 | Unitaria    | Validación de datos correctos           | Media     | RF-05         |
| CP-04 | Integración | Registro y almacenamiento de cita       | Crítica   | RF-01         |
| CP-05 | Integración | Modificación de cita existente          | Alta      | RF-03         |
| CP-06 | Aceptación  | Registro completo por parte del usuario | Crítica   | RF-01         |

---

# 7. TRAZABILIDAD ENTRE REQUERIMIENTOS Y PRUEBAS

La trazabilidad permite comprobar qué casos de prueba verifican cada requerimiento funcional.

| Requerimiento | Descripción                    | Casos de prueba         |
| ------------- | ------------------------------ | ----------------------- |
| RF-01         | Registrar una cita veterinaria | CP-04, CP-06            |
| RF-02         | Consultar citas registradas    | CP-04, CP-06            |
| RF-03         | Modificar una cita             | CP-05                   |
| RF-04         | Cancelar una cita              | Pendiente de ampliación |
| RF-05         | Validar los datos de una cita  | CP-01, CP-02, CP-03     |

### Trazabilidad principal

El caso **CP-04** se deriva directamente del requerimiento **RF-01**, ya que verifica que una cita válida pueda registrarse y almacenarse correctamente en la base de datos.

---

# 8. CASO DE PRUEBA MÁS CRÍTICO

## CP-04 — Registro y almacenamiento de una cita

El caso de prueba más crítico del módulo es **CP-04**, porque verifica una de las funciones esenciales del sistema: registrar una cita y almacenarla correctamente en la base de datos.

Si este caso falla, el usuario podría ingresar los datos de una cita, pero la información no quedaría almacenada correctamente. Esto impediría posteriormente consultar o gestionar la cita.

Por esta razón, **CP-04 tendrá prioridad para ser automatizado en la Semana 12**.

El caso **CP-06** también tiene prioridad alta porque valida el flujo completo desde el punto de vista del usuario.

---

# 9. CRITERIOS DE APROBACIÓN

El diseño de pruebas se considera completo cuando:

* Existen al menos 3 casos de prueba unitarios.
* Existen al menos 2 casos de prueba de integración.
* Existe al menos 1 caso de prueba de aceptación.
* Cada caso posee un identificador.
* Cada caso identifica su nivel de prueba.
* Cada caso contiene entrada y pasos.
* Cada caso contiene un resultado esperado concreto y verificable.
* Al menos un caso está relacionado directamente con un requerimiento del SRS.
* Existe trazabilidad entre requerimientos y casos de prueba.
* Se identifica el caso de prueba más crítico.
* Los casos están preparados para su automatización en la Semana 12.

---

# 10. TRABAJO FUTURO — SEMANA 12

Los casos definidos en este documento serán utilizados como base para implementar las pruebas automáticas del proyecto.

En la Semana 12 se convertirán los casos de prueba en pruebas automatizadas utilizando las herramientas correspondientes al proyecto desarrollado con Python + Django.

Los casos prioritarios para automatización serán:

1. CP-04 — Registro y almacenamiento de una cita.
2. CP-01 — Validación de fecha.
3. CP-02 — Validación de campos obligatorios.
4. CP-03 — Validación de datos correctos.
5. CP-05 — Modificación de una cita.
6. CP-06 — Flujo completo de aceptación.

Las pruebas automatizadas posteriormente serán integradas al flujo de CI del repositorio.

---

# 11. CONCLUSIÓN

El presente plan de pruebas establece una estrategia para verificar el correcto funcionamiento del módulo de Gestión de Citas Veterinarias.

Se definieron seis casos de prueba distribuidos en tres niveles: tres pruebas unitarias, dos pruebas de integración y una prueba de aceptación.

Los casos permiten comprobar la validación de datos, el registro y almacenamiento de citas, la modificación de información y el flujo de registro desde la perspectiva del usuario.

Además, se estableció la trazabilidad con los requerimientos funcionales y se identificó el caso CP-04 como el caso más crítico para su posterior automatización en la Semana 12.
