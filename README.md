EJERCICIO 3 
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

EJERCICIO 4 
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
EJERCICIO 1
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

MULTIPLECHOICE 
¡Dale! Vamos a barrer todas las preguntas del multiple choice.

OJO IMPORTANTE: He notado que en las capturas del PDF hay varias respuestas marcadas (los "checkmarks" azules) que están MAL. El alumno que sacó las capturas se equivocó en varias. No te fíes de los tildes azules de las fotos.

Aquí tienes las correctas, analizadas con lupa para que no caigas en las trampas.

Página 4
1. Código de Cereales y Flakes (Genéricos)

Pregunta: Marque la opción INCORRECTA (sobre dónde falla la compilación).

Análisis:

Línea 6: new List<...> -> Falla (List es interface, no se instancia).

Línea 7: List<Cereal> c1 = new ArrayList<Cereal>(); -> Correcto (Tipos coinciden).

Línea 8: List<Cereal> c2 = new ArrayList<Flakes>(); -> Falla (Genéricos no son covariantes, deben ser idénticos).

Línea 11: Falla (mismo error que la 8).

La Trampa: La pregunta dice "marque la opción INCORRECTA".

La afirmación "Falla en línea 6" es VERDADERA.

La afirmación "Falla en línea 7" es FALSA (porque la línea 7 sí funciona).

Respuesta Correcta: ☐ Compilación falla debido a error en línea 7. (Esta es la afirmación falsa).

Nota: Si la pregunta fuera "¿Dónde está el error?", serían la 6, 8, 9, 10 y 11. Pero como pide la "incorrecta", buscamos la mentira.

2. Método close() de BufferedWriter

Respuesta Correcta: ☑ Cierra el flujo de escritura y cierra el archivo.

Por qué: El check en la foto marca "Vuelca el contenido...", eso es lo que hace flush(). close() hace flush y además cierra. La opción completa es la correcta.

Página 5
3. Iteradores (Afirmación INCORRECTA)

Respuesta Correcta: ☑ a. Únicamente las clases que implementan la interfaz List permiten el uso de iteradores.

Por qué: Esto es falso (y por tanto la respuesta correcta). Los Set, Queue y cualquier Collection tienen iteradores, no solo las Listas.

4. Método flush() de BufferedWriter

Respuesta Correcta: ☑ Vuelca el contenido del Buffer al archivo.

Por qué: flush fuerza la escritura física de lo que hay en memoria sin cerrar el archivo. (En la foto marcaron "Cierra...", eso está mal).

Página 6
5. Try-Catch anidado ("phew")

Respuesta Correcta: ☑ "phew"

Análisis:

Lanza Error (línea 5).

Atrapa Error (línea 7).

Dentro del catch, lanza RuntimeException (línea 8).

Esa excepción cae inmediatamente en el catch(Throwable t) interno (línea 9).

El flujo sigue y llega al System.out.println("phew").

6. Característica de java.lang.Exception

Respuesta Correcta: ☑ extends Throwable

Por qué: Exception hereda de Throwable. No es private ni final.

Página 7
7. Definición de Interface (Correcta)

Respuesta Correcta: ☑ d. Aunque no se indique usando la palabra clave final, todos los campos son tratados como si así fuesen.

Por qué: En una interfaz, todas las variables son implícitamente public static final.

8. Método write(int car)

Respuesta Correcta: ☑ Escribe un caracter en el archivo.

Por qué: Escribe el valor ASCII/Unicode de un solo carácter.

Página 9
9. Definición de método con Exception

Respuesta Correcta: ☑ a. void m() throws IOException {}

Por qué: La palabra clave en la firma del método es throws (plural), no throw (singular, que se usa dentro del código).

10. Clase "Transforma caracteres a bytes"

Respuesta Correcta: ☑ OutputStreamWriter

Por qué: Estás escribiendo (Output). Tomas caracteres (de tu programa) y los conviertes a bytes (para el archivo).

Ojo: InputStreamReader hace lo contrario (bytes a caracteres).

Página 10
11. Salida por consola (Try-Catch i, j)

Código: i=1, j=1. Luego i++ (2), j-- (0).

El dilema visual: La imagen está borrosa en el if.

Si dice if (i/j > 1): Divide por cero (2/0) -> ArithmeticException. Imprime 0 (catch), luego 3 (finally), luego , 4. Salida: 0, 4.

Si dice if (i==j): 2 == 0 es falso. No entra, no falla. Imprime 3 (finally), luego , 4. Salida: 3, 4.

Respuesta experta: Dado que hay un catch(ArithmeticException) explícito en el código, el ejercicio está diseñado para que falle.

Respuesta Recomendada: a. 0, 4 (Asumiendo que hay división por cero). Si la opción A dice "0, 4" y la D dice "3, 4", marca la A. Es la típica trampa de "El finally se ejecuta siempre, pero la excepción se imprime antes".

Página 13
12. Interfaz par (clave, valor)

Respuesta Correcta: ☑ a. Java.util.Map.

13. Serialización (Afirmación INCORRECTA)

Respuesta Correcta: ☑ No todas las subclases de Person podrían ser serializables.

Por qué: Esta afirmación es falsa (y por ende la que hay que marcar). En Java, si el padre implementa Serializable, los hijos lo son obligatoriamente. No se puede "quitar" la serialización.

Nota: La opción "No se produce error de compilación" es VERDADERA (el código compila, falla al ejecutar), así que no deberías marcarla si buscas la incorrecta.

Página 14
14. Abre archivo modo lectura

Respuesta Correcta: ☑ FileReader

15. Herencia Noodle (Equals)

Respuesta Correcta: ☑ false false | true false | true false (La tercera opción en la lista).

Análisis:

Noodle (Padre): No tiene equals, compara memoria -> false.

AsianNoodle (Hijo): Tiene equals por nombre -> true.

Soba (Nieto): Hereda el equals del hijo -> true.

Los == siempre dan false porque son objetos distintos.

Página 15
16. Excepciones (Afirmación CORRECTA)

Respuesta Correcta: ☑ d. Tanto Error como Exception son subclases directas de Throwable.

Por qué: Es la jerarquía base de Java.

17. HashSet (Salida)

Respuesta Correcta: ☑ b. Se muestran por pantalla JAVA 5 y true en un orden no determinado.

Por qué: Set elimina duplicados (solo un "true") y HashSet no garantiza orden.

Página 16
18. Código añadir para compilar

Respuesta Correcta: ☑ b. throws Exception

Por qué: El método runTest() lanza una excepción chequeada. Quien lo llame (test()) debe capturarla o declararla (throws).

19. Clase "Lee bytes y transforma a caracteres"

Respuesta Correcta: ☐ InputStreamReader

Atención: En la foto del PDF marcaron "OutputStreamWriter". ESTÁ MAL.

Input = Leer. Reader = Transformar a caracteres. Es InputStreamReader.

20. Representación abstracta de ficheros

Respuesta Correcta: ☑ File (o java.io.File).

Página 17
21. Abre archivo modo escritura

Respuesta Correcta: ☑ FileWriter

22. newLine() de BufferedWriter

Respuesta Correcta: ☑ Escribe un salto de línea en el archivo.

23. Definición de Set (Opción CORRECTA)

Respuesta Correcta: ☑ c. Que almacena cada elemento individual una sola vez como máximo. No mantiene un orden específico.

Por qué:

"Una sola vez como máximo" = Sin duplicados (0 o 1 vez).

"No mantiene orden" = Definición estándar de la interfaz Set (particularmente HashSet).

La opción que dice "Mantiene un orden específico" solo aplica a TreeSet o LinkedHashSet, no al Set genérico.


