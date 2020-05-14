---
title: C-Enumerationsdeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: bc238dd0088558233d84f8bbd15d06743e133449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326013"
---
# <a name="c-enumeration-declarations"></a>C-Enumerationsdeklarationen

Eine Enumeration besteht aus einem Satz von benannten ganzzahligen Konstanten. Die Deklaration eines Enumerationstyps gibt den Namen des (optionalen) Enumerationstags an und definiert den Satz benannter ganzzahliger Bezeichner (bezeichnet als "Enumerationssatz", "Enumeratorkonstanten", "Enumeratoren" oder "Member"). Eine Variable mit Enumerationstyp speichert einen der Werte des Enumerationssatzes, der durch diesen Typ definiert ist.

Variablen des Typs `enum` können in Indizierungsausdrücken und als Operanden aller arithmetischen und relationalen Operatoren verwendet werden. Enumerationen bieten eine Alternative zur Präprozessordirektive `#define` und bieten den Vorteil, dass die Werte für Sie generiert werden und normalen Bereichsregeln folgen.

In ANSI C weisen die Ausdrücke, die den Wert einer Enumeratorkonstante definieren, immer den `int`-Typ auf. Folglich ist der einer Enumerationsvariable zugeordnete Speicher der für einen einzelnen `int`-Wert benötigte Speicher. Eine Enumerationskonstante oder ein Wert des enumerierten Typs kann überall dort verwendet werden, wo die Programmiersprache C einen ganzzahligen Ausdruck gestattet.

## <a name="syntax"></a>Syntax

*enum-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *Bezeichner*<sub>opt</sub> **{** *enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifier*

Der optionale Wert *identifier* benennt den von *enumerator-list* definierten Enumerationstyp. Dieser Bezeichner wird oft als „Tag“ der Enumeration bezeichnet, die von der Liste angegeben wird. Ein Typspezifizierer der Art

```
enum identifier
{
    enumerator-list
}
```

deklariert *identifier* als Tag der Enumeration, die vom *enumerator-list*-Nichtterminal spezifiziert wird. Der „Enumeratorinhalt“ wird von *enumerator-list* definiert. Nachfolgend wird *enumerator-list* ausführlich beschrieben.

Falls die Deklaration eines Tags sichtbar ist, geben nachfolgende Deklarationen, die das Tag verwenden, *enumerator-list* jedoch weglassen, den zuvor deklarierten enumerierten Typ an. Das Tag muss auf einen definierten Enumerationstyp verweisen, der sich im aktuellen Bereich befindet. Da der Enumerationstyp an einer anderen Stelle definiert ist, wird *enumerator-list* in dieser Deklaration nicht angezeigt. Deklarationen von Typen, die aus Enumerationen abgeleitet sind, und `typedef`-Deklarationen für Enumerationstypen können das Enumerationstag vor der Definition des Enumerationstyps verwenden.

## <a name="syntax"></a>Syntax

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator-list* **,** *enumerator*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant* **=** *constant-expression*

*enumeration-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

Jeder *enumeration-constant*-Wert in *enumeration-list* benennt einen Wert des Enumerationssatzes. Standardmäßig wird der erste *enumeration-constant*-Wert mit dem Wert 0 verknüpft. Der folgende *enumeration-constant*-Listeneintrag wird mit dem Wert von ( *constant-expression* + 1) verknüpft, außer er wird explizit einem anderen Wert zugeordnet. Der Name von *enumeration-constant* entspricht dessen Wert.

Sie können mit *enumeration-constant = constant-expression* die Standardabfolge der Werte überschreiben. Wird also *enumeration-constant = constant-expression* in *enumerator-list* angezeigt, wird *enumeration-constant* dem Wert zugeordnet, der von *constant-expression* bereitgestellt wird. *constant-expression* muss den `int`-Typ aufweisen und kann negativ sein.

Die folgenden Regeln gelten für Member eines Enumerationssatzes:

- Ein Enumerationssatz kann doppelte konstante Werte enthalten. Beispielsweise könnten Sie den Wert 0 für zwei verschiedene Bezeichner mit den Namen `null` und `zero` im gleichen Satz zuweisen.

- Die Bezeichner in der Enumerationsliste müssen sich von anderen Bezeichnern im gleichen Bereich mit der gleichen Sichtbarkeit – das schließt gewöhnliche Variablennamen und Bezeichner in anderen Enumerationslisten ein – unterscheiden.

- Enumerationstags folgen normalen Bereichsregeln. Sie müssen sich von anderen Enumerations-, Struktur- und Union-Tags mit derselben Sichtbarkeit unterscheiden.

## <a name="examples"></a>Beispiele

Diese Beispiele veranschaulichen Enumerationsdeklarationen:

```
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

```
enum DAY today = wednesday;
```

Beachten Sie, dass der Name der Enumerationskonstante zum Zuweisen des Werts verwendet wird. Da zuvor der Enumerationstyp `DAY` deklariert wurde, ist nur das Enumerationstag `DAY` erforderlich.

Um einen ganzzahligen Wert explizit der Variable des enumerierten Datentyps zuzuweisen, verwenden Sie eine Typumwandlung:

```
workday = ( enum DAY ) ( day_value - 1 );
```

Diese Umwandlung ist in C empfohlen, aber nicht erforderlich.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Diese Deklaration kann auch so angegeben werden:

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

Oder so:

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Ein Beispiel mit diesen Variablen könnte folgendermaßen aussehen:

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Auch unbenannte Enumeratordatentypen können deklariert werden. Der Name des Datentyps wird weggelassen, aber Variablen lassen sich deklarieren. Die Variable `response` ist eine Variable des definierten Typs:

```
enum { yes, no } response;
```

## <a name="see-also"></a>Siehe auch

[Enumerationen](../cpp/enumerations-cpp.md)
