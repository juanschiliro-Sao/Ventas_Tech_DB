Contexto
Sos el DBA de TechStore, una cadena de tiendas de tecnología. Tu tarea es crear la base de datos Ventas_Tech_DB con un modelo relacional correcto que soporte las operaciones de ventas del negocio.
--Crear la base de datos
CREATE DATABASE Ventas_Tech_DB
--DROP TABLES
Se agrego al inicio del script las sentencias para eliminar las tablas si ya existen, respetando el orden inverso de las dependencias para no violar las foreign keys:
DROP TABLE IF EXISTS ventas;
DROP TABLE IF EXISTS productos;
DROP TABLE IF EXISTS clientes;
DROP TABLE IF EXISTS categorias;
--Se creo las Tablas:
-Tabla Categorias:
Columna,Tipo,Restricción
id_categoria,INT,PRIMARY KEY
nombre_categoria,VARCHAR(50),NOT NULL
descripcion,VARCHAR(200),​
- Tabla clientes:
- Columna,Tipo,Restricción
id_cliente,INT,PRIMARY KEY
nombre,VARCHAR(100),NOT NULL
email,VARCHAR(100),UNIQUE
ciudad,VARCHAR(50),​
fecha_registro,DATE,NOT NULL
-Tabla productos:
Columna,Tipo,Restricción
id_producto,INT,PRIMARY KEY
nombre_producto,VARCHAR(100),NOT NULL
id_categoria,INT,FOREIGN KEY → categorias
precio,"DECIMAL(10,2)",NOT NULL
stock,INT,DEFAULT 0
activo,TINYINT(1),DEFAULT 1
-Tabla ventas:
Columna,Tipo,Restricción
id_producto,INT,PRIMARY KEY
nombre_producto,VARCHAR(100),NOT NULL
id_categoria,INT,FOREIGN KEY → categorias
precio,"DECIMAL(10,2)",NOT NULL
stock,INT,DEFAULT 0
activo,TINYINT(1),DEFAULT 1
--INSERT DATA
  -Pasamos a insertar resgistros en las tablas creadas:
INSERT INTO clientes VALUES (1, 'María López',   'maria@mail.com',   'Buenos Aires', '2024-01-05');
INSERT INTO clientes VALUES (2, 'Carlos Ruiz',   'carlos@mail.com',  'Córdoba',      '2024-01-10');
INSERT INTO clientes VALUES (3, 'Ana Gómez',     'ana@mail.com',     'Rosario',      '2024-02-01');
INSERT INTO clientes VALUES (4, 'Pedro Sanz',    'pedro@mail.com',   'Mendoza',      '2024-02-15');
INSERT INTO clientes VALUES (5, 'Laura Torres',  'laura@mail.com',   'Tucumán',      '2024-03-01');
INSERT INTO categorias VALUES (1, 'Computación', 'Laptops, PCs y monitores');
INSERT INTO categorias VALUES (2, 'Accesorios', 'Periféricos y complementos');
INSERT INTO categorias VALUES (3, 'Audio', 'Auriculares y parlantes');
INSERT INTO categorias VALUES (4, 'Almacenamiento', 'Discos y memorias');
INSERT INTO productos VALUES (1, 'Laptop Pro 15',       1, 1200.00, 15, 1);
INSERT INTO productos VALUES (2, 'Mouse Inalámbrico',   2,   28.00, 80, 1);
INSERT INTO productos VALUES (3, 'Monitor 4K 27"',      1,  450.00, 12, 1);
INSERT INTO productos VALUES (4, 'Auriculares BT Pro',  3,  120.00, 35, 1);
INSERT INTO productos VALUES (5, 'SSD Externo 1TB',     4,  130.00, 18, 1);
INSERT INTO productos VALUES (6, 'Teclado Mecánico',    2,   95.00, 40, 1);

Ejecute exitosamente el script sin errores.

-- Confirmá que cada tabla se cargó correctamente
SELECT * FROM categorias;
SELECT * FROM clientes;
SELECT * FROM productos;
SELECT * FROM ventas;

