---
title: nested_exception-Klasse
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 6ae95880f0bc18928ed9bd4f6b6da14722f6ec60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212188"
---
# <a name="nested_exception-class"></a>nested_exception-Klasse

Die Klasse beschreibt eine Ausnahme für die Verwendung mit Mehrfachvererbung. Die aktuell behandelte Ausnahme wird erfasst und zur späteren Verwendung gespeichert.

## <a name="syntax"></a>Syntax

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_as)||

### <a name="functions"></a>Functions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Löst die gespeicherte Ausnahme aus.|
|[nested_ptr](#nested_ptr)|Gibt die gespeicherte Ausnahme zurück.|

### <a name="operator"></a><a name="op_as"></a>Operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a><a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Rückgabewert

Die von diesem-Objekt erfasste gespeicherte Ausnahme `nested_exception` .

### <a name="rethrow_nested"></a><a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Bemerkungen

Wenn `nested_ptr()` einen NULL-Zeiger zurückgibt, ruft die Funktion auf `std::terminate()` . Andernfalls wird die von erfasste gespeicherte Ausnahme ausgelöst **`*this`** .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<exception>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Exception-Klasse](../standard-library/exception-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
