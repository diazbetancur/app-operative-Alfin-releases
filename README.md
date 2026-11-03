# app-operative-Alfin-releases

Descargas oficiales de las versiones de prueba (QA) de la aplicación operativa de ALFIN para Android.

**Versión actual: `qa-v1.4.0`** (2026-11-03). Se descarga desde la sección *Releases* de este
repositorio.

Estas versiones son **solo para el ambiente de pruebas**. No se usan contra producción.

---

## Los dos bugs reportados por QA el 22/10 están corregidos en `qa-v1.4.0`

**No lo estaban en `qa-v1.3.1`.** Con la 1.3.1 siguen ocurriendo; con la 1.4.0 no deben ocurrir.
Si ocurren con la 1.4.0, **sí es un defecto**: repórtalo.

1. **Datos del cónyuge al registrar un cliente** casado o en unión libre.
2. **Guardar un cliente viudo.**

---

## Estado de la aplicación en `qa-v1.4.0`

### ✅ Verificado en dispositivo (ambiente de pruebas)

La cadena completa de un crédito, con usuarios de un solo rol:

1. Alta de cliente con sus diez datos, incluido el cónyuge cuando corresponde.
2. Creación de la solicitud.
3. Inventario del negocio.
4. Fotografías de la solicitud.
5. Dueño del negocio y ubicación de la casa y del negocio.
6. Envío a evaluación.
7. Asignación del verificador.
8. Evaluación de la zona y verificación.
9. Aprobación, con cobrador y desembolsador.
10. Desembolso con sus dos fotografías (identidad y firma del contrato).
11. Cambio de cobrador.
12. Cartera del cobrador y registro de pagos con comprobante.

También: rechazar y devolver a corrección desde la bandeja del aprobador, y el buscador de la
cartera de cobros.

### 🆕 Nuevo en `qa-v1.4.0`, pendiente de verificar en dispositivo

- **Buscador en las listas**: cola de desembolso, "Mis solicitudes", bandeja del aprobador y
  préstamos. Si una búsqueda no cubre la lista completa, la pantalla lo dice con un aviso
  amarillo: **ese aviso no es un defecto**.
- **Desglose de cada pago**: el total pagado y en qué se aplicó (mora, servicio de cobranza,
  interés, capital y otros cargos). Un pago puede aplicarse entero a mora: el saldo baja poco
  aunque el cliente pagó, y es correcto.
- **Saldo actual, días de atraso y mora pendiente** en el detalle del crédito.
- **Detalle del crédito en dos pestañas**, "Solicitud" y "Pagos recientes", para el cobrador.
- **Aviso de crédito saldado** en el comprobante del pago.
- **Corregidos:** el estado de las solicitudes en la ficha del cliente, el importe de los pagos
  aplicados a mora (salía L 0.00) y el orden de la bandeja del aprobador.

### ⛔ Pendiente de backend

- **Aprobación de solicitudes marcadas con aval.** La aprobación responde *"Debe seleccionar un
  aval"*. Hoy no existe en el servicio una forma de registrar el aval desde la aplicación; está
  consultado con backend. **No es un defecto de la aplicación.** Las solicitudes sin esa marca se
  aprueban con normalidad.

### Mensajes que no son defectos

- **"Mora pendiente no disponible"** o **"Desglose no disponible para este pago"**: aparecen cuando
  los importes del servidor no cuadran entre sí, en lugar de mostrar una cifra que podría ser
  falsa.
- **Un crédito saldado desaparece de la cartera del cobrador.** Es conocido: el comprobante lo
  avisa en el momento del pago.

---

## Qué usuario hace falta en cada paso

Cada sección de la solicitud **solo la ve el responsable que el sistema tiene asignado a esa
solicitud**, no cualquier usuario con el mismo rol. Si una sección no aparece, lo primero es
comprobar **quién está asignado**: casi siempre la causa es esa, y **no es un defecto**.

| Paso | Usuario que lo hace |
|---|---|
| Alta de cliente y creación de la solicitud | Un **asesor** |
| Inventario, fotografías, dueño y ubicaciones, envío a evaluación | **El asesor que creó el borrador**. Otro asesor no ve estas secciones en esa solicitud |
| Asignación del verificador | Un **jefe** (agencia o regional) |
| Evaluación de la zona y verificación | **El verificador asignado** a esa solicitud |
| Aprobación (y elegir cobrador y desembolsador) | Un **jefe** con permiso de aprobar |
| Fotos del desembolso y confirmación | **El desembolsador asignado** en la aprobación. Puede ser un jefe, si se asignó a sí mismo |
| Cambio de cobrador | Un **jefe** |
| Cartera, registro de pagos, saldo y desglose | **El cobrador asignado** en la aprobación o en el cambio |

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
