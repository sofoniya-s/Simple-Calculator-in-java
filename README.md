# Simple-Calculator-in-java
BASIC JAVA PROJECT
import java.util.Scanner;

/**
 * Student Grade Calculator
 * A simple program that calculates student grades based on input scores.
 */
public class StudentGradeCalculator {

    // Convert an average score into a letter grade
    static String getGrade(double average) {
        if (average >= 90) return "A";
        else if (average >= 80) return "B";
        else if (average >= 70) return "C";
        else if (average >= 60) return "D";
        else return "F";
    }

    // Keep asking until the user enters a valid number in the given range
    static double readScore(Scanner scanner, String prompt) {
        while (true) {
            System.out.print(prompt);
            String input = scanner.nextLine().trim();
            try {
                double value = Double.parseDouble(input);
                if (value >= 0 && value <= 100) {
                    return value;
                }
                System.out.println("  Score must be between 0 and 100.");
            } catch (NumberFormatException e) {
                System.out.println("  Please enter a valid number.");
            }
        }
    }

    static int readPositiveInt(Scanner scanner, String prompt) {
        while (true) {
            System.out.print(prompt);
            String input = scanner.nextLine().trim();
            try {
                int value = Integer.parseInt(input);
                if (value > 0) {
                    return value;
                }
                System.out.println("  Enter a number greater than 0.");
            } catch (NumberFormatException e) {
                System.out.println("  Please enter a whole number.");
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("=== Student Grade Calculator ===");
        System.out.println("Calculates student grades based on input scores.\n");

        System.out.print("Student name: ");
        String name = scanner.nextLine().trim();

        int subjects = readPositiveInt(scanner, "Number of subjects: ");

        double[] scores = new double[subjects];
        double total = 0;

        for (int i = 0; i < subjects; i++) {
            scores[i] = readScore(scanner, "Score for subject " + (i + 1) + " (0-100): ");
            total += scores[i];
        }

        double average = total / subjects;
        String grade = getGrade(average);

        System.out.println("\n--- Result ---");
        System.out.println("Student : " + name);
        System.out.println("Total   : " + String.format("%.2f", total));
        System.out.println("Average : " + String.format("%.2f", average));
        System.out.println("Grade   : " + grade);

        scanner.close();
    }
}
