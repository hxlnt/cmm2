# COLOUR MAXIMITE 2 DEVELOPER MANUAL

## Commands by category
| Category                 | Commands |
|--------------------------|----------|
| Code flow                | [`CHOICE`](#choiceexpression-value1-value2) ⁕ `CONTINUE` ⁕ `DO` ... `LOOP` ⁕ `DO WHILE` ... `LOOP` ⁕ `FOR` ... `NEXT` ⁕ [`FUNCTION`](#function-name-arg1-as-type-arg2-as-type-as-type) ⁕ `GOTO` ⁕ [`IF` ... `THEN`](#if-expr1-then-expr2) ⁕ [`SELECT CASE`](#select-case-var) ⁕ [`SUB`](#sub-arg1-as-type-arg2-as-type) |
| Console and debugging    | [`'`](#-single-quote) ⁕ `?` ⁕ `COLOR` ⁕ `MM.ERRMSG$` ⁕ `MM.ERRNO` ⁕ [`ON ERROR ABORT`](#on-error-abort) ⁕ [`ON ERROR IGNORE`](#on-error-ignore) ⁕ [`ON ERROR SKIP`](#on-error-skip) ⁕ [`PRINT`](#print-string) ⁕ `REM` |
| Constants and variables  | `CONST` ⁕ `DIM` ⁕ `LOCAL` ⁕ `STATIC` |
| Device settings and info | `COPYRIGHT` ⁕ [`MM.DEVICE$`](#mmdevice) ⁕ [`MM.DRIVE$`](#mmdrive) |
| Files and folders        | `CHDIR` ⁕ `CLOSE` ⁕ `CWD$` ⁕ `DIR$` ⁕ `EOF` ⁕ `#INCLUDE` ⁕ `KILL` ⁕ `LOC` ⁕ [`OPEN` ... `AS`](#open) ⁕ `RENAME` ... `AS` |
| Graphics                 | `BLIT` ⁕ `BOX` ⁕ `CIRCLE` ⁕ [`CLS`](#cls-color) ⁕ `DRAW3D` ⁕ `LOAD BMP` ⁕ `LOAD GIF` ⁕ `LOAD JPG` ⁕ `LOAD PNG` ⁕ `LINE` ⁕ `PAGE COPY` ⁕ `PAGE DISPLAY` ⁕ `PAGE SCROLL` ⁕ `PAGE WRITE` ⁕ `PIXEL` ⁕ `PIXEL FILL` ⁕ `MODE` ⁕ `RBOX` ⁕ [`RGB`](#rgb-number1-number2-number3-number4) ⁕ `SPRITE LOAD` ⁕ `SPRITE SHOW` ⁕ `TEXT` |
| Hardware I/O             | `DISTANCE` ⁕ [`INKEY$`](#inkey) ⁕ `PIN` |
| Numbers and math         | `COS` ⁕ `DEG` ⁕ `EXP` ⁕ `FIX` ⁕ `FLOAT` ⁕ `HEX$` ⁕ `INTEGER` ⁕ `SGN` ⁕ `SIN` ⁕ `SQR` ⁕ [`STR$`](#str-number) |
| Program execution        | `AUTO` ⁕ `CHAIN` ⁕ `CLEAR` ⁕ `END` ⁕ `RUN` |
| Sound                    | `PLAY TONE` ⁕ `PLAYMOD` ⁕ `PLAYMOD STOP` |
| Strings                  | `INSTR` ⁕ `LEFT$` ⁕ `MID$` ⁕ [`RIGHT$`](#rightstr-number) ⁕ `STRING` ⁕ `UCASE$` ⁕ `VAL` |
| Timing                   | `DATE$` ⁕ `DATETIME$` ⁕ `DAY$` ⁕ `EPOCH` ⁕ `GETSCANLINE` ⁕ `PAUSE` ⁕ `WATCHDOG` |

---

### ' (single quote)
A single quote precedes a comment. This is the same as, but preferred over, using REM.

```BASIC
' Print line to file (#1)
PRINT #1, STR$(result)
```

*See also: `REM`*

---

### ? 

### AUTO

### BLIT

### BOX

--- 

### CHOICE (*expression*, *value1*, *value2*)
If the first expression is true, *value1* is returned; otherwise, *value2* is returned.
```BASIC
timeOfDay = CHOICE(hour >= 12, "PM", "AM")
```

---

### CIRCLE

### CLEAR

### CLOSE

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

### COPYRIGHT

### DATA

### DIM

### END

### ERASE

### ERROR

### FILES

### FLOAT [(*number*)]

---

### FUNCTION *Name* ([*arg1* AS *TYPE*], [*arg2* AS *TYPE*]) AS *TYPE*
A function is a subroutine that returns a value of the data type specified in the final AS *TYPE* declaration. A function without arguments should include a blank set of parentheses.

```BASIC
FUNCTION GetAverage (number1 AS FLOAT, number2 AS FLOAT) AS FLOAT
  GetAverage = (number1 + number2) / 2
END FUNCTION
```

*See also: [`SUB`](#sub-arg1-as-type-arg2-as-type)*

---

### GOTO

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

```BASIC
  IF INKEY$ = "q" THEN EXIT SUB
```

### INTEGER [(*number*)]

### KILL

### LOCAL

### MAP

### MM.DEVICE$

### MM.DRIVE$

### MM.ERRMSG

### MM.ERRNO

### ON ERROR ABORT

### ON ERROR IGNORE

### ON ERROR SKIP

### OPEN

### OPTION BREAK

### OPTION ERROR

### PRINT *string*

### RBOX

### RENAME *string1* AS *string2*

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

---

### RUN

---

### SELECT CASE *var*
An alternative to `IF`/`THEN` statements.
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

### SGN

### SIN

### SQR

### STATIC

---

### STR$ (*number*)
Parses numeric data as a string.
```BASIC
PRINT "Your price is " + STR$(price)
```

---

### STRING ([*number*])

---

### SUB ([*arg1* AS *TYPE*], [*arg2* AS *TYPE*])
A subroutine has optional arguments.
```BASIC
SUB DebugPrint (msg AS STRING)
  PRINT #8, msg
END SUB
```

---

### VAL

---
