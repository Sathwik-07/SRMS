The "Student Report Management System" project is a Java program that allows users to manage and generate reports for student information. Here's an explanation of the code:

The program uses the Java Scanner class to read user input from the console.

The main method serves as the entry point of the program. It presents a menu of options to the user and repeatedly prompts for input until the user chooses to exit.

The program maintains a list of Student objects in the "students" ArrayList. Each Student object represents an individual student's information.

The available menu options are:
a. Add Student: Allows the user to input details for a new student and add them to the list.
b. Display Student Information: Prompts the user to enter a student ID or name and displays the corresponding student's information if found.
c. Search Students: Prompts the user to enter a search term and displays a list of students matching the search term.
d. Update Student Information: Prompts the user to enter a student ID and allows them to update the student's name, age, grade, or marks for each subject.
e. Delete Student: Prompts the user to enter a student ID and removes the student from the list if found.
f. Generate Reports: Generates a report for each student in the list, displaying their information and marks.
g. Exit: Terminates the program.

The addStudent method prompts the user to input details for a new student, validates the input, and creates a Student object with the provided information. The Student object is then added to the students list.

The displayStudentInformation method prompts the user to enter a student ID or name and searches the students list for a match. If found, it displays the student's information.

The searchStudents method prompts the user to enter a search term and searches the students list for students whose ID or name contains the search term. It displays a list of matching students if found.

The updateStudentInformation method prompts the user to enter a student ID and searches the students list for a match. If found, it allows the user to choose which information to update (name, age, grade, or marks) and performs the corresponding update.

The deleteStudent method prompts the user to enter a student ID and searches the students list for a match. If found, it removes the student from the list.


The generateReports method checks if the students list is empty. If not, it generates a report for each student, displaying their information and marks.

The Student class defines the attributes and methods for a student. Each student has a unique student ID, name, age, grade, and a map of subject marks.

The Student class includes getters and setters for accessing and modifying the student's attributes.

That's an overview of the Student Report Management System project. It allows users to manage student information, search for students, update their details, delete students, and generate reports.Certainly! In the provided code, exception handling mechanisms are used to handle invalid inputs in various scenarios. Here's how the code handles exceptions for invalid inputs:

In the addStudent method:

When inputting the student ID, if the user enters a non-numeric value, an InputMismatchException is caught, and the program displays an error message and consumes the invalid input.
When inputting the age, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
When inputting the number of subjects, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
When inputting subject marks, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
In the updateStudentInformation method:

When inputting the student ID, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
When inputting the age, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
When inputting subject marks for updating, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
In the deleteStudent method:

When inputting the student ID, if the user enters a non-numeric value, a NumberFormatException is caught, and the program displays an error message and consumes the invalid input.
These exception handling blocks ensure that the program gracefully handles invalid input by displaying appropriate error messages and consuming the invalid input, allowing the program to continue functioning without crashing.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import java.util.InputMismatchException;

import java.util.Scanner;

public class StudentReportManagementSystem {
    private static List<Student> students = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("=========================================");
            System.out.println("Student Report Management System");
            System.out.println("=========================================");
            System.out.println("1. Add Student");
            System.out.println("2. Display Student Information");
            System.out.println("3. Search Students");
            System.out.println("4. Update Student Information");
            System.out.println("5. Delete Student");
            System.out.println("6. Generate Reports");
            System.out.println("7. Exit");
            System.out.println("=========================================");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addStudent(scanner);
                    break;
                case 2:
                    displayStudentInformation(scanner);
                    break;
                case 3:
                    searchStudents(scanner);
                    break;
                case 4:
                    updateStudentInformation(scanner);
                    break;
                case 5:
                    deleteStudent(scanner);
                    break;
                case 6:
                    generateReports();
                    break;
                case 7:
                    System.out.println("Exiting... Thank you!");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
                    break;
            }
        } while (choice != 7);

        scanner.close();
    }

    private static void addStudent(Scanner scanner) {
        System.out.println("Enter student details:");
        int studentId = 0;
        String name = "";
        int age = 0;
        String grade = "";
        int numSubjects = 0;
        try {
            System.out.print("Student ID: ");
            studentId = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
        } catch (InputMismatchException e) {
            System.out.println("Invalid student ID. Please enter a numeric value.");
            scanner.nextLine(); // Consume invalid input
            return;
        }

        System.out.print("Name: ");
        name = scanner.nextLine();

        try {
            System.out.print("Age: ");
            age = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
        } catch (NumberFormatException e) {
            System.out.println("Invalid age. Please enter a numeric value.");
            scanner.nextLine(); // Consume invalid input
            return;
        }

        System.out.print("Grade: ");
        grade = scanner.nextLine();

        try {
            System.out.print("Number of subjects: ");
            numSubjects = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
        } catch (NumberFormatException e) {
            System.out.println("Invalid number of subjects. Please enter a numeric value.");
            scanner.nextLine(); // Consume invalid input
            return;
        }

        Map<String, Integer> marks = new HashMap<>();
        for (int i = 1; i <= numSubjects; i++) {
            String subjectName;
            while (true) {
                System.out.print("Subject " + i + " Name: ");
                subjectName = scanner.nextLine();
                if (subjectName.matches("[a-zA-Z]+")) {
                    break;
                } else {
                    System.out.println("Invalid subject name. Please enter only alphabets.");
                }
            }
            System.out.print("Subject " + i + " Marks: ");
            int subjectMarks = 0;
            try {
                subjectMarks = scanner.nextInt();
                scanner.nextLine(); // Consume newline character
            } catch (NumberFormatException e) {
                System.out.println("Invalid subject marks. Please enter a numeric value.");
                scanner.nextLine(); // Consume invalid input
                return;
            }
            marks.put(subjectName, subjectMarks);
        }

        Student student = new Student(studentId, name, age, grade, marks);
        students.add(student);
        System.out.println("Student added successfully.");
    }

    private static void displayStudentInformation(Scanner scanner) {
        System.out.print("Enter student ID or name: ");
        String searchTerm = scanner.nextLine();

        for (Student student : students) {
            if (String.valueOf(student.getStudentId()).equals(searchTerm)
                    || student.getName().equalsIgnoreCase(searchTerm)) {
                System.out.println("Student Information:");
                System.out.println("Student ID: " + student.getStudentId());
                System.out.println("Name: " + student.getName());
                System.out.println("Age: " + student.getAge());
                System.out.println("Grade: " + student.getGrade());
                System.out.println("Marks:");
                for (Map.Entry<String, Integer> entry : student.getMarks().entrySet()) {
                    System.out.println(entry.getKey() + ": " + entry.getValue());
                }
                return;
            }
        }

        System.out.println("No student found with the given ID or name.");
    }

    private static void searchStudents(Scanner scanner) {
        System.out.print("Enter search term: ");
        String searchTerm = scanner.nextLine();

        List<Student> searchResults = new ArrayList<>();

        for (Student student : students) {
            if (String.valueOf(student.getStudentId()).equals(searchTerm) || student.getName().contains(searchTerm)) {
                searchResults.add(student);
            }
        }

        if (!searchResults.isEmpty()) {
            System.out.println("Search Results:");
            for (Student student : searchResults) {
                System.out.println("Student ID: " + student.getStudentId());
                System.out.println("Name: " + student.getName());
                System.out.println("Age: " + student.getAge());
                System.out.println("Grade: " + student.getGrade());
                System.out.println("---------------------------");
            }
        } else {
            System.out.println("No students found matching the search term.");
        }
    }

    private static void updateStudentInformation(Scanner scanner) {
        System.out.print("Enter student ID: ");
        int studentId = 0;
        try {
            studentId = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
        } catch (NumberFormatException e) {
            System.out.println("Invalid student ID. Please enter a numeric value.");
            scanner.nextLine(); // Consume invalid input
            return;
        }

        for (Student student : students) {
            if (student.getStudentId() == studentId) {
                System.out.println("Enter updated student details:");
                System.out.println("1. Name");
                System.out.println("2. Age");
                System.out.println("3. Grade");
                System.out.println("4. Marks");
                System.out.print("Enter your choice: ");
                int choice = scanner.nextInt();
                scanner.nextLine(); // Consume newline character

                switch (choice) {
                    case 1:
                        System.out.print("Name: ");
                        String name = scanner.nextLine();
                        student.setName(name);
                        System.out.println("Name updated successfully.");
                        break;
                    case 2:
                        System.out.print("Age: ");
                        int age = 0;
                        try {
                            age = scanner.nextInt();
                            scanner.nextLine(); // Consume newline character
                        } catch (NumberFormatException e) {
                            System.out.println("Invalid age. Please enter a numeric value.");
                            scanner.nextLine(); // Consume invalid input
                            return;
                        }
                        student.setAge(age);
                        System.out.println("Age updated successfully.");
                        break;
                    case 3:
                        System.out.print("Grade: ");
                        String grade = scanner.nextLine();
                        student.setGrade(grade);
                        System.out.println("Grade updated successfully.");
                        break;
                    case 4:
                        System.out.println("Enter updated marks for each subject:");
                        Map<String, Integer> marks = new HashMap<>();
                        for (Map.Entry<String, Integer> entry : student.getMarks().entrySet()) {
                            System.out.print(entry.getKey() + ": ");
                            int subjectMarks = 0;
                            try {
                                subjectMarks = scanner.nextInt();
                                scanner.nextLine(); // Consume newline character
                            } catch (NumberFormatException e) {
                                System.out.println("Invalid subject marks. Please enter a numeric value.");
                                scanner.nextLine(); // Consume invalid input
                                return;
                            }
                            marks.put(entry.getKey(), subjectMarks);
                        }
                        student.setMarks(marks);
                        System.out.println("Marks updated successfully.");
                        break;
                    default:
                        System.out.println("Invalid choice. No fields updated.");
                        break;
                }

                return;
            }
        }

        System.out.println("No student found with the given ID.");
    }

    private static void deleteStudent(Scanner scanner) {
        System.out.print("Enter student ID: ");
        int studentId = 0;
        try {
            studentId = scanner.nextInt();
            scanner.nextLine(); // Consume newline character
        } catch (NumberFormatException e) {
            System.out.println("Invalid student ID. Please enter a numeric value.");
            scanner.nextLine(); // Consume invalid input
            return;
        }

        for (int i = 0; i < students.size(); i++) {
            Student student = students.get(i);
            if (student.getStudentId() == studentId) {
                students.remove(i);
                System.out.println("Student deleted successfully.");
                return;
            }
        }

        System.out.println("No student found with the given ID.");
    }

    private static void generateReports() {
        if (students.isEmpty()) {
            System.out.println("No students found. Generate reports later.");
            return;
        }

        System.out.println("Generating reports...");

        for (Student student : students) {
            System.out.println("=========================================");
            System.out.println("Student Report");
            System.out.println("=========================================");
            System.out.println("Student ID: " + student.getStudentId());
            System.out.println("Name: " + student.getName());
            System.out.println("Age: " + student.getAge());
            System.out.println("Grade: " + student.getGrade());
            System.out.println("Marks:");

            for (Map.Entry<String, Integer> entry : student.getMarks().entrySet()) {
                System.out.println(entry.getKey() + ": " + entry.getValue());
            }

            System.out.println("=========================================");
        }

        System.out.println("Reports generated successfully.");
    }

}

class Student {
    private int studentId;
    private String name;
    private int age;
    private String grade;
    private Map<String, Integer> marks;

    public Student(int studentId, String name, int age, String grade, Map<String, Integer> marks) {
        this.studentId = studentId;
        this.name = name;
        this.age = age;
        this.grade = grade;
        this.marks = marks;
    }

    // Getters and Setters

    public int getStudentId() {
        return studentId;
    }

    public void setStudentId(int studentId) {
        this.studentId = studentId;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getGrade() {
        return grade;
    }

    public void setGrade(String grade) {
        this.grade = grade;
    }

    public Map<String, Integer> getMarks() {
        return marks;
    }

    public void setMarks(Map<String, Integer> marks) {
        this.marks = marks;
    }
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
