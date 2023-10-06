import java.util.Scanner;

public class HangmanGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        String[] words = {"java", "programming", "hangman", "computer", "developer"};
        String wordToGuess = words[(int) (Math.random() * words.length)];
        char[] guessedWord = new char[wordToGuess.length()];
        
        for (int i = 0; i < guessedWord.length; i++) {
            guessedWord[i] = '_';
        }
        
        int attempts = 6; // Number of attempts allowed
        
        System.out.println("Welcome to Hangman!");
        
        while (attempts > 0) {
            System.out.println("\nWord to guess: " + String.valueOf(guessedWord));
            System.out.println("Attempts left: " + attempts);
            System.out.print("Guess a letter: ");
            char guess = scanner.next().charAt(0);
            
            boolean correctGuess = false;
            for (int i = 0; i < wordToGuess.length(); i++) {
                if (wordToGuess.charAt(i) == guess) {
                    guessedWord[i] = guess;
                    correctGuess = true;
                }
            }
            
            if (!correctGuess) {
                System.out.println("Incorrect guess!");
                attempts--;
            }
            
            if (String.valueOf(guessedWord).equals(wordToGuess)) {
                System.out.println("\nCongratulations! You guessed the word: " + wordToGuess);
                break;
            }
        }
        
        if (attempts == 0) {
            System.out.println("\nGame over! The word was: " + wordToGuess);
        }
        
        scanner.close();
    }
}
