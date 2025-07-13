import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int totalScore = 0;
        int rounds = 3; // Number of rounds

        System.out.println("🎯 Welcome to the Number Guessing Game!");
        System.out.println("You have to guess a number between 1 and 100.");
        System.out.println("You have 7 attempts per round.\n");

        for (int round = 1; round <= rounds; round++) {
            int numberToGuess = random.nextInt(100) + 1;
            int attempts = 7;
            int pointsEarned = 0;

            System.out.println("🔁 Round " + round + " starts now!");

            for (int i = 1; i <= attempts; i++) {
                System.out.print("Attempt " + i + " - Enter your guess: ");
                int userGuess;

                // Validate input
                if (scanner.hasNextInt()) {
                    userGuess = scanner.nextInt();
                } else {
            System.out.println("⚠ Please enter a valid number!");
                    scanner.next(); // Clear invalid input
                    i--; // Don't count invalid input as attempt
                    continue;
                }

                if (userGuess == numberToGuess) {
                    System.out.println("🎉 Correct! You guessed the number in " + i + " attempt(s).");
                    pointsEarned = 100 - (i - 1) * 10; // Fewer attempts = higher score
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("📉 Too low!");
                } else {
                    System.out.println("📈 Too high!");
                }

                if (i == attempts) {
                    System.out.println("❌ You've used all attempts. The correct number was: " + numberToGuess);
                }
            }

            System.out.println("✅ Points this round: " + pointsEarned);
            totalScore += pointsEarned;
            System.out.println("-----------------------------\n");
        }

        System.out.println("🏁 Game Over!");
        System.out.println("🎯 Your Total Score after " + rounds + " round(s): " + totalScore);
        scanner.close();
    }
}# NumberGuessingGame
