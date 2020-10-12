---
title: C-Enumerationsdeklarationen
description: Enumerationsdeklarationen in der Programmiersprache C
ms.date: 10/02/2020
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: b7df41475a630b9f6e1d735f5454f6d9601cdd16
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765212"
---
# <a name="c-enumeration-declarations"></a>C-Enumerationsdeklarationen

Eine Enumeration besteht aus einem Satz von benannten ganzzahligen Konstanten. Eine Enumerationstypdeklaration gibt den Namen des (optionalen) Enumerationstags an. Darüber hinaus definiert sie die angegebenen ganzzahligen Bezeichner (*Enumerationssatz*, *Enumeratorkonstanten*, *Enumeratoren* oder *Member* genannt). Eine Variable vom Typ Enumeration speichert einen der Werte des Enumerationssatzes, der durch diesen Typ definiert wird.

Variablen des Typs **`enum`** können in Indizierungsausdrücken und als Operanden aller arithmetischen und relationalen Operatoren verwendet werden. Enumerationen bieten eine Alternative zur Präprozessordirektive `#define` und bieten den Vorteil, dass die Werte für Sie generiert werden und normalen Bereichsregeln folgen.

In ANSI C sind die Ausdrücke, die den Wert einer Enumeratorkonstante definieren, immer vom Typ **`int`** . Dies bedeutet, dass der Speicher, der einer Enumerationsvariablen zugeordnet ist, dem Speicher entspricht, der für einen einzelnen **`int`** -Wert erforderlich ist. Eine Enumerationskonstante oder ein Wert des enumerierten Typs kann überall dort verwendet werden, wo die Programmiersprache C einen ganzzahligen Ausdruck gestattet.

## <a name="syntax"></a>Syntax

*`enum-specifier`*:\
&emsp; **`enum`** *`identifier`* <sub>opt</sub> **`{`** *`enumerator-list`* **`}`** \
&emsp;**`enum`** *`identifier`*

*`enumerator-list`*:\
&emsp;*`enumerator`*\
&emsp;*`enumerator-list`* **`,`** *`enumerator`*

*`enumerator`*:\
&emsp;*`enumeration-constant`*\
&emsp;*`enumeration-constant`* **`=`** *`constant-expression`*

*`enumeration-constant`*:\
&emsp;*`identifier`*

Der optionale Bezeichner ( *`identifier`* ) gibt den durch *`enumerator-list`* definierten Enumerationstyp an. Dieser Bezeichner wird oft als „Tag“ der Enumeration bezeichnet, die von der Liste angegeben wird. Ein Typspezifizierer deklariert `identifier` als Tag der Enumeration, die vom *`enumerator-list`* -Nichtterminal spezifiziert wird, wie hier zu sehen:

```C
enum identifier
{
    // enumerator-list
}
```

*`enumerator-list`* definiert die Member des Enumerationssatzes.

Wenn die Deklaration eines Tags sichtbar ist, geben nachfolgende Deklarationen, die das Tag verwenden, *`enumerator-list`* jedoch weglassen, den zuvor deklarierten Aufzählungstyp an. Das Tag muss auf einen definierten Enumerationstyp verweisen, der sich im aktuellen Bereich befindet. Da der Enumerationstyp an anderer Stelle definiert ist, wird *`enumerator-list`* in dieser Deklaration nicht verwendet. Deklarationen von Typen, die aus Enumerationen abgeleitet sind, und **`typedef`** -Deklarationen für Enumerationstypen können das Enumerationstag vor der Definition des Enumerationstyps verwenden.

*`enumeration-constant`* in *`enumerator-list`* gibt immer einen Wert des Enumerationssatzes an. Standardmäßig wird der ersten *`enumeration-constant`* der Wert 0 (null) zugeordnet. Dem nächsten *`enumeration-constant`* -Listeneintrag wird der Wert ( *`constant-expression`* + 1) zugeordnet, außer Sie ordnen ihm explizit einem anderen Wert zu. Der Name einer *`enumeration-constant`* entspricht ihrem Wert.

Sie können *`enumeration-constant`*  =  *`constant-expression`* verwenden, um die Standardwertesequenz außer Kraft zu setzen. Das heißt, wenn *`enumeration-constant`*  =  *`constant-expression`* in *`enumerator-list`* verwendet wird, wird *`enumeration-constant`* der in *`constant-expression`* festgelegte Wert zugeordnet. *`constant-expression`* muss vom Typ **`int`** sein und kann negativ sein.

Die folgenden Regeln gelten für Member eines Enumerationssatzes:

- Ein Enumerationssatz kann doppelte konstante Werte enthalten. Beispielsweise könnten Sie den Wert 0 (null) zwei verschiedenen Bezeichnern, z. B. Membern mit den Namen `null` und `zero`, im selben Satz zuweisen.

- Die Bezeichner in der Enumerationsliste müssen sich von anderen Bezeichnern im selben Bereich mit der gleichen Sichtbarkeit unterscheiden. Dies schließt gewöhnliche Variablennamen und Bezeichner in anderen Enumerationslisten ein.

- Enumerationstags folgen normalen Bereichsregeln. Sie müssen sich von anderen Enumerations-, Struktur- und Union-Tags mit derselben Sichtbarkeit unterscheiden.

## <a name="examples"></a>Beispiele

Diese Beispiele veranschaulichen Enumerationsdeklarationen:

```C
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

Der Wert 0 wird standardmäßig `saturday` zugeordnet. Der Bezeichner `sunday` wird explizit auf 0 festgelegt. Den verbleibenden Bezeichnern werden standardmäßig die Werte 1 bis 5 zugewiesen.

In diesem Beispiel wird ein Wert aus dem `DAY`-Satz der Variable `today` zugewiesen.

```C
enum DAY today = wednesday;
```

Der Name der Enumerationskonstante wird zum Zuweisen des Werts verwendet. Da zuvor der Enumerationstyp `DAY` deklariert wurde, ist nur das Enumerationstag `DAY` erforderlich.

Um einen ganzzahligen Wert explizit der Variable des enumerierten Datentyps zuzuweisen, verwenden Sie eine Typumwandlung:

```C
workday = ( enum DAY ) ( day_value - 1 );
```

Diese Umwandlung wird in C empfohlen, ist aber nicht erforderlich.

```C
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Diese Deklaration kann auch so angegeben werden:

```C
enum BOOLEAN { false, true } end_flag, match_flag;\
```

Oder so:

```C
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Ein Beispiel mit diesen Variablen könnte folgendermaßen aussehen:

```C
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Auch unbenannte Enumeratordatentypen können deklariert werden. Der Name des Datentyps wird weggelassen, aber Variablen lassen sich deklarieren. Die Variable `response` ist eine Variable des definierten Typs:

```C
enum { yes, no } response;
```

## <a name="see-also"></a>Siehe auch

[Enumerationen](../cpp/enumerations-cpp.md)
