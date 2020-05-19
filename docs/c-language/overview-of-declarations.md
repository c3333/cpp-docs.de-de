---
title: Übersicht über Deklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 0ffda6522e632533b0aaa4ba146e8fad082ed435
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857059"
---
# <a name="overview-of-declarations"></a>Übersicht über Deklarationen

Eine "Deklaration" gibt die Interpretation und die Attribute eines Satzes von Bezeichnern an. Eine Deklaration, die auch bewirkt, dass Speicher für Objekte oder Funktionen reserviert wird, die vom Bezeichner benannt werden, wird "Definition" genannt. C-Deklarationen für Variablen, Funktionen und Typen haben diese Syntax:

## <a name="syntax"></a>Syntax

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer* *Attributsequenz*<sub>opt</sub> *Initialisierungsdeklaratorliste*<sub>opt</sub> **;**

/\* *Attributsequenz*<sub>opt</sub> ist Microsoft-spezifisch */

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Speicherklassenspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Deklarationsspezifizierer*<sub>opt</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisierungsdeklaratorliste* **,** *Initialisierungsdeklarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator* **=** *Initialisierer*

> [!NOTE]
> Diese Syntax für *declaration* wird in den folgenden Abschnitten nicht wiederholt. Die Syntax in den folgenden Abschnitten beginnt normalerweise mit dem *declarator*-Nichtterminal.

Die Deklarationen in der *init-declarator-list* enthalten die Bezeichner, die benannt werden. *init* ist eine Abkürzung für Initialisierer. Die *init-declarator-list* ist eine durch Komma getrennte Sequenz von Deklaratoren, die jeweils zusätzliche Typinformationen oder einen Initialisierer oder beides enthalten können. *declarator* enthält die Bezeichner, sofern vorhanden, die deklariert werden. Das Nichtterminal *declaration-specifiers* besteht aus einer Sequenz aus Typ- und Speicherklassenspezifizierern, mit denen die Bindung, die Speicherdauer und mindestens der Teil des Typs der Entitäten angegeben werden, die von den Deklaratoren festgelegt werden. Daher bestehen Deklarationen aus einer Kombination aus Speicherklassenspezifizierern, Typspezifizierern, Typqualifizierern, Deklaratoren und Initialisierern.

Deklarationen können mindestens eines der optionalen Attribute enthalten, die in *attribute-seq* aufgelistet sind. *seq* ist eine Abkürzung für Sequenz. Diese Microsoft-spezifischen Attribute führen eine Vielzahl von Funktionen aus, die in diesem Buch im Detail besprochen werden.

In der allgemeinen Form einer Variablendeklaration gibt *type-specifier* den Datentyp der Variablen an. *type-specifier* kann ein zusammengesetztes Element sein, wie in der Typänderung mit **const** oder `volatile`. Der `declarator` gibt den Namen der Variablen an, der möglicherweise so geändert ist, dass ein Array oder ein Zeigertyp deklariert wird. Ein auf ein Objekt angewendeter

```C
int const *fp;
```

deklariert eine Variable mit dem Namen `fp` als Zeiger auf einen nicht veränderbaren (**const**) `int`-Wert. Sie können mehr als eine Variable in einer Deklaration definieren, indem Sie mehrere Deklaratoren verwenden, die durch Kommas getrennt werden.

Eine Deklaration muss mindestens einen Deklarator aufweisen, oder ihr Typspezifizierer muss ein Struktur-Tag, ein Union-Tag oder Member einer Enumeration deklarieren. Deklaratoren stellen alle verbleibenden Informationen über einen Bezeichner bereit. Ein Deklarator ist ein Bezeichner, der mit eckigen Klammern ( **[ ]** ), Sternchen (<strong>\*</strong>) oder runden Klammern ( **( )** ) geändert werden kann, um jeweils ein Array, einen Zeiger oder einen Funktionstyp zu deklarieren. Wenn Sie einfache Variablen (wie Zeichen, ganze Zahlen und Gleitkommawerte) oder Strukturen und Unions einfacher Variablen deklarieren, ist `declarator` nur ein Bezeichner. Weitere Informationen über Deklaratoren finden Sie im Artikel über [Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md).

Alle Definitionen sind implizite Deklarationen, aber nicht alle Deklarationen sind Definitionen. So sind beispielsweise Variablendeklarationen, die mit dem `extern`-Speicherklassenspezifizierer beginnen, eher "verweisende" als "definierende" Deklarationen. Wenn auf eine externe Variable verwiesen wird, bevor sie definiert wurde, oder wenn sie in einer anderen Quelldatei als derjenigen definiert wird, in der sie verwendet wird, ist eine `extern`-Deklaration erforderlich. Der Speicher wird nicht durch "verweisende" Deklarationen zugeordnet. Außerdem können Variablen nicht in Deklarationen initialisiert werden.

Variablendeklarationen erfordern eine Speicherklasse oder einen Typ (oder beides). Mit Ausnahme von `__declspec` ist nur ein Speicherklassenspezifizierer in einer Deklaration zulässig. Außerdem sind nicht alle Speicherklassenspezifizierer in jedem Kontext gestattet. Die `__declspec`-Speicherklasse ist mit anderen Speicherklassenspezifizierern zulässig, zudem ist sie mehrmals zulässig. Der Speicherklassenspezifizierer einer Deklaration beeinflusst, wie das deklarierte Element gespeichert und initialisiert wird und welche Teile eines Programms auf das Element verweisen können.

Die in C definierten *storage-class-specifier*-Terminale umfassen **auto**, `extern`, **register**, **static** und `typedef`. Darüber hinaus ist auch das *storage-class-specifier*-Terminal `__declspec` in Microsoft C enthalten. Alle *storage-class-specifier*-Terminale außer `typedef` und `__declspec` werden in den [Speicherklassen](../c-language/c-storage-classes.md) erläutert. Weitere Informationen zu `typedef` finden Sie im Artikel über [Typedef-Deklarationen](../c-language/typedef-declarations.md). Weitere Informationen zu `__declspec` erhalten Sie im Artikel über [erweiterte Speicherklassenattribute](../c-language/c-extended-storage-class-attributes.md).

Der Speicherort der Deklaration innerhalb des Quellprogramms und das Vorhandensein oder Nichtvorhandensein anderer Deklarationen der Variablen sind wichtige Faktoren für die Bestimmung der Lebensdauer von Variablen. Es können mehrere Neudeklarationen, jedoch nur eine Definition erstellt werden. Eine Definition kann jedoch in mehr als einer Übersetzungseinheit vorhanden sein. Für Objekte mit interner Verknüpfung gilt diese Regel für jede Übersetzungseinheit gesondert, da intern verknüpfte Objekte für eine Übersetzungseinheit eindeutig sind. Für Objekte mit externer Verknüpfung gilt diese Regel für das gesamte Programm. Weitere Informationen zur Sichtbarkeit erhalten Sie im Artikel über [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md).

Typspezifizierer stellen einige Informationen zu den Datentypen von Bezeichnern bereit. Der Standardtypbezeichner ist `int`. Weitere Informationen finden Sie im Artikel über [Typbezeichner](../c-language/c-type-specifiers.md). Typspezifizierer können auch Typ-Tags, Namen von Strukturkomponenten und Union-Komponenten sowie Enumerationskonstanten definieren. Weitere Informationen finden Sie in den Artikeln über [Enumerationsdeklarationen](../c-language/c-enumeration-declarations.md), [Strukturdeklarationen](../c-language/structure-declarations.md) und [Union-Deklarationen](../c-language/union-declarations.md).

Es gibt zwei *type-qualifier*-Terminale: **const** und `volatile`. Mit diesen Qualifizierern werden zusätzliche Eigenschaften von Typen angegeben, die nur relevant sind, sofern ein Zugriff auf Objekte dieses Typs über L-Werte erfolgt. Weitere Informationen zu **const** und `volatile` finden Sie im Artikel über [Typqualifizierer](../c-language/type-qualifiers.md). Eine Definition des l-Werts erhalten Sie im Artikel über [L-Wert- und R-Wert-Ausdrücke](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Siehe auch

[Zusammenfassung der C-Sprachsyntax](../c-language/c-language-syntax-summary.md)<br/>
[Deklarationen und Typen](../c-language/declarations-and-types.md)<br/>
[Zusammenfassung der Deklarationen](../c-language/summary-of-declarations.md)
