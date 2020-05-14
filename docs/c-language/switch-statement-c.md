---
title: switch-Anweisung (C)
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
ms.openlocfilehash: eb18b6244318b595e67cc45f99dfcde314866f55
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825677"
---
# <a name="switch-statement-c"></a>`switch`-Anweisung (C)

Die Anweisungen __`switch`__ und __`case`__ helfen beim Steuern von komplexen bedingten Vorgängen und Branchvorgängen. Mit der __`switch`__ -Anweisung wird die Steuerung an eine Anweisung innerhalb des Texts übergeben.

## <a name="syntax"></a>Syntax

> *`selection-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__ &nbsp; *`expression`* &nbsp; __`)`__ &nbsp; *`statement`*

> *`labeled-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__ &nbsp; *`constant-expression`* &nbsp; __`:`__ &nbsp; *`statement`* \
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__ &nbsp; __`:`__ &nbsp; *`statement`*

## <a name="remarks"></a>Hinweise

Eine __`switch`__ -Anweisung bewirkt, dass die Steuerung abhängig vom Wert *`expression`* auf eine *`labeled-statement`* im Anweisungstext übertragen wird.

Die Werte von *`expression`* und jedem *`constant-expression`* müssen einen integralen Typ aufweisen. Ein *`constant-expression`* muss zur Kompilierzeit einen eindeutigen und konstanten Integralwert aufweisen.

Die Steuerung wird an die **`case`** -Anweisung übertragen, deren *`constant-expression`* -Wert mit dem Wert von *`expression`* übereinstimmt. Die __`switch`__ -Anweisung kann eine beliebige Anzahl von __`case`__ -Instanzen enthalten. Es können jedoch keine zwei *`constant-expression`* -Werte innerhalb derselben __`switch`__ -Anweisung denselben Wert aufweisen. Die Ausführung des __`switch`__ -Anweisungstexts beginnt bei der ersten Anweisung in oder nach der passenden *`labeled-statement`* . Die Ausführung verläuft bis zum Ende des Texts oder bis eine __`break`__ -Anweisung die Steuerung aus dem Text überträgt.

Die Verwendung der __`switch`__ -Anweisung sieht in etwa folgendermaßen aus:

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

Sie können mit der __`break`__ -Anweisung die Verarbeitung einer bestimmten Anweisung mit Bezeichnung innerhalb der __`switch`__ -Anweisung beenden. Sie verzweigt sich bis zum Ende der __`switch`__ -Anweisung. Ohne __`break`__ wird das Programm mit der nächsten Anweisung mit Bezeichnung fortgesetzt, und die Anweisungen werden bis zu einer __`break`__ -Anweisung oder dem Ende der Anweisung ausgeführt. Diese Fortsetzung kann in einigen Situationen wünschenswert sein.

Die __`default`__ -Anweisung wird ausgeführt, wenn kein __`case`__ *`constant-expression`* -Wert mit dem Wert von *`expression`* übereinstimmt. Wenn keine __`default`__ -Anweisung vorhanden ist und keine __`case`__ -Übereinstimmung gefunden wird, wird keine der Anweisungen im __`switch`__ -Text ausgeführt. Es kann höchstens eine __`default`__ -Anweisung geben. Die __`default`__ -Anweisung muss nicht am Ende stehen. Sie kann an beliebiger Stelle im Text der __`switch`__ -Anweisung auftauchen. Eine __`case`__ - oder __`default`__ -Bezeichnung kann nur innerhalb einer __`switch`__ -Anweisung erscheinen.

Der Typ von __`switch`__ *`expression`* und __`case`__ *`constant-expression`* muss integral sein. Der Wert von jedem __`case`__ *`constant-expression`* muss innerhalb des Anweisungstexts eindeutig sein.

Die __`case`__ - und __`default`__ -Bezeichnungen des __`switch`__ -Anweisungstexts sind nur im ersten Test wichtig, in dem bestimmt wird, an welcher Stelle des Anweisungstexts die Ausführung beginnt. __`switch`__ -Anweisungen können geschachtelt werden. Alle statischen Variablen werden vor dem Ausführen in einer __`switch`__ -Anweisung initialisiert.

> [!NOTE]
> Deklarationen können im Kopfteil der Verbundanweisung stehen, die den __`switch`__ -Text bildet. In den Deklarationen enthaltene Initialisierungen werden jedoch nicht ausgeführt. Mit der __`switch`__ -Anweisung wird die Steuerung direkt an eine ausführbare Anweisung innerhalb des Texts übertragen. Dabei werden die Zeilen umgangen, die Initialisierungen enthalten.

In den folgenden Beispielen werden __`switch`__ -Anweisungen veranschaulicht:

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

Alle drei Anweisungen des __`switch`__ -Texts in diesem Beispiel werden ausgeführt, wenn `c` gleich `'A'` ist, da vor der folgenden __`case`__ -Anweisung keine __`break`__ -Anweisung steht. Die Ausführungssteuerung wird auf die erste Anweisung (`capital_a++;`) übertragen und im verbleibenden Text der Reihe nach fortgeführt. Wenn `c` gleich `'a'` ist, werden `letter_a` und `total` erhöht. Wenn `c` nicht mit `'A'` oder `'a'` übereinstimmt, wird nur `total` inkrementiert.

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

In diesem Beispiel folgt eine __`break`__ -Anweisung auf jede Anweisung des __`switch`__ -Texts. Die __`break`__ -Anweisung erzwingt eine Beendigung vom Anweisungstext, nachdem eine Anweisung ausgeführt wurde. Wenn `i` gleich -1 ist, wird nur `n` inkrementiert. Die __`break`__ -Anweisung, die auf die `n++;`-Anweisung folgt, führt dazu, dass die Ausführungssteuerung aus dem Anweisungstext übergeben wird und die übrigen Anweisungen übersprungen werden. Wenn `i` gleich 0 ist, wird dementsprechend nur `z` erhöht. Wenn `i` gleich 1 ist, wird nur `p` erhöht. Die abschließende __`break`__ -Anweisung ist nicht unbedingt erforderlich, da die Steuerung am Ende der Verbundanweisung aus dem Text übergeben wird. Aus Konsistenzgründen ist sie jedoch enthalten.

Eine einzelne Anweisung kann wie das folgende Beispiel zeigt mehrere __`case`__ -Bezeichnungen tragen:

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

In Microsoft C wird die Anzahl von __`case`__ -Werten in einer __`switch`__ -Anweisung nicht beschränkt. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass mindestens 257 __`case`__ -Abschnitte in einer __`switch`__ -Anweisung zulässig sind.

Bei Microsoft C sind die Microsoft-Erweiterungen in der default-Einstellung aktiviert. Verwenden Sie die [/Za](../build/reference/za-ze-disable-language-extensions.md)-Compileroption, um diese Erweiterungen zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[switch-Anweisung (C++)](../cpp/switch-statement-cpp.md)
