import java.util.Scanner;

public class FolhaDePagamento {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Solicita o valor da hora e a quantidade de horas trabalhadas
        System.out.print("Digite o valor da hora: R$ ");
        double valorHora = input.nextDouble();

        System.out.print("Digite a quantidade de horas trabalhadas no mês: ");
        int horasTrabalhadas = input.nextInt();

        double salarioBruto = valorHora * horasTrabalhadas;
        double descontoIR = 0.0;

        if (salarioBruto <= 900.0) {
            descontoIR = 0.0;
        } else if (salarioBruto <= 1500.0) {
            descontoIR = 5;
        } else if (salarioBruto <= 2500.0) {
            descontoIR = 10;
        } else {
            descontoIR = 20;
        }

        double descontoINSS = (salarioBruto * 10) / 100;
        double descontoSindicato = (salarioBruto * 3) / 100;
        double fgts = (salarioBruto * 11) / 100;
        double totalDescontos = descontoIR + descontoINSS + descontoSindicato;
        double salarioLiquido = salarioBruto - totalDescontos;

        // Exibe os resultados
        System.out.println("Salário bruto: R$ " + salarioBruto);
        System.out.println("(-) IR (" + descontoIR + "%): R$ " + (salarioBruto * descontoIR / 100));
        System.out.println("(-) INSS (10%): R$ " + descontoINSS);
        System.out.println("FGTS (11%): R$ " + fgts);
        System.out.println("Total de descontos: R$ " + totalDescontos);
        System.out.println("Salário Líquido: R$ " + salarioLiquido);
    }
}
