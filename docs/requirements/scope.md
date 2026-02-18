# Scope - Bankify Diagrama de contexto

## a. Sistema
**Nombre:** Bankify — Sistema de gestión básica de cuentas bancarias.  
**Descripción breve:** Sistema orientado a gestionar cuentas bancarias, validar códigos de bancos, consultar saldos, procesar depósitos y generar reportes tributarios PDF para clientes y JSON para la autoridad.

## b. Problema a resolver
Actualmente no existe un sistema centralizado que permita:
- Registrar cuentas bancarias con validación del banco asociado.
- Consultar el saldo de las cuentas de forma segura.
- Realizar depósitos con control básico de validaciones.
- Generar reportes tributarios en PDF para cada cliente y exportar reportes en JSON para la autoridad tributaria.

## c. Diagrama de contexto
**Imagen :** `docs/uml/context.png`  
**Descripción del diagrama:** El sistema Bankify muestra su límite frente a actores externos: clientes consultas y depósitos, asesores/operadores gestión de cuentas, supervisores gestión de clientes, gerente financiero reportes, la autoridad tributaria receptor de JSON y bancos externos validación de códigos. Las interacciones principales son: consultas de saldo, depósitos, gestión de cuentas, validación de bancos y envío de reportes agregados.

## d. Alcance del sistema
**Incluido en el MVP:**
- Registro y validación de cuentas formato: 10 dígitos los 2 primeros identifican el banco.
- Consulta de saldo por cliente.
- Realizar depósitos y registro de transacciones.
- Generación de reportes en PDF para clientes.
- Exportación de reportes agregados en JSON para la autoridad tributaria.

**Fuera del alcance:**
- Transferencias interbancarias en tiempo real.
- Integración con pasarelas de pago externas.
- Funcionalidades de inversión, préstamos o multi-moneda.
- Alta disponibilidad y replicación distribuida.

**Suposiciones y restricciones:**
- El catálogo de bancos válidos se mantiene en una lista administrable.
- Formato de cuenta: exactamente 10 dígitos numéricos.
- Los reportes a la autoridad usan un esquema JSON simplificado .
