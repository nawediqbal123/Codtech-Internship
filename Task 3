#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX_WORD_LEN 100

const char *keywords[] = {
    "auto", "break", "case", "char", "const", "continue", "default", "do", "double",
    "else", "enum", "extern", "float", "for", "goto", "if", "int", "long",
    "register", "return", "short", "signed", "sizeof", "static", "struct", "switch",
    "typedef", "union", "unsigned", "void", "volatile", "while"
};

const char operators[] = "+-*/=<>!&|%";

int isKeyword(const char *word) {
    for (int i = 0; i < sizeof(keywords) / sizeof(keywords[0]); i++) {
        if (strcmp(keywords[i], word) == 0)
            return 1;
    }
    return 0;
}

int isOperator(char ch) {
    for (int i = 0; i < strlen(operators); i++) {
        if (ch == operators[i])
            return 1;
    }
    return 0;
}

void analyze(FILE *fp) {
    char ch;
    char word[MAX_WORD_LEN];
    int index = 0;

    while ((ch = fgetc(fp)) != EOF) {
        // Word separator
        if (isalnum(ch) || ch == '_') {
            word[index++] = ch;
        } else {
            if (index != 0) {
                word[index] = '\0';
                if (isKeyword(word))
                    printf("Keyword\t\t: %s\n", word);
                else
                    printf("Identifier\t: %s\n", word);
                index = 0;
            }

            // Operator check
            if (isOperator(ch)) {
                printf("Operator\t: %c\n", ch);
            }
        }
    }

    // For the last word if file doesn't end with space
    if (index != 0) {
        word[index] = '\0';
        if (isKeyword(word))
            printf("Keyword\t\t: %s\n", word);
        else
            printf("Identifier\t: %s\n", word);
    }
}

int main() {
    FILE *fp = fopen("input.txt", "r");

    if (fp == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    printf("Lexical Analysis Output:\n\n");
    analyze(fp);

    fclose(fp);
    return 0;
}
