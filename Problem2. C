#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>

#define BUFFER_SIZE 100

int main() {
    int fd;         // File descriptor
    ssize_t n;      // Number of bytes read/written
    char buffer[BUFFER_SIZE];

    // 1. Create a new file (or open if exists) with read/write permissions
    fd = open("example.txt", O_CREAT | O_RDWR, 0644);
    if (fd == -1) {
        perror("Error opening file");
        exit(EXIT_FAILURE);
    }
    printf("File opened/created successfully.\n");

    // 2. Write data to the file
    const char *write_data = "Hello, Unix system calls and C libraries!\n";
    n = write(fd, write_data, strlen(write_data));
    if (n == -1) {
        perror("Error writing to file");
        close(fd);
        exit(EXIT_FAILURE);
    }
    printf("%ld bytes written to file.\n", n);

    // 3. Use lseek to move the file pointer to the beginning
    if (lseek(fd, 0, SEEK_SET) == -1) {
        perror("Error using lseek");
        close(fd);
        exit(EXIT_FAILURE);
    }
    printf("File pointer repositioned to the beginning.\n");

    // 4. Read data from the file
    n = read(fd, buffer, BUFFER_SIZE - 1); // -1 to leave space for null terminator
    if (n == -1) {
        perror("Error reading from file");
        close(fd);
        exit(EXIT_FAILURE);
    }
    buffer[n] = '\0'; // Null-terminate the string
    printf("Data read from file: \n%s", buffer);

    // 5. Truncate the file
    if (ftruncate(fd, 10) == -1) {
        perror("Error truncating file");
        close(fd);
        exit(EXIT_FAILURE);
    }
    printf("File truncated to 10 bytes.\n");

    // 6. Close the file
    if (close(fd) == -1) {
        perror("Error closing file");
        exit(EXIT_FAILURE);
    }
    printf("File closed successfully.\n");

    return 0;
}
