# Crosswords Generator in C

---

## Description

This program reads four words from the user and creates:
- Two single crosses (one vertical word intersecting with a horizontal word),
- One double cross by combining the two single crosses with a space between them.

**Rules:**
- Words must consist only of **uppercase English letters** (`A-Z`).
- Words must be up to **10 letters** long.
- Crossings occur at the **first common letter** between the vertical and horizontal words.

## How It Works

1. The user is asked to input four words.
2. The program tries to form two crosses:
    - First cross: Word 1 (vertical) and Word 2 (horizontal),
    - Second cross: Word 3 (vertical) and Word 4 (horizontal).
3. The two crosses are merged into a **double cross** with a gap of three spaces between them.
4. The final crossword is printed to the console.

If crossing is impossible (no common letters), the program informs the user.

## Compilation

Use `gcc` to compile:

```bash
gcc -o main main.c
```

### Running
```bash
./crossword
```

### Example
```bash
Enter words:SHAVO ODADJIAN JOHN DOLMAYAN
  O
  D      D
SHAVO   JOHN
  D      L
  J      M
  I      A
  A      Y
  N      A
         N
```

## Functions Overview

| Function | Description |
| :------- | :---------- |
| `create_leading_word_cross(const char* vertical, const char* horizontal, char*** cross)` | Creates a single crossword grid from two words that cross at a common letter. |
| `create_double_leading_word_cross(const char* v1, const char* h1, const char* v2, const char* h2, char*** cross1, char*** cross2, char*** double_cross)` | Merges two individual crosses into a single double crossword grid. |
| `display(char** cross)` | Prints a given crossword grid to the console, row by row. |
| `destroy(char** cross)` | Frees the dynamically allocated memory for a crossword grid. |

---

## Error Handling

- **Invalid Input:**
    - If the user inputs words containing non-uppercase English letters (A-Z), the program displays an error and exits.

- **Memory Allocation Failure:**
    - If dynamic memory allocation (malloc) fails during crossword creation, the function returns a specific error code and handles cleanup.

- **No Common Letters (Cross Failure):**
    - If two words cannot be crossed (no shared letters), the program prints an informative message indicating crossing is impossible.

- **General Robustness:**
    - All dynamically allocated memory is properly freed after use to avoid memory leaks.

## Notes

- **Maximum Allowed Word Length:**
    - Each word can have a maximum length of 10 letters, plus the null-terminator (`\0`). Words longer than 10 characters will be truncated.

- **Character Restrictions:**
    - Only uppercase English letters (A-Z) are allowed in the input words. Any other characters will result in incorrect input.
