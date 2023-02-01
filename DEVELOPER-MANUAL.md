# COLOUR MAXIMITE 2 DEVELOPER MANUAL

## Commands by category
| Category                 | Commands |
|--------------------------|----------|
| Code flow                | [`CHOICE`](#choiceexpression-value1-value2) ⁕ `CONTINUE` ⁕ `DO` ... `LOOP` ⁕ `DO WHILE` ... `LOOP` ⁕ `END FUNCTION` ⁕ `END SUB` ⁕ `EXIT DO` ⁕ `EXIT FOR` ⁕ `EXIT FUNCTION` ⁕ `EXIT SUB` ⁕ `FOR` ⁕ [`FUNCTION`](#function-name-arg1-as-type-arg2-as-type-as-type) ⁕ `GOTO` ⁕ [`IF` ... `THEN`](#if-expr1-then-expr2) ⁕ `NEXT` ⁕ [`SELECT CASE`](#select-case-var) ⁕ [`SUB`](#sub-name-arg1-as-type-arg2-as-type) |
| Debugging                | [`'`](#-single-quote) ⁕ `#MMDEBUG ON` ⁕ `#MMDEBUG OFF` ⁕ `MM.ERRMSG$` ⁕ `MM.ERRNO` ⁕ `#COMMENT` ⁕ [`ON ERROR ABORT`](#on-error-abort) ⁕ [`ON ERROR IGNORE`](#on-error-ignore) ⁕ [`ON ERROR SKIP`](#on-error-skip) ⁕ `REM` ⁕ `TRACE LIST` ⁕ `TRACE OFF` ⁕ `TRACE ON` |
| Constants and variables  | `CONST` ⁕ `#DEFINE` ⁕ `DIM` ⁕ `LOCAL` ⁕ `STATIC` ⁕ `VAR CLEAR` ⁕ `VAR RESTORE` ⁕ `VAR SAVE` ⁕|
| Device settings and info | [`MM.DEVICE$`](#mmdevice) |
| Files and folders        | `CHDIR` ⁕ `CLOSE` ⁕ `CWD$` ⁕ `DIR$` ⁕ `EOF` ⁕ `#INCLUDE` ⁕ [`KILL`](#kill) ⁕ `LOC` ⁕ `MKDIR` ⁕ [`OPEN` ... `AS`](#open) ⁕ `RENAME` ... `AS` |
| Graphics                 | `BLIT` ⁕ `BOX` ⁕ `CIRCLE` ⁕ [`CLS`](#cls-color) ⁕ `DRAW3D` ⁕ `LOAD BMP` ⁕ `LOAD GIF` ⁕ `LOAD JPG` ⁕ `LOAD PNG` ⁕ `LINE` ⁕ `MAP RESET` ⁕ `MAP SET` ⁕ `MODE` ⁕ `PAGE COPY` ⁕ `PAGE DISPLAY` ⁕ `PAGE RESIZE` ⁕ `PAGE SCROLL` ⁕ `PAGE STITCH` ⁕ `PAGE WRITE` ⁕ `PIXEL` ⁕ `PIXEL FILL` ⁕ `MODE` ⁕ `RBOX` ⁕ [`RGB`](#rgb-number1-number2-number3-number4) ⁕ `SPRITE LOAD` ⁕ `SPRITE SHOW` ⁕ `TEXT` ⁕ `TRIANGLE` |
| Graphics: Turtle         | `TURTLE BACKWARD` ⁕ `TURTLE BEGIN FILL` ⁕ `TURTLE DRAW CIRCLE` ⁕ `TURTLE DRAW LINE` ⁕ `TURTLE DRAW PIXEL` ⁕ `TURTLE DRAW TURTLE` ⁕ `TURTLE END FILL` ⁕ `TURTLE FILL PIXEL` ⁕ `TURTLE FORWARD` ⁕ `TURTLE HEADING` ⁕ `TURTLE FILL COLOUR` ⁕ `TURTLE MOVE` ⁕ `TURTLE PEN COLOUR` ⁕ `TURTLE PEN DOWN` ⁕ `TURTLE PEN UP ` ⁕ `TURTLE RESET` ⁕ `TURTLE TURN LEFT` ⁕ `TURTLE TURN RIGHT` |
| I/O                      | `?` ⁕ `ADC FREQUENCY` ⁕ `ADC OPEN` ⁕ `COLOR`/`COLOUR` ⁕ `DISTANCE` ⁕ [`INKEY$`](#inkey) ⁕ `PIN` ⁕  [`PRINT`](#print-port-value) ⁕ [`PRINT @`](#print-x-y-m-value) ⁕ `TEMPR` |
| Numbers and math         | `COS` ⁕ `DEG` ⁕ `EXP` ⁕ `FIX` ⁕ `FLOAT` ⁕ `HEX$` ⁕ `INTEGER` ⁕ `SGN` ⁕ `SIN` ⁕ `SQR` ⁕ [`STR$`](#str-number) ⁕ `TAN` |
| Program execution        | `AUTO` ⁕ `CHAIN` ⁕ `CLEAR` ⁕ `END` ⁕ `NEW` ⁕ `RUN` |
| Sound                    | `PLAY TONE` ⁕ `PLAYMOD` ⁕ `PLAYMOD STOP` |
| Strings                  | `INSTR` ⁕ [`LEFT$`](#left-str-number) ⁕ `MID$` ⁕ [`RIGHT$`](#right-str-number) ⁕ `SPACE$` ⁕ `STRING` ⁕ `TAB` ⁕ `UCASE$` ⁕ `VAL` |
| Timing                   | `DATE$` ⁕ `DATETIME$` ⁕ `DAY$` ⁕ `EPOCH` ⁕ `GETSCANLINE` ⁕ `PAUSE` ⁕ `TIME$` ⁕ `TIMER` ⁕ `WATCHDOG` ⁕ `WATCHDOG OFF` |


## Commands

### ' (single quote)
A single quote precedes a comment. This is the same as, but preferred over, using REM.

```BASIC
' Print line to file (#1)
PRINT #1, STR$(result)
```

*See also: `REM`*

---

### CHOICE (*expression*, *value1*, *value2*)
If the first expression is true, *value1* is returned; otherwise, *value2* is returned.

```BASIC
timeOfDay = CHOICE(hour >= 12, "PM", "AM")
```

---

### CLS *color*
Clears the screen with a specified color.

```BASIC
CLS rgb(0, 140, 240)
```

*See also: [`RGB`](#rgb-number1-number2-number3-number4)*

---

### CONST
Declare a constant value.

```BASIC
CONST LINEHEIGHT = 30
```

---

### FUNCTION *Name* ([*arg1* AS *TYPE*], [*arg2* AS *TYPE*]) AS *TYPE*
A function is a subroutine that returns a value of the data type specified in the final AS *TYPE* declaration. A function without arguments should include a blank set of parentheses. `EXIT FUNCTION` can be used to exit the function early.

```BASIC
FUNCTION GetAverage (number1 AS FLOAT, number2 AS FLOAT) AS FLOAT
  GetAverage = (number1 + number2) / 2
END FUNCTION
```

*See also: `EXIT FUNCTION`, [`SUB`](#sub-name-arg1-as-type-arg2-as-type)*

---

### IF *expr1* THEN *expr2*
A simple `IF`/`THEN` branch can be written on a single line without a closing `ENDIF`. More complex flows include like breaks and additional keywords such as `ELSE IF` or `ELSE`.

```BASIC
IF color = "red" THEN background = rgb(255, 0, 0)
IF number < 10 THEN
  PRINT "Less than 10."
ELSE IF number = 10 THEN
  PRINT "It's 10."
ELSE
  PRINT "More than 10."
ENDIF
```

*See also: `SELECT CASE`*

---

### INKEY$
Reads keyboard input buffer and returns a single character.

```BASIC
  IF INKEY$ = "q" THEN EXIT SUB
```

*See also: `ASC`, `CHR$`*

---

### KILL
Deletes a file from the SD card.

```BASIC
  KILL "file.tmp"
```

---

### LEFT$ (*str*, *number*)

Returns the leftmost *number* letters of a string (*str*).

```BASIC
PRINT LEFT$("Hello world!xxxxx", 12)
```

*See also: `MID$`*, [`RIGHT$`](#right-str-number)

---

### MM.DEVICE$
A read-only variable that contains the device MMBasic is running on.

---

### PRINT [#*port*] *value*
Prints text to the console, file, or serial port specified by the number #*port*. If #*port* is not specified, the default is #0, which will print to the console (VGA display and/or serial).

```BASIC
' "Hello world!" will print on a single line
' because the semicolon supresses the default
' line break.
PRINT "Hello";
PRINT " world!"

' A comma between values will be printed as a
' tab. A semicolon or space between values will
' not print.
PRINT firstname, age

' This will print to file.txt and the COM1 
' serial port.
OPEN "file.txt" FOR APPEND AS #2
PRINT #2 "Last modified: " timestamp
OPEN "COM1:9600" AS #3
PRINT #3 "File timestamp updated."
```

*See also: `OPEN` ... `AS`, `OPEN` ... `FOR`, [`PRINT @`](#print-x-y-m-value)*

---

### PRINT @(*x*, [*y,*] [*m*]) *value*
An alternative [`PRINT`](#print-port-value) command where x and y coordinates and an optional color mode *m* can be specified. The options for *m* are 0 (normal), 1 (transparent background), 2 (inverted), and 5 (inverted and transpent background). The `PRINT @` command does not automatically wrap lines, allowing for text to run outside of screen boundaries. Multiple `PRINT @` coordinates can be specified inline as shown in the example below.

```BASIC
PRINT @(100, 10) "Guess what?)
PRINT @(200, 100, 1) "These words can" @(205, 105, 1) "overlap"
PRINT @(-10, -10) "or print off-screen."
```

*See also: [`PRINT`](#print-port-value)*

---

### RENAME *string1* AS *string2*
Renames a file on the SD card.

```BASIC
RENAME "file.tmp" AS "file.txt"
```

---

### RGB([*number1*], *number2*, *number3*, *number4*) or RGB(*color*)
Specify a color with at least three numbers from 0-255 representing red, green, and blue values. An optional preceding value specifies a transparency value from 0-15. The Colour Maximite 2 does not display the full range of 16 million colors; actual rendered color depends on the graphics mode set.

Alternatively, a set of default colors can be used by name. The default color names are black, blue, green, cyan, red, magenta, yellow, brown, white, orange, pink, gold, salmon, beige, lightgray, and gray.

```BASIC
COLOR rgb(white), rgb(240, 20, 180)
```

*See also: `MAP`, `MODE`*

---

### RIGHT$ (*str*, *number*)
Returns the rightmost *number* letters of a string (*str*).

```BASIC
fileExtension = RIGHT$(filename, 3)
```

*See also: [`LEFT$`](#left-str-number), `MID$`*

---

### SELECT CASE *var*
An alternative to using `IF`/`THEN` statements for code branches.

```BASIC
SELECT CASE numberGuess
  CASE 4, 9, 12 TO 14
    PRINT "You win!"
  CASE IS < 3, IS > 15, 5 TO 7
    PRINT "You lose!"
  CASE ELSE
    PRINT "It's a tie!"
  END SELECT
```

---

### STR$ (*number*)
Parses numeric data as a string.

```BASIC
LOCAL STRING pricetag = "$" + STR$(price)
```

---

### SUB *Name* ([*arg1* AS *TYPE*], [*arg2* AS *TYPE*])
The first line of a subroutine sets its name and any optional arguments in parentheses. The last line is a subroutine is `END SUB`. `EXIT SUB` can be called within the subroutine to exit early. 

```BASIC
SUB DebugPrint (msg AS STRING)
  PRINT #8, msg
END SUB

DebugPrint "Hello!"
```

*See also: `END SUB`, `EXIT SUB`, [`FUNCTION`](#function-name-arg1-as-type-arg2-as-type-as-type)*