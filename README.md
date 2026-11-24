# Prácticas de C# y Windows Forms

Repositorio de ejercicios introductorios de desarrollo de aplicaciones de escritorio con C#. Cada carpeta contiene una solución independiente de Visual Studio; no hay una única aplicación que reúna todas las prácticas.

## Stack y herramientas

- **Lenguaje:** C#.
- **Interfaz gráfica:** Windows Forms (WinForms).
- **Framework:** .NET Framework 4.5.
- **IDE y compilación:** soluciones y proyectos clásicos de Visual Studio/MSBuild.
- **Persistencia en la práctica ABM:** Microsoft SQL Server mediante ADO.NET (`System.Data.SqlClient`).

WinForms y .NET Framework requieren Windows. Para abrir y compilar estos proyectos, usa Visual Studio con el soporte de desarrollo de escritorio de .NET y el paquete de destino de .NET Framework 4.5.

## Prácticas incluidas

| Carpeta | Solución | Qué se practica |
| --- | --- | --- |
| [`MiPrimeraApp`](MiPrimeraApp/MiPrimeraApp.sln) | `MiPrimeraApp.sln` | Estructura inicial de un formulario, eventos de controles y cierre de la ventana desde un botón. |
| [`Combo List Picture`](Combo%20List%20Picture/Combo%20List%20Picture.sln) | `Combo List Picture.sln` | Uso de `ListBox`, `ComboBox` y `PictureBox` para seleccionar lenguajes y mostrar sus imágenes. Incluye imágenes de C, C++ y C#. |
| [`Log in`](Log%20in/Log%20in.sln) | `Log in.sln` | Formulario de inicio de sesión, validación de campos, mensajes al usuario y apertura de una segunda ventana que simula un escritorio. |
| [`ABM`](ABM/ABM.sln) | `ABM.sln` | Alta, baja y modificación de alumnos; búsqueda por nombre y presentación de registros en un `DataGridView` conectado a SQL Server. |

## Estructura

Cada carpeta contiene un archivo `.sln` y un proyecto `.csproj`. Dentro del proyecto se encuentran el código de los formularios (`Form1.cs` y los formularios adicionales), sus archivos del diseñador (`*.Designer.cs`) y recursos. Los formularios se inician desde `Program.cs`.

La práctica **ABM** también incluye:

- `ABM/ABM/Conexion.cs`: conexión y operaciones de consulta con SQL Server.
- `ABM/ABM/sql/query.sql`: inserciones de ejemplo y una consulta de lectura para `alumnos_Tabla`.
- `ABM/ABM/AlumnosDataSet.xsd`: definición del conjunto de datos tipado.

## Cómo abrir y ejecutar una práctica

1. Clona o descarga el repositorio en un equipo Windows.
2. Abre en Visual Studio el archivo `.sln` de la práctica que quieras ejecutar.
3. Restaura o instala los componentes de desarrollo de .NET Framework 4.5 si Visual Studio los solicita.
4. Selecciona el proyecto como proyecto de inicio y ejecuta con **F5**.

Por ejemplo, para trabajar con la gestión de alumnos, abre [`ABM/ABM.sln`](ABM/ABM.sln). Los proyectos son independientes: abre una solución por vez.

## Configuración de la base de datos (ABM)

La aplicación espera una instancia local de SQL Server, una base de datos llamada `Alumnos` y una tabla `alumnos_Tabla` con los campos `Codigo_Alumno`, `Nombre_Alumno`, `Apellido_Alumno` y `Edad_Alumno`. La cadena de conexión está definida en `ABM/ABM/Conexion.cs` y usa autenticación integrada de Windows; ajústala si tu servidor o base de datos tienen otro nombre.

`ABM/ABM/sql/query.sql` contiene datos de ejemplo y un `SELECT`, pero no crea la base de datos ni la tabla. Prepara ese esquema antes de ejecutar la aplicación y carga los datos de ejemplo solo si los necesitas.

## Alcance y consideraciones

- Son ejercicios educativos y de alcance pequeño, no aplicaciones listas para producción.
- El inicio de sesión es una simulación: la validación usa credenciales fijas en el código y no implementa autenticación segura.
- La práctica de imágenes tiene rutas absolutas locales en `Form1.cs`. En otro equipo, actualiza esas rutas para que apunten a la carpeta `images` del proyecto o utiliza recursos/rutas relativas.
- La práctica ABM construye algunas consultas SQL concatenando texto. No uses ese patrón con datos reales; en una aplicación robusta, emplea consultas parametrizadas y administra la conexión de forma segura.
- Los directorios `bin` y `obj` contienen artefactos de compilación existentes; el código fuente y los formularios editables están en cada carpeta de proyecto.
