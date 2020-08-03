---
title: Union-Deklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: 3414a478ec741351f1e1540a214cca38c029749f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213696"
---
# <a name="union-declarations"></a>Union-Deklarationen

Eine „Unionsdeklaration“ gibt einen Satz Variablenwerte und optional ein Tag an, der die Union benennt. Die Variablenwerte werden als "Member" der Union bezeichnet und können unterschiedliche Typen aufweisen. Unions ähneln varianten Datensätzen in anderen Sprachen.

## <a name="syntax"></a>Syntax

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*<sub>opt</sub> **{** *Strukturdeklarationsliste* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`union`**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklarationsliste* *Strukturdeklaration*

Der Unioninhalt wird definiert als

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Spezifizierer-/Qualifiziererliste* *Strukturdeklaratorliste*  **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklaratorliste*  **,**  *Strukturdeklarator*

Eine Variable vom Typ **`union`** speichert einen der von diesem Typ definierten Werte. Die gleichen Regeln steuern Struktur- und Uniondeklarationen. Unions können auch Bitfelder aufweisen.

Member von Unions können nicht über einen unvollständigen Typ, den Typ **`void`** oder einen Funktionstyp verfügen. Daher können Member keine Instanz der Union sein, können aber Zeiger auf den Uniontyp sein, der deklariert wird.

Eine Uniontypdeklaration ist nur eine Vorlage. Arbeitsspeicher wird nicht reserviert, bis die Variable deklariert ist.

> [!NOTE]
> Wenn eine Union von zwei Typen deklariert wird und ein Wert gespeichert ist, aber mit dem anderen Typ auf die Union zugegriffen wird, sind die Ergebnisse unzuverlässig. Beispielsweise wird eine Union von **`float`** und **`int`** deklariert. Ein **`float`** -Wert wird gespeichert, aber später greift das Programm auf den Wert als **`int`** zu. In einer solchen Situation ist der Wert von der internen Speicherung von **`float`** -Werten abhängig. Der Ganzzahlwert wäre nicht zuverlässig.

## <a name="examples"></a>Beispiele

Nachstehend einige Beispiele für Unions:

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

In diesem Beispiel wird eine Unionvariable mit dem `sign`-Typ definiert und die Variable `number` mit zwei Membern deklariert: `svar`, eine ganze Zahl mit Vorzeichen, und `uvar`, eine ganze Zahl ohne Vorzeichen. Diese Deklaration ermöglicht das Speichern des aktuellen Werts von `number` als Wert mit Vorzeichen oder ohne Vorzeichen. Das Tag, das diesem Uniontyp zugeordnet ist, ist `sign`.

```C
union               /* Defines a two-dimensional */
{                   /*  array named screen */
    struct
    {
      unsigned int icon : 8;
      unsigned color : 4;
    } window1;
    int screenval;
} screen[25][80];
```

Das `screen`-Array enthält 2.000 Elemente. Jedes Element des Arrays ist eine einzelne Union mit zwei Membern: `window1` und `screenval`. Der Member `window1` ist eine Struktur mit zwei Bitfeldmembern, `icon` und `color`. Der Member `screenval` ist ein Wert vom Typ **`int`** . Zu jedem Zeitpunkt enthält jedes Unionelement entweder den durch `screenval` dargestellten **`int`** -Wert oder die durch `window1` dargestellte Struktur.

**Microsoft-spezifisch**

Geschachtelte Unions können anonym deklariert werden, wenn sie Member einer anderen Struktur oder Union sind. Dies ist ein Beispiel für eine namenlose Union:

```C
struct str
{
    int a, b;
    union            / * Unnamed union */
    {
      char c[4];
      long l;
      float f;
   };
   char c_array[10];
} my_str;
.
.
.
my_str.l == 0L;  /* A reference to a field in the my_str union */
```

Unions werden häufig in einer Struktur geschachtelt, die ein Feld enthält, das den Typ der Daten angibt, die in der Union zu einem bestimmten Zeitpunkt enthalten sind. Dies ist ein Beispiel für die Deklaration einer solchen Union:

```C
struct x
{
    int type_tag;
    union
    {
      int x;
      float y;
    }
}
```

Weitere Informationen über den Verweis auf Unions finden Sie unter [Struktur- und Union-Elemente](../c-language/structure-and-union-members.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
