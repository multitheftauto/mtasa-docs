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

# General principles

-   Write clear, readable, and maintainable code.
-   Follow the [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
    (Don't Repeat Yourself) principle.
-   Adhere to the [KISS](https://en.wikipedia.org/wiki/KISS_principle)
    (Keep It Simple, Stupid) principle.
-   Use meaningful variable and function names that convey their purpose.
-   Comment your code where necessary to explain the logic.

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

### Error handling

Use the Lua [`error (message [, level])`](https://www.lua.org/manual/5.1/manual.html#pdf-error) function to raise warnings when validating parameters passed to a function, with `level` set to `2` so that the error points the error at the function call location. For example:

```lua
-- This function outputs player's name to the chat box
function outputPlayerName(player)
    -- If player is invalid, raise an error
    if not (isElement(player) and getElementType(player) == "player") then
        error("Invalid player!", 2)
    end

    outputChatBox(getPlayerName(player))
end

-- This function is triggered each time a player joins and calls outputPlayerName
local function playerJoin()
    outputPlayerName() -- note the missing player argument; the error will point to this line
end
addEventHandler("onPlayerJoin", root, playerJoin)
```

### Consistent naming conventions

All function names and variables should use the camel case naming convention. Constant variables should use upper snake case (see below).

### Use of constants and avoiding [magic numbers](https://en.wikipedia.org/wiki/Magic_number_(programming))

Don't use magic numbers in blocks of code - instead, define such values as "constants" at the top of the file using upper snake case.

*Note: the version of Lua used by MTA does not support the `const` keyword added in Lua 5.4. In MTA Lua, the concept of a `const` is just that - a concept.*


### Indentation and formatting

Ensure your code editor (e.g. [Visual Studio Code](https://code.visualstudio.com/) 
applies the rules established by the project's **.editorconfig** file.

# Performance considerations

-   Avoid unnecessary computations within loops.
-   Cache results of expensive operations whenever possible.
-   Use local variables to improve performance.

### Don't use OOP functionality

Enabling the [OOP](https://wiki.multitheftauto.com/wiki/OOP) functionality in any given resource will incur a performance hit. In general, pull requests to the official resources repository that enable it will generally fail code review.

### Use range-based for loops rather than [`ipairs`](https://www.lua.org/manual/5.1/manual.html#pdf-ipairs)

Range-based for loops are more performant than loops using `ipairs` and should be used whenever possible. For example:

```lua
-- Rather than this:
for _, player in ipairs(getElementsByType("player")) do
    iprint(player)
end

-- Do this:
local players = getElementsByType("player")
for i = 1, #players do
    iprint(players[player])
end
```

# Script security

Follow the [Script security](https://wiki.multitheftauto.com/wiki/Script_security) 
principles established for MTA:SA scripts to ensure the safety and integrity of your code.



