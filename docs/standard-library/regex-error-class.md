---
title: regex_error-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: f8f3c88c1b203ed7fcea148843fa99590e27b888
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331871"
---
# <a name="regex_error-class"></a>regex_error-Klasse

Meldet ein ungültiges basic_regex-Objekt.

## <a name="syntax"></a>Syntax

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt ein Ausnahmeobjekt, das ausgelöst wurde, um einen Fehler bei der Erstellung oder Verwendung eines `basic_regex` -Objekts zu melden.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[regex_error](#regex_error)|Erstellt das Objekt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Code](#code)|Gibt den Fehlercode zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<regex >

**Namespace:** std

## <a name="example"></a>Beispiel

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="regex_errorcode"></a><a name="code"></a>regex_error::code

Gibt den Fehlercode zurück.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den Wert zurück, der an den Konstruktor des Objekts übergeben wurde.

## <a name="regex_errorregex_error"></a><a name="regex_error"></a>regex_error::regex_error

Erstellt das Objekt.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Parameter

*Fehler*\
Der Fehlercode.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor erstellt ein Objekt, das den *Wertfehler*enthält.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_constants-Klasse](../standard-library/regex-constants-class.md)\
[\<regex> Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<regex> Operatoren](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
