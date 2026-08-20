# Sistema de Gestión de Citas Veterinarias

## Información del proyecto

**Módulo:** Gestión de citas veterinarias  
**Tecnología:** Python + Django  
**Asignatura:** Ingeniería de Software  
**Universidad:** Universidad Estatal Amazónica

## Descripción

El módulo de Gestión de Citas Veterinarias permitirá registrar, consultar, modificar y cancelar citas para mascotas.

## Integrantes

- Wilmer Danilo Quitio Pilataxi
- Agregar integrantes si corresponde

## Estructura del proyecto

```text
gestion-citas-veterinarias/
├── README.md
├── .gitignore
├── src/
└── .github/
    └── workflows/
        └── ci.yml
## Flujo de trabajo con GitHub Flow

El proyecto utiliza un flujo de trabajo basado en GitHub Flow.

- `main`: rama principal y estable del proyecto.
- `feature/*`: ramas utilizadas para desarrollar nuevas funcionalidades.
- Cada funcionalidad se desarrolla en una rama independiente.
- Los cambios se guardan mediante commits con mensajes claros.
- Al finalizar una funcionalidad, se realiza un Pull Request hacia `main`.
- Después de revisar y verificar los cambios, se fusionan a `main`.

### Ejemplo de rama de trabajo

`feature/registrar-cita`