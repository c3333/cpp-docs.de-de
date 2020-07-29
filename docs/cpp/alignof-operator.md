---
title: alignof-Operator
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
ms.openlocfilehash: 6a2046774674858211ae89abb9b4cfc7b09c0a6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227633"
---
# <a name="alignof-operator"></a>alignof-Operator

Der- **`alignof`** Operator gibt die Ausrichtung des angegebenen Typs in Bytes als Wert des Typs zurück **`size_t`** .

## <a name="syntax"></a>Syntax

```cpp
alignof( type )
```

## <a name="remarks"></a>Bemerkungen

Zum Beispiel:

| expression | Wert |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

Der **`alignof`** Wert ist identisch mit dem Wert für **`sizeof`** für grundlegende Typen. Betrachten Sie jedoch das Beispiel:

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

In diesem Fall entspricht der **`alignof`** Wert der Ausrichtungs Anforderung des größten Elements in der Struktur.

Entsprechend gilt:

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)` ist gleich `32`.

Eine Verwendung für **`alignof`** wäre als Parameter für eine ihrer eigenen Speicher Belegungs Routinen. Beispielsweise könnten Sie angesichts der folgenden definierten Struktur `S` eine Speicherbelegungsroutine mit dem Namen `aligned_malloc` aufrufen, um einen bestimmten Grenzwert mit Speicher zu belegen.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

Weitere Informationen über das Ändern der Ausrichtung finden Sie unter:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/ZP (Strukturelement Ausrichtung)](../build/reference/zp-struct-member-alignment.md)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

Weitere Informationen zu den Unterschieden bei der Ausrichtung im Code für x86 und x64 finden Sie unter:

- [Konflikte mit dem x86-Compiler](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>Microsoft-spezifisch

**`alignof`** und **`__alignof`** sind Synonyme im Microsoft-Compiler. Bevor es Teil des Standards in c++ 11 wurde, stellte der Microsoft-spezifische **`__alignof`** Operator diese Funktionalität bereit. Zur maximalen Portabilität sollten Sie den **`alignof`** -Operator anstelle des Microsoft-spezifischen **`__alignof`** Operators verwenden.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_alignof`** ein Synonym für, **`__alignof`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
