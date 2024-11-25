# Codetechtask-2

import java.util.ArrayList;

import java.util.List;

import java.util.Scanner;



public class StudentGradeTracker {

    private List<Double> grades;



    public StudentGradeTracker() {

        grades = new ArrayList<>();

    }



    public void addGrade(double grade) {

        grades.add(grade);

    }



    public double calculateAverage() {

        double sum = 0;

        for (double grade : grades) {

            sum += grade;

        }

        return grades.isEmpty() ? 0 : sum / grades.size();

    }



    public String getLetterGrade(double average) {

        if (average >= 90) {

            return "A";

        } else if (average >= 80) {

            return "B";

        } else if (average >= 70) {

            return "C";

        } else if (average >= 60) {

            return "D";

        } else {

            return "F";

        }

    }



    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        StudentGradeTracker tracker = new StudentGradeTracker();



        System.out.println("Welcome to the Student Grade Tracker!");

        String choice;



        do {

            System.out.print("Enter a grade (0-100) or type 'done' to finish: ");

            choice = scanner.nextLine();



            if (choice.equalsIgnoreCase("done")) {

                break;

            }



            try {

                double grade = Double.parseDouble(choice);

                if (grade < 0 || grade > 100) {

                    System.out.println("Please enter a valid grade between 0 and 100.");

                } else {

                    tracker.addGrade(grade);

                    System.out.println("Grade added: " + grade);

                }

            } catch (NumberFormatException e) {

                System.out.println("Invalid input. Please enter a numeric grade or 'done'.");

            }

        } while (true);



        double average = tracker.calculateAverage();

        String letterGrade = tracker.getLetterGrade(average);



        System.out.printf("Average Grade: %.2f\n", average);

        System.out.println("Letter Grade: " + letterGrade);

        scanner.close();

    }

}
