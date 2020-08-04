---
title: Funktionsrumpf
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 2ae73ab4ca91e06e3b6cd41166a8d05ae0857e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229700"
---
# <a name="function-body"></a>Funktionsrumpf

Ein *Funktionsrumpf* entspricht einer Verbundanweisung mit den Anweisungen, die die Aufgabe der Funktion angeben.

## <a name="syntax"></a>Syntax

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer*<sub>opt</sub> *Attributsequenz*<sub>opt</sub> *Deklarator* *Deklarationsliste*<sub>opt</sub> *compound-Anweisung*

/\* *Attributsequenz* ist Microsoft-spezifisch \*/

*compound-statement*: /\* Der Funktionsrumpf \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Deklarationsliste*<sub>opt</sub> *Anweisungsliste*<sub>opt</sub> **}**

Variablen, die in einem Funktionsrumpf deklariert werden, sogenannte *lokale Variablen*, weisen die Speicherklasse **`auto`** auf, sofern nicht anders angegeben. Wenn die Funktion aufgerufen wird, wird Speicherplatz für die lokalen Variablen erstellt, und lokale Initialisierungen werden ausgeführt. Die Ausführungssteuerung wird an die erste Anweisung in *compound-statement* übergeben und fortgesetzt, bis eine **`return`** -Anweisung ausgeführt wurde oder das Ende des Funktionsrumpfs erreicht wird. Anschließend wird die Steuerung wieder an den Punkt zurückgegeben, an dem die Funktion aufgerufen wurde.

Eine **`return`** -Anweisung, die einen Ausdruck enthält, muss ausgeführt werden, wenn die Funktion einen Wert zurückgeben soll. Der Rückgabewert einer Funktion ist nicht definiert, wenn keine **`return`** -Anweisung ausgeführt wird oder wenn die **`return`** -Anweisung keinen Ausdruck enthält.

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
