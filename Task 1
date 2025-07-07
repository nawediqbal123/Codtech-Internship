#include <stdio.h>
#include <stdlib.h>

void createAndWriteFile(const char *filename)
{
    FILE *fp = fopen(filename, "w"); //"w" creates or overwrites the file
    if(fp == NULL)
    {
        perror("Error creating file");
        return;
    }
    fprintf(fp, "this is the initial content of the file. \n");
    fclose(fp);
    printf("file created and written successfully. \n");
}

void readfile(const char *filename)
{
    FILE *fp = fopen(filename, "r");
    if (fp == NULL)
    {
        perror("Error reading file");
        return;
    }
    char ch;
    printf("Reading file content:\n");
    while ((ch = fgetc(fp)) != EOF)
    {
        putchar(ch);
    }
    
    fclose(fp);
}

void appendToFile(const char *filename)
{
    FILE *fp = fopen(filename, "a"); // "a" for append
    if (fp == NULL)
    {
        perror("Error appending to file");
        return;
    }
    
    fprintf(fp, "This line is appended to the file. \n");
    fclose(fp);
    printf("Data appended successully. \n");
}

int main()
{
    const char *filename = "example.txt";

    //1. Create and write to file
    createAndWriteFile(filename);

    //2. Read file content
    readfile(filename);

    //3. Append to file
    appendToFile(filename);

    //4. Read again to show changes
    readfile(filename);

    return 0;
}
