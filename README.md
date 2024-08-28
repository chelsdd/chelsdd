import java.util.Scanner;

class Estudiante {
    private String cedula;

    public Estudiante(String cedula) {
        this.cedula = cedula;
    }

    public int obtenerUltimoDigito() {
        return Character.getNumericValue(cedula.charAt(cedula.length() - 1));
    }
}

class GestionModelos {
    private int[] conteoModelos;

    public GestionModelos() {
        conteoModelos = new int[5];  // Hay 5 modelos
    }

    public void asignarModelo(Estudiante estudiante) {
        int ultimoDigito = estudiante.obtenerUltimoDigito();

        switch (ultimoDigito) {
            case 1:
            case 6:
                conteoModelos[0]++;
                break;
            case 2:
            case 7:
                conteoModelos[1]++;
                break;
            case 3:
            case 8:
                conteoModelos[2]++;
                break;
            case 4:
            case 9:
                conteoModelos[3]++;
                break;
            case 5:
            case 0:
                conteoModelos[4]++;
                break;
        }
    }

    public void mostrarConteo() {
        for (int i = 0; i < conteoModelos.length; i++) {
            System.out.println("Cantidad de estudiantes con el modelo " + (i + 1) + ": " + conteoModelos[i]);
        }
    }
}

public class AsignacionParciales {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Ingrese la cantidad de estudiantes: ");
        int numEstudiantes = scanner.nextInt();
        scanner.nextLine();  // Consumir el salto de línea

        GestionModelos gestionModelos = new GestionModelos();

        // Ingreso de cédulas y asignación de modelos
        for (int i = 0; i < numEstudiantes; i++) {
            System.out.print("Ingrese la cédula del estudiante " + (i + 1) + ": ");
            String cedula = scanner.nextLine();
            Estudiante estudiante = new Estudiante(cedula);
            gestionModelos.asignarModelo(estudiante);
        }

        // Mostrar el conteo de estudiantes por modelo
        gestionModelos.mostrarConteo();
    }
}
