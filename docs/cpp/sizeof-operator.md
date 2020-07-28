---
title: sizeof-Operator
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 13e181bf84e359d433fbe951b1aa69320a1f0013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186294"
---
# <a name="sizeof-operator"></a>sizeof-Operator

Gibt die Größe des Operanden in Bezug auf die Größe des Typs an **`char`** .

> [!NOTE]
> Weitere Informationen zum `sizeof ...` -Operator finden Sie unter [Ellipsis-und Variadic-Vorlagen](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntax

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Bemerkungen

Das Ergebnis des- **`sizeof`** Operators ist vom Typ `size_t` , ein ganzzahliger Typ, der in der Includedatei definiert ist \<stddef.h> . Mithilfe dieses Operators können Sie es vermeiden, rechnerabhängige Datengrößen in Ihren Programmen anzugeben.

Der Operand für **`sizeof`** kann eine der folgenden sein:

- Ein Typname. Um **`sizeof`** mit einem Typnamen zu verwenden, muss der Name in Klammern eingeschlossen werden.

- Ein Ausdruck. Bei Verwendung mit einem Ausdruck **`sizeof`** kann mit oder ohne Klammern angegeben werden. Der Ausdruck wird nicht ausgewertet.

Wenn der- **`sizeof`** Operator auf ein Objekt vom Typ angewendet wird **`char`** , ergibt er 1. Wenn der- **`sizeof`** Operator auf ein Array angewendet wird, ergibt er die Gesamtzahl der Bytes in diesem Array, nicht die Größe des Zeigers, der durch den Array Bezeichner dargestellt wird. Zum Abrufen der Größe des Zeigers, der durch den Array Bezeichner dargestellt wird, übergeben Sie ihn als Parameter an eine Funktion, die verwendet **`sizeof`** . Zum Beispiel:

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

Wenn der- **`sizeof`** Operator auf einen- **`class`** ,-oder-Typ angewendet wird **`struct`** **`union`** , ist das Ergebnis die Anzahl von Bytes in einem Objekt dieses Typs sowie alle Auffüll Zeichen, die hinzugefügt wurden, um Member an Wortgrenzen auszurichten. Daher stimmt das Ergebnis möglicherweise nicht mit der Größe überein, die durch Addieren der Speicheranforderungen der einzelnen Member berechnet wird. Die [/ZP](../build/reference/zp-struct-member-alignment.md) -Compileroption und das [Pack](../preprocessor/pack.md) -Pragma beeinflussen die Ausrichtungs Grenzen für Member.

Der **`sizeof`** Operator ergibt niemals 0, auch für eine leere Klasse.

Der **`sizeof`** Operator kann nicht mit den folgenden Operanden verwendet werden:

- Funktionen (Kann jedoch **`sizeof`** auf Zeiger auf Funktionen angewendet werden.)

- Bitfelder.

- Nicht definierte Klassen.

- Der Typ **`void`** .

- Dynamisch zugeordnete Arrays.

- Externe Arrays.

- Unvollständige Typen.

- In Klammern gesetzte Namen unvollständiger Typen.

Wenn der- **`sizeof`** Operator auf einen Verweis angewendet wird, ist das Ergebnis das gleiche wie, wenn **`sizeof`** auf das Objekt selbst angewendet wurde.

Wenn ein Array ohne Größen Grad das letzte Element einer Struktur ist, **`sizeof`** gibt der Operator die Größe der Struktur ohne das Array zurück.

Der- **`sizeof`** Operator wird häufig verwendet, um die Anzahl von Elementen in einem Array mithilfe eines Ausdrucks in der Form zu berechnen:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
