public class Estudiante {

  
    private final double[] notas;
    private final double promedio;

    // Constructor para inicializar las notas
    public Estudiante(double[] notas) {
        this.notas = notas;
        this.promedio = calcularPromedio();
    }

    // Método para calcular el promedio
    private double calcularPromedio() {
        double suma = 0;
        for (double nota : notas) {
            suma += nota;
        }
        return suma / notas.length;
    }

    // Método para contar cuántas notas están por encima del promedio
    public int contarNotasPorEncima() {
        int contador = 0;
        for (double nota : notas) {
            if (nota > promedio) {
                contador++;
            }
        }
        return contador;
    }

    // Método para contar cuántas notas están por debajo del promedio
    public int contarNotasPorDebajo() {
        int contador = 0;
        for (double nota : notas) {
            if (nota < promedio) {
                contador++;
            }
        }
        return contador;
    }

    // Método para obtener el promedio
    public double getPromedio() {
        return promedio; 
}
}
