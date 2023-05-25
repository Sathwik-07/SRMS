# StudentReportManagementSystem
Welcome to my Student Report Management System 


This "Student Report Management System" project is a Java program that allows users to manage and generate reports for student information. Here's an explanation of the code:

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

That's an overview of the Student Report Management System project. It allows users to manage student information, search for students, update their details, delete students, and generate reports.
Certainly! In the provided code, exception handling mechanisms are used to handle invalid inputs in various scenarios. Here's how the code handles exceptions for invalid inputs:

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
