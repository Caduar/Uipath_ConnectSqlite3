# 🔗 UiPath + SQLite3 Integration

Este proyecto demuestra cómo conectarse a una base de datos **SQLite3** desde **UiPath** utilizando código VB.NET dentro de una actividad **Invoke Code**.

> ✅ Ideal para proyectos que necesitan una base de datos liviana sin instalar servidores externos.

---

## ⚙️ Requisitos

- UiPath Studio (2021 o superior recomendado)
- Archivo DLL: `System.Data.SQLite.dll`
- Base de datos `.db` (ej: `test.db`)
- Actividad `Invoke Code` habilitada

---

## 🧠 ¿Qué hace el flujo?

1. **Carga dinámicamente la DLL** de SQLite.
2. **Establece una conexión** con la base de datos.
3. Ejecuta una consulta `SELECT * FROM usuarios`.
4. Llena un `DataTable` (`out_DtbUsers`) con los resultados.

---

## 📌 Consideraciones importantes

- 📍 **Ruta relativa**: Asegúrate de que las rutas en `Assembly.LoadFrom(...)` y `Data Source=...` coincidan con la estructura real de tu proyecto.
- 🔒 **Evita mover los archivos** luego de configurar las rutas.
- 🔄 **Puedes adaptar este código** para ejecutar `INSERT`, `UPDATE` o `DELETE` simplemente cambiando la consulta SQL.

---

## 🧪 Tabla esperada en la base de datos

Asegúrate de tener esta tabla en tu archivo `test.db`:

```sql
CREATE TABLE usuarios (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nombre TEXT NOT NULL,
    apellido TEXT NOT NULL UNIQUE
);

y algunos datos de ejemplo:
    INSERT INTO usuarios (nombre, apellido)
    VALUES ('Camilo', 'Duarte');
