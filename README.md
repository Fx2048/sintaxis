¡Aquí tienes la **GUÍA DEFINITIVA DE SINTAXIS SQL + NoSQL** para tu parcial, hecha súper simple, directa y con ejemplos que se usan EXACTAMENTE en los exámenes!
Si dominas esto, pasas sí o sí. 💯

---

# 🔥 **GUÍA RÁPIDA DE SINTAXIS SQL – EXAMEN UNIVERSITARIO**

---

# 🟦 1. SELECT (consultas básicas)

### **Estructura general:**

```sql
SELECT columnas
FROM tabla;
```

### Ejemplos:

```sql
SELECT * FROM productos;
SELECT nombre, precio FROM productos;
```

---

# 🟦 2. WHERE (condiciones)

### Sintaxis:

```sql
SELECT columnas
FROM tabla
WHERE condición;
```

### Ejemplos:

```sql
SELECT * FROM productos WHERE precio > 100;
SELECT * FROM compras WHERE fecha = '2024-06-01';
```

---

# 🟦 3. ORDER BY (ordenamiento)

### Sintaxis:

```sql
ORDER BY columna ASC;   -- menor a mayor
ORDER BY columna DESC;  -- mayor a menor
```

### Ejemplo:

```sql
SELECT * FROM productos
ORDER BY precio DESC;
```

---

# 🟦 4. GROUP BY (agregaciones)

### Reglas:

✔ SOLO funciona con funciones como **SUM, COUNT, AVG, MAX, MIN**
✔ No puedes usar SELECT *.

### Sintaxis correcta:

```sql
SELECT columna, SUM(columna2)
FROM tabla
GROUP BY columna;
```

### Ejemplo:

```sql
SELECT id_producto, SUM(cantidad) AS total
FROM compras
GROUP BY id_producto;
```

---

# 🟦 5. HAVING (condiciones para grupos)

```sql
SELECT id_producto, SUM(cantidad) AS total
FROM compras
GROUP BY id_producto
HAVING total > 5;
```

---

# 🟦 6. JOIN (unir tablas)

### Sintaxis general:

```sql
SELECT columnas
FROM tabla1 t1
JOIN tabla2 t2 ON t1.campo = t2.campo;
```

### Ejemplo:

```sql
SELECT c.id_compra, p.nombre, c.cantidad
FROM compras c
JOIN productos p ON c.id_producto = p.id_producto;
```

---

# 🟦 7. DELETE con JOIN (MUY USADO EN EXÁMENES)

### Sintaxis:

```sql
DELETE alias1
FROM tabla1 alias1
JOIN tabla2 alias2 ON alias1.campo = alias2.campo
WHERE condición;
```

### Ejemplo:

```sql
DELETE c
FROM compras c
JOIN productos p ON c.id_producto = p.id_producto
WHERE p.nombre = 'Mouse';
```

---

# 🟦 8. UPDATE (actualizar datos)

### Sintaxis:

```sql
UPDATE tabla
SET columna = valor
WHERE condición;
```

### Ejemplos:

```sql
UPDATE productos
SET precio = 500
WHERE id_producto = 1;

UPDATE productos
SET precio = precio * 1.10   -- aumentar 10%
WHERE id_producto = 3;
```

---

# 🟦 9. INSERT (insertar datos)

### Sintaxis:

```sql
INSERT INTO tabla(col1, col2)
VALUES (valor1, valor2);
```

### Ejemplo:

```sql
INSERT INTO compras(id_producto, cantidad, fecha)
VALUES (2, 3, NOW());
```

---

# 🟦 10. CREATE INDEX (Crear índices)

### Sintaxis:

```sql
CREATE INDEX nombre_indice
ON tabla(columna);
```

### Ejemplo:

```sql
CREATE INDEX idx_precio
ON productos(precio);
```

---

# 🟦 11. FUNCIONES (MySQL)

### Sintaxis correcta:

```sql
CREATE FUNCTION nombre(par1 tipo, par2 tipo)
RETURNS tipo
BEGIN
  RETURN expresión;
END;
```

### Ejemplo real:

```sql
CREATE FUNCTION calcularSubtotal(precio DECIMAL(10,2), cantidad INT)
RETURNS DECIMAL(10,2)
BEGIN
  RETURN precio * cantidad;
END;
```

---

# 🟦 12. PROCEDIMIENTOS (Stored Procedures)

### Sintaxis:

```sql
CREATE PROCEDURE nombre(IN par1 tipo, IN par2 tipo)
BEGIN
  instrucciones SQL;
END;
```

### Ejemplo:

```sql
CREATE PROCEDURE registrarCompra(
  IN p_producto INT,
  IN p_cantidad INT
)
BEGIN
  INSERT INTO compras(id_producto, cantidad, fecha)
  VALUES(p_producto, p_cantidad, NOW());
END;
```

---

# 🟩 **GUÍA RÁPIDA DE NoSQL (MongoDB)**

---

# 🟧 1. find()

```js
db.coleccion.find({ campo: valor })
```

Ejemplo:

```js
db.productos.find({ precio: { $gt: 1000 } })
```

---

# 🟧 2. Insertar documento

```js
db.coleccion.insertOne({
  nombre: "Laptop",
  precio: 3500
})
```

---

# 🟧 3. Actualizar campos

### SET

```js
db.productos.updateOne(
  { nombre: "Laptop" },
  { $set: { precio: 4000 } }
)
```

### PUSH (para agregar al arreglo)

```js
db.productos.updateOne(
  { nombre: "Laptop" },
  { $push: { stock: 14 } }
)
```

### INC (sumar)

```js
db.productos.updateOne(
  { nombre: "Laptop" },
  { $inc: { precio: 100 } }
)
```

---

# 🟩 ¿QUIERES UNA VERSIÓN PDF IMPRIMIBLE?

Te puedo generar un PDF listo para estudiar o imprimir.

¿Quieres que te lo prepare?
