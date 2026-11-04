# java-student-management-system 

import java.util.ArrayList;
import java.util.Scanner;

public class StudentManagementSystem {

    static class Student {
        String name;
        int mark;

        Student(String name, int mark) {
            this.name = name;
            this.mark = mark;
        }
    }

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        int choice;

        do {
            System.out.println("\n===== STUDENT MANAGEMENT SYSTEM =====");
            System.out.println("1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");

            choice = input.nextInt();
            input.nextLine();

            switch (choice) {

                case 1:
                    System.out.print("Enter student name: ");
                    String name = input.nextLine();

                    System.out.print("Enter student mark: ");
                    int mark = input.nextInt();

                    if (mark >= 0 && mark <= 100) {
                        students.add(new Student(name, mark));
                        System.out.println("Student saved successfully!");
                    } else {
                        System.out.println("Invalid mark. Enter 0 to 100.");
                    }
                    break;

                case 2:
                    System.out.println("\n===== STUDENT RECORDS =====");

                    if (students.isEmpty()) {
                        System.out.println("No students registered.");
                    } else {
                        for (Student student : students) {
                            System.out.println("Name: " + student.name);
                            System.out.println("Mark: " + student.mark);

                            if (student.mark >= 50) {
                                System.out.println("Result: Passed");
                            } else {
                                System.out.println("Result: Failed");
                            }

                            System.out.println("--------------------");
                        }
                    }
                    break;

                case 3:
                    System.out.println("Thank you for using the system!");
                    break;

                default:
                    System.out.println("Invalid choice. Try again.");
            }

        } while (choice != 3);

        input.close();
    }
}
