import java.util.Scanner;

public class Main {
    static int count = 0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int N = scanner.nextInt();
        int M = scanner.nextInt();

        int[] dp = new int[N + 1];
        for (int i = 0; i <= N; i++) {
            dp[i] = -1;
        }

        printPaths(N, M, "");
        System.out.println();
        System.out.println(countPaths(N, M, dp));
    }

    static int countPaths(int N, int M, int[] dp) {
        if (N == 0) {
            return 1;
        }
        if (dp[N] != -1) {
            return dp[N];
        }
        int paths = 0;
        for (int i = 1; i <= M; i++) {
            if (N - i >= 0) {
                paths += countPaths(N - i, M, dp);
            }
        }
        dp[N] = paths;
        return paths;
    }

    static void printPaths(int N, int M, String path) {
        if (N == 0) {
            System.out.print(path + " ");
            return;
        }
        for (int i = 1; i <= M; i++) {
            if (N - i >= 0) {
                printPaths(N - i, M, path + i);
            }
        }
    }
}
