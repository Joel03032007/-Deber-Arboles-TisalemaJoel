# Catálogo de la Biblioteca FISEI: árbol general y ABB en Java

**Asignatura:** Estructura de Datos · **Nivel:** Tercero, Ingeniería de Software
**Estudiante:** Darwin Joel Tisalema Guashco · **Modalidad:** Individual
**Entrega:** 22 de octubre de 2026

## Descripción del problema

La Biblioteca FISEI se organiza en áreas, y cada área contiene estantes. Esa jerarquía (BIBLIOTECA → AREA → ESTANTE) se modela con un **árbol general n-ario**. Cada estante guarda sus libros en un **Árbol Binario de Búsqueda (ABB)** ordenado por el código del libro, un entero positivo que no se repite.

El programa permite construir, consultar, recorrer y modificar ambas estructuras. Todas las operaciones sobre los árboles son recursivas y no se usan `TreeSet`, `TreeMap`, `PriorityQueue`, `NavigableSet`, `NavigableMap`, `Collections.sort` ni `List.sort`.

### Estructura inicial

```
BIB  Biblioteca FISEI
├── SW   Software
│    ├── SW-E1  Estante 1 de Software  → 60, 35, 80, 20, 45, 70, 90, 40, 75
│    └── SW-E2  Estante 2 de Software  → 15, 10, 25
├── TI   Tecnologías de la Información
│    └── TI-E1  Estante 1 de TI        → 50
└── TEL  Telecomunicaciones
```

Resultado esperado: 7 unidades, 4 hojas, altura 2 y 13 libros.

## Estructura del proyecto

```
src/
├── enums/     TipoUnidad.java, TipoRecorrido.java
├── modelo/    Libro.java, UnidadBiblioteca.java
├── negocio/   NodoUnidad.java, NodoLibro.java, ArbolBiblioteca.java, CatalogoABB.java
└── app/       Main.java, DatosPrueba.java, PruebasBiblioteca.java
```

| Clase | Qué hace |
|---|---|
| `TipoUnidad` | Define BIBLIOTECA, AREA y ESTANTE e indica qué tipo puede ser hijo de cuál |
| `TipoRecorrido` | Define PREORDEN, INORDEN y POSORDEN |
| `Libro` | Guarda código (sin setter), título, autor y año (1900–2026), con validaciones |
| `UnidadBiblioteca` | Guarda código (en mayúsculas), nombre y tipo |
| `NodoUnidad` | Nodo del árbol general: dato, lista de hijos y un ABB si es ESTANTE |
| `NodoLibro` | Nodo del ABB: dato, hijo izquierdo y derecho |
| `ArbolBiblioteca` | Agregar y buscar unidades; altura, hojas, nivel, jerarquía y total de libros |
| `CatalogoABB` | Insertar, buscar, contar, recorrer, traza, modificar y eliminar; retos y extra |
| `Main` | Menú interactivo con `Scanner` |
| `DatosPrueba` | Carga la estructura inicial |
| `PruebasBiblioteca` | Casos de prueba con el resultado `X/N pruebas OK` |

## Funcionalidades

- **Árbol general:** agregar unidades respetando la jerarquía y sin códigos repetidos, buscar sin distinguir mayúsculas, altura, número de hojas, nivel de una unidad, jerarquía en preorden y total de libros.
- **ABB de libros:** inserción (rechaza códigos repetidos), búsqueda, recorridos, traza del recorrido, modificación (el código no cambia) y eliminación de hoja, nodo con un hijo y nodo con dos hijos (sucesor inorden).
- **Retos:** `contarEnRango`, `caminoBusqueda` y `esABBValido`.
- **Extra:** `desdePreorden`, que reconstruye el ABB a partir de su preorden.

## Requisitos

- JDK 11 o superior
- Git y una terminal (o Visual Studio Code)

## Instrucciones de ejecución

Desde la carpeta raíz del proyecto:

```bash
# Compilar
javac -encoding UTF-8 -d out src/enums/*.java src/modelo/*.java src/negocio/*.java src/app/*.java

# Ejecutar el menú interactivo
java -cp out app.Main

# Ejecutar las pruebas
java -cp out app.PruebasBiblioteca
```

En Windows (PowerShell), si el comando de compilación falla por los comodines, usa:

```powershell
javac -encoding UTF-8 -d out (Get-ChildItem -Recurse src -Filter *.java).FullName
```

## Pruebas

`PruebasBiblioteca` ejecuta los casos obligatorios del deber y muestra al final `X/N pruebas OK`. Cubre la raíz sola, la estructura inicial, los niveles, la jerarquía inválida, los tres recorridos de SW-E1, el código repetido, el camino de búsqueda, el rango, las inserciones y eliminaciones, los códigos inexistentes, los datos inválidos y el ABB mal formado.

![Captura de PruebasBiblioteca](docs/capturas/pruebas.png)

## Documentación adicional

El archivo [TRAZAS.md](TRAZAS.md) contiene los ejercicios resueltos a mano: inserciones, recorridos, traza del preorden y eliminaciones, con los árboles en Mermaid.

## Autoría

[Escribe aquí cómo se hizo el proyecto. Por ejemplo: "El código Java se desarrolló en grupo; el README, el TRAZAS.md y el PDF de evidencias son trabajo individual."]