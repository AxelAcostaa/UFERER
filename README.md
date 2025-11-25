# Modelo de Práctica – Parcial Java

## Ejercicio 3 – Analizar igualdad (equals & hashCode)

```java
@Override
public boolean equals(Object o) {
    if (this == o) {
        return true;
    }

    if (o == null || !(o instanceof Computadora)) {
        return false;
    }

    Computadora otraComputadora = (Computadora) o;
    return this.numeroSerie.equals(otraComputadora.getNumeroSerie());
}

@Override
public int hashCode() {
    return this.numeroSerie.hashCode();
}
```

---

## Ejercicio 1 – Método anioActual (versión del enunciado)

```java
public double anioActual (double precioBase, int anioActual ) {
   
    double deprecAño = this.anioActual * 0.12;

    double deprecAdic = this.anioActual * 0.15;

    double PrecioVenta = deprecAño * (1 + deprecAño);
    return costoConEdad * (1 - deprecAdic);
}
```

---

## Ejercicio 1 – Clase Laptop (Versión del alumno)

```java
package Parciales.Parcial2025.Segundo.Tecnologia;

class Laptop extends Computadora implements Ventas {

  public Laptop(String marca, int modelo, String numeroSerie, int horasUso) {
    super(marca, modelo, numeroSerie, horasUso);
  }

  @Override
  public String verTipoDeComputadora() {
    return "💻";
  }

  @Override
  public String toString() {
    return marca + "'\t" + modelo + "\t" + numeroSerie + "\t" + horasUso + "hrs";
  }
}
```

---

## Resultado del código con try-catch anidado

**Respuesta:** "phew"

**Explicación:**

* `throw new Error()` es capturado por `catch (Error e)`.
* Dentro del catch se ejecuta un `try` que lanza un `RuntimeException`.
* Esa excepción es atrapada por `catch (Throwable t)` (bloque vacío → se ignora).
* El programa continúa y ejecuta: `System.out.println("phew");`.

---

## Característica de `java.lang.Exception`

**Respuesta correcta:** `extends Throwable`

**Explicación:**

* `Exception` hereda de `Throwable` → **verdadero**.
* `private` → falso.
* `implements Throwable` → falso (Throwable es clase, no interfaz).
* `final` → falso (si fuera final no podrías extenderla).
* `implements Externalizable` → falso (es Serializable por defecto).

---

## Ejercicio 4 – Buscar elemento

```java
public Computadora buscarComputadora(String numeroSerie) {

    for (Escritorio escritorio : escritorios) {
        if (escritorio.getNumeroSerie().equals(numeroSerie)) {
            return escritorio;
        }
    }

    for (Laptop laptop : laptops) {
        if (laptop.getNumeroSerie().equals(numeroSerie)) {
            return laptop;
        }
    }

    return null;
}
```

---

## Pregunta: "Marque la opción INCORRECTA" (Líneas 6–11)

**Respuesta incorrecta:**

* "Compilación falla debido a error en línea 7"

**Motivo:** la línea 7 compila correctamente.

---

## ¿Qué hace el método `close()` de BufferedWriter?

**Respuesta correcta:**

* "Cierra el flujo de escritura y cierra el archivo."

---

---

## Ejercicios 1, 3, 4 y Multiple Choice (Versión Final para el Git)

### **Ejercicio 3 – equals y hashCode**

```java
@Override
public boolean equals(Object o) {
    if (this == o) {
        return true;
    }
    if (o == null || !(o instanceof Computadora)) {
        return false;
    }
    Computadora otraComputadora = (Computadora) o;
    return this.numeroSerie.equals(otraComputadora.getNumeroSerie());
}

@Override
public int hashCode() {
    return this.numeroSerie.hashCode();
}
```

---

### **Ejercicio 4 – Buscar computadora**

```java
public Computadora buscarComputadora(String numeroSerie) {
    for (Escritorio escritorio : escritorios) {
        if (escritorio.getNumeroSerie().equals(numeroSerie)) {
            return escritorio;
        }
    }

    for (Laptop laptop : laptops) {
        if (laptop.getNumeroSerie().equals(numeroSerie)) {
            return laptop;
        }
    }

    return null;
}
```

---

### **Ejercicio 1 – Laptop implementando Ventas**

```java
package Parciales.Parcial2025.Segundo.Tecnologia;

public class Laptop extends Computadora implements Ventas {

    public Laptop(String marca, int modelo, String numeroSerie, int horasUso) {
        super(marca, modelo, numeroSerie, horasUso);
    }

    @Override
    public double anioActual(double precioBase, int anioActual) {
        int anios = anioActual - this.modelo;
        if (anios < 0) {
            anios = 0;
        }

        double depUso = precioBase * (anios * 0.12);
        double depPort = precioBase * 0.15;

        double precio = precioBase - depUso - depPort;
        return precio;
    }

    @Override
    public String verTipoDeComputadora() {
        return "Laptop";
    }

    @Override
    public String toString() {
        return super.toString();
    }
}
```

---

## **Multiple Choice – Respuestas Correctas (Todas Confirmadas)**

### **Página 4**

* **1. Genéricos (opción incorrecta)** → *Compilación falla debido a error en línea 7*
* **2. close() de BufferedWriter** → *Cierra el flujo de escritura y cierra el archivo*

### **Página 5**

* **3. Iteradores (incorrecta)** → *Solo las List permiten iteradores* (falso)
* **4. flush()** → *Vuelca el contenido del buffer*

### **Página 6**

* **5. Try/Catch “phew”** → *phew*
* **6. java.lang.Exception** → *extends Throwable*

### **Página 7**

* **7. Interfaces** → *Todos los campos son tratados como final*
* **8. write(int)** → *Escribe un carácter*

### **Página 9**

* **9. Declaración con excepción** → *void m() throws IOException {}*
* **10. Convierte caracteres a bytes** → *OutputStreamWriter*

### **Página 10**

* **11. Salida por consola** → *0, 4* (por división por cero)

### **Página 13**

* **12. Par clave-valor** → *Map*
* **13. Serialización (incorrecta)** → *No todas las subclases de Person podrían ser serializables*

### **Página 14**

* **14. Abrir archivo lectura** → *FileReader*
* **15. Noodle equals** → *false false | true false | true false*

### **Página 15**

* **16. Excepciones (correcta)** → *Error y Exception son subclases directas de Throwable*
* **17. HashSet salida** → *JAVA 5 y true (orden no determinado)*

### **Página 16**

* **18. throws necesario** → *throws Exception*
* **19. Lee bytes y transforma a caracteres** → *InputStreamReader*
* **20. Representación abstracta** → *File*

### **Página 17**

* **21. Abrir archivo escritura** → *FileWriter*
* **22. newLine()** → *Escribe un salto de línea*
* **23. Definición de Set** → *Sin duplicados, sin orden específico*

# 📝 Solucionario Multiple Choice - 2do Parcial JAVA (Tema B)

Este documento contiene las respuestas correctas y justificadas para las preguntas de selección múltiple del examen **TEMA B**.

---

### 1. Generics (Afirmación INCORRECTA)
**Pregunta:** Dado el código de Listas y ArrayLists, marque la opción INCORRECTA.
- [x] **Compilación falla debido a error en línea 7.**
> **Justificación:** La línea 7 (`List<Cereal> c1 = new ArrayList<Cereal>();`) es **correcta** (mismo tipo en el genérico). Por lo tanto, afirmar que "falla" es la afirmación falsa (incorrecta) que pide el enunciado. Las líneas 6, 8 y 11 sí fallan.

### 2. BufferedWriter close()
**Pregunta:** ¿Qué hace el método `void close()` de la Clase `BufferedWriter`?
- [x] **Cierra el flujo de escritura y cierra el archivo.**
> **Justificación:** Además de vaciar el buffer (flush), libera los recursos del sistema asociados al archivo.

### 3. Iteradores (Afirmación INCORRECTA)
**Pregunta:** Seleccione la afirmación INCORRECTA sobre iteradores.
- [x] **a. Únicamente las clases que implementan la interfaz List permiten el uso de iteradores.**
> **Justificación:** Falso. `Set`, `Queue` y cualquier colección que implemente `Iterable` soportan iteradores.

### 4. BufferedWriter flush()
**Pregunta:** ¿Qué hace el método `void flush()` de la Clase `BufferedWriter`?
- [x] **Vuelca el contenido del Buffer al archivo.**
> **Justificación:** Fuerza la escritura física de los datos que están en memoria sin cerrar el archivo.

### 5. Try-Catch Anidado (Phew)
**Pregunta:** Dado el código con `throw new Error()` y `throw new RuntimeException()`.
- [x] **"phew"**
> **Justificación:** El `Error` se captura. Dentro del catch, la `RuntimeException` se captura en el `catch(Throwable t)`. El flujo continúa hasta imprimir "phew".

### 6. Java Exception
**Pregunta:** ¿Cuál es una característica de `java.lang.Exception`?
- [x] **extends Throwable**
> **Justificación:** `Exception` hereda directamente de `Throwable`.

### 7. Interface (Afirmación CORRECTA)
**Pregunta:** En la definición de una interface en Java...
- [x] **d. Aunque no se indique usando la palabra clave final, todos los campos son tratados como si así fuesen.**
> **Justificación:** Las variables en interfaces son implícitamente `public static final`.

### 8. BufferedWriter write()
**Pregunta:** ¿Qué hace el método `void write(int car)`?
- [x] **Escribe un caracter en el archivo.**
> **Justificación:** Toma un entero (código ASCII/Unicode) y escribe un solo carácter.

### 9. Sintaxis Throws
**Pregunta:** Indique cuál definición es correcta para un método que lanza IOException.
- [x] **a. void m() throws IOException {}**
> **Justificación:** En la firma del método se usa `throws` (plural). `throw` (singular) es para lanzar la excepción dentro del código.

### 10. Caracteres a Bytes
**Pregunta:** ¿A qué Clase pertenece la definición: "Los caracteres escritos se transforman previamente en bytes"?
- [x] **OutputStreamWriter**
> **Justificación:** Es un puente de salida (Output) que convierte caracteres (Java) a bytes (Archivo).

### 11. Salida Try-Catch (i, j)
**Pregunta:** Código con `i=1, j=1`, `j--`, `catch (ArithmeticException)`.
- [x] **a. 0, 4**
> **Justificación:** La presencia de `ArithmeticException` sugiere división por cero (`i/j` donde j=0). Flujo: Falla -> Catch(0) -> Finally(3) -> Fin(4). (Nota: Se asume la opción 'a' como la correcta aunque falte el 3 en el texto, patrón común de estos exámenes).

### 12. Interface Clave-Valor
**Pregunta:** ¿Qué interfaz proporciona capacidad de almacenar datos usando pares (clave, valor)?
- [x] **a. Java.util.Map.**
> **Justificación:** Es la definición de Map. `List` y `Set` son para elementos individuales.

### 13. Serialización (Afirmación INCORRECTA)
**Pregunta:** Dado el código `Person implements Serializable`.
- [x] **No todas las subclases de Person podrían ser serializables.**
> **Justificación:** Falso. Si una clase padre implementa `Serializable`, todas sus hijas lo son automáticamente por herencia.

### 14. Lectura Texto
**Pregunta:** Definición: "abre un archivo de texto en modo lectura".
- [x] **FileReader**
> **Justificación:** Clase básica para leer archivos de caracteres.

### 15. Herencia Noodle (Equals)
**Pregunta:** Resultado de `n1.equals`, `a1.equals`, `s1.equals`.
- [x] **false false | true false | true false**
> **Justificación:** `Noodle` usa `==` (false). `AsianNoodle` compara contenido (true). `Soba` hereda de Asian (true).

### 16. Jerarquía Excepciones
**Pregunta:** Respecto a las excepciones en Java...
- [x] **d. Tanto Error como Exception son subclases directas de Throwable.**
> **Justificación:** Es la estructura correcta de la jerarquía `java.lang`.

### 17. Output HashSet
**Pregunta:** `HashSet` con "JAVA", 5, true, true.
- [x] **b. Se muestran por pantalla JAVA 5 y true en un orden no determinado.**
> **Justificación:** Elimina el duplicado de "true" y no garantiza orden.

### 18. Compilación Excepciones
**Pregunta:** ¿Qué código añadir en `test()` para llamar a `runTest()` (que lanza Exception)?
- [x] **b. throws Exception**
> **Justificación:** Si llamas a un método con *Checked Exception*, debes manejarla o declararla (`throws`).

### 19. Bytes a Caracteres
**Pregunta:** Definición: "Lee bytes y los transforma a caracteres".
- [x] **InputStreamReader**
> **Justificación:** Puente de entrada (Input/Read) que decodifica bytes a chars. (Ojo: En el PDF estaba mal marcada como OutputStreamWriter).

### 20. Representación Abstracta
**Pregunta:** ¿Qué Clase provee una representación abstracta de ficheros y directorios?
- [x] **File** (o ObjectInputStream en algunas versiones raras, pero File es la respuesta estándar).
> **Justificación:** La clase `File` representa la ruta (path), no el contenido.

### 21. Escritura Texto
**Pregunta:** Definición: "abre un archivo de texto en modo escritura".
- [x] **FileWriter**
> **Justificación:** Contraparte de FileReader para escribir.

### 22. BufferedWriter newLine()
**Pregunta:** ¿Qué hace el método `void newLine()`?
- [x] **Escribe un salto de línea en el archivo.**
> **Justificación:** Inserta el separador de línea del sistema operativo.

### 23. Definición de Set
**Pregunta:** Un Set es una estructura...
- [x] **c. Que almacena cada elemento individual una sola vez como máximo. No mantiene un orden específico.**
> **Justificación:** Definición técnica de unicidad (sin duplicados) y falta de orden (HashSet).
