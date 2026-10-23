# 9618 Code Playground

A free, in-browser playground for **Cambridge International AS & A Level Computer Science (9618)**. Students can write and run **Cambridge-style pseudocode** and **Python**, step through a program one line at a time, and watch the **trace table** fill itself in.

The whole playground is a single HTML file. There is no install, no account and no server: open it in a browser, or host it on GitHub Pages.

---

## Features

- **Two languages in one page.** Switch between Pseudocode (for Paper 2) and Python (for Paper 4) with one click. Each language keeps its own code.
- **Run, Step and Stop.**
  - **Run** executes the whole program.
  - **Step** pauses before each line and highlights the line that runs next. You can switch between stepping and running at any point with **Continue**.
  - **Speed** can be set to instant, fast or slow. At fast and slow, each line is highlighted as it runs.
  - **Stop** ends a program at any time, including one stuck in an endless loop.
- **Automatic trace table.** One column per variable and a new row each time a value changes, with output in the last column, laid out like a trace table in an exam. In Python, variables inside a function are marked *(local)*.
- **Variables panel.** Shows every variable's type, current value and scope while the program is paused or after it finishes.
- **Console with input.** `INPUT` and `input()` open a box in the console, so programs can ask the user for values.
- **Friendly error messages.** Errors explain what went wrong in plain English, suggest a fix, and highlight the line. For example:
  - `Total = 0` → *Use ← (or type <-) for assignment. = is only for comparing values.*
  - `IF X > 3` with no `THEN` → *Expected THEN after the IF condition.*
  - `if x > 3` with no colon → *SyntaxError: expected ':'*
  - `"Total: " + 5.5` → *TypeError: can only concatenate str (not "float") to str*, with a hint to use `str(…)`
- **Text files for pseudocode.** A Files tab holds text files that programs can use with `OPENFILE`, `READFILE`, `WRITEFILE` and `EOF`. You can edit them, add new ones, and see what a program wrote.
- **28 ready-made examples** (listed below), including a "Spot the errors" program in each language for practising debugging.
- **Reference tab** with a pseudocode cheat sheet and Python notes for Paper 4.
- **Syntax highlighting**, line numbers, light and dark themes, and a layout that works on phones.
- **Autosave.** Your code, files and theme are kept in your browser between visits.

## Examples

| Pseudocode | Python |
|---|---|
| Welcome: average of marks | Welcome: average of marks |
| INPUT, IF and validation | input() and if/elif |
| CASE OF menu | Linear search |
| Linear search | Bubble sort |
| Bubble sort | Insertion sort |
| Binary search (function) | Binary search |
| String functions | Strings |
| Procedures: BYREF and BYVAL | Recursion |
| Recursion | Classes: inheritance and polymorphism |
| Trace table: reverse the digits | Exception handling |
| Records | Stack and queue classes |
| Stack using an array | Dictionary: word count |
| Text files | Spot the errors |
| 2D array: times table | |
| Spot the errors | |

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Ctrl` + `Enter` (`Cmd` + `Enter` on Mac) | Run, or continue when paused |
| `F8` | Step one line |
| `Esc` | Stop the program |
| `Tab` | Indent by 4 spaces |
| `<-` | Turns into `←` as you type (pseudocode) |

There is also a **←** button in the toolbar for inserting the assignment arrow.

## What's supported

### Pseudocode

Follows the Cambridge 9618 pseudocode guide:

- `DECLARE`, `CONSTANT`, and the types `INTEGER`, `REAL`, `CHAR`, `STRING` and `BOOLEAN`
- 1D and 2D arrays: `ARRAY[1:10] OF INTEGER`, `ARRAY[1:3, 1:3] OF CHAR`
- Records (`TYPE … ENDTYPE`) and enumerated types (`TYPE Season = (Spring, Summer, Autumn, Winter)`)
- `INPUT` and `OUTPUT`
- `IF … THEN … ELSE … ENDIF` and `CASE OF … OTHERWISE … ENDCASE`, including ranges such as `2 TO 5`
- `FOR … TO … STEP … NEXT`, `WHILE … ENDWHILE` and `REPEAT … UNTIL`
- `PROCEDURE` and `FUNCTION` with `BYREF` and `BYVAL` parameters, `CALL` and `RETURN`, including recursion
- Text files: `OPENFILE … FOR READ / WRITE / APPEND`, `READFILE`, `WRITEFILE`, `EOF` and `CLOSEFILE`
- Operators: `+ - * / ^`, `DIV`, `MOD`, `&`, `= <> < > <= >=`, `AND`, `OR` and `NOT`
- Built-in functions: `LENGTH`, `LEFT`, `RIGHT`, `MID`, `SUBSTRING`, `TO_UPPER`, `TO_LOWER`, `UCASE`, `LCASE`, `NUM_TO_STR`, `STR_TO_NUM`, `IS_NUM`, `ASC`, `CHR`, `INT`, `RAND` and `ROUND`

Types are checked as the program runs: storing `"abc"` in an `INTEGER` variable, reading an array index outside its bounds, or using a variable before it has a value all give a clear error. Variables used without `DECLARE` still work, with a warning reminding you to declare them.

**Not supported yet:** classes (OOP) in pseudocode, random-access files (`SEEK`, `GETRECORD`, `PUTRECORD`), pointer and set types, and the `DATE` functions.

### Python

Python runs in the browser using [Skulpt](https://skulpt.org), which supports most of Python 3: variables, lists, tuples, dictionaries, strings and f-strings, functions, recursion, classes and inheritance, and `try` / `except`. The `math` and `random` modules are available.

Skulpt formats decimal numbers slightly differently from standard Python (for example, it prints `367 / 5` as `73.40000000000001`), so the playground patches how decimal numbers are printed and rounded. The output now matches standard Python 3. Every Python example was checked against standard Python and gives identical output.

**Not supported:** reading and writing files, and most modules other than `math` and `random`.

### Limits

| | Pseudocode | Python |
|---|---|---|
| Maximum steps before a program is stopped | 2,000,000 | 3,000,000 |
| Maximum depth of nested subroutine calls | 500 | Browser limit |
| Rows recorded in the trace table | 3,000 | 3,000 |

## Getting started

### Open it locally

Download `code-playground-9618.html` and double-click it. It opens in any modern browser (Chrome, Edge, Firefox or Safari).

### Host it on GitHub Pages

1. Create a new repository, for example `9618-code-playground`.
2. Upload `code-playground-9618.html` renamed to `index.html`, together with this `README.md`.
3. In the repository, go to **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then **Save**.
5. After a minute or two, the site is live at `https://zohxair.github.io/9618-code-playground/` (or at your own repository name).

## How it works

- **Pseudocode** runs on an interpreter written for this project. It reads the program, checks its structure (for example, that every `IF` has an `ENDIF`), and runs it line by line, so it can pause at any line and record every change to a variable.
- **Python** runs on Skulpt, which turns Python into JavaScript in the browser. The playground pauses Skulpt before each line to highlight the line and update the trace table.
- **The code editor** is [CodeMirror 5](https://codemirror.net/5/), with a custom highlighting mode for Cambridge pseudocode.
- **Internet connection.** The page loads three things from the internet:
  - CodeMirror, from the jsDelivr CDN.
  - Skulpt, from the same CDN. It's about 1 MB, loaded only the first time you run Python.
  - Fonts, from Google Fonts.

  Offline, pseudocode still runs in a plain text editor. Python needs a connection the first time it loads.
- **Storage.** Code, files, the chosen language and the theme are stored in the browser's `localStorage`. Nothing is sent to a server.

## Accuracy

Every example has been run in the browser, and stepping, input, stopping and the error messages were tested in both languages. Every pseudocode example has also been run through a separate test suite. The suite covers parameter passing, file handling, type checking and error messages. If a program behaves differently from what you expect in the exam, please [open an issue](../../issues) with the code and what you expected to happen.

## Contributing

Contributions are welcome, especially new examples, clearer error messages, and support for the pseudocode features that are missing.

1. Fork the repository and create a branch.
2. Make your change in `index.html`:
   - The pseudocode interpreter is the script that defines `window.Pseudo`.
   - The examples are in the script that defines `window.EXAMPLES`. Each one is a `{ title, code }` object.
3. Test your change in both languages, then open a pull request describing what you changed and why.

## Disclaimer

This is an independent learning tool. It is **not affiliated with, endorsed by or produced by Cambridge University Press & Assessment**. "Cambridge International" and the syllabus code 9618 are used only to identify the course it supports.

The pseudocode interpreter follows the published 9618 pseudocode guide as closely as possible, but examiners mark the meaning of your answer, not whether it runs here. For the official pseudocode guide, syllabus, past papers and mark schemes, use the [Cambridge International website](https://www.cambridgeinternational.org/programmes-and-qualifications/cambridge-international-as-and-a-level-computer-science-9618/) or ask your teacher.
