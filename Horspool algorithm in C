#include <stdio.h>
#include <string.h>
int shiftTable[256];
void shiftTableFunction(char pattern[]) {
    int m = strlen(pattern);
    for (int i = 0; i < 256; i++)
        shiftTable[i] = m;
    for (int j = 0; j < m - 1; j++)
        shiftTable[(int)pattern[j]] = m - 1 - j;
    printf("\n--- Shift Table ---\n");
    for (int j = 0; j < m - 1; j++) {
        printf("%c: %d  ", pattern[j], shiftTable[(int)pattern[j]]);
    }
    printf("Others: %d\n\n", m);
}
int horspool(char text[], char pattern[]) {
    int n = strlen(text);
    int m = strlen(pattern);
    shiftTableFunction(pattern);
    int i = m - 1;
    int step = 1;
    while (i < n) {
        printf("Step %d:\n", step++);
        printf("%s\n", text);
        printf("%*s\n", i + 1, pattern);
        int k = 0;
        while (k < m && pattern[m - 1 - k] == text[i - k])
            k++;
        if (k == m) {
            printf("Result: Match found!\n");
            return i - m + 1;
        } else {
            int shift = shiftTable[(int)text[i]];
            printf("Mismatch! Shifting by: %d\n\n", shift);
            i = i + shift;
        }
    }
    return -1;
}
int main() {
    char text[100], pattern[100];
    printf("Enter text: ");
    scanf("%s", text);
    printf("Enter pattern: ");
    scanf("%s", pattern);
    int pos = horspool(text, pattern);
    if (pos == -1)
        printf("\nPattern not found\n");
    else
        printf("\nPattern found at position: %d\n", pos);
    return 0;
}
