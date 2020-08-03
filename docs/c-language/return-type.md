---
title: Rückgabetyp
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 1d905e02be02784b562b9d1a8f72a9bfa4057b9b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226326"
---
# <a name="return-type"></a>Rückgabetyp

Der Rückgabetyp einer Funktion legt die Größe und den Typ des Werts fest, der von der Funktion zurückgegeben wird, und dem Typspezifizierer in der folgenden Syntax entspricht:

## <a name="syntax"></a>Syntax

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer*<sub>opt</sub> *Attributsequenz*<sub>opt</sub> *Deklarator* *Deklarationsliste*<sub>opt</sub> *compound-Anweisung*

/\* *Attributsequenz* ist Microsoft-spezifisch \*/

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Speicherklassenspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Deklarationsspezifizierer*<sub>opt</sub>

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int8`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int16`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int32`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int64`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-specifier* kann einen beliebigen grundlegenden, Struktur- oder Union-Typ angeben. Wenn Sie keinen *Typspezifizierer* angeben, wird der Rückgabetyp **`int`** angenommen.

Der Rückgabetyp, der in der Funktionsdefinition angegeben ist, muss dem Rückgabetyp in der Funktionsdeklarationen an anderer Stelle im Programm entsprechen. Eine Funktion gibt einen Wert zurück, wenn eine **`return`** -Anweisung ausgeführt wird, die einen Ausdruck enthält. Der Ausdruck wird ausgewertet, in den Rückgabewert konvertiert, falls erforderlich, und an den Punkt zurückgegeben, an dem die Funktion aufgerufen wurde. Wenn eine Funktion mit dem Rückgabetyp **`void`** deklariert wird, generiert eine return-Anweisung, die einen Ausdruck enthält, eine Warnung, und der Ausdruck wird nicht ausgewertet.

Die folgenden Beispiele veranschaulichen Funktionsrückgabewerte.

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

In diesem Beispiel wird der Typ `STUDENT` mit einer **`typedef`** -Deklaration definiert. Außerdem wird die Funktion `sortstu` so definiert, dass sie über den Rückgabetyp `STUDENT` verfügt. Die Funktion wählt eines ihrer beiden Strukturargumente aus und gibt dieses zurück. Bei nachfolgenden Aufrufen der Funktion überprüft der Compiler, ob die Argumenttypen `STUDENT` sind.

> [!NOTE]
> Effizienz wird erhöht, indem Zeiger auf die Struktur, statt auf die gesamte Struktur übergeben werden.

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

In diesem Beispiel wird eine Funktion definiert, die einen Zeiger an ein Zeichenarray zurückgibt. Die Funktion ruft zwei Zeichenarrays (Zeichenfolgen) als Argumente ab und gibt einen Zeiger auf die kürzere der beiden Zeichenfolgen zurück. Ein Zeiger auf ein Array zeigt auf das erste Arrayelement und weist den gleichen Typ auf wie dieses. Daher ist der Rückgabetyp der Funktion ein Zeiger auf den Typ **`char`** .

Funktionen mit dem Rückgabetyp **`int`** müssen vor dem Aufrufen nicht deklariert werden. Prototypen werden jedoch empfohlen, um eine ordnungsgemäße Typüberprüfung für Argumente und Rückgabewerte zu ermöglichen.

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
