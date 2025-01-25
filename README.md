# LLDB Debugger Guide for macOS

## Introduction
This guide provides an overview of using the LLDB debugger on macOS. It covers compiling your code with debug symbols, basic usage, working with breakpoints, GUI navigation, handling special cases, and troubleshooting common issues.

---

## 1. Compile with Debug Symbols

To enable debugging, compile your code with the `-g` flag:

```bash
cc -Wall -Werror -Wextra -g main.c
```

For multi-file projects, ensure you add `-g` to your Makefile.

---

## 2. Basic Usage

Launch LLDB with your executable and its arguments:

```bash
lldb ./your_program <arguments>
```

### Examples:
```bash
lldb ./philo
lldb ./push_swap 13 23 4234 14
```

---

## 3. Breakpoints & Debugging

### Setting Breakpoints:
- Break at `main()`:
  ```bash
  (lldb) b main
  ```
- Break at a specific line in a file:
  ```bash
  (lldb) b file.c:42
  ```

### Running the Program:
- To start the program:
  ```bash
  (lldb) run
  ```
- To open the graphical interface:
  ```bash
  (lldb) gui
  ```

---

## 4. GUI Navigation

| Command | Action                  |
|---------|-------------------------|
| `n`     | Next line               |
| `s`     | Step into function      |
| `Tab`   | Switch focus            |
| `Esc`   | Close GUI               |
| `Ctrl+D`| Exit LLDB               |

---

## 5. Handling Special Cases

When dealing with commands that involve pipes or special characters, use one of the following methods:

### Method 1:
```bash
lldb ./a.out
(lldb) settings set target.run-args "/bin/ls" "|" "/usr/bin/wc"
(lldb) b main
(lldb) process launch
```

### Method 2:
```bash
lldb ./a.out "/bin/ls" "|" "/usr/bin/wc"
(lldb) b main
(lldb) process launch
```

---

