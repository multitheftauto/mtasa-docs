## Introduction
Welcome to the coding guidelines for the **[mtasa-resources](https://github.com/multitheftauto/mtasa-resources)** repository!<br>
We are aware that cooperative work and high-quality code require compliance with the following rules, so we ask all interested parties to take the following into account in all of their contributions.

## Contents
- [General](#general)
    - [Simplicity](#simplicity)
    - [Comments](#comments)
    - [Returns](#returns)
- [Style](#style)
- [Security](#security)
- [Performance](#performance)

## General
When you contribute to our codebase, you should always<br>
Write code that is
- Readable
- Secure
- Scalable
- Maintainable

### Simplicity
Striving for simplicity is always important, as simple code is easier to read and maintain.<br>
Some example:

```lua
local foo = true

-- Bad
function bar()
    if foo then
        return true
    else
        return false
    end
end

-- Good
function baz()
    return foo
end
```

### Comments
Comments are good - If you use them well!<br>
Commenting is useful for making complex logic tasks easier to explain, but it's unnecessary to comment every line, like here:

```lua
-- Never do this!
-- No one wants to read a comment on every line

addEvent("foo", true) -- Add the event
addEventHandler("foo", root, -- Add the event handler
    function()
        bar = 10 -- Set the bar variable to 10
        baz(bar) -- Call the baz function
    end
)
```

### Returns
Early return pattern is preferred, as they provide easier readability and transparency.<br>
Example:

```lua
-- Nested
function a()
    if foo then
        if bar then
            if baz then
                return true
            end
        end
    end
end

-- Early
function b()
    if not (foo and bar and baz) then
        return
    end

    return true
end
```

## Style
To do

## Security
To do

## Performance
To do