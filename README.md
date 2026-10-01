# app-operative-Alfin-releases

Descargas oficiales de las versiones de prueba (QA) de la aplicación operativa de ALFIN para Android.

**Versión actual: `qa-v1.3.1`** (2026-10-01). Se descarga desde la sección *Releases* de este
repositorio.

Estas versiones son **solo para el ambiente de pruebas**. No se usan contra producción.

---

## Estado de la aplicación en `qa-v1.3.1`

### ✅ Verificado en dispositivo (2026-10-01, ambiente de pruebas)

Recorrido completo de una solicitud de crédito, de principio a fin de la originación:

1. Alta de cliente con sus diez datos.
2. Creación de la solicitud.
3. Inventario del negocio.
4. Fotografías de la solicitud.
5. Dueño del negocio y ubicación de la casa y del negocio.
6. Envío a evaluación.
7. Asignación del verificador.
8. Evaluación de la zona: referencias zonales y nivel de delincuencia.
9. Verificación.
10. Aprobación.

### ⚙️ Construido, pendiente de verificar en dispositivo

- **Confirmación del desembolso con sus dos fotografías** (identidad y firma del contrato). La
  captura está implementada, pero no se pudo probar: el usuario de prueba del desembolso dejó de
  poder iniciar sesión.
- **Rol de Cobrador**: cartera del cobrador y registro de pagos con comprobante. Está en esta
  versión, pero no se ha probado en dispositivo.

### ⛔ Pendiente de backend

- **Aprobación de solicitudes marcadas con aval.** Si una solicitud tiene marcado que requiere
  aval, la aprobación responde *"Debe seleccionar un aval"*. Hoy no existe en el servicio una forma
  de registrar el aval desde la aplicación; está consultado con backend. **No es un defecto de la
  aplicación.** Las solicitudes sin esa marca se aprueban con normalidad.

---

## Qué usuario hace falta en cada paso

Desde esta versión, cada sección de la solicitud **solo la ve el responsable que el sistema tiene
asignado a esa solicitud**, no cualquier usuario con el mismo rol. Si una sección no aparece, lo
primero es comprobar **quién está asignado**: casi siempre la causa es esa, y **no es un defecto**.

| Paso | Usuario que lo hace |
|---|---|
| Alta de cliente y creación de la solicitud | Un **asesor** |
| Inventario, fotografías, dueño y ubicaciones, envío a evaluación | **El asesor que creó el borrador**. Otro asesor no ve estas secciones en esa solicitud |
| Asignación del verificador | Un **jefe** (agencia o regional) |
| Evaluación de la zona y verificación | **El verificador asignado** a esa solicitud |
| Aprobación (y elegir cobrador y desembolsador) | Un **jefe** con permiso de aprobar |
| Fotos del desembolso y confirmación | **El desembolsador asignado** en la aprobación. Puede ser un jefe, si se asignó a sí mismo |
| Cartera y registro de pagos | **El cobrador asignado** en la aprobación |

Los usuarios de prueba y sus credenciales se entregan **por canal aparte**, junto con el paquete de
entrega a QA.

---

## Cómo instalar

En el teléfono, la aplicación aparece como **Alfin Operative QA**. Es el nombre de la versión de
pruebas: no es un defecto.

Todas las versiones de prueba tienen el mismo número interno de compilación. **Si ya tienes
instalada una versión anterior, desinstálala antes**: Android puede rechazar la actualización.

1. Descarga el archivo `.apk` de la release desde el teléfono.
2. Permite la instalación desde el navegador si Android lo pide.
3. Abre el archivo descargado e instala.

La aplicación pedirá permiso de **ubicación** (casa, negocio y desembolso) y de **cámara**
(fotografías). Sin esos permisos, esas secciones lo indican y no envían nada.
