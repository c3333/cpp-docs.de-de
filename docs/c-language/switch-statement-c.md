---
title: switchAnweisung (C)
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167675"
---
# <a name="opno-locswitch-statement-c"></a>switchAnweisung (C)

Die **switch** - **case** und-Anweisungen helfen, komplexe bedingte und Verzweigungs Vorgänge zu steuern. Die **switch** -Anweisung überträgt die Steuerung an eine Anweisung innerhalb des Texts.

## <a name="syntax"></a>Syntax

*Auswahl-Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***Expression* **`)`** - *Anweisung*

*Bezeichnung-Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *Constant-Expression***`:`**-*Anweisung*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *an*

Das Steuerelement wird an die **case** Anweisung weitergeleitet, deren *Konstantenausdruck* mit dem Wert von ** switch (** *Ausdruck* **)** übereinstimmt. Die **switch** -Anweisung kann eine beliebige Anzahl **case** von-Instanzen enthalten. Es können jedoch keine case zwei Konstanten innerhalb derselben **switch** Anweisung denselben Wert aufweisen. Die Ausführung des Anweisungs Texts beginnt bei der ausgewählten Anweisung. Es wird bis zum Ende des Texts fortgesetzt oder bis eine **break** -Anweisung die Steuerung aus dem Text überträgt.

Die **switch** Verwendung der-Anweisung sieht in etwa wie folgt aus:

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

Sie können die- **break** Anweisung verwenden, um die Verarbeitung einer bestimmten beschrifteten Anweisung **switch** innerhalb der-Anweisung zu beenden. Sie verzweigt sich bis zum Ende **switch** der-Anweisung. Ohne **break** wird das Programm mit der nächsten gekennzeichneten Anweisung fortgesetzt, und die Anweisungen werden **break** ausgeführt, bis ein oder das Ende der Anweisung erreicht wird. Diese Fortsetzung ist in einigen Situationen möglicherweise erwünscht.

Die **default** -Anweisung wird ausgeführt, **case** wenn kein *konstanter Ausdruck* gleich dem Wert von ** switch (** *Expression* **)** ist. Wenn keine **default** -Anweisung vorhanden ist und keine **case** Entsprechung gefunden wird, wird keine der Anweisungen im **switch** Text ausgeführt. Es darf höchstens eine **default** Anweisung vorhanden sein. Die **default** -Anweisung muss nicht am Ende stehen. Es kann an beliebiger Stelle im Hauptteil der **switch** Anweisung vorkommen. Eine **case** - **default** oder-Bezeichnung kann nur innerhalb **switch** einer-Anweisung angezeigt werden.

Der Typ von **switch** *Ausdruck* und **case** *Constant-Expression* müssen ganzzahlig sein. Der Wert jedes **case** *konstanten Ausdrucks* muss innerhalb des Anweisungs Texts eindeutig sein.

Die **case** - **default** und-Bezeichnungen **switch** des-Anweisungs Texts sind nur im ersten Test wichtig, der bestimmt, wo die Ausführung im Anweisungs Text beginnt. **switch**-Anweisungen können eingebettet werden. Alle statischen Variablen werden vor dem Ausführen in einer **switch** -Anweisung initialisiert.

> [!NOTE]
> Deklarationen können am Anfang der Verbund Anweisung stehen, die den **switch** Text bildet, aber in den Deklarationen enthaltene Initialisierungen werden nicht ausgeführt. Mit **switch** der-Anweisung wird die Steuerung direkt an eine ausführbare Anweisung innerhalb des Texts übertragen. dabei werden die Zeilen umgangen, die Initialisierungen enthalten.

In den folgenden Beispielen **switch** werden-Anweisungen veranschaulicht:

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

Alle drei **switch** Anweisungen des Texts in diesem Beispiel werden ausgeführt `c` `'A'`, wenn gleich ist, da keine **break** Anweisung vor den folgenden caseerscheint. Die Ausführungssteuerung wird auf die erste Anweisung (`capital_a++;`) übertragen und im verbleibenden Text der Reihe nach fortgeführt. Wenn `c` gleich `'a'` ist, werden `letter_a` und `total` erhöht. Wird `total` nur inkrementiert, `'A'` Wenn `'a'` `c` nicht gleich oder ist.

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

In diesem Beispiel folgt eine **break** -Anweisung auf jede Anweisung des **switch** Texts. Die **break** Anweisung erzwingt eine Beendigung aus dem Anweisungs Text, nachdem eine Anweisung ausgeführt wurde. Wenn `i` gleich -1 ist, wird nur `n` inkrementiert. Die **break** folgende Anweisung `n++;` bewirkt, dass die Ausführungs Steuerung aus dem Anweisungs Text übergeben wird, wobei die restlichen Anweisungen umgangen werden. Wenn `i` gleich 0 ist, wird dementsprechend nur `z` erhöht. Wenn `i` gleich 1 ist, wird nur `p` erhöht. Die abschließende **break** Anweisung ist nicht unbedingt erforderlich, da die Steuerung am Ende der Verbund Anweisung aus dem Text übergeht. Es ist aus Gründen der Konsistenz eingeschlossen.

Eine einzelne Anweisung kann mehrere **case** Bezeichnungen enthalten, wie im folgenden Beispiel gezeigt:

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

In diesem Beispiel wird im Fall, dass *constant-expression* einem beliebigen Buchstaben zwischen `'a'` und `'f'` entspricht, die `convert_hex`-Funktion aufgerufen.

### <a name="microsoft-specific"></a>Microsoft-spezifisch

Microsoft C schränkt die Anzahl von case Werten in einer- **switch** Anweisung nicht ein. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass mindestens case 257 Bezeichnungen in einer **switch** -Anweisung zulässig sind.

default Bei Microsoft C sind die Microsoft-Erweiterungen aktiviert. Verwenden Sie die [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption, um diese Erweiterungen zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen:

[switchAnweisung (C++)](../cpp/switch-statement-cpp.md)
