## Contents:
- [Introduction](#introduction)
- [Code style](#code-style)
    - [Avoid magic numbers](#avoid-magic-numbers)
    - [Naming conventions](#naming-conventions)
    - [Functions without arguments](#functions-without-arguments)
    - [Code readability](#code-readability)
    - [Header files](#header-files)
- [General coding practices](#general-coding-practices)
    - [Specifiers](#specifiers)
    - [Null pointers](#null-pointers)
    - [Initializing a class member](#initializing-a-class-member)
    - [Type preference](#type-preference)
- [Argument parser](#argument-parser)

# Introduction

We appreciate your interest in contributing to the development and
improvement of the **Multi Theft Auto (MTA) multiplayer mod**. To ensure 
high-quality code and a smooth collaboration process, please adhere to 
the following **coding guidelines**.

# Code style

### Avoid magic numbers

We always try to avoid magic numbers like memory addresses, offsets,
some constant numbers, etc. You can use the **#define** macro to define
the numbers or at least use comments to document these numbers.

``` cpp
float CWeatherSA::GetWetRoads() const
{
    return *(float*)0xC81308; // CWeather::WetRoads
}
```

``` cpp
// In the header
#define NUM_WETROADS    0xC81308

// In the .cpp
float CWeatherSA::GetWetRoads() const
{
    return *(float*)NUM_WETROADS;
}
```

When using the **#define** macro, we use a prefix that specifies what it
defines.

``` cpp
#define FUNC_RemoveRef                               0x4C4BB0 // Function address
#define ARRAY_aCannons                               0xC80740 // Array address
#define STRUCT_CAESoundManager                       0xB62CB0 // Struct address
#define SIZE_CWaterCannon                            0x3CC    // Size of object (e.g., struct object)
#define CLASSSIZE_WeaponInfo                         112      // Class size
#define NUM_CWaterCannon_Audio_Offset                0x32C    // Number (e.g., offsets, integers, etc.)
#define CLASS_CText                                  0xC1B340 // Class address
#define VAR_CTempColModels_ModelPed1                 0x968DF0 // Variable address (CColModel colModelPeds)
```

### Naming conventions

We use different naming conventions depending on the context.

-   Use **lower camel case** for variable names and types:
    ``` cpp
    SSomeStruct   valueOne;
    ESomeEnum     m_valueTwo;
    ```
-   Use **upper camel case** for functions and classes:
    ``` cpp
    void UpperCamelCase();
    class Vector;
    ```
-   Class member, should start with the prefix **m\_**
    ``` cpp
    CVector       m_vecPosition;
    CVector       m_vecRotation;
    bool          m_isVisible;
    bool          m_isFrozen;
    ```
-   We **avoid** Hungarian notation in new codes, so use it only if
    necessary for consistency with the current code you are editing.
    ``` cpp
    float         fValue;               // Local variable
    unsigned char m_ucValue;            // Class member variable
    char          ms_cValue;            // Class static member variable
    bool          g_bCrashTwiceAnHour;  // Global variable
    char*         szUsername;           // Zero-terminated string
    SString       strUsername;          // String
    CVector       vecPosition;          // 3D Vector
    ```

### Functions without arguments

Define and call functions without arguments simply with empty
parentheses. Don't use *void* in this case as it is an old practice!

``` cpp
// Bad
void MyFunction(void);
MyFunction(void);

// Good
void MyFunction();
MyFunction();
```

### Code readability

This is another very important point of the guidelines. Always try to
make your code as readable as possible so that anyone can easily read it
and understand its purpose.

-   Use **early-returns** to improve code readability.
    ``` cpp
    // Poor readability
    bool CStaticFunctionDefinitions::RespawnObject(CElement* pElement)
    {
        if (IS_OBJECT(pElement))
        {
            CObject* pObject = static_cast<CObject*>(pElement);
            if (pObject)
            {
                pObject->Respawn();
                return true;
            }
        }

        return false;
    }

    // Clearer readability
    bool CStaticFunctionDefinitions::RespawnObject(CElement* pElement)
    {
        if (!IS_OBJECT(pElement))
            return false;

        CObject* pObject = static_cast<CObject*>(pElement);
        if (!pObject)
            return false;

        pObject->Respawn();

        return true;
    }
    ```
-   Always strive to maintain code readability. If a type is lengthy to
    write, you can use auto to improve readability
    ``` cpp
    CDeatchmatchObject* pObject = static_cast<CDeathmatchObject*>(pEntity);
    // Can be
    auto* pObject = static_cast<CDeathmatchObject*>(pEntity);
    ```

    We prefer to use **auto\*** when it comes to pointer, even though
    auto itself is sufficient.
-   Use logical conditions whenever possible
    ``` cpp
    // Poor readability
    const CPositionRotationAnimation* CObject::GetMoveAnimation()
    {
        if (IsMoving())
        {
            return m_pMoveAnimation;
        }
        else
        {
            return nullptr;
        }
    }

    // Good readability
    const CPositionRotationAnimation* CObject::GetMoveAnimation()
    {
        return IsMoving() ? m_pMoveAnimation : nullptr;
    }
    ```
-   If a loop or condition is short, omit curly braces
    ``` cpp
    // Instead of
    if (!bStillRunning)
    {
        StopMoving();
    }

    // You can do
    if (!bStillRunning)
        StopMoving();

    // However, do not omit curly braces for larger blocks:
    for (dont)
        for (do)
            for (this)
                ...
    ```
-   The final line of a brace-less condition/loop should be separated for readability, e.g:
    ``` cpp
    // Instead of
    PreCheck();
    if (!bStillRunning)
        StopMoving();
    PostCheck();

    // You should do
    PreCheck();
    if (!bStillRunning)
        StopMoving();
    
    PostCheck();
    ```
    
-   Functions that only return a value should be placed in header files.
    For example, instead of:
    ``` cpp
    // In .cpp file
    int GetGameSpeed()
    {
        return m_iGameSpeed;
    }
    ```

    Do it in the header:

    ``` cpp
    int GetGameSpeed() const noexcept { return m_iGameSpeed; }
    ```
-   Don't use unnecessary parenthesis.
    ``` cpp
    // Bad
    bool CClientPed::IsDead()
    {
        (return (m_status == STATUS_DEAD));
    }

    // Good
    bool CClientPed::IsDead()
    {
        return m_status == STATUS_DEAD;
    }
    ```
-   Use [range-based for loops](https://en.cppreference.com/w/cpp/language/range-for) when possible.
    ``` cpp
    std::vector<int> vec; // Example std container

    // Bad:
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); it++)

    // Good:
    for (const auto& v : vec)
    for (const int& v : vec)

    // In case of maps you can use structured binding:
    std::map<std::string, int> myMap;
    for (const auto& [k, v] : myMap)

    // There are situations where you must use old style loops, in this case use `auto`
    for (auto it = vec.begin(); it != vec.end(); it++)
    ```

### Header files

-   Always place a copyight comment at the beginning of header files  
  
    ``` cpp
    /*****************************************************************************
    *
    *  PROJECT:     Multi Theft Auto
    *  LICENSE:     See LICENSE in the top level directory
    *
    *  Multi Theft Auto is available from https://www.multitheftauto.com/
    *
    *****************************************************************************/

    #pragma once
    ```

- Use **#pragma once** preprocessor directive after the copyright
comment for new header files, and the ones you are modifying for the
pull request. Make sure to remove include guard if you are using
**#pragma once**.
  
  
# General coding practices

We always try to create good code that complies with modern practices.

### Specifiers

These are the basic specifiers we try to use, especially in new codes:

* Use [const](https://en.cppreference.com/w/cpp/keyword/const) and
[constexpr](https://en.cppreference.com/w/cpp/language/constexpr)
wherever possible.

* Use the
[noexcept](https://en.cppreference.com/w/cpp/language/noexcept_spec)
specifier whenever possible, but **be cautious** as it can cause the
program to terminate if an exception is thrown.

### Null pointers

Use [nullptr](https://en.cppreference.com/w/cpp/language/nullptr)
instead of [NULL](https://en.cppreference.com/w/cpp/types/NULL) when
setting or returning a null pointer.

### Initializing a class member

Use [member initialization lists](https://en.cppreference.com/w/cpp/language/constructor) 
whenever possible. Instead of doing:

``` cpp
CObject::CObject(CElement* pParent, CObjectManager* pObjectManager, bool bIsLowLod) 
    : CElement(pParent), m_bIsLowLod(bIsLowLod), m_pLowLodObject(NULL)
{
    // Init
    m_iType = CElement::OBJECT;
    SetTypeName("object");

    m_pObjectManager = pObjectManager;
    m_usModel = 0xFFFF;
    m_pMoveAnimation = NULL;
    m_ucAlpha = 255;
    m_vecScale = CVector(1.0f, 1.0f, 1.0f);
    m_fHealth = 1000.0f;
    m_bSyncable = true;
    m_pSyncer = NULL;
    m_bIsFrozen = false;
    m_bDoubleSided = false;
    m_bBreakable = false;
    m_bCollisionsEnabled = true;

    // Add us to the manager's list
    pObjectManager->AddToList(this);
}
```

Do:

``` cpp
CObject::CObject(CElement* pParent, CObjectManager* pObjectManager, bool bIsLowLod)
    : CElement(pParent),
      m_bIsLowLod(bIsLowLod),
      m_pLowLodObject(nullptr),
      m_iType(CElement::OBJECT),
      m_pObjectManager(pObjectManager),
      m_usModel(0xFFFF),
      m_pMoveAnimation(nullptr),
      m_ucAlpha(255),
      m_vecScale(1.0f, 1.0f, 1.0f),
      m_fHealth(1000.0f),
      m_bSyncable(true),
      m_pSyncer(nullptr),
      m_bIsFrozen(false),
      m_bDoubleSided(false),
      m_bBreakable(false),
      m_bCollisionsEnabled(true)
{
    SetTypeName("object");

    // Add us to the manager's list
    pObjectManager->AddToList(this);
}
```

### Type preference

1.  In C++, prefer using types from the std namespace provided by
appropriate headers (such as **`<cstdint>`**,
**`<cstddef>`**, etc.). This is recommended for several reasons:

    -   Namespace Safety: Types defined in these headers are
        encapsulated within the std namespace, which helps avoid naming
        conflicts with user-defined types or macros. This follows the
        C++ standard practice of minimizing global namespace pollution.

    <!-- -->

    -   Consistency and Readability: Using **std::** types ensures
        consistency and improves code readability by making it clear
        that these types are part of the standard library.

    <!-- -->

    -   C++ Standard Compliance: The C++ standard (C++11 and later)
        includes headers like **`<cstdint>`** and
        **`<cstddef>`**, which provide standardized types:

        * `<cstdint>` includes exact-width integer types such as
        **'std::uint32_t**, **std::int32_t**, etc.

        * `<cstddef>` includes types like **std::size_t**,
        **std::ptrdiff_t**, etc.

    -   Portability and Maintainability: Using these headers makes your
        code more portable across different compilers and platforms, as
        it guarantees that these types are defined in a standardized way. 
        This is especially important in a C++ environment, where the focus 
        is on maintainability and cross-platform compatibility.

    By adhering to these practices, you ensure that your codebase
    remains clean, consistent, and adheres to modern C++ standards,
    which ultimately contributes to better maintainability and fewer
    integration issues.
1.  In new codes, try not to use the **SString** type anymore, use
    **std::string** instead.

# Argument parser

We have had a new parser argument for several years, although it has not
yet been used in many places and you can often see the old **CScriptArgReader**. 
For new codes, use a new parser if possible. If you are refactoring older functions, 
you usually need to use **ArgumentParserWarn** to maintain backward compatibility.

``` cpp
// New function
{"pathListDir", ArgumentParser<pathListDir>},

// Old function with new argument parser
{"outputChatBox", ArgumentParserWarn<false, OutputChatBox>},
```

More information about the parser can be found
[here](https://github.com/multitheftauto/mtasa-blue/wiki/Lua-API#how-to-add-a-new-lua-definition).  
