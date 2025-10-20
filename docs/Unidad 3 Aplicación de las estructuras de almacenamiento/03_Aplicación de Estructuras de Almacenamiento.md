# Programación - 03 Aplicación de Estructuras de Almacenamiento

**Tema 03 Aplicación de Estructuras de Almacenamiento. 1DAM. Curso 2025/2026.**

------

## 1. Arrays unidimensionales

### 🔍 Definición

Un array es una estructura de datos que permite almacenar un conjunto de datos contiguos del mismo tipo. Se caracterizan por tener un tamaño fijo, es decir, una vez definido el array no se puede modificar su tamaño y que su acceso de lectura y escritura se realiza mediante un índice.

Si una variable es como un cajón de un tamaño del tipo de dato (es decir, el identificador apunta a la zona de memoria donde se almacena el valor), un array puede verse como un conjunto de cajones (una cajonera) del mismo tamaño del tipo de dato, donde cada cajón tiene un índice que nos permite acceder a él. Por tanto, un array es una estructura de datos que nos permite almacenar un conjunto de datos del mismo tipo.

En Kotlin y Java, el primer índice es el 0. Esto se debe a la forma de redireccionar de memoria que han ido heredando los lenguajes y compiladores (como en C), el primer elemento de un array se almacena en la posición 0. Por tanto, si tenemos un array de 10 elementos, el último elemento se almacena en la posición 9. Si nos salimos del límite obtendremos una excepción (tanto si consultamos como índice un número negativo, como si consultamos un índice mayor o igual al tamaño del array). Esta excepción es `ArrayIndexOutOfBoundsException`.

| Value | 7    | 11   | 6    | 55   | 98   | 45   | 16   | 96   | 46   |
| :---- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Index | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |

**Lower Bound = 0**
**Array Length = 9**

### 📝 Definición de arrays

=== "Kotlin"

    ```kotlin
    // Array de 10 enteros
    var arrayEnteros = IntArray(10) // valor inicial 0
    var arrayEnteros = intArrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
    var arrayEnteros = IntArray(10) { 0 } // array de 10 enteros inicializados a 0
    var arrayCaracteres = CharArray(10)
    var arrayBooleanos = BooleanArray(10)

    // Otros tipos de arrays
    var arrayCadenas = arrayOf("Hola", "mundo")
    var arrayEnteros = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
    // Usando Array<Tipo>
    var arrayEnteros = Array<Int>(10) { 0 }
    var arrayCadenas = Array<String>(10) { "" }
    ```
=== "Java"
    ```java
    // Array de 10 enteros
    int[] arrayEnteros = new int[10]; // valor inicial 0
    int[] arrayEnteros = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int[] arrayEnteros = new int[10]; // todos inicializados a 0
    char[] arrayCaracteres = new char[10];
    boolean[] arrayBooleanos = new boolean[10];

    // Arrays de objetos
    String[] arrayCadenas = {"Hola", "mundo"};
    String[] arrayCadenas = new String[10]; // inicializados a null
    ```

=== "Python"
    ```python
    # Lista en Python (equivalente a array)
    array_enteros = [0] * 10  # lista de 10 ceros
    array_enteros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    array_cadenas = ["Hola", "mundo"]

    # Usando array module para arrays tipados
    import array
    array_enteros = array.array('i', [1, 2, 3, 4, 5])
    ```




### 🔄 Recorrido

Para recorrer un array y trabajar con él, el índice será clave. Para ello, podemos utilizar un bucle for o for-each o while, que nos permitirá recorrer el array de principio a fin.

=== "Kotlin"

    ```kotlin
    fun main() {
        val array = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

        // Recorrido con for indices
        for (i in array.indices) {
            println(array[i])
        }

        // Con reversed con indices
        for (i in array.indices.reversed()) {
            println(array[i])
        }

        // Con for each
        for (i in array) {
            println(i)
        }

        // Saltando posiciones
        for (i in array.indices step 2) {
            println(array[i])
        }

        // Con while
        var i = 0
        while (i < array.size) {
            println(array[i])
            i++
        }

        // With index, para obtener el índice y el valor
        for ((index, value) in array.withIndex()) {
            println("El elemento $value está en la posición $index")
        }
    }
    ```




=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

            // Recorrido con for tradicional
            for (int i = 0; i < array.length; i++) {
                System.out.println(array[i]);
            }

            // Recorrido inverso
            for (int i = array.length - 1; i >= 0; i--) {
                System.out.println(array[i]);
            }

            // For-each
            for (int elemento : array) {
                System.out.println(elemento);
            }

            // Saltando posiciones
            for (int i = 0; i < array.length; i += 2) {
                System.out.println(array[i]);
            }

            // Con while
            int i = 0;
            while (i < array.length) {
                System.out.println(array[i]);
                i++;
            }
        }
    }
    ```




=== "Python"


    ```python
    def main():
        array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

        # Recorrido con for tradicional
        for i in range(len(array)):
            print(array[i])

        # Recorrido inverso
        for i in range(len(array)-1, -1, -1):
            print(array[i])

        # For-each
        for elemento in array:
            print(elemento)

        # Saltando posiciones
        for i in range(0, len(array), 2):
            print(array[i])

        # Con while
        i = 0
        while i < len(array):
            print(array[i])
            i += 1

        # Con enumerate (índice y valor)
        for indice, valor in enumerate(array):
            print(f"El elemento {valor} está en la posición {indice}")

    if __name__ == "__main__":
        main()
    ```




### 📤 Paso por referencia

Los arrays siempre pasan por referencia en las funciones, esto quiere decir, que si modificamos un array en una función, este cambio será visible después de ejecutar la función.

=== "Kotlin"


    ```kotlin
    fun main() {
        val array = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
        println("Array original: ${array.contentToString()}")
        // Modificamos el array
        modificarArray(array)
        println("Array modificado: ${array.contentToString()}")
    }

    fun modificarArray(array: IntArray) {
        array[0] = 100
        array[1] = 200
        array[2] = 300
    }
    ```

=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
            System.out.println("Array original: " + java.util.Arrays.toString(array));
            // Modificamos el array
            modificarArray(array);
            System.out.println("Array modificado: " + java.util.Arrays.toString(array));
        }

        public static void modificarArray(int[] array) {
            array[0] = 100;
            array[1] = 200;
            array[2] = 300;
        }
    }
    ```

=== "Python"


    ```python
    def modificar_array(array):
        array[0] = 100
        array[1] = 200
        array[2] = 300

    def main():
        array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        print(f"Array original: {array}")
        # Modificamos el array
        modificar_array(array)
        print(f"Array modificado: {array}")

    if __name__ == "__main__":
        main()
    ```




### 🔙 Devolución de arrays

Para devolver un array, podemos utilizar la palabra reservada return, pero en este caso, no devolveremos el array, sino que devolveremos la referencia a la posición de memoria donde se encuentra el array.

=== "Kotlin"


    ```kotlin
    fun main() {
        val array = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
        println("Array original: ${array.contentToString()}")
        // Modificamos el array
        val array2 = modificarArray(array)
        println("Array modified: ${array.contentToString()}")
        println("Array2 modified: ${array2.contentToString()}")
    }

    fun modificarArray(array: IntArray): IntArray {
        array[0] = 100
        array[1] = 200
        array[2] = 300
        return array
    }
    ```

=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
            System.out.println("Array original: " + java.util.Arrays.toString(array));
            // Modificamos el array
            int[] array2 = modificarArray(array);
            System.out.println("Array modified: " + java.util.Arrays.toString(array));
            System.out.println("Array2 modified: " + java.util.Arrays.toString(array2));
        }

        public static int[] modificarArray(int[] array) {
            array[0] = 100;
            array[1] = 200;
            array[2] = 300;
            return array;
        }
    }
    ```

=== "Python"


    ```python
    def modificar_array(array):
        array[0] = 100
        array[1] = 200
        array[2] = 300
        return array

    def main():
        array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        print(f"Array original: {array}")
        # Modificamos el array
        array2 = modificar_array(array)
        print(f"Array modified: {array}")
        print(f"Array2 modified: {array2}")

    if __name__ == "__main__":
        main()
    ```




### ⚖️ Identidad vs Igualdad

Uno de los problemas fundamentales en la programación es la identidad y la igualdad.

- Se dice que dos objetos son **idénticos** si apuntan a la misma posición de memoria, es decir, si son el mismo objeto.
- Se dice que dos objetos son **iguales** si tienen el mismo contenido, es decir, si tienen el mismo valor.

=== "Kotlin"


    ```kotlin
    fun main() {
        val arrayA = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
        val arrayB = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

        println("Array A: ${arrayA.contentToString()}")
        println("Array B: ${arrayB.contentToString()}")
        
        // Igualdad
        println("Son iguales: ${igualdad(arrayA, arrayB)}")
        // ==
        println("Son iguales: ${arrayA == arrayB}")
        // contentEquals
        println("Son iguales: ${arrayA.contentEquals(arrayB)}")
        // Identidad
        println("Son idénticos: ${arrayA === arrayB}")
    }

    fun igualdad(origin: IntArray, destino: IntArray): Boolean {
        // Early exit
        if (origin.size != destino.size) {
            return false
        }
        for (i in origin.indices) {
            if (origin[i] != destino[i]) {
                return false
            }
        }
        return true
    }
    ```




=== "Java"


    ```java
    import java.util.Arrays;

    public class Main {
        public static void main(String[] args) {
            int[] arrayA = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
            int[] arrayB = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

            System.out.println("Array A: " + Arrays.toString(arrayA));
            System.out.println("Array B: " + Arrays.toString(arrayB));
            
            // Igualdad
            System.out.println("Son iguales: " + igualdad(arrayA, arrayB));
            // Arrays.equals
            System.out.println("Son iguales: " + Arrays.equals(arrayA, arrayB));
            // Identidad
            System.out.println("Son idénticos: " + (arrayA == arrayB));
        }

        public static boolean igualdad(int[] origin, int[] destino) {
            // Early exit
            if (origin.length != destino.length) {
                return false;
            }
            for (int i = 0; i < origin.length; i++) {
                if (origin[i] != destino[i]) {
                    return false;
                }
            }
            return true;
        }
    }
    ```




=== "Python"


    ```python
    def igualdad(origin, destino):
        # Early exit
        if len(origin) != len(destino):
            return False
        for i in range(len(origin)):
            if origin[i] != destino[i]:
                return False
        return True

    def main():
        arrayA = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        arrayB = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

        print(f"Array A: {arrayA}")
        print(f"Array B: {arrayB}")
        
        # Igualdad
        print(f"Son iguales: {igualdad(arrayA, arrayB)}")
        # ==
        print(f"Son iguales: {arrayA == arrayB}")
        # Identidad
        print(f"Son idénticos: {arrayA is arrayB}")

    if __name__ == "__main__":
        main()
    ```




### 📋 Métodos y propiedades

Algunos métodos interesantes para trabajar con arrays:

=== "Kotlin"


    ```kotlin
    val numeros = arrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

    // tamaño
    println("Tamaño: ${numeros.size}")
    // primer elemento
    println("Primer elemento: ${numeros.first()}")
    // último elemento
    println("Último elemento: ${numeros.last()}")
    // a string
    println("Array a string: ${numeros.contentToString()}")
    // a string con separador
    println("Array a string con separador: ${numeros.joinToString(" - ")}")
    // saber si existe en qué índice esta
    println("Índice del elemento 5: ${numeros.indexOf(5)}")
    // Subarray
    println("Subarray: ${numeros.sliceArray(0..4).contentToString()}")
    ```




=== "Java"


    ```java
    import java.util.Arrays;

    public class Main {
        public static void main(String[] args) {
            int[] numeros = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
            
            // tamaño
            System.out.println("Tamaño: " + numeros.length);
            // primer elemento
            System.out.println("Primer elemento: " + numeros[0]);
            // último elemento
            System.out.println("Último elemento: " + numeros[numeros.length - 1]);
            // a string
            System.out.println("Array a string: " + Arrays.toString(numeros));
            // saber si existe en qué índice esta
            int index = -1;
            for (int i = 0; i < numeros.length; i++) {
                if (numeros[i] == 5) {
                    index = i;
                    break;
                }
            }
            System.out.println("Índice del elemento 5: " + index);
            // Subarray
            int[] subarray = Arrays.copyOfRange(numeros, 0, 5);
            System.out.println("Subarray: " + Arrays.toString(subarray));
        }
    }
    ```




=== "Python"


    ```python
    def main():
        numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        
        # tamaño
        print(f"Tamaño: {len(numeros)}")
        # primer elemento
        print(f"Primer elemento: {numeros[0]}")
        # último elemento
        print(f"Último elemento: {numeros[-1]}")
        # a string
        print(f"Array a string: {numeros}")
        # a string con separador
        print(f"Array a string con separador: {' - '.join(map(str, numeros))}")
        # saber si existe en qué índice esta
        try:
            index = numeros.index(5)
            print(f"Índice del elemento 5: {index}")
        except ValueError:
            print("Elemento no encontrado")
        # Subarray
        subarray = numeros[0:5]
        print(f"Subarray: {subarray}")

    if __name__ == "__main__":
        main()
    ```




------

## 2. Arrays multidimensionales

Los arrays multidimensionales son arrays que contienen otros arrays, por ejemplo, un array de dos dimensiones es un array donde cada elemento es un array. Es decir, es un array de arrays. Para recorrerlo usaremos tanto índices como dimensiones tenga.

### 📊 Estructura

```
Columns
Column 1   Column 2   Column 3

Row 1      111        112        113        Array 1    Arrays 6
Row 2      121        211        212        213        Array 2
Row 3      131        221        311        312        313        Array 3
                    231        321        322        323
                    331        332        333
```



### 📝 Definición

=== "Kotlin"


    ```kotlin
    val array = arrayOf(
        arrayOf(1, 2, 3), 
        arrayOf(4, 5, 6), 
        arrayOf(7, 8, 9)
    )
    val array2 = arrayOfNulls<Array<Int>>(3)
    val array3 = Array(3) { IntArray(3) } // array de 3x3
    ```




=== "Java"


    ```java
    int[][] array = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    int[][] array2 = new int[3][3]; // array de 3x3
    Integer[][] array3 = new Integer[3][3]; // con nulls
    ```




=== "Python"


    ```python
    # Lista de listas
    array = [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ]

    # Crear array 3x3 con ceros
    array2 = [[0] * 3 for _ in range(3)]
    ```




### 🔄 Recorrido

Necesitaremos tantos índices como dimensiones, y por lo tanto tantos bucles definidos como dimensiones.

=== "Kotlin"


    ```kotlin
    fun main() {
        val array = arrayOf(
            arrayOf(1, 2, 3),
            arrayOf(4, 5, 6), 
            arrayOf(7, 8, 9)
        )
        
        // Usando índices
        for (i in array.indices) {
            for (j in array[i].indices) {
                println("array[$i][$j] = ${array[i][j]}")
            }
        }
        
        // Con while
        var i = 0
        while (i < array.size) {
            var j = 0
            while (j < array[i].size) {
                println("array[$i][$j] = ${array[i][j]}")
                j++
            }
            i++
        }
        
        // Con for each
        for (fila in array) {
            for (elemento in fila) {
                println("element = $elemento")
            }
        }
    }
    ```




=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            int[][] array = {
                {1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}
            };
            
            // Usando índices
            for (int i = 0; i < array.length; i++) {
                for (int j = 0; j < array[i].length; j++) {
                    System.out.println("array[" + i + "][" + j + "] = " + array[i][j]);
                }
            }
            
            // Con while
            int i = 0;
            while (i < array.length) {
                int j = 0;
                while (j < array[i].length) {
                    System.out.println("array[" + i + "][" + j + "] = " + array[i][j]);
                    j++;
                }
                i++;
            }
            
            // Con for-each
            for (int[] fila : array) {
                for (int elemento : fila) {
                    System.out.println("element = " + elemento);
                }
            }
        }
    }
    ```




=== "Python"


    ```python
    def main():
        array = [
            [1, 2, 3],
            [4, 5, 6],
            [7, 8, 9]
        ]
        
        # Usando índices
        for i in range(len(array)):
            for j in range(len(array[i])):
                print(f"array[{i}][{j}] = {array[i][j]}")
        
        # Con while
        i = 0
        while i < len(array):
            j = 0
            while j < len(array[i]):
                print(f"array[{i}][{j}] = {array[i][j]}")
                j += 1
            i += 1
        
        # Con for-each
        for fila in array:
            for elemento in fila:
                print(f"element = {elemento}")

    if __name__ == "__main__":
        main()
    ```




------

## 3. Cadenas de caracteres (Strings)

Una cadena es una secuencia de caracteres, es decir, una cadena es un array de caracteres. En Kotlin y Java, las cadenas son inmutables, es decir, no podemos modificar una cadena, si queremos modificar una cadena, tendremos que crear una nueva cadena.

### 📝 Definición

=== "Kotlin"


    ```kotlin
    val cadena = "Hola mundo"
    val cadenaVacia = ""
    val cadenaNula: String? = null
    ```




=== "Java"


    ```java
    String cadena = "Hola mundo";
    String cadenaVacia = "";
    String cadenaNula = null;
    ```




=== "Python"


    ```python
    cadena = "Hola mundo"
    cadena_vacia = ""
    cadena_nula = None
    ```




### 🔄 Recorrido

=== "Kotlin"


    ```kotlin
    fun main() {
        val cadena = "Hola mundo"
        
        for (caracter in cadena) {
            println("caracter = $caracter")
        }
        
        // Con indices
        for (i in cadena.indices) {
            println("cadena[$i] = ${cadena[i]}")
        }
    }
    ```




=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            String cadena = "Hola mundo";
            
            // Con for-each (convertir a char array)
            for (char caracter : cadena.toCharArray()) {
                System.out.println("caracter = " + caracter);
            }
            
            // Con indices
            for (int i = 0; i < cadena.length(); i++) {
                System.out.println("cadena[" + i + "] = " + cadena.charAt(i));
            }
        }
    }
    ```




=== "Python"


    ```python
    def main():
        cadena = "Hola mundo"
        
        for caracter in cadena:
            print(f"caracter = {caracter}")
        
        # Con indices
        for i in range(len(cadena)):
            print(f"cadena[{i}] = {cadena[i]}")

    if __name__ == "__main__":
        main()
    ```




### 🛠️ Métodos y operadores

=== "Kotlin"


    ```kotlin
    val cadena = "Hola mundo"

    // Longitud
    println("Longitud: ${cadena.length}")
    // Obtener un carácter
    println("Carácter: ${cadena[0]}")
    // Obtener un subcadena
    println("Subcadena: ${cadena.substring(0, 4)}")
    // Obtener un array de caracteres
    println("Array de caracteres: ${cadena.toCharArray().contentToString()}")
    // Obtener un array de cadenas
    println("Array de cadenas: ${cadena.split(" ")}")
    // Concatenación
    println("Concatenación: ${cadena + "!!"}")
    // Comparación
    println("Son iguales: ${cadena == "Hola mundo"}")
    // pasar a mayúsculas
    println("Mayúsculas: ${cadena.uppercase()}")
    // pasar a minúsculas
    println("Minúsculas: ${cadena.lowercase()}")
    // Contiene
    println("Contiene: ${cadena.contains("Hola")}")
    // primer elemento
    println("Primer elemento: ${cadena.first()}")
    // último elemento
    println("Último elemento: ${cadena.last()}")
    // Eliminar espacios en blanco
    println("Eliminar espacios en blanco: ${cadena.trim()}")
    // saber si existe en qué índice está
    println("Índice: ${cadena.indexOf("mundo")}")
    // Subarray con slice
    println("Subarray: ${cadena.slice(0..4)}")
    // reemplazar
    println("Reemplazar: ${cadena.replace("Hola", "Adiós")}")
    ```




=== "Java"


    ```java
    public class Main {
        public static void main(String[] args) {
            String cadena = "Hola mundo";
            
            // Longitud
            System.out.println("Longitud: " + cadena.length());
            // Obtener un carácter
            System.out.println("Carácter: " + cadena.charAt(0));
            // Obtener un subcadena
            System.out.println("Subcadena: " + cadena.substring(0, 4));
            // Obtener un array de caracteres
            System.out.println("Array de caracteres: " + java.util.Arrays.toString(cadena.toCharArray()));
            // Obtener un array de cadenas
            System.out.println("Array de cadenas: " + java.util.Arrays.toString(cadena.split(" ")));
            // Concatenación
            System.out.println("Concatenación: " + cadena + "!!");
            // Comparación
            System.out.println("Son iguales: " + cadena.equals("Hola mundo"));
            // pasar a mayúsculas
            System.out.println("Mayúsculas: " + cadena.toUpperCase());
            // pasar a minúsculas
            System.out.println("Minúsculas: " + cadena.toLowerCase());
            // Contiene
            System.out.println("Contiene: " + cadena.contains("Hola"));
            // primer elemento
            System.out.println("Primer elemento: " + cadena.charAt(0));
            // último elemento
            System.out.println("Último elemento: " + cadena.charAt(cadena.length() - 1));
            // Eliminar espacios en blanco
            System.out.println("Eliminar espacios en blanco: " + cadena.trim());
            // saber si existe en qué índice está
            System.out.println("Índice: " + cadena.indexOf("mundo"));
            // Subarray con substring
            System.out.println("Subarray: " + cadena.substring(0, 5));
            // reemplazar
            System.out.println("Reemplazar: " + cadena.replace("Hola", "Adiós"));
        }
    }
    ```




=== "Python"


    ```python
    def main():
        cadena = "Hola mundo"
        
        # Longitud
        print(f"Longitud: {len(cadena)}")
        # Obtener un carácter
        print(f"Carácter: {cadena[0]}")
        # Obtener un subcadena
        print(f"Subcadena: {cadena[0:4]}")
        # Obtener un array de caracteres
        print(f"Array de caracteres: {list(cadena)}")
        # Obtener un array de cadenas
        print(f"Array de cadenas: {cadena.split(' ')}")
        # Concatenación
        print(f"Concatenación: {cadena + '!!'}")
        # Comparación
        print(f"Son iguales: {cadena == 'Hola mundo'}")
        # pasar a mayúsculas
        print(f"Mayúsculas: {cadena.upper()}")
        # pasar a minúsculas
        print(f"Minúsculas: {cadena.lower()}")
        # Contiene
        print(f"Contiene: {'Hola' in cadena}")
        # primer elemento
        print(f"Primer elemento: {cadena[0]}")
        # último elemento
        print(f"Último elemento: {cadena[-1]}")
        # Eliminar espacios en blanco
        print(f"Eliminar espacios en blanco: {cadena.strip()}")
        # saber si existe en qué índice está
        print(f"Índice: {cadena.find('mundo')}")
        # Subarray con slice
        print(f"Subarray: {cadena[0:5]}")
        # reemplazar
        print(f"Reemplazar: {cadena.replace('Hola', 'Adiós')}")

    if __name__ == "__main__":
        main()
    ```




### 🔧 StringBuilder

StringBuilder es una clase que nos permite crear cadenas de forma mutable, es decir, podemos modificarlas.

=== "Kotlin"


    ```kotlin
    val sb = StringBuilder()
    val sb2 = StringBuilder("Hola mundo")
    sb.append("Hola mundo")
    val mensaje = sb2.toString()
    ```




=== "Java"


    ```java
    StringBuilder sb = new StringBuilder();
    StringBuilder sb2 = new StringBuilder("Hola mundo");
    sb.append("Hola mundo");
    String mensaje = sb2.toString();
    ```




=== "Python"


    ```python
    # En Python las cadenas son inmutables, pero podemos usar join o f-strings
    # Para operaciones complejas podemos usar lista y join
    partes = []
    partes.append("Hola")
    partes.append("mundo")
    mensaje = " ".join(partes)

    # O usando f-strings
    nombre = "mundo"
    mensaje = f"Hola {nombre}"
    ```


## 4. Expresiones regulares

Una expresión regular es una secuencia de caracteres que forma un patrón de búsqueda, principalmente utilizada para la búsqueda de patrones de cadenas de caracteres u operaciones de sustitución.

### 📝 Definición

=== "Kotlin"


    ```kotlin
    val regex = Regex("Hola")
    val regex2 = "\\d+".toRegex()
    ```




=== "Java"


    ```java
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    Pattern regex = Pattern.compile("Hola");
    Pattern regex2 = Pattern.compile("\\d+");
    ```




=== "Python"


    ```python
    import re

    regex = re.compile("Hola")
    regex2 = re.compile(r"\d+")
    ```




### 🛠️ Métodos y operadores

=== "Kotlin"


    ```kotlin
    val regex = Regex("Hola")

    // Comprobar si una cadena cumple el patrón
    println("Cumple el patrón: ${regex.matches("Hola mundo")}")
    // Obtener un array de cadenas
    println("Array de cadenas: ${regex.split("Hola mundo").contentToString()}")
    // Reemplazar
    println("Reemplazar: ${regex.replace("Hola mundo", "Adiós mundo")}")
    ```




=== "Java"


    ```java
    import java.util.regex.Pattern;
    import java.util.regex.Matcher;

    public class Main {
        public static void main(String[] args) {
            Pattern regex = Pattern.compile("Hola");
            
            // Comprobar si una cadena cumple el patrón
            Matcher matcher = regex.matcher("Hola mundo");
            System.out.println("Cumple el patrón: " + matcher.matches());
            
            // Obtener un array de cadenas
            String[] partes = regex.split("Hola mundo");
            System.out.println("Array de cadenas: " + java.util.Arrays.toString(partes));
            
            // Reemplazar
            String resultado = regex.matcher("Hola mundo").replaceAll("Adiós mundo");
            System.out.println("Reemplazar: " + resultado);
        }
    }
    ```




=== "Python"


    ```python
    import re

    def main():
        regex = re.compile("Hola")
        
        # Comprobar si una cadena cumple el patrón
        print(f"Cumple el patrón: {bool(regex.match('Hola mundo'))}")
        # Obtener un array de cadenas
        print(f"Array de cadenas: {regex.split('Hola mundo')}")
        # Reemplazar
        print(f"Reemplazar: {regex.sub('Adiós mundo', 'Hola mundo')}")

    if __name__ == "__main__":
        main()
    ```




### 🔍 Ejemplos

=== "Kotlin"


    ```kotlin
    fun main() {
        // Solo números
        val regexNum = "\\d+".toRegex()
        println("Solo números: ${regexNum.matches("1234567890")}")
        
        // Letras minúsculas
        val regexMin = "[a-z]+".toRegex()
        println("Letras minúsculas: ${regexMin.matches("abcdefghijklmnñopqrstuvwxyz")}")
        
        // Letras mayúsculas
        val regexMay = "[A-Z]+".toRegex()
        println("Letras mayúsculas: ${regexMay.matches("ABCDEFGHIJKLMNÑOPQRSTUVWXYZ")}")
        
        // Letras minúsculas y mayúsculas
        val regexLetras = "[a-zA-Z]+".toRegex()
        println("Letras minúsculas y mayúsculas: ${regexLetras.matches("abcdefghijklmnñopqrstuvwxyzABCDEFGHIJKLMNÑOPQRSTUVWXYZ")}")
        
        // Teléfono
        val regexTel = "\\d{9}".toRegex()
        println("Teléfono: ${regexTel.matches("123456789")}")
        
        // DNI
        val regexDNI = "\\d{8}[A-Z]".toRegex()
        println("DNI: ${regexDNI.matches("12345678A")}")
        
        // Email
        val regexEmail = "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}".toRegex()
        println("Email: ${regexEmail.matches("pepe@pepilandia.com")}")
        
        // URL
        val regexURL = "^(http|https)://[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}".toRegex()
        println("URL: ${regexURL.matches("http://pepilandia.com")}")
        
        // Tarjeta de crédito
        val regexTarjeta = "\\d{4} \\d{4} \\d{4} \\d{4}".toRegex()
        println("Tarjeta de crédito: ${regexTarjeta.matches("1234 5678 9012 3456")}")
        
        // Fecha
        val regexFecha = "\\d{2}/\\d{2}/\\d{4}".toRegex()
        println("Fecha: ${regexFecha.matches("01/01/2020")}")
    }
    ```




=== "Java"


    ```java
    import java.util.regex.Pattern;

    public class Main {
        public static void main(String[] args) {
            // Solo números
            Pattern regexNum = Pattern.compile("\\d+");
            System.out.println("Solo números: " + regexNum.matcher("1234567890").matches());
            
            // Letras minúsculas
            Pattern regexMin = Pattern.compile("[a-z]+");
            System.out.println("Letras minúsculas: " + regexMin.matcher("abcdefghijklmnñopqrstuvwxyz").matches());
            
            // Letras mayúsculas
            Pattern regexMay = Pattern.compile("[A-Z]+");
            System.out.println("Letras mayúsculas: " + regexMay.matcher("ABCDEFGHIJKLMNÑOPQRSTUVWXYZ").matches());
            
            // Teléfono
            Pattern regexTel = Pattern.compile("\\d{9}");
            System.out.println("Teléfono: " + regexTel.matcher("123456789").matches());
            
            // DNI
            Pattern regexDNI = Pattern.compile("\\d{8}[A-Z]");
            System.out.println("DNI: " + regexDNI.matcher("12345678A").matches());
            
            // Email
            Pattern regexEmail = Pattern.compile("[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}");
            System.out.println("Email: " + regexEmail.matcher("pepe@pepilandia.com").matches());
        }
    }
    ```




=== "Python"


    ```python
    import re

    def main():
        # Solo números
        regex_num = re.compile(r"\d+")
        print(f"Solo números: {bool(regex_num.match('1234567890'))}")
        
        # Letras minúsculas
        regex_min = re.compile(r"[a-z]+")
        print(f"Letras minúsculas: {bool(regex_min.match('abcdefghijklmnñopqrstuvwxyz'))}")
        
        # Letras mayúsculas
        regex_may = re.compile(r"[A-Z]+")
        print(f"Letras mayúsculas: {bool(regex_may.match('ABCDEFGHIJKLMNÑOPQRSTUVWXYZ'))}")
        
        # Teléfono
        regex_tel = re.compile(r"\d{9}")
        print(f"Teléfono: {bool(regex_tel.match('123456789'))}")
        
        # DNI
        regex_dni = re.compile(r"\d{8}[A-Z]")
        print(f"DNI: {bool(regex_dni.match('12345678A'))}")
        
        # Email
        regex_email = re.compile(r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}")
        print(f"Email: {bool(regex_email.match('pepe@pepilandia.com'))}")

    if __name__ == "__main__":
        main()
    ```




------

## 5. Métodos de ordenación

Los métodos de ordenación nos permite ordenar arrays. Pero debemos tener en cuenta que dependiendo del método de ordenación así será su eficiencia.

### 🔴 Burbuja

Es un método de ordenación con eficiencia O(n²). Consiste en ir comparando cada elemento con el siguiente, y si el elemento actual es mayor que el siguiente, se intercambian.


```
6  5  3  1  8  7  2  4
```



=== "Kotlin"


    ```kotlin
    fun burbuja(array: IntArray) {
        var aux: Int
        for (i in 0 until array.size) {
            for (j in 0 until array.size - 1) {
                if (array[j] > array[j + 1]) {
                    aux = array[j]
                    array[j] = array[j + 1]
                    array[j + 1] = aux
                }
            }
        }
    }
    ```




=== "Java"


    ```java
    public static void burbuja(int[] array) {
        int aux;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array.length - 1; j++) {
                if (array[j] > array[j + 1]) {
                    aux = array[j];
                    array[j] = array[j + 1];
                    array[j + 1] = aux;
                }
            }
        }
    }
    ```




=== "Python"


    ```python
    def burbuja(array):
        for i in range(len(array)):
            for j in range(len(array) - 1):
                if array[j] > array[j + 1]:
                    array[j], array[j + 1] = array[j + 1], array[j]
    ```




### 🔵 Selección

El algoritmo de selección tiene eficiencia O(n²). Consiste en ir buscando el elemento más pequeño del array y colocarlo en la primera posición, luego el segundo más pequeño y colocarlo en la segunda posición, y así sucesivamente.


=== "Kotlin"


    ```kotlin
    fun seleccion(array: IntArray) {
        var aux: Int
        var min: Int
        for (i in 0 until array.size) {
            min = i
            for (j in i + 1 until array.size) {
                if (array[j] < array[min]) {
                    min = j
                }
            }
            aux = array[i]
            array[i] = array[min]
            array[min] = aux
        }
    }
    ```




=== "Java"


    ```java
    public static void seleccion(int[] array) {
        int aux, min;
        for (int i = 0; i < array.length; i++) {
            min = i;
            for (int j = i + 1; j < array.length; j++) {
                if (array[j] < array[min]) {
                    min = j;
                }
            }
            aux = array[i];
            array[i] = array[min];
            array[min] = aux;
        }
    }
    ```




=== "Python"


    ```python
    def seleccion(array):
        for i in range(len(array)):
            min_idx = i
            for j in range(i + 1, len(array)):
                if array[j] < array[min_idx]:
                    min_idx = j
            array[i], array[min_idx] = array[min_idx], array[i]
    ```




### 🟢 Inserción

El algoritmo de inserción tiene eficiencia O(n²). Inicialmente se tiene un solo elemento, que obviamente es un conjunto ordenado. Después, cuando hay k elementos ordenados de menor a mayor, se toma el elemento k+1 y se compara con todos los elementos ya ordenados.


=== "Kotlin"


    ```kotlin
    fun insercion(array: IntArray) {
        var aux: Int
        var j: Int
        for (i in 1 until array.size) {
            aux = array[i]
            j = i - 1
            while (j >= 0 && array[j] > aux) {
                array[j + 1] = array[j]
                j--
            }
            array[j + 1] = aux
        }
    }
    ```




=== "Java"


    ```java
    public static void insercion(int[] array) {
        int aux, j;
        for (int i = 1; i < array.length; i++) {
            aux = array[i];
            j = i - 1;
            while (j >= 0 && array[j] > aux) {
                array[j + 1] = array[j];
                j--;
            }
            array[j + 1] = aux;
        }
    }
    ```




=== "Python"


    ```python
    def insercion(array):
        for i in range(1, len(array)):
            aux = array[i]
            j = i - 1
            while j >= 0 and array[j] > aux:
                array[j + 1] = array[j]
                j -= 1
            array[j + 1] = aux
    ```




### 🟡 Shell

El algoritmo de Shell es una mejora del algoritmo de inserción. Su eficiencia es de O(n log n). Este método consiste en ordenar los elementos de un array de forma que los elementos que están lejos entre sí se ordenan primero.


=== "Kotlin"


    ```kotlin
    fun shell(array: IntArray) {
        var aux: Int
        var j: Int
        var intervalo = 1
        while (intervalo < array.size) {
            intervalo = intervalo * 3 + 1
        }
        while (intervalo > 0) {
            for (i in intervalo until array.size) {
                aux = array[i]
                j = i
                while (j > intervalo - 1 && array[j - intervalo] >= aux) {
                    array[j] = array[j - intervalo]
                    j -= intervalo
                }
                array[j] = aux
            }
            intervalo = (intervalo - 1) / 3
        }
    }
    ```




=== "Java"


    ```java
    public static void shell(int[] array) {
        int aux, j, intervalo = 1;
        while (intervalo < array.length) {
            intervalo = intervalo * 3 + 1;
        }
        while (intervalo > 0) {
            for (int i = intervalo; i < array.length; i++) {
                aux = array[i];
                j = i;
                while (j > intervalo - 1 && array[j - intervalo] >= aux) {
                    array[j] = array[j - intervalo];
                    j -= intervalo;
                }
                array[j] = aux;
            }
            intervalo = (intervalo - 1) / 3;
        }
    }
    ```




=== "Python"


    ```python
    def shell(array):
        n = len(array)
        intervalo = 1
        while intervalo < n:
            intervalo = intervalo * 3 + 1
        
        while intervalo > 0:
            for i in range(intervalo, n):
                aux = array[i]
                j = i
                while j >= intervalo and array[j - intervalo] > aux:
                    array[j] = array[j - intervalo]
                    j -= intervalo
                array[j] = aux
            intervalo = (intervalo - 1) // 3
    ```




### 🟣 QuickSort

El algoritmo de quicksort es el algoritmo más rápido que veremos. Su eficiencia es de O(n log n). Consiste en dividir el array en dos partes, una con los elementos menores que el pivote y otra con los elementos mayores que el pivote.

Veamos este ejemplo de [Wikipedia](https://es.wikipedia.org/wiki/Quicksort)

En el siguiente ejemplo se marcan el pivote y los índices i y j con las letras p, i y j respectivamente.

```bash

Comenzamos con la lista completa. El elemento pivote será el 4:
 5 - 3 - 7 - 6 - 2 - 1 - 4
                         p
Comparamos con el 5 por la izquierda y el 1 por la derecha.
 5 - 3 - 7 - 6 - 2 - 1 - 4 
 i                   j   p
5 es mayor que 4 y 1 es menor. Intercambiamos:
 1 - 3 - 7 - 6 - 2 - 5 - 4
 i                   j   p 
Avanzamos por la izquierda y la derecha:
 1 - 3 - 7 - 6 - 2 - 5 - 4
     i           j       p 
3 es menor que 4: avanzamos por la izquierda. 2 es menor que 4: nos mantenemos ahí.
 1 - 3 - 7 - 6 - 2 - 5 - 4
         i       j       p 
7 es mayor que 4 y 2 es menor: intercambiamos.
 1 - 3 - 2 - 6 - 7 - 5 - 4
         i       j       p 
Avanzamos por ambos lados:
 1 - 3 - 2 - 6 - 7 - 5 - 4
            iyj          p 
En este momento termina el ciclo principal, porque los índices se cruzaron. Ahora intercambiamos lista[i] con lista[p] (pasos 16-18):
 1 - 3 - 2 - 4 - 7 - 5 - 6
             p 
Aplicamos recursivamente a la sublista de la izquierda (índices 0 - 2). Tenemos lo siguiente:
 1 - 3 - 2 
1 es menor que 2: avanzamos por la izquierda. 3 es mayor: avanzamos por la derecha. Como se intercambiaron los índices termina el ciclo. Se intercambia lista[i] con lista[p]:
 1 - 2 - 3 
El mismo procedimiento se aplicará a la otra sublista. Al finalizar y unir todas las sublistas queda la lista inicial ordenada en forma ascendente.
 1 - 2 - 3 - 4 - 5 - 6 - 7
```



=== "Kotlin"


    ```kotlin
    fun pivote(array: IntArray, izq: Int, der: Int): Int {
        var i = izq
        var j = der
        var pivote = array[izq]
        while (i < j) {
            while (array[i] <= pivote && i < j) {
                i++
            }
            while (array[j] > pivote) {
                j--
            }
            if (i < j) {
                val aux = array[i]
                array[i] = array[j]
                array[j] = aux
            }
        }
        array[izq] = array[j]
        array[j] = pivote
        return j
    }

    fun quicksort(array: IntArray, izq: Int, der: Int) {
        var piv: Int
        if (izq < der) {
            piv = pivote(array, izq, der)
            quicksort(array, izq, piv - 1)
            quicksort(array, piv + 1, der)
        }
    }
    ```




=== "Java"


```java
import java.util.Arrays;
public class Main {

    public static int pivote(int[] array, int izq, int der) {
        int i = izq;
        int j = der;
        int pivote = array[izq];
        while (i < j) {
            while (array[i] <= pivote && i < j) {
                i++;
            }
            while (array[j] > pivote) {
                j--;
            }
            if (i < j) {
                int aux = array[i];
                array[i] = array[j];
                array[j] = aux;
            }
        }
        array[izq] = array[j];
        array[j] = pivote;
        return j;
    }

    public static void quicksort(int[] array, int izq, int der) {
        int piv;
        if (izq < der) {
            piv = pivote(array, izq, der);
            quicksort(array, izq, piv - 1);
            quicksort(array, piv + 1, der);
        }
    }

    public static void main(String[] args) {
       int[] vector = {5, 3, 7, 6, 2, 1, 4};
        quicksort(vector, 0, vector.length - 1);
        System.out.println(Arrays.toString(vector));

    }
}

```




=== "Python"


    ```python
    def pivote(array, izq, der):
        i = izq
        j = der
        pivote = array[izq]
        while i < j:
            while array[i] <= pivote and i < j:
                i += 1
            while array[j] > pivote:
                j -= 1
            if i < j:
                array[i], array[j] = array[j], array[i]
        array[izq] = array[j]
        array[j] = pivote
        return j

    def quicksort(array, izq, der):
        if izq < der:
            piv = pivote(array, izq, der)
            quicksort(array, izq, piv - 1)
            quicksort(array, piv + 1, der)
    ```




------

## 6. Métodos de búsqueda

Los métodos de búsqueda nos servirán para encontrar un elemento en un array.

### 🔍 Búsqueda secuencial

La búsqueda secuencial o lineal consiste en recorrer el vector hasta devolver el elemento buscado. Su eficiencia es de O(n).


```
0  1  2  3  4  5  6  7  8  9  10
| I | N | F | O | R | M | A | T | I | C | A |
| M | M | M | M | M | M | M | INDICE=5 |
```



=== "Kotlin"



    ```kotlin
    fun busquedaSecuencial(array: IntArray, elemento: Int): Int {
        for (i in array.indices) {
            if (array[i] == elemento) {
                return i
            }
        }
        return -1
    }
    ```




=== "Java"



    ```java
    public static int busquedaSecuencial(int[] array, int elemento) {
        for (int i = 0; i < array.length; i++) {
            if (array[i] == elemento) {
                return i;
            }
        }
        return -1;
    }
    ```




=== "Python"


    ```python
    def busqueda_secuencial(array, elemento):
        for i in range(len(array)):
            if array[i] == elemento:
                return i
        return -1
    ```




### 🔎 Búsqueda binaria

En la búsqueda binaria partimos de un array ordenado. Su eficiencia es de O(log n). Se compara el dato buscado con el elemento en el centro del vector.

Definición de [Wikipedia](https://es.wikipedia.org/wiki/B%C3%BAsqueda_binaria)

**Elemento buscado:** 12



```
izq = 1   medio = 4   der = 7
(=(izq+der)/2)

12 > v[medio] = 4

Cogemos el subvector derecho
izq = 5   medio = 6   der = 7
(=medio+1)   (=(izq+der)/2)

12 < v[medio] = 13

Cogemos el subvector izquierdo
izq = 5   medio = 5   der = 5
(=(izq+der)/2)   (=medio-1)
(antes de modificar medio)

12 = v[medio] = 12

ENCONTRADO
```



=== "Kotlin"


    ```kotlin
    // Versión Iterativa
    fun busquedaBinariaIterativa(array: IntArray, elemento: Int): Int {
        var centro: Int
        var inf = 0
        var sup = array.size - 1
        while (inf <= sup) {
            centro = (sup + inf) / 2
            if (array[centro] == elemento) {
                return centro
            } else if (elemento < array[centro]) {
                sup = centro - 1
            } else {
                inf = centro + 1
            }
        }
        return -1
    }

    // Versión recursiva
    fun busquedaBinariaRecursiva(array: IntArray, elemento: Int, inf: Int, sup: Int): Int {
        if (inf > sup) {
            return -1
        }
        val centro = (sup + inf) / 2
        return if (array[centro] == elemento) {
            centro
        } else if (elemento < array[centro]) {
            busquedaBinariaRecursiva(array, elemento, inf, centro - 1)
        } else {
            busquedaBinariaRecursiva(array, elemento, centro + 1, sup)
        }
    }
    ```




=== "Java"


    ```java
    // Versión Iterativa
    public static int busquedaBinariaIterativa(int[] array, int elemento) {
        int centro, inf = 0, sup = array.length - 1;
        while (inf <= sup) {
            centro = (sup + inf) / 2;
            if (array[centro] == elemento) {
                return centro;
            } else if (elemento < array[centro]) {
                sup = centro - 1;
            } else {
                inf = centro + 1;
            }
        }
        return -1;
    }

    // Versión recursiva
    public static int busquedaBinariaRecursiva(int[] array, int elemento, int inf, int sup) {
        if (inf > sup) {
            return -1;
        }
        int centro = (sup + inf) / 2;
        if (array[centro] == elemento) {
            return centro;
        } else if (elemento < array[centro]) {
            return busquedaBinariaRecursiva(array, elemento, inf, centro - 1);
        } else {
            return busquedaBinariaRecursiva(array, elemento, centro + 1, sup);
        }
    }
    ```




=== "Python"


    ```python
    # Versión Iterativa
    def busqueda_binaria_iterativa(array, elemento):
        inf = 0
        sup = len(array) - 1
        while inf <= sup:
            centro = (sup + inf) // 2
            if array[centro] == elemento:
                return centro
            elif elemento < array[centro]:
                sup = centro - 1
            else:
                inf = centro + 1
        return -1

    # Versión recursiva
    def busqueda_binaria_recursiva(array, elemento, inf, sup):
        if inf > sup:
            return -1
        centro = (sup + inf) // 2
        if array[centro] == elemento:
            return centro
        elif elemento < array[centro]:
            return busqueda_binaria_recursiva(array, elemento, inf, centro - 1)
        else:
            return busqueda_binaria_recursiva(array, elemento, centro + 1, sup)
    ```




------

## 7. Nulabilidad

En determinados lenguajes de programación existe el concepto de variable nula, es decir, una variable que no tiene valor (no apunta a ninguna zona de memoria o dicha zona no tiene valor).

=== "Kotlin"


    ```kotlin
    // En Kotlin, todas las variables son no nulas por defecto
    var numero: Int? = null

    // Comprobar nulabilidad
    val nombre: String? = null
    println(nombre?.length)  // Safe call

    // Operador Elvis
    val longitud = nombre?.length ?: 0

    // Operador !! (peligroso)
    // val longitud = nombre!!.length  // Lanza excepción si es null

    // Ejemplo práctico
    var numero: Int? = null
    do {
        print("Introduce un número: ")
        numero = readln().toIntOrNull()
    } while (numero == null)
    println("Número introducido: $numero")

    // Arrays de componentes nulas
    val array = arrayOfNulls<Int>(10)
    val otro: Array<Int?> = arrayOfNulls(10)
    ```




=== "Java"


    ```java
    // En Java, los objetos pueden ser null
    Integer numero = null;
    String nombre = null;

    // Comprobar nulabilidad
    if (nombre != null) {
        System.out.println(nombre.length());
    }

    // Operador ternario (similar a Elvis)
    int longitud = (nombre != null) ? nombre.length() : 0;

    // Ejemplo práctico
    Integer numero = null;
    Scanner scanner = new Scanner(System.in);
    do {
        System.out.print("Introduce un número: ");
        try {
            numero = Integer.parseInt(scanner.nextLine());
        } catch (NumberFormatException e) {
            numero = null;
        }
    } while (numero == null);
    System.out.println("Número introducido: " + numero);

    // Arrays de objetos (pueden ser null)
    Integer[] array = new Integer[10];  // Todos null inicialmente
    String[] otro = new String[10];     // Todos null inicialmente
    ```




=== "Python"


    ```python
    # En Python, None es el equivalente a null
    numero = None
    nombre = None

    # Comprobar nulabilidad
    if nombre is not None:
        print(len(nombre))

    # Operador ternario (similar a Elvis)
    longitud = len(nombre) if nombre is not None else 0

    # Ejemplo práctico
    numero = None
    while numero is None:
        try:
            entrada = input("Introduce un número: ")
            numero = int(entrada)
        except ValueError:
            numero = None
            print("Por favor, introduce un número válido")
    print(f"Número introducido: {numero}")

    # Listas pueden contener None
    array = [None] * 10
    otro = [1, None, 3, None, 5]
    ```

