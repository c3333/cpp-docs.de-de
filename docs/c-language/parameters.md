---
title: Parameter
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 78ad91ea86d81a3b6d888335ba7b78399a1d2aea
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032069"
---
# <a name="parameters"></a>Parameter

Argumente sind Namen von Werten, die einer Funktion durch einen Funktionsaufruf übergeben werden. Parameter sind die Werte, deren Empfang die Funktion erwartet. In einem Funktionsprototyp enthalten die Klammern nach dem Funktionsnamen eine vollständige Liste der Funktionsparameter und ihrer Typen. Parameterdeklarationen geben die Typen, Größen und Bezeichner der Werte an, die in den Parametern gespeichert sind.

## <a name="syntax"></a>Syntax

*Funktionsdefinition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribut-seq* ist Microsoft-spezifisch\*/

*Deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *Direct-Deklarator*

*Direktdeklarator*:\* / Ein Funktionsdeklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direktdeklarator***(***Parametertypliste***)**  / \* Neuer Deklarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direktdeklarator***(***Identifier-List*<sub>opt</sub> **)**  / \* Obsolete-Style Deklarator    \*/

*parameter-type-list*:\* / Die Parameterliste\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameterliste* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameterliste* **, ...**

*Parameterliste*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameter-Deklaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameterliste* **,**  *Parameter-Deklaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

Die *parameter-type-list* ist eine Folge von Parameterdeklarationen, die durch Trennzeichen getrennt sind. Die Form jedes Parameters in einer Parameterliste sieht wie folgt aus:

```C
[register]  type-specifier [declarator]
```

Funktionsparameter, die mit dem Attribut **auto** deklariert sind, generieren Fehler. Die Bezeichner der Parameter werden im Funktionstext verwendet und beziehen sich auf die Werte, die der Funktion übergeben werden. Sie können die Parameter in einem Prototyp benennen, aber die Namen verlassen den Gültigkeitsbereich am Ende der Deklaration. Daher können Parameternamen in der Funktionsdefinition auf die gleiche Weise oder anders zugewiesen werden. Diese Bezeichner können im äußersten Block des Funktionstexts nicht neu definiert werden, sie können jedoch in inneren, geschachtelten Blöcken neu definiert werden, als wäre die Parameterliste ein einschließender Block.

Jedem Bezeichner in *parameter-type-list* muss der entsprechende Typspezifizierer vorangestellt werden, wie in diesem Beispiel gezeigt:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Wenn mindestens ein Parameter in der Parameterliste auftritt, kann die Liste mit einem Komma gefolgt von drei Punkten (**, ... )** enden. Diese Konstruktion, die als "Ellipsennotation" bezeichnet wird, gibt eine variable Anzahl von Argumenten für die Funktion an. (Weitere Informationen finden Sie unter [Aufrufe mit einer Variablenanzahl von Argumenten.)](../c-language/calls-with-a-variable-number-of-arguments.md) Ein Aufruf der Funktion muss jedoch mindestens so viele Argumente haben, wie vor dem letzten Komma Parameter vorhanden sind.

Wenn keine Argumente an die Funktion übergeben werden sollen, wird die Liste der Parameter durch das Schlüsselwort `void` ersetzt. Diese Verwendung von `void` unterscheidet sich von der Verwendung als Typspezifizierer.

Reihenfolge und Typ der Parameter, einschließlich aller Auslassungsnotationen, müssen in allen Funktionsdeklarationen (falls vorhanden) und in der Funktionsdefinition gleich sein. Die Typen der Argumente nach üblichen arithmetische Konvertierungen müssen mit den Typen der entsprechenden Parameter zuweisungskompatibel sein. (Informationen zu arithmetischen Konvertierungen finden Sie unter [Übliche arithmetische Konvertierungen.)](../c-language/usual-arithmetic-conversions.md) Argumente, die auf die Auslassung folgen, werden nicht überprüft. Basis, Struktur, Union, Zeiger oder Arraytyp eines Parameters können beliebig sein.

Der Compiler führt die üblichen arithmetischen Konvertierungen unabhängig für jeden Parameter und ggf. für jedes Argument aus. Nach der Konvertierung ist kein Parameter kürzer als `int`, und kein Parameter verfügt über einen **float**-Typ, es sei denn, der Parametertyp ist explizit als **float** im Prototyp angegeben. Dies bedeutet beispielsweise, dass die Deklaration eines Parameters als `char` denselben Effekt hat wie eine Deklaration als `int`.

## <a name="see-also"></a>Weitere Informationen

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
