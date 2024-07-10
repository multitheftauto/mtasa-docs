## Contents:
- [Introduction](#introduction)
- [Code style](#code-style)
    - [Early return](#early-return)
    - [Consistent naming conventions](#consistent-naming-conventions)
    - [Use of constants](#use-of-constants)
    - [Indentation and formatting](#indentation-and-formatting)
- [General principles](#general-principles)
- [Script security](#script-security)
- [Error handling](#error-handling)
- [Performance considerations](#performance-considerations)

# Introduction

We appreciate your interest in contributing to the development and
improvement of the **Default Lua resources that come with the Multi
Theft Auto (MTA) multiplayer mod**. To ensure high-quality code and a
smooth collaboration process, please adhere to the following **coding
guidelines**.

# Code style

### Early return

To improve code readability, prefer using early returns to handle error
conditions or special cases at the beginning of functions. This helps to
avoid deep nesting and makes the main logic easier to follow.

```lua
-- Bad example 
function exampleFunction(value) 
    if value > 0 then 
        -- Some logic here 
        if value < 100 then 
            -- More logic here 
            if value ~= 50 then 
                -- Main logic here 
            end 
        end 
    end 
end 

-- Good example 
function exampleFunction(value) 
    if value \<= 0 then return end 
    if value \>= 100 then return end 
    if value == 50 then return end 
    -- Main logic here end 
end
```

### Consistent naming conventions

TODO

### Use of constants

TODO

### Indentation and formatting

Ensure your code editor (e.g. [Visual Studio Code](https://code.visualstudio.com/) 
applies the rules established by the project's **.editorconfig** file.

# General principles

-   Write clear, readable, and maintainable code.
-   Follow the [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
    (Don't Repeat Yourself) principle.
-   Adhere to the [KISS](https://en.wikipedia.org/wiki/KISS_principle)
    (Keep It Simple, Stupid) principle.
-   Use meaningful variable and function names that convey their purpose.
-   Comment your code where necessary to explain the logic.

# Script security

Follow the [Script security](https://wiki.multitheftauto.com/wiki/Script_security) 
principles established for MTA:SA scripts to ensure the safety and integrity of your code.

# Error handling

TODO

# Performance considerations

-   Avoid unnecessary computations within loops.
-   Cache results of expensive operations whenever possible.
-   Use local variables to improve performance.


