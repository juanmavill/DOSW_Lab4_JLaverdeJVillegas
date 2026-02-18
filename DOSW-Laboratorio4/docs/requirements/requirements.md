# 📄 Requerimientos del Sistema

## 1. Lista general de requerimientos

El sistema de Bankify tiene los siguientes requerimientos (descripción a alto nivel):

### 1.1 Requerimientos funcionales

El sistema de Bankify debe tener la capacidad de:

1. Permitir el registro y gestión de clientes con sus datos básicos.
2. Crear cuentas bancarias asociadas a un cliente específico.
3. Realizar consignaciones a cuentas Bankify validando el origen de los fondos.
4. Consultar el saldo actual y el historial de movimientos de una cuenta.
5. Generar reportes de transacciones mensuales en formato PDF para el cliente.

### 1.2 Requerimientos no funcionales

El sistema de Bankify debe cumplir con:

1. El número de cuenta debe ser único y tener una longitud exacta de 10 dígitos numéricos.
2. Los reportes generados para la DIAN deben estar en formato JSON estandarizado.
3. La interfaz de usuario debe incluir el logo de Bankify visible en todas las pantallas.
4. El sistema solo debe permitir transacciones de bancos autorizados (ej. Bancolombia, Davivienda).
5. Las contraseñas de los usuarios deben almacenarse encriptadas (SHA-256 o superior).

## 2. Diagramas de caso de uso

### 2.1 Requerimiento Funcional 1: Crear Cuenta Bancaria

| Campo | Descripción |
|------|-------------|
| **ID** | RF-02 |
| **Nombre del requerimiento** | Crear cuenta bancaria |
| **Descripción** | *El sistema debe permitir a un operador crear una nueva cuenta de ahorros para un cliente existente.* |
| **Precondiciones** | *El cliente debe estar previamente registrado en el sistema y no estar bloqueado.* |
| **Actor** | Operador de Bankify |
| **Flujo principal** | 1. El operador selecciona al cliente.<br>2. El sistema solicita tipo de cuenta.<br>3. El sistema genera un número de cuenta único de 10 dígitos.<br>4. El sistema confirma la creación exitosa. |
| **Diagrama de caso de uso** | ![alt text](image.png) |
| **Poscondiciones** | *La cuenta queda activa y con saldo inicial de $0.* |


### 2.2 Requerimiento Funcional 2: Realizar Consignación

| Campo | Descripción |
|------|-------------|
| **ID** | RF-03 |
| **Nombre del requerimiento** | Realizar consignación |
| **Descripción** | *El sistema debe permitir ingresar dinero a una cuenta Bankify proveniente de bancos externos.* |
| **Precondiciones** | *La cuenta destino debe existir y estar activa.* |
| **Actor** | Cliente / Cajero |
| **Flujo principal** | 1. El actor ingresa el número de cuenta destino y el monto.<br>2. El sistema valida que el banco origen sea permitido (Bancolombia/Davivienda).<br>3. El sistema registra la transacción.<br>4. El sistema actualiza el saldo. |
| **Diagrama de caso de uso** | ![alt text](image-1.png) |
| **Poscondiciones** | *El saldo de la cuenta se incrementa por el valor consignado.* |

### 2.3 Requerimiento Funcional 3: Generar Reporte DIAN

| Campo | Descripción |
|------|-------------|
| **ID** | RF-06 |
| **Nombre del requerimiento** | Generar reporte regulatorio (DIAN) |
| **Descripción** | *El sistema debe generar un archivo con las transacciones que superen los topes legales.* |
| **Precondiciones** | *Deben existir transacciones registradas en el periodo seleccionado.* |
| **Actor** | Supervisor / Auditor |
| **Flujo principal** | 1. El supervisor selecciona el rango de fechas.<br>2. El sistema filtra las transacciones.<br>3. El sistema formatea la data a estructura JSON.<br>4. El sistema permite descargar el archivo. |
| **Diagrama de caso de uso** |![alt text](image-2.png) |
| **Poscondiciones** | *Se descarga un archivo .json con la estructura requerida.* |

## 3. Preguntas de Análisis

### a. ¿Identifica algún requerimiento que deba detallarse más? ¿cuál(es)?
Sí, el requerimiento de "Validar origen de fondos de bancos externos". Actualmente es ambiguo cómo Bankify se conecta con Bancolombia o Davivienda. No se especifica si es una integración por API en tiempo real, una carga de archivos planos (batch) o una validación manual por parte del operador. Esto es crítico para la arquitectura.

### b. ¿Existen requerimientos que se contradigan entre sí? ¿cuál(es)?
Sí. Existe una contradicción entre la experiencia de usuario (Inmediatez) y la seguridad (Validación Externa).

Al realizar una consignación (RF-03), el usuario espera ver su saldo actualizado al instante. Sin embargo, el requisito de "Validar el origen de los fondos con el banco externo" obliga al sistema a esperar una confirmación de Bancolombia o Davivienda. Si el sistema externo es lento, no se puede cumplir con la actualización inmediata del saldo.

### c. Si tuviera que dar una prioridad a los requerimientos, ¿cuáles deberían ser los 2 más importantes?
1.  **RF-01 Gestión de Clientes y Cuentas:** Sin clientes ni cuentas, no existe el negocio base.
2.  **RF-03 Realizar Consignación:** Es la funcionalidad principal que permite el ingreso de capital al sistema. Los reportes y la integración con la DIAN pueden esperar a una segunda iteración.

### d. ¿Existe algún requerimiento que no debería realizarse?
En una primera fase (MVP), el requerimiento de Reportes para la DIAN en JSON podría posponerse. Es un requerimiento regulatorio importante, pero no bloquea la operación funcional básica de captar dinero y gestionar cuentas. Este debería realizarse solo cuando el núcleo de la aplicación sea estable y funcional.

### agregamos el link del mockups 
https://group-duct-40810633.figma.site/
