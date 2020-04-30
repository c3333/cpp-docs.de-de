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
ms.openlocfilehash: 5858447602a28dcc5573aa3138e869d106b5aa23
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587376"
---
# <a name="switch-statement-c"></a>`switch`Anweisung (C)

Die __`switch`__ - __`case`__ und-Anweisungen helfen, komplexe bedingte und Verzweigungs Vorgänge zu steuern. Die __`switch`__ -Anweisung überträgt die Steuerung an eine Anweisung innerhalb des Texts.

## <a name="syntax"></a>Syntax

> *`selection-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Bemerkungen

Eine __`switch`__ -Anweisung bewirkt, dass die Steuerung *`labeled-statement`* abhängig vom Wert von *`expression`* zu einer in Ihrem Anweisungs Text übertragen wird.

Die Werte von *`expression`* und jeweils *`constant-expression`* müssen einen ganzzahligen Typ aufweisen. Ein *`constant-expression`* -Wert muss zum Zeitpunkt der Kompilierung einen eindeutigen Konstanten ganzzahligen Wert aufweisen.

Das Steuerelement wird **`case`** an die *`constant-expression`* -Anweisung weitergeleitet, *`expression`* deren Wert dem Wert von entspricht. Die __`switch`__ -Anweisung kann eine beliebige Anzahl __`case`__ von-Instanzen enthalten. In derselben __`switch`__ Anweisung können *`constant-expression`* jedoch nicht zwei Werte denselben Wert aufweisen. Die Ausführung des __`switch`__ Anweisungs Texts beginnt bei der ersten Anweisung in oder nach der *`labeled-statement`* Übereinstimmung. Die Ausführung wird bis zum Ende des Texts fortgesetzt oder bis __`break`__ eine-Anweisung die Steuerung aus dem Text überträgt.

Die __`switch`__ Verwendung der-Anweisung sieht in etwa wie folgt aus:

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

Sie können die- __`break`__ Anweisung verwenden, um die Verarbeitung einer bestimmten beschrifteten Anweisung __`switch`__ innerhalb der-Anweisung zu beenden. Sie verzweigt sich bis zum Ende __`switch`__ der-Anweisung. Ohne __`break`__ wird das Programm mit der nächsten gekennzeichneten Anweisung fortgesetzt, und die Anweisungen werden __`break`__ ausgeführt, bis ein oder das Ende der Anweisung erreicht wird. Diese Fortsetzung ist in einigen Situationen möglicherweise erwünscht.

Die __`default`__ -Anweisung wird ausgeführt, __`case`__ *`constant-expression`* wenn kein Wert gleich dem Wert von *`expression`* ist. Wenn keine __`default`__ -Anweisung vorhanden ist und keine __`case`__ Entsprechung gefunden wird, wird keine der Anweisungen im __`switch`__ Text ausgeführt. Es darf höchstens eine __`default`__ Anweisung vorhanden sein. Die __`default`__ -Anweisung muss nicht am Ende stehen. Es kann an beliebiger Stelle im Hauptteil der __`switch`__ Anweisung vorkommen. Eine __`case`__ - __`default`__ oder-Bezeichnung kann nur innerhalb __`switch`__ einer-Anweisung angezeigt werden.

Der Typ von __`switch`__ *`expression`* und __`case`__ *`constant-expression`* muss ganzzahlig sein. Der Wert jedes __`case`__ *`constant-expression`* muss innerhalb des Anweisungs Texts eindeutig sein.

Die __`case`__ - __`default`__ und-Bezeichnungen __`switch`__ des-Anweisungs Texts sind nur im ersten Test wichtig, der bestimmt, wo die Ausführung im Anweisungs Text beginnt. __`switch`__-Anweisungen können eingebettet werden. Alle statischen Variablen werden vor dem Ausführen in einer __`switch`__ -Anweisung initialisiert.

> [!NOTE]
> Deklarationen können am Anfang der Verbund Anweisung stehen, die den __`switch`__ Text bildet, aber in den Deklarationen enthaltene Initialisierungen werden nicht ausgeführt. Mit __`switch`__ der-Anweisung wird die Steuerung direkt an eine ausführbare Anweisung innerhalb des Texts übertragen. dabei werden die Zeilen umgangen, die Initialisierungen enthalten.

In den folgenden Beispielen __`switch`__ werden-Anweisungen veranschaulicht:

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

Alle drei __`switch`__ Anweisungen des Texts in diesem Beispiel werden ausgeführt `c` `'A'`, wenn gleich ist, da keine __`break`__ Anweisung vor den folgenden __`case`__ erscheint. Die Ausführungssteuerung wird auf die erste Anweisung (`capital_a++;`) übertragen und im verbleibenden Text der Reihe nach fortgeführt. Wenn `c` gleich `'a'` ist, werden `letter_a` und `total` erhöht. Wird `total` nur inkrementiert, `'A'` Wenn `'a'` `c` nicht gleich oder ist.

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

In diesem Beispiel folgt eine __`break`__ -Anweisung auf jede Anweisung des __`switch`__ Texts. Die __`break`__ Anweisung erzwingt eine Beendigung aus dem Anweisungs Text, nachdem eine Anweisung ausgeführt wurde. Wenn `i` gleich -1 ist, wird nur `n` inkrementiert. Die __`break`__ folgende Anweisung `n++;` bewirkt, dass die Ausführungs Steuerung aus dem Anweisungs Text übergeben wird, wobei die restlichen Anweisungen umgangen werden. Wenn `i` gleich 0 ist, wird dementsprechend nur `z` erhöht. Wenn `i` gleich 1 ist, wird nur `p` erhöht. Die abschließende __`break`__ Anweisung ist nicht unbedingt erforderlich, da die Steuerung am Ende der Verbund Anweisung aus dem Text übergeht. Es ist aus Gründen der Konsistenz eingeschlossen.

Eine einzelne Anweisung kann mehrere __`case`__ Bezeichnungen enthalten, wie im folgenden Beispiel gezeigt:

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

Microsoft C schränkt die Anzahl von __`case`__ Werten in einer- __`switch`__ Anweisung nicht ein. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass mindestens __`case`__ 257 Bezeichnungen in einer __`switch`__ -Anweisung zulässig sind.

default Bei Microsoft C sind die Microsoft-Erweiterungen aktiviert. Verwenden Sie die [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption, um diese Erweiterungen zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

[switchAnweisung (C++)](../cpp/switch-statement-cpp.md)
