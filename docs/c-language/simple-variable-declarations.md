---
title: Einfache Variablendeklarationen
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 42547828e78566982053d22e8288fe1ccbe6e26b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229531"
---
# <a name="simple-variable-declarations"></a>Einfache Variablendeklarationen

Die Deklaration einer einfachen Variable, die einfachste Form eines direkten Deklarators, gibt den Namen und den Typ der Variable an. Sie gibt auch die Speicherklasse und den Datentyp für die Variable an.

Variablendeklarationen erfordern Speicherklassen oder Typen (oder beides). Nicht typisierte Variablen (wie `var;`) generieren Warnungen.

## <a name="syntax"></a>Syntax

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direkter-Deklarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner* *keine Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner* *Ziffer*

Bei arithmetischen Typen, Struktur-, Union-, Enumerations- und void-Typen sowie bei durch **`typedef`** -Namen dargestellten Typen können einfache Deklaratoren in einer Deklaration verwendet werden, da der Typspezifizierer alle Typisierungsinformationen bereitstellt. Zeiger-, Array- und Funktionstypen benötigen komplexere Deklaratoren.

Sie können eine Liste mit durch Komma ( **,** ) getrennten Bezeichnern verwenden, um mehrere Variablen in der gleichen Deklaration anzugeben. Alle Variablen, die in der Deklaration definiert sind, weisen denselben Basistyp auf. Zum Beispiel:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Die Variablen `x` und `y` können einen beliebigen Wert des Satzes enthalten, der vom **`int`** -Typ für eine bestimmte Implementierung definiert wird. Das einfache Objekt `z` wird auf den Wert 1 initialisiert und ist nicht änderbar.

Falls die Deklaration von `z` für eine nicht initialisierte statische Variable oder für den Dateibereich bestimmt wäre, erhielte sie den Anfangswert 0, und dieser Wert wäre nicht änderbar.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

In diesem Beispiel weisen sowohl `reply` als auch `flag` einen **`unsigned long`** -Typ auf und enthalten Ganzzahlwerte ohne Vorzeichen.

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
