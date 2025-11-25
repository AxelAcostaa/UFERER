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

EJERCICIO 3 @Override public boolean equals(Object o) { if (this == o) { return true; } if (o == null || !(o instanciade Computadora)) { return false; } Computadora otraComputadora = (Computadora) o; return this.numeroSerie.equals(otraComputadora.getNumeroSerie()); } @Override public int hashCode() { return this.numeroSerie.hashCode(); }
EJERCICIO 4 public Computadora buscarComputadora(String numeroSerie) { for (Escritorio escritorio : escritorios) { if (escritorio.getNumeroSerie().equals(numeroSerie)) { return escritorio; } } para (Laptop laptop : laptops) { if (laptop.getNumeroSerie().equals(numeroSerie)) { return laptop; } } devolver nulo; } 
EJERCICIO 1 paquete Parciales.Parcial2025.Segundo.Tecnologia; public class Laptop extiende Computadora implementa Ventas { public Laptop(String marca, int modelo, String numeroSerie, int horasUso) { super(marca, modelo, numeroSerie, horasUso); } @Override public double anioActual(double precioBase, int anioActual) { int anios = anioActual - this.modelo; if (anios < 0) { anios = 0; } double depUso = precioBase * (anios * 0.12); double depPort = precioBase * 0.15; double precio = precioBase - depUso - depPort; return precio; } @Override public String verTipoDeComputadora() { return "Laptop"; } @Override public String toString() { return super.toString(); } } 
OPCIÓN MÚLTIPLE ¡Dale! Vamos a barrer todas las preguntas de opción múltiple. OJO IMPORTANTE: He notado que en las capturas del PDF hay varias respuestas marcadas (los "checkmarks" azules) que están MAL. El alumno que sacó las capturas se equivocó en varias. No te fíes de los tildes azules de las fotos. Aquí tienes las correctas, analizadas con lupa para que no caigas en las trampas. Página 4 Código de Cereales y Flakes (Genéricos) Pregunta: Marque la opción INCORRECTA (sobre dónde falla la compilación). Análisis: Línea 6: nueva Lista<...> -> Falla (List es interface, no se instancia). Línea 7: Lista c1 = new ArrayList(); -> Correcto (Tipos coinciden). Línea 8: Lista c2 = new ArrayList(); -> Falla (Genéricos no son covariantes, deben ser idénticos). Línea 11: Falla (mismo error que la 8). La Trampa: La pregunta dice "marque la opción INCORRECTA". La afirmación "Falla en línea 6" es VERDADERA. La afirmación "Falla en línea 7" es FALSA (porque la línea 7 sí funciona). Respuesta Correcta: ☐ Compilación falla debido a error en línea 7. (Esta es la afirmación falsa). Nota: Si la pregunta fuera "¿Dónde está el error?", serán las 6, 8, 9, 10 y 11. Pero como pide la "incorrecta", buscamos la mentira. Método close() de BufferedWriter Respuesta Correcta: ☑ Cierra el flujo de escritura y cierra el archivo. Por qué: El check en la foto marca "Vuelca el contenido...", eso es lo que hace flush(). close() hace color y además cierra. La opción completa es la correcta. Página 5 3. Iteradores (Afirmación INCORRECTA) Respuesta correcta: ☑ a. Únicamente las clases que implementan la interfaz List permiten el uso de iteradores. Por qué: Esto es falso (y por tanto la respuesta correcta). Los Set, Queue y cualquier Collection tienen iteradores, no solo las Listas. Método de descarga() de BufferedWriter Respuesta Correcta: ☑ Vuelca el contenido del Buffer al archivo. Por qué: fluya fuerza la escritura física de lo que hay en memoria sin cerrar el archivo. (En la foto marcaron "Cierra...", eso está mal). Página 6 5. Try-Catch anidado ("uf") Respuesta Correcta: ☑ "uf" Análisis: Lanza Error (línea 5). Atrapa Error (línea 7). Dentro del catch, lanza RuntimeException (línea 8). Esa excepción cae inmediatamente en el catch(Throwable t) interno (línea 9). El flujo sigue y llega al System.out.println("phew"). Característica de java.lang.Exception Respuesta Correcta: ☑ extiende Throwable Por qué: Excepción aquída de Throwable. No es privado ni final. Página 7 7. Definición de interfaz (correcta) Respuesta correcta: ☑ d. Aunque no se indica usando la palabra clave final, todos los campos son tratados como si así fuesen. Por qué: En una interfaz, todas las variables son implícitamente públicas estáticas finales. Método write(int car) Respuesta Correcta: ☑ Escribe un carácter en el archivo. Por qué: Escribe el valor ASCII/Unicode de un solo carácter. Página 9 9. Definición de método con excepción Respuesta correcta: ☑ a. void m() throws IOException {} Por qué: La palabra clave en la firma del método es throws (plural), no throw (singular, que se usa dentro del código). Clase "Transforma caracteres a bytes" Respuesta correcta: ☑ OutputStreamWriter Por qué: Estás escribiendo (Salida). Tomas caracteres (de tu programa) y los conviertes a bytes (para el archivo). Ojo: InputStreamReader hace lo contrario (bytes a caracteres). Página 10 11. Salida por consola (Try-Catch i, j) Código: i=1, j=1. Luego i++ (2), j-- (0). El dilema visual: La imagen está borrosa en el if. Si dice if (i/j > 1): Divide por cero (2/0) -> ArithmeticException. Imprime 0 (atrapar), luego 3 (finalmente), luego , 4. Salida: 0, 4. Si dice if (i==j): 2 == 0 es falso. No entra, no falla. Imprime 3 (finalmente), luego , 4. Salida: 3, 4. Respuesta experta: Dado que hay un catch(ArithmeticException) explícito en el código, el ejercicio está diseñado para que falle. Respuesta recomendada: a. 0, 4 (Asumiendo que hay división por cero). Si la opción A dice "0, 4" y la D dice "3, 4", marca la A. Es la típica trampa de "El finalmente se ejecuta siempre, pero la excepción se imprime antes". Página 13 12. Interfaz par (clave, valor) Respuesta correcta: ☑ a. Java.util.Mapa. Serialización (Afirmación INCORRECTA) Respuesta Correcta: ☑ No todas las subclases de Person podrían ser serializables. Por qué: Esta afirmación es falsa (y por ende la que hay que marcar). En Java, si el padre implementa Serializable, los hijos lo son obligatoriamente. No se puede "quitar" la serialización. Nota: La opción "No se produce error de compilación" es VERDADERA (el código compila, falla al ejecutar), así que no deberías marcarla si buscas la incorrecta. Página 14 14. Abre archivo modo lectura Respuesta correcta: ☑ FileReader Fideos Herencia (Iguales) Respuesta Correcta: ☑ falso falso | verdadero falso | verdadero falso (La tercera opción en la lista). Análisis: Noodle (Padre): No tiene iguales, compara memoria -> false. AsianNoodle (Hijo): Tiene igual por nombre -> true. Soba (Nieto): Hereda el es igual al hijo -> verdadero. Los == siempre dan false porque son objetos distintos. Página 15 16. Excepciones (Afirmación CORRECTA) Respuesta correcta: ☑ d. Tanto Error como Exception son subclases directas de Throwable. Por qué: Es la jerarquía base de Java. HashSet (Salida) Respuesta correcta: ☑ b. Se muestra por pantalla JAVA 5 y true en un orden no determinado. Por qué: Set elimina duplicados (solo un "true") y HashSet no garantiza el orden. Página 16 18. Código añadir para compilar Respuesta correcta: ☑ b. lanza una excepción Por qué: El método runTest() lanza una excepción marcada. Quien lo llame (test()) debe capturarla o declararla (tira). Clase "Lee bytes y transforma a caracteres" Respuesta correcta: ☐ InputStreamReader Atención: En la foto del PDF marcaron "OutputStreamWriter". ESTA MAL. Input = Leer. Reader = Transformar a caracteres. Es InputStreamReader. Representación abstracta de ficheros Respuesta Correcta: ☑ Archivo (o java.io.File). Página 17 21. Abre archivo modo escritura Respuesta correcta: ☑ FileWriter newLine() de BufferedWriter Respuesta Correcta: ☑ Escribe un salto de línea en el archivo. Definición de conjunto (Opción CORRECTA) Respuesta Correcta: ☑ c. Que almacena cada elemento individual una sola vez como máximo. No mantiene un orden específico. Por qué: "Una sola vez como máximo" = Sin duplicados (0 o 1 vez). "No mantiene el orden" = Definición estándar de la interfaz Set (particularmente HashSet). La opción que dice "Mantiene un orden específico" solo se aplica a TreeSet o LinkedHashSet, no al Set genérico. TODO esto esta bien?? armalo asi para mi git si es todo correcto

