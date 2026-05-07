import java.util.Scanner;

public class stringmatch {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the main text: ");
        String text = sc.nextLine();

        System.out.print("Enter the pattern to find: ");
        String pattern = sc.nextLine();

        int n = text.length();
        int m = pattern.length();
        boolean found = false;
        for (int i = 0; i <= n - m; i++) {
            int j;
            for (j = 0; j < m; j++) {
                if (text.charAt(i + j) != pattern.charAt(j)) {
                    break;
                }
            }
            if (j == m) {
                System.out.println("Pattern found at index: " + i);
                found = true;
            }
        }

        if (!found) {
            System.out.println("Pattern not found in the given text.");
        }
        sc.close();
    }
}
