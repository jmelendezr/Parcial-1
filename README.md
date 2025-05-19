## Punto 2

```java
public class Triangulo {
    // Atributos principales de la clase (Identidades a, b, c son los lados)
    private double area, altura;
    private int a, b, c;

    // Constructor (Inicializa las variables locales con valores de entrada)
    public Triangulo(int la, int lb, int lc) {
        a = la;
        b = lb;
        c = lc;
    }

    // Método que invoca variables globales (asigna valores a, b, c)
    public void f(int la, int lb, int lc) {
        a = la;
        b = lb;
        c = lc;
    }

    // Método privado (No accesible desde fuera) para calcular raíz cuadrada por aproximación
    private double raiz(double m) {
        double g1, g2;
        g2 = m / 2.0;
        do {
            g1 = g2;
            g2 = (g1 + m / g1) / 2.0;
        } while (g1 != g2);
        return g2;
    }

    // Método público para calcular el área del triángulo (Herón)
    public void areaTriangulo() {
        double s = (a + b + c) / 2.0;
        area = raiz(s * (s - a) * (s - b) * (s - c));
    }

    // Método público para calcular la altura respecto al lado a
    public void alturaTriangulo() {
        altura = (2 * area) / a;
    }

    // Getters y Setters para acceder y modificar atributos privados
    public int getA() { return a; }
    public void setA(int a) { this.a = a; }
    public int getB() { return b; }
    public void setB(int b) { this.b = b; }
    public int getC() { return c; }
    public void setC(int c) { this.c = c; }
    public double getArea() { return area; }
    public void setArea(double area) { this.area = area; }
    public double getAltura() { return altura; }
    public void setAltura(double altura) { this.altura = altura; }

    // Métodos que retornan valores calculados (f1 = área, f2 = altura)
    public double f1() { return area; }
    public double f2() { return altura; }

    // Cartel de salida concatenada (muestra los resultados)
    public void imprimirCartel() {
        System.out.println("Lado a: " + a + ", Lado b: " + b + ", Lado c: " + c +
                           ", Área: " + area + ", Altura: " + altura);
    }

    // Método principal que prueba la clase (Instancia de objeto y ejecución de métodos)
    public static void main(String[] args) {
        Triangulo t = new Triangulo(5, 6, 7);
        t.areaTriangulo();
        t.alturaTriangulo();
        t.imprimirCartel();
    }
}
```

---

## Punto 3

```java
import java.util.Scanner;

class CoefBinomio {
    // Método para calcular producto de una secuencia de números
    int calculo(int x, int n) {
        int resul = 1;
        for (int i = x; i <= n; i++) {
            resul *= i;
        }
        return resul;
    }

    // Método para calcular factorial de un número
    int factorial(int num) {
        int r = 1;
        for (int i = num; i >= 1; i--) {
            r *= i;
        }
        return r;
    }

    // Método que calcula el coeficiente binomial 
    int coef(int n, int r) {
        int r1 = calculo(n - r + 1, n); // Calcula numerador del binomio
        int r2 = factorial(r);          // Calcula denominador (r!)
        return r1 / r2;
    }
}

public class TriPascal {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Scanner para leer número de filas
        System.out.print("Ingrese el número de filas para el Triángulo de Pascal: ");
        int filas = sc.nextInt();

        // Objeto de la clase CoefBinomio
        CoefBinomio objeto = new CoefBinomio();

        // Generación del Triángulo de Pascal
        for (int i = 0; i < filas; i++) {
            // Espacios para centrar los números
            for (int k = filas - i; k > 0; k--) {
                System.out.print("  ");
            }
            for (int j = 0; j <= i; j++) {
                int resul = objeto.coef(i, j); // Cálculo del coeficiente binomial
                System.out.printf("%4d", resul); // Salida formateada
            }
            System.out.println();
        }
        // Cartel de salida adicional (Literal h)
        System.out.println("Fin de la ejecución del Triángulo de Pascal.");
    }
}
```

---

## Punto 4

```java
import java.util.Scanner;

class Recursion {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Objeto de la clase FRecur
        FRecur objeto = new FRecur();

        // Leer dos números como Strings y sumarlos (Literal j y m - Uso de Scanner)
        System.out.print("Ingrese dos números para la suma: ");
        String a = sc.next();
        String b = sc.next();

        int suma = objeto.G(a, b);
        System.out.println("Suma = " + suma);

        Recursion r = new Recursion();
        System.out.println("Factorial de 5 = " + r.fact(5)); // Prueba de método recursivo

        System.out.println("Multiplicación 6 * 4 = " + objeto.multi(6, 4)); // Multiplicación recursiva

        // Cálculo de varios términos de la serie de Fibonacci
        for (int i = 0; i <= 10; i++) {
            System.out.println("Fibo(" + i + ") = " + objeto.fibo(i));
        }

        // Impresión recursiva
        System.out.print("F1 (Impresión recursiva hasta 5): ");
        objeto.F1(5);

        // Cartel de salida adicional (Literal l)
        System.out.println("\nFin de la ejecución del programa.");
    }

    // Método recursivo para calcular factorial
    int fact(int x) {
        if (x == 0) return 1;
        else return x * fact(x - 1);
    }
}

class FRecur {

    // Suma dos valores recibidos como String
    int G(String a, String b) {
        return F(a, b);
    }

    int fact(int x) {
        if (x == 0) return 1;
        else return x * fact(x - 1);
    }

    // Multiplicación recursiva
    int multi(int a, int b) {
        if (b == 0) return 0;
        else return a + multi(a, b - 1);
    }

    // Cálculo de Fibonacci recursivamente
    int fibo(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;
        return fibo(n - 1) + fibo(n - 2);
    }

    // Suma dos valores convertidos desde String a int
    int F(String a, String b) {
        return Integer.parseInt(a) + Integer.parseInt(b);
    }

    // Impresión recursiva hasta x
    void F1(int x) {
        if (x > 0) {
            F1(x - 1);
            System.out.print(x + " ");
        }
    }
}
```


