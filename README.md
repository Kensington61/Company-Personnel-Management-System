import java.util.ArrayList;
import java.util.Scanner;

class Employee {
    private String name;
    private int age;
    private String position;

    public Employee(String name, int age, String position) {
        this.name = name;
        this.age = age;
        this.position = position;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public String getPosition() {
        return position;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Age: " + age + ", Position: " + position;
    }
}

class EmployeeManager {
    private ArrayList<Employee> employees;

    public EmployeeManager() {
        this.employees = new ArrayList<>();
    }

    public void addEmployee(Employee employee) {
        employees.add(employee);
    }

    public Employee findEmployee(String name) {
        for (Employee employee : employees) {
            if (employee.getName().equalsIgnoreCase(name)) {
                return employee;
            }
        }
        return null;
    }

    public void displayEmployees() {
        for (Employee employee : employees) {
            System.out.println(employee);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        EmployeeManager employeeManager = new EmployeeManager();

        System.out.println("Company Personnel Management System");
        System.out.println("1. Add Employee");
        System.out.println("2. Find Employee");
        System.out.println("3. Display All Employees");
        System.out.println("4. Exit");

        int choice;
        do {
            System.out.print("\nEnter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // consume the newline character

            switch (choice) {
                case 1:
                    System.out.print("Enter employee name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter employee age: ");
                    int age = scanner.nextInt();
                    scanner.nextLine(); // consume the newline character
                    System.out.print("Enter employee position: ");
                    String position = scanner.nextLine();
                    Employee employee = new Employee(name, age, position);
                    employeeManager.addEmployee(employee);
                    System.out.println("Employee added successfully.");
                    break;
                case 2:
                    System.out.print("Enter employee name to search: ");
                    String searchName = scanner.nextLine();
                    Employee foundEmployee = employeeManager.findEmployee(searchName);
                    if (foundEmployee != null) {
                        System.out.println("Employee found:");
                        System.out.println(foundEmployee);
                    } else {
                        System.out.println("Employee not found.");
                    }
                    break;
                case 3:
                    System.out.println("All Employees:");
                    employeeManager.displayEmployees();
                    break;
                case 4:
                    System.out.println("Exiting the program.");
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        } while (choice != 4);

        scanner.close();
    }
}
