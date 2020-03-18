---
title: __alignof-Operator
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: b3764e95846d48d293991d69d04bc71c6b3aed90
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443607"
---
# <a name="__alignof-operator"></a>__alignof-Operator

C++ 11 führt den **alignof** -Operator ein, der die Ausrichtung des angegebenen Typs in Bytes zurückgibt. Zur maximalen Portabilität sollten Sie den „alignof“ des Operators statt des Microsoft-spezifischen „__alignof“-Operators verwenden.

**Microsoft-spezifisch**

Gibt einen Wert vom Typ `size_t` zurück, der der Ausrichtungs Anforderung des Typs entspricht.

## <a name="syntax"></a>Syntax

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Bemerkungen

Beispiel:

|Ausdruck|value|
|----------------|-----------|
|**__alignof (Char)**|1|
|**__alignof (Short)**|2|
|**__alignof (int)**|4|
|**__alignof (\__int64)**|8|
|**__alignof (float)**|4|
|**__alignof (Double)**|8|
|**__alignof (Char\*)**|4|

Der **__alignof** -Wert ist identisch mit dem Wert für `sizeof` für grundlegende Typen. Betrachten Sie jedoch das Beispiel:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

In diesem Fall ist der **__alignof** Wert die Ausrichtungs Anforderung des größten Elements in der Struktur.

Entsprechend gilt:

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` ist gleich `32`.

Eine Verwendung für **__alignof** wäre als Parameter für eine ihrer eigenen Speicher Belegungs Routinen. Beispielsweise könnten Sie angesichts der folgenden definierten Struktur `S` eine Speicherbelegungsroutine mit dem Namen `aligned_malloc` aufrufen, um einen bestimmten Grenzwert mit Speicher zu belegen.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Aus Gründen der Kompatibilität mit früheren Versionen ist **_alignof** ein Synonym für **__alignof** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Weitere Informationen über das Ändern der Ausrichtung finden Sie unter:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Strukturmemberausrichtung)](../build/reference/zp-struct-member-alignment.md)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

Weitere Informationen zu den Unterschieden bei der Ausrichtung im Code für x86 und x64 finden Sie unter:

- [Konflikt mit dem x86-Compiler](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)