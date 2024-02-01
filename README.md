
## Unas gotas de ArrayList en Java

### Introducción
La clase `ArrayList` en Java es parte del "paquete" `java.util`. Nos ofrece arrays dinámicos en Java. Esto lo matizaremos en breve cuando lleguemos a la O.O. 
A diferencia de los arrays tradicionales que tienen un tamaño fijo, un `ArrayList` puede cambiar su tamaño dinámicamente, proporcionando más flexibilidad y utilidad en la programación.

### ¿Por qué ArrayList?
- **Tamaño Dinámico**: Se redimensiona automáticamente cuando se agregan o eliminan elementos.
- **Facilidad de Operaciones**: Proporciona métodos para tareas comunes como agregar, eliminar y buscar elementos.

### Operaciones básicas

#### Crear un ArrayList
```java
ArrayList<String> miLista = new ArrayList<String>();
```

#### Agregar Elementos
```java
miLista.add("Hola");
miLista.add("Mundo");
```

#### Acceder a Elementos
```java
String elemento = miLista.get(0); // Accede al primer elemento
```

#### Modificar Elementos
```java
miLista.set(0, "Hi"); // Cambia el primer elemento a "Hi"
```

#### Eliminar Elementos
```java
miLista.remove("Hi"); // Elimina "Hi" de la lista
```

#### Tamaño del ArrayList
```java
int tamaño = miLista.size();
```
### Revisemos la W3CSchool

### Ejemplo Práctico: Usar ArrayList en un Programa

Creemos un pequeño programa donde almacenamos una lista de nombres y los recuperamos.

```java
import java.util.ArrayList;

public class Principal {
    public static void main(String[] args) {
        ArrayList<String> nombres = new ArrayList<String>();

        // Agregando nombres
        nombres.add("Alice");
        nombres.add("Bob");
        nombres.add("Charlie");

        // Mostrando nombres
        for(String nombre : nombres) {
            System.out.println(nombre);
        }

        // Tamaño del ArrayList
        System.out.println("Total de nombres: " + nombres.size());
    }
}
```

### Comparación: ArrayList vs. Array clásico

#### Ventajas del ArrayList
- **Flexibilidad de Tamaño**: A diferencia de los arrays clásicos, el `ArrayList` puede cambiar su tamaño automáticamente.
- **Facilidad de Uso**: Proporciona métodos útiles para operaciones comunes, mejorando la legibilidad y reduciendo el código necesario.

#### Inconvenientes del ArrayList
- **Rendimiento**: Operaciones como el redimensionamiento pueden ser más lentas que en un array clásico.
- **Consumo de Memoria**: Usa más memoria que un array clásico debido a la flexibilidad de tamaño.En realidad, la implementación del ArrayList hace uso de arrays internamente.

#### Ventajas del Array clásico
- **Rendimiento**: Los arrays clásicos pueden tener un rendimiento más rápido para operaciones simples debido a su tamaño fijo.
- **Eficiencia de memoria**: Utilizan menos memoria al tener un tamaño predeterminado.

#### Inconvenientes del Array clásico
- **Tamaño fijo**: Una vez creado, su tamaño no puede cambiar, lo que puede limitar su utilidad.
- **Menos funcionalidades**: No ofrece métodos incorporados para tareas comunes como añadir o eliminar elementos. Se gestionan mediante índices y el uso de índices puede generar errores.

Un codewars: Transform to Prime. https://www.codewars.com/kata/5a946d9fba1bb5135100007c

    import java.util.ArrayList;

    public class TransformToPrime {

    public static boolean esPrimo(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }

    public static int minimumNumber(ArrayList<Integer> numbers) {
        int suma = 0;
        for (int num : numbers) {
            suma += num;
        }
        int numeroNecesario = 0;
        while (!esPrimo(suma + numeroNecesario)) {
            numeroNecesario++;
        }
        return numeroNecesario;
    }

    public static void main(String[] args) {
        ArrayList<Integer> ejemplo1 = new ArrayList<>();
        ejemplo1.add(3);
        ejemplo1.add(1);
        ejemplo1.add(2);

        ArrayList<Integer> ejemplo2 = new ArrayList<>();
        ejemplo2.add(2);
        ejemplo2.add(12);
        ejemplo2.add(8);
        ejemplo2.add(4);
        ejemplo2.add(6);

        ArrayList<Integer> ejemplo3 = new ArrayList<>();
        ejemplo3.add(50);
        ejemplo3.add(39);
        ejemplo3.add(49);
        ejemplo3.add(6);
        ejemplo3.add(17);
        ejemplo3.add(28);

        System.out.println(minimumNumber(ejemplo1)); // Debería devolver 1
        System.out.println(minimumNumber(ejemplo2)); // Debería devolver 5
        System.out.println(minimumNumber(ejemplo3)); // Debería devolver 2
    }
}

- Una versión alternativa que me permite reconocer números primos sería:

        public static boolean esPrimo(int num) {
            if (num <= 1) {
                return false; // Los números menores o iguales a 1 no son primos por definición.
            }
            for (int i = 2; i < num; i++) { // Iteramos desde 2 hasta num.
                if (num % i == 0) {
                    return false; // Si num es divisible por cualquier número en este rango, no es primo.
                }
            }
            return true; // Si no encontramos divisores, entonces el número es primo.
        }

- Ojo con la siguiente optimización:

- En lugar de comprobar todos los números hasta num para ver si num se puede dividir por ellos, solo comprobamos hasta la raíz cuadrada de num. Esto funciona porque si num tiene un divisor mayor que su raíz cuadrada, entonces necesariamente debe tener un divisor menor que ella, por lo que solo necesitamos buscar hasta la raíz cuadrada para encontrar al menos un divisor si existe.

