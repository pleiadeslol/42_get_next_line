
# Get Next Line - Reading a Line Made Simple

The **Get Next Line** project involves creating a function that reads a line from a file descriptor. This essential utility is designed to help manage input efficiently, one line at a time, even with varying buffer sizes and multiple file descriptors.

## 🚀 Features

### Mandatory Part
- Function Prototype: 
  ```c
  char *get_next_line(int fd);
  ```
- **Functionality:**
  - Reads a line (including the newline character, if present) from the file descriptor `fd`.
  - Returns `NULL` if there's nothing else to read or if an error occurs.
- **Specifications:**
  - Works with any valid file descriptor (e.g., regular files, standard input).
  - Handles lines of any length with efficient memory usage.
  - Dynamically allocates memory for each line read using `malloc`.

### Bonus Part
- **Enhanced Features:**
  - Manages multiple file descriptors simultaneously:
    - Allows reading from different file descriptors without losing track of the read state.
  - Utilizes only one static variable per file descriptor.
- **Additional Files for Bonus:**
  - `get_next_line_bonus.c`
  - `get_next_line_bonus.h`
  - `get_next_line_utils_bonus.c`

## 🛠️ Technical Details
- **External Functions Used:** `read`, `malloc`, `free`
- **Forbidden:**
  - Global variables.
  - Functions like `lseek()` and libraries such as `libft`.
- **Buffer Size:** The buffer size is defined using the compiler flag `-D BUFFER_SIZE=n` and can be adjusted for testing.

## 📂 Files and Structure
- **Mandatory Files:**
  - `get_next_line.c` – Core implementation.
  - `get_next_line_utils.c` – Helper functions.
  - `get_next_line.h` – Header file with function prototypes.
- **Bonus Files:**
  - `get_next_line_bonus.c` – Extended implementation for multiple file descriptors.
  - `get_next_line_utils_bonus.c` – Helper functions for the bonus.
  - `get_next_line_bonus.h` – Header file for the bonus.
- **Makefile:** Includes rules for `all`, `clean`, `fclean`, `re`, and `bonus`.

## 🔧 How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/get_next_line.git
   cd get_next_line
   ```
2. Compile the project with a buffer size:
   ```bash
   make
   ```
   or for the bonus:
   ```bash
   make bonus
   ```
3. Use the `get_next_line` function in your program:
   ```c
   #include "get_next_line.h"

   int main() {
       int fd = open("example.txt", O_RDONLY);
       char *line;

       while ((line = get_next_line(fd)) != NULL) {
           printf("%s", line);
           free(line);
       }
       close(fd);
       return 0;
   }
   ```
4. Compile your program with the library:
   ```bash
   gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 your_program.c get_next_line.c get_next_line_utils.c -o your_program
   ```
