import java.util.Scanner;

class Employee {
    int employeeNumber;
    String name;
    double basicPay;
    double da;
    double hra;
    double grossSalary;

    public Employee(int employeeNumber, String name, double basicPay) {
        this.employeeNumber = employeeNumber;
        this.name = name;
        this.basicPay = basicPay;
    }

    public void calculateSalary() {
        da = 0.20 * basicPay; // DA is 20% of basic pay
        hra = 0.05 * basicPay; // HRA is 5% of basic pay
        grossSalary = basicPay + da + hra;
    }

    public void displayDetails() {
        System.out.println("Employee Number: " + employeeNumber);
        System.out.println("Employee Name: " + name);
        System.out.println("Basic Pay: " + basicPay);
        System.out.println("DA: " + da);
        System.out.println("HRA: " + hra);
        System.out.println("Gross Salary: " + grossSalary);
    }
}

public class EmployeeSalaryCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of employees: ");
        int n = scanner.nextInt();

        Employee[] employees = new Employee[n];

        for (int i = 0; i < n; i++) {
            System.out.print("Enter Employee Number for Employee " + (i + 1) + ": ");
            int empNumber = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character

            System.out.print("Enter Employee Name for Employee " + (i + 1) + ": ");
            String empName = scanner.nextLine();

            System.out.print("Enter Basic Pay for Employee " + (i + 1) + ": ");
            double basicPay = scanner.nextDouble();

            employees[i] = new Employee(empNumber, empName, basicPay);
            employees[i].calculateSalary();
        }

        for (Employee employee : employees) {
            System.out.println("\nEmployee Details:");
            employee.displayDetails();
        }

        scanner.close();
    }
}
