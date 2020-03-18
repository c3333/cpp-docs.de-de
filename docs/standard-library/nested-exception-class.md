---
title: nested_exception-Klasse
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441619"
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

## <a name="members"></a>Members

### <a name="operators"></a>Operatoren

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>Functions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Löst die gespeicherte Ausnahme aus.|
|[nested_ptr](#nested_ptr)|Gibt die gespeicherte Ausnahme zurück.|

### <a name="op_as"></a>Operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Rückgabewert

Die von diesem `nested_exception` Objekt erfasste gespeicherte Ausnahme.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Bemerkungen

Wenn `nested_ptr()` einen NULL-Zeiger zurückgibt, ruft die Funktion `std::terminate()`auf. Andernfalls wird die von `*this`erfasste gespeicherte Ausnahme ausgelöst.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Ausnahme >

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Ausnahme Klasse](../standard-library/exception-class.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
