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

---

