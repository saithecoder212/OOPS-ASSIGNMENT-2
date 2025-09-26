# OOPS-ASSIGNMENT-2
// Save this file as MainExam.java

// ===== Package Declaration =====
package onlineexam;

// ===== Base Class =====
class User {
    String username;
    String password;

    User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public boolean login(String u, String p) {
        return username.equals(u) && password.equals(p);
    }
}

// ===== Inheritance =====
class Student extends User {
    int score;

    Student(String username, String password) {
        super(username, password);
        this.score = 0;
    }

    public void takeExam() {
        System.out.println("\n--- Online Exam Started ---");

        String[] questions = {
            "1. Which keyword is used to inherit a class in Java?",
            "2. Which exception occurs when dividing by zero?",
            "3. Which OOP concept represents real-world objects?"
        };

        String[][] options = {
            {"a) this", "b) super", "c) extends", "d) implements"},
            {"a) NullPointerException", "b) ArithmeticException", "c) IOException", "d) RuntimeException"},
            {"a) Polymorphism", "b) Inheritance", "c) Encapsulation", "d) Abstraction"}
        };

        char[] answers = {'c', 'b', 'c'}; // correct answers

        java.util.Scanner sc = new java.util.Scanner(System.in);

        try {
            for (int i = 0; i < questions.length; i++) {
                System.out.println("\n" + questions[i]);
                for (String opt : options[i]) {
                    System.out.println(opt);
                }
                System.out.print("Your answer (a/b/c/d): ");
                char ans = sc.next().charAt(0);

                if (ans == answers[i]) {
                    score += 5;
                }
            }
        } catch (Exception e) {
            System.out.println("Error during exam: " + e.getMessage());
        }
    }

    public void showResult() {
        System.out.println("\n--- Exam Completed ---");
        System.out.println("Student: " + username);
        System.out.println("Score: " + score);
        if (score >= 10)
            System.out.println("Result: PASS 🎉");
        else
            System.out.println("Result: FAIL ❌");
    }
}

// ===== Main Class =====
public class MainExam {
    public static void main(String[] args) {
        java.util.Scanner sc = new java.util.Scanner(System.in);

        // Creating student object
        Student st = new Student("selva", "1234");

        System.out.println("=== Online Exam System ===");
        System.out.print("Enter Username: ");
        String u = sc.nextLine();
        System.out.print("Enter Password: ");
        String p = sc.nextLine();

        if (st.login(u, p)) {
            st.takeExam();
            st.showResult();
        } else {
            System.out.println("Login Failed! Invalid credentials.");
        }
    }
}
