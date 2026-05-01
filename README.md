# Sistema-de-ventas
Este es un sistema de ventas como proyecto de Bases de datos 2
# Dulceria
# Enunciado
a: La dulcería registra información sobre las personas, incluyendo el nombre, apellido, número de identificación (DNI), dirección, teléfono y correo electrónico.
Las personas pueden clasificarse en clientes y empleados.
Para los clientes, se almacena el tipo de cliente (regular o frecuente) y la fecha de registro.
Para los empleados, se registra el cargo, salario y horario de trabajo.
El DNI tiene valores únicos para cada persona.

b: Cada categoría de productos está descrita por un nombre y una descripción.
El nombre de la categoría es único para cada una.

c: Cada producto tiene un código, nombre, descripción, precio y stock disponible.
Los productos pertenecen a una categoría.
Existen dos tipos de productos:
Productos simples, que se venden de manera individual.
Productos compuestos, que están formados por uno o más productos simples, incluyendo la cantidad de cada uno dentro del compuesto.
El código de producto es único para cada producto.

d: Cada venta está asociada a un cliente y es registrada por un empleado.
De cada venta se registra la fecha, el total y un identificador único de venta.
Cada venta incluye uno o varios productos. Para cada producto vendido se registra la cantidad y el precio unitario en el momento de la venta.

e: Cada pago corresponde a una venta e incluye el tipo de pago, el monto y la fecha.
Existen diferentes tipos de pago:
Pago en efectivo, donde se registra el monto entregado y el cambio.
Pago con tarjeta, donde se almacena el número de transacción y la entidad bancaria.
Pago por transferencia, donde se registra el número de operación y el banco emisor.
# Entidades y atributos
1. Persona (Entidad general)
DNI (PK)
nombre
apellido
dirección
teléfono
correo

2. Cliente (Subclase de Persona)
DNI (PK, FK de Persona)
tipo_cliente
fecha_registro
3. Empleado (Subclase de Persona)
DNI (PK, FK de Persona)
cargo
salario
horario
4. Categoría
id_categoria (PK)
nombre (único)
descripción
5. Producto (Entidad general)
codigo_producto (PK)
nombre
descripción
precio
stock
id_categoria (FK)
6. ProductoSimple (Subclase de Producto)
codigo_producto (PK, FK de Producto)

7. ProductoCompuesto (Subclase de Producto)
codigo_producto (PK, FK de Producto)

8. Venta
id_venta (PK)
fecha
total
DNI_cliente (FK)
DNI_empleado (FK)
9. DetalleVenta (Entidad débil o intermedia)
id_venta (PK, FK)
codigo_producto (PK, FK)
cantidad
precio_unitario

10. Pago (Entidad general)
id_pago (PK)
fecha
monto
id_venta (FK)

11. PagoEfectivo (Subclase de Pago)
id_pago (PK, FK)
monto_entregado
cambio

12. PagoTarjeta (Subclase de Pago)
id_pago (PK, FK)
numero_transaccion
entidad_bancaria

13. PagoTransferencia (Subclase de Pago)
id_pago (PK, FK)
numero_operacion
banco_emisor