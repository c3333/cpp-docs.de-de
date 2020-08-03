---
title: Typedef-Deklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: 3d477e33def7168d01f9c5f8a64579fed0b497eb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190064"
---
# <a name="typedef-declarations"></a>Typedef-Deklarationen

Eine typedef-Deklaration ist eine Deklaration mit typedef als Speicherklasse. Der Deklarator wird ein neuer Typ. Sie können typedef-Deklarationen verwenden, um kürzere oder aussagekräftigere Namen für Typen zu erstellen, die bereits von der C-Programmiersprache definiert sind, oder für Typen, die deklariert wurden. Mithilfe von typedef-Namen können Sie die Implementierungsdetails kapseln, die sich möglicherweise ändern.

Eine typedef-Deklaration wird auf die gleiche Weise wie eine Variable oder eine Funktionsdeklaration interpretiert. Der Bezeichner wird allerdings ein Synonym für den Typ, statt den von der Deklaration angegebenen Typ anzunehmen.

## <a name="syntax"></a>Syntax

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer Initialisierungsdeklaratorliste*<sub>opt</sub> **;**

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier declaration-specifiers*<sub>opt</sub>

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`typedef`**

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*typedef-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

Beachten Sie, dass in einer typedef-Deklaration keine Typen erstellt werden. Es werden Synonyme für vorhandene Typen oder Namen für Typen erstellt, die auf andere Weise angegeben werden können. Wenn ein typedef-Name als Typspezifizierer verwendet wird, kann er nur mit bestimmten Typspezifizierern kombiniert werden. Zulässige Modifizierer sind **`const`** und **`volatile`** .

Typedef-Namen verwenden denselben Namespace wie gewöhnliche Bezeichner (weitere Informationen finden Sie unter [Namespaces](../c-language/name-spaces.md)). Aus diesem Grund kann ein Programm einen typedef-Namen und einen Bezeichner für den lokalen Gültigkeitsbereich mit dem gleichen Namen aufweisen. Zum Beispiel:

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

Wenn ein Bezeichner für den lokalen Gültigkeitsbereich mit dem gleichen Namen wie eine typedef deklariert wird oder wenn ein Member einer Struktur oder Union im gleichen Gültigkeitsbereich oder im inneren Bereich deklariert wird, muss der Typspezifizierer angegeben werden. Das folgende Beispiel veranschaulicht diese Einschränkung:

```C
typedef char FlagType;
const FlagType x;
```

Um den `FlagType`-Namen für einen Bezeichner, einen Strukturmember oder einen Unionsmember wiederzuverwenden, muss der Typ angegeben werden:

```C
const int FlagType;  /* Type specifier required */
```

Folgendes ist nicht ausreichend:

```C
const FlagType;      /* Incomplete specification */
```

Das liegt daran, dass `FlagType` als ein Teil des Typs angesehen wird, und nicht als Bezeichner, der neu deklariert wird. Diese Deklaration wird als ungültige Deklaration angesehen, wie etwa

```C
int;  /* Illegal declaration */
```

Sie können einen beliebigen Typ mit typedef deklarieren, einschließlich Zeiger-, Funktions- und Arraytypen. Sie können einen typedef-Namen für einen Zeiger auf einen Struktur- oder einen Union-Typ deklarieren, bevor Sie den Struktur- oder Union-Typ definieren, solange die Definition die gleiche Sichtbarkeit wie die Deklaration aufweist.

Typedef-Namen können verwendet werden, um die Codelesbarkeit zu verbessern. Alle drei der folgenden Deklarationen von `signal` geben genau den gleichen Typ an, wobei der erste keine typedef-Namen verwendet.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Beispiele

Die folgenden Beispiele veranschaulichen typedef-Deklarationen:

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Beachten Sie, dass `WHOLE` jetzt in einer Variablendeklaration wie `WHOLE i;` oder `const WHOLE i;` verwendet werden kann. Die Deklaration `long WHOLE i;` ist hingegen ungültig.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Diese Anweisung deklariert `GROUP` als Strukturtyp mit drei Membern. Da auch ein Strukturtag, `club`, angegeben wird, kann entweder der typedef-Name (`GROUP`) oder das Strukturtag in Deklarationen verwendet werden. Sie müssen das struct-Schlüsselwort mit dem Tag verwenden. Das struct-Schlüsselwort kann nicht mit dem typedef-Namen verwenden werden.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Der Typ `PG` wird als Zeiger auf den `GROUP`-Typ deklariert, der wiederum als Strukturtyp definiert ist.

```C
typedef void DRAWF( int, int );
```

In diesem Beispiel wird der Typ `DRAWF` für eine Funktion bereitgestellt, die keinen Wert zurückgibt und zwei int-Argumente akzeptiert. Dies bedeutet beispielsweise, dass die Deklaration

```C
DRAWF box;
```

äquivalent ist zur Deklaration

```C
void box( int, int );
```

## <a name="see-also"></a>Siehe auch

[Deklarationen und Typen](../c-language/declarations-and-types.md)
