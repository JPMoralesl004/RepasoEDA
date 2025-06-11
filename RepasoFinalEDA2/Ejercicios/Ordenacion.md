# Ordenacion

## Ejercicio

- **Dada la cadena ASDFGHJKLÑ usa un algoritmo de ordenamiento para ordenarlo mediante ordenamiento alfabetico inverso:**

### ArraySort en orden inverso

``` java
import java.util.Arrays;
import java.util.Collections;

public class OrdenarCadenaInverso {
    public static void main(String[] args) {
        String cadena = "ASDFGHJKLÑ";

        // Convertir la cadena a un arreglo de caracteres
        Character[] caracteres = new Character[cadena.length()];
        for (int i = 0; i < cadena.length(); i++) {
            caracteres[i] = cadena.charAt(i);
        }

        // Ordenar en orden alfabético inverso
        Arrays.sort(caracteres, Collections.reverseOrder());

        // Convertir el arreglo ordenado de nuevo en String
        StringBuilder resultado = new StringBuilder();
        for (char c : caracteres) {
            resultado.append(c);
        }

        System.out.println("Cadena ordenada inversamente: " + resultado);
    }
}
```

### BubbleSort en orden inverso

``` java
public class OrdenarInversoBubble {
    public static void main(String[] args) {
        String cadena = "ASDFGHJKLÑ";
        char[] caracteres = cadena.toCharArray();

        // Bubble Sort en orden inverso (Z a A)
        for (int i = 0; i < caracteres.length - 1; i++) {
            for (int j = 0; j < caracteres.length - i - 1; j++) {
                if (caracteres[j] < caracteres[j + 1]) {
                    // Intercambio
                    char temp = caracteres[j];
                    caracteres[j] = caracteres[j + 1];
                    caracteres[j + 1] = temp;
                }
            }
        }

        // Mostrar resultado
        String resultado = new String(caracteres);
        System.out.println("Cadena ordenada inversamente (Bubble Sort): " + resultado);
    }
}
```

### CountingSort en orden inverso

``` java
public class CountingSortInverso {
    public static void main(String[] args) {
        String cadena = "ASDFGHJKLÑ";

        // Se define un arreglo para contar ocurrencias de cada carácter (basado en ASCII extendido)
        int[] contador = new int[256];

        // Se recorre la cadena original y se contabiliza la frecuencia de cada carácter
        for (int i = 0; i < cadena.length(); i++) {
            char c = cadena.charAt(i);
            contador[c]++;
        }

        // Se construye el resultado recorriendo el arreglo de conteo en orden descendente
        // Esto asegura un orden alfabético inverso (de mayor a menor valor ASCII)
        StringBuilder resultado = new StringBuilder();
        for (int i = 255; i >= 0; i--) {
            while (contador[i] > 0) {
                resultado.append((char) i);
                contador[i]--;
            }
        }

        // Se imprime la cadena ordenada en orden alfabético inverso
        System.out.println("Cadena ordenada inversamente (Counting Sort): " + resultado);
    }
}
```
