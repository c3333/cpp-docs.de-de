---
title: Speicherklasse
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: 872a014dfc7c21b46f9af810f1cb3463016c7e09
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211683"
---
# <a name="storage-class"></a>Speicherklasse

Der Speicherklassenspezifizierer in einer Funktionsdefinition gibt für die Funktion entweder die Speicherklasse **`extern`** oder **`static`** an.

## <a name="syntax"></a>Syntax

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer*<sub>opt</sub> *Attributsequenz*<sub>opt</sub> *Deklarator* *Deklarationsliste*<sub>opt</sub> *compound-Anweisung*

/\* *Attributsequenz* ist Microsoft-spezifisch \*/

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Speicherklassenspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Deklarationsspezifizierer*<sub>opt</sub>

*storage-class-specifier*: /\* Für Funktionsdefinitionen \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`extern`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`static`**

Wenn kein *Speicherklassenspezifizierer* in einer Funktionsdefinition enthalten ist, verwendet die Speicherklasse standardmäßig **`extern`** . Sie können eine Funktion explizit als **`extern`** deklarieren, dies ist jedoch nicht erforderlich.

Wenn die Deklaration einer Funktion den *Speicherklassenspezifizierer* **`extern`** enthält, hat der Bezeichner dieselben Verknüpfungen wie jede sichtbare Deklaration des Bezeichners mit Dateigültigkeitsbereich. Wenn es keine sichtbare Deklaration mit Dateigültigkeitsbereich gibt, verfügt der Bezeichner über externe Verknüpfung. Wenn ein Bezeichner über einen Dateigültigkeitsbereich, aber nicht über *storage-class-specifier* verfügt, hat der Bezeichner keine externe Verknüpfung. Externe Verknüpfung bedeutet, dass jede Instanz des Bezeichners das gleiche Objekt bzw. die gleiche Funktion bezeichnet. Weitere Informationen zu Verknüpfungen und zum Dateigültigkeitsbereich erhalten Sie im Artikel über [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md).

Funktionsdeklarationen für Blockbereiche mit einem anderen Speicherklassenspezifizierer als **`extern`** führen zu Fehlern.

Eine Funktion mit der Speicherklasse **`static`** wird nur innerhalb der Quelldatei angezeigt, in der sie definiert ist. Alle andere Funktionen sind unabhängig davon, ob ihnen die Speicherklasse **`extern`** explizit oder implizit zugewiesen wurde, in allen Quelldateien im Programm sichtbar. Wenn die Speicherklasse **`static`** benötigt wird, muss diese beim ersten Vorkommen einer Funktionsdeklaration deklariert werden (sofern vorhanden) und in der Definition der Funktion deklariert werden.

**Microsoft-spezifisch**

Wenn die Microsoft-Erweiterungen aktiviert sind, wird einer Funktion, die ursprünglich ohne Speicherklasse (oder mit der Speicherklasse **`extern`** ) deklariert wurde, die Speicherklasse **`static`** zugewiesen, wenn sich die Funktionsdefinition in derselben Quelldatei befindet und die Definition explizit die Speicherklasse **`static`** angibt.

Beim Kompilieren mit der Compileroption „/Ze“ verfügen Funktionen über globale Sichtbarkeit, die in einem Block mit dem Schlüsselwort **`extern`** deklariert wurden. Dies gilt nicht beim Kompilieren mit "/Za". Auf diese Funktion sollte nicht zurückgegriffen werden, wenn die Portabilität von Quellcode zu berücksichtigen ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
