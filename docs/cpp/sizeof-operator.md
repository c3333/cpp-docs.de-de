---
title: sizeof-Operator
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 8789bb5e0e363458edffa7207ea1e138aae4d284
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365569"
---
# <a name="sizeof-operator"></a>sizeof-Operator

Ergibt die Größe seines Operanden in Bezug auf die Größe des Typs **char**.

> [!NOTE]
> Weitere Informationen `sizeof ...` zum Operator finden Sie unter [Ellipsen und Variadic Templates](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntax

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Bemerkungen

Das Ergebnis der **Größe des** `size_t`Operators ist vom Typ , \<einem integralen Typ, der in der Includedatei stddef.h> definiert ist. Mithilfe dieses Operators können Sie es vermeiden, rechnerabhängige Datengrößen in Ihren Programmen anzugeben.

Der Operand bis **zur Größe** kann einer der folgenden sein:

- Ein Typname. Um **sizeof** mit einem Typnamen zu verwenden, muss der Name in Klammern eingeschlossen werden.

- Ein Ausdruck. Bei Verwendung mit einem Ausdruck kann **sizeof** mit oder ohne Klammern angegeben werden. Der Ausdruck wird nicht ausgewertet.

Wenn der **Sizeof-Operator** auf ein Objekt vom Typ **char**angewendet wird, ergibt er 1. Wenn der **Sizeof-Operator** auf ein Array angewendet wird, ergibt er die Gesamtzahl der Bytes in diesem Array, nicht die Größe des Zeigers, der durch den Arraybezeichner dargestellt wird. Um die Größe des Zeigers zu erhalten, der durch den Arraybezeichner dargestellt wird, übergeben Sie ihn als Parameter an eine Funktion, die **sizeof**verwendet. Beispiel:

## <a name="example"></a>Beispiel

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>Beispielausgabe

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Wenn der **Sizeof-Operator** auf eine **Klasse**, **eine Struktur**oder einen **Union-Typ** angewendet wird, ist das Ergebnis die Anzahl der Bytes in einem Objekt dieses Typs sowie alle Auffüllungen, die hinzugefügt werden, um Member an Wortgrenzen auszurichten. Daher stimmt das Ergebnis möglicherweise nicht mit der Größe überein, die durch Addieren der Speicheranforderungen der einzelnen Member berechnet wird. Die [/Zp-Compileroption](../build/reference/zp-struct-member-alignment.md) und das [Pack-Pragma](../preprocessor/pack.md) wirken sich auf Ausrichtungsgrenzen für Member aus.

Der **Sizeof-Operator** ergibt nie 0, auch nicht für eine leere Klasse.

Der **Sizeof-Operator** kann nicht mit den folgenden Operanden verwendet werden:

- Funktionen (Die **Größe** des kann jedoch auf Zeiger auf Funktionen angewendet werden.)

- Bitfelder.

- Nicht definierte Klassen.

- Der Typ **void**.

- Dynamisch zugeordnete Arrays.

- Externe Arrays.

- Unvollständige Typen.

- In Klammern gesetzte Namen unvollständiger Typen.

Wenn der **Operator "Sizeof"** auf einen Verweis angewendet wird, entspricht das Ergebnis dem, als ob **die Größe auf** das Objekt selbst angewendet worden wäre.

Wenn ein nicht geerzielztes Array das letzte Element einer Struktur ist, gibt der **Sizeof-Operator** die Größe der Struktur ohne das Array zurück.

Der **Sizeof-Operator** wird häufig verwendet, um die Anzahl der Elemente in einem Array mithilfe eines Ausdrucks des Formulars zu berechnen:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
