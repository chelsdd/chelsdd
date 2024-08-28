package javaapplication23;  // Se declara el paquete

// Se importa la clase Scanner para la entrada del usuario.
import java.util.Scanner;

// Clase 
class Estudiante {
    private final String cedula;  // Atributo privado y final para almacenar la cédula del estudiante.

    // Constructor que inicializa la cédula del estudiante.
    public Estudiante(String cedula) {
        this.cedula = cedula;
    }

    // Método que obtiene el último dígito de la cédula del estudiante.
    public int obtenerUltimoDigito() {
        // Convierte el último carácter de la cédula a su valor numérico.
        return Character.getNumericValue(cedula.charAt(cedula.length() - 1));
    }
}

// Clase que gestiona la asignación de modelos a los estudiantes.
class GestionModelos {
    private final int[] conteoModelos;  // Arreglo para contar los estudiantes por cada modelo (hay 5 modelos).

    // Constructor que inicializa el arreglo de conteo de modelos.
    public GestionModelos() {
        conteoModelos = new int[5];  // Inicializa el arreglo con 5 elementos, cada uno representando un modelo.
    }

    // Método que asigna un modelo a un estudiante basado en el último dígito de su cédula.
    public void asignarModelo(Estudiante estudiante) {
        int ultimoDigito = estudiante.obtenerUltimoDigito();  // Obtiene el último dígito de la cédula del estudiante.

        // Asigna un modelo según el último dígito de la cédula utilizando una instrucción switch.
        switch (ultimoDigito) {
            case 1, 6 -> conteoModelos[0]++;  // Incrementa el contador del modelo 1.
            case 2, 7 -> conteoModelos[1]++;  // Incrementa el contador del modelo 2.
            case 3, 8 -> conteoModelos[2]++;  // Incrementa el contador del modelo 3.
            case 4, 9 -> conteoModelos[3]++;  // Incrementa el contador del modelo 4.
            case 5, 0 -> conteoModelos[4]++;  // Incrementa el contador del modelo 5.
        }
    }

    // Método que muestra el conteo de estudiantes asignados a cada modelo.
    public void mostrarConteo() {
        // Recorre el arreglo de conteo de modelos y muestra el número de estudiantes para cada modelo.
        for (int i = 0; i < conteoModelos.length; i++) {
            System.out.println("Cantidad de estudiantes con el modelo " + (i + 1) + ": " + conteoModelos[i]);
        }
    }
}

// Clase principal que contiene el método main para ejecutar el programa.
public class AsignacionParciales {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);  // Crea un objeto Scanner para leer la entrada del usuario.

        // Solicita al usuario la cantidad de estudiantes.
        System.out.print("Ingrese la cantidad de estudiantes: ");
        int numEstudiantes = scanner.nextInt();  // Lee el número de estudiantes ingresado por el usuario.
        scanner.nextLine();  // Consumir el salto de línea que queda tras la lectura del número.

        // Crea un objeto de la clase GestionModelos para manejar la asignación de modelos.
        GestionModelos gestionModelos = new GestionModelos();

        // Bucle para ingresar la cédula de cada estudiante y asignar un modelo.
        for (int i = 0; i < numEstudiantes; i++) {
            System.out.print("Ingrese la cédula del estudiante " + (i + 1) + ": ");
            String cedula = scanner.nextLine();  // Lee la cédula del estudiante.
            Estudiante estudiante = new Estudiante(cedula);  // Crea un objeto Estudiante con la cédula ingresada.
            gestionModelos.asignarModelo(estudiante);  // Asigna un modelo al estudiante.
        }

        // Muestra el conteo de estudiantes por modelo.
        gestionModelos.mostrarConteo();
    }
}


    
            
