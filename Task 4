#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

// Function to compress input file using Run-Length Encoding (RLE)
void compressFile(const char *inputFile, const char *outputFile) {
    FILE *in = fopen(inputFile, "r");
    FILE *out = fopen(outputFile, "w");

    if (!in || !out) {
        printf("Error opening files.\n");
        exit(1);
    }

    char currentChar, prevChar;
    int count = 1;

    prevChar = fgetc(in);
    if (prevChar == EOF) {
        fclose(in);
        fclose(out);
        return;
    }

    while ((currentChar = fgetc(in)) != EOF) {
        if (currentChar == prevChar) {
            count++;
        } else {
            fprintf(out, "%d%c", count, prevChar);
            count = 1;
        }
        prevChar = currentChar;
    }

    // Write last sequence
    fprintf(out, "%d%c", count, prevChar);

    fclose(in);
    fclose(out);
    printf("Compression complete. Output written to %s\n", outputFile);
}

// Function to decompress a Run-Length Encoded file
void decompressFile(const char *inputFile, const char *outputFile) {
    FILE *in = fopen(inputFile, "r");
    FILE *out = fopen(outputFile, "w");

    if (!in || !out) {
        printf("Error opening files.\n");
        exit(1);
    }

    int count;
    char ch;

    while (fscanf(in, "%d%c", &count, &ch) == 2) {
        for (int i = 0; i < count; i++) {
            fputc(ch, out);
        }
    }

    fclose(in);
    fclose(out);
    printf("Decompression complete. Output written to %s\n", outputFile);
}

int main(int argc, char *argv[]) {
    if (argc != 4) {
        printf("Usage: %s <compress|decompress> <input_file> <output_file>\n", argv[0]);
        return 1;
    }

    if (strcmp(argv[1], "compress") == 0) {
        compressFile(argv[2], argv[3]);
    } else if (strcmp(argv[1], "decompress") == 0) {
        decompressFile(argv[2], argv[3]);
    } else {
        printf("Invalid operation. Use 'compress' or 'decompress'.\n");
        return 1;
    }

    return 0;
}
