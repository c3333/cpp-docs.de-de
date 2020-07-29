---
title: :::no-loc(switch):::-Anweisung (C)
ms.date: 04/25/2020
f1_keywords:
- ':::no-loc(switch):::'
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C]'
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
ms.openlocfilehash: bdd6885f67728a3c81e395f05c33191156896ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220781"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`-Anweisung (C)

Die Anweisungen **`:::no-loc(switch):::`** und **`:::no-loc(case):::`** helfen beim Steuern von komplexen bedingten Vorgängen und Branchvorgängen. Mit der **`:::no-loc(switch):::`** -Anweisung wird die Steuerung an eine Anweisung innerhalb des Texts übergeben.

## <a name="syntax"></a>Syntax

> *`selection-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(switch)::: (`** &nbsp; *`expression`* &nbsp; **`)`** &nbsp; *`statement`*

> *`labeled-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`** &nbsp; *`constant-expression`* &nbsp; **`:`** &nbsp; *`statement`* \
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`** &nbsp; **`:`** &nbsp; *`statement`*

## <a name="remarks"></a>Hinweise

Eine **`:::no-loc(switch):::`** -Anweisung bewirkt, dass die Steuerung abhängig vom Wert *`expression`* auf eine *`labeled-statement`* im Anweisungstext übertragen wird.

Die Werte von *`expression`* und jedem *`constant-expression`* müssen einen integralen Typ aufweisen. Ein *`constant-expression`* muss zur Kompilierzeit einen eindeutigen und konstanten Integralwert aufweisen.

Die Steuerung wird an die **`:::no-loc(case):::`** -Anweisung übertragen, deren *`constant-expression`* -Wert mit dem Wert von *`expression`* übereinstimmt. Die **`:::no-loc(switch):::`** -Anweisung kann eine beliebige Anzahl von **`:::no-loc(case):::`** -Instanzen enthalten. Es können jedoch keine zwei *`constant-expression`* -Werte innerhalb derselben **`:::no-loc(switch):::`** -Anweisung denselben Wert aufweisen. Die Ausführung des **`:::no-loc(switch):::`** -Anweisungstexts beginnt bei der ersten Anweisung in oder nach der passenden *`labeled-statement`* . Die Ausführung verläuft bis zum Ende des Texts oder bis eine **`:::no-loc(break):::`** -Anweisung die Steuerung aus dem Text überträgt.

Die Verwendung der **`:::no-loc(switch):::`** -Anweisung sieht in etwa folgendermaßen aus:

```C
:::no-loc(switch)::: ( expression )
{
    // declarations
    // . . .
    :::no-loc(case)::: constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        :::no-loc(break):::;
    :::no-loc(default)::::
        // statements executed if expression does not equal
        // any :::no-loc(case)::: constant_expression
}
```

Sie können mit der **`:::no-loc(break):::`** -Anweisung die Verarbeitung einer bestimmten Anweisung mit Bezeichnung innerhalb der **`:::no-loc(switch):::`** -Anweisung beenden. Sie verzweigt sich bis zum Ende der **`:::no-loc(switch):::`** -Anweisung. Ohne **`:::no-loc(break):::`** wird das Programm mit der nächsten Anweisung mit Bezeichnung fortgesetzt, und die Anweisungen werden bis zu einer **`:::no-loc(break):::`** -Anweisung oder dem Ende der Anweisung ausgeführt. Diese Fortsetzung kann in einigen Situationen wünschenswert sein.

Die **`:::no-loc(default):::`** -Anweisung wird ausgeführt, wenn kein **`:::no-loc(case):::`** *`constant-expression`* -Wert mit dem Wert von *`expression`* übereinstimmt. Wenn keine **`:::no-loc(default):::`** -Anweisung vorhanden ist und keine **`:::no-loc(case):::`** -Übereinstimmung gefunden wird, wird keine der Anweisungen im **`:::no-loc(switch):::`** -Text ausgeführt. Es kann höchstens eine **`:::no-loc(default):::`** -Anweisung geben. Die **`:::no-loc(default):::`** -Anweisung muss nicht am Ende stehen. Sie kann an beliebiger Stelle im Text der **`:::no-loc(switch):::`** -Anweisung auftauchen. Eine **`:::no-loc(case):::`** - oder **`:::no-loc(default):::`** -Bezeichnung kann nur innerhalb einer **`:::no-loc(switch):::`** -Anweisung erscheinen.

Der Typ von **`:::no-loc(switch):::`** *`expression`* und **`:::no-loc(case):::`** *`constant-expression`* muss integral sein. Der Wert von jedem **`:::no-loc(case):::`** *`constant-expression`* muss innerhalb des Anweisungstexts eindeutig sein.

Die **`:::no-loc(case):::`** - und **`:::no-loc(default):::`** -Bezeichnungen des **`:::no-loc(switch):::`** -Anweisungstexts sind nur im ersten Test wichtig, in dem bestimmt wird, an welcher Stelle des Anweisungstexts die Ausführung beginnt. **`:::no-loc(switch):::`** -Anweisungen können geschachtelt werden. Alle statischen Variablen werden vor dem Ausführen in einer **`:::no-loc(switch):::`** -Anweisung initialisiert.

> [!NOTE]
> Deklarationen können im Kopfteil der Verbundanweisung stehen, die den **`:::no-loc(switch):::`** -Text bildet. In den Deklarationen enthaltene Initialisierungen werden jedoch nicht ausgeführt. Mit der **`:::no-loc(switch):::`** -Anweisung wird die Steuerung direkt an eine ausführbare Anweisung innerhalb des Texts übertragen. Dabei werden die Zeilen umgangen, die Initialisierungen enthalten.

In den folgenden Beispielen werden **`:::no-loc(switch):::`** -Anweisungen veranschaulicht:

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'A':
        capital_a++;
    :::no-loc(case)::: 'a':
        letter_a++;
    :::no-loc(default)::: :
        total++;
}
```

Alle drei Anweisungen des **`:::no-loc(switch):::`** -Texts in diesem Beispiel werden ausgeführt, wenn `c` gleich `'A'` ist, da vor der folgenden **`:::no-loc(case):::`** -Anweisung keine **`:::no-loc(break):::`** -Anweisung steht. Die Ausführungssteuerung wird auf die erste Anweisung (`capital_a++;`) übertragen und im verbleibenden Text der Reihe nach fortgeführt. Wenn `c` gleich `'a'` ist, werden `letter_a` und `total` erhöht. Wenn `c` nicht mit `'A'` oder `'a'` übereinstimmt, wird nur `total` inkrementiert.

```C
:::no-loc(switch):::( i )
{
    :::no-loc(case)::: -1:
        n++;
        :::no-loc(break):::;
    :::no-loc(case)::: 0 :
        z++;
        :::no-loc(break):::;
    :::no-loc(case)::: 1 :
        p++;
        :::no-loc(break):::;
}
```

In diesem Beispiel folgt eine **`:::no-loc(break):::`** -Anweisung auf jede Anweisung des **`:::no-loc(switch):::`** -Texts. Die **`:::no-loc(break):::`** -Anweisung erzwingt eine Beendigung vom Anweisungstext, nachdem eine Anweisung ausgeführt wurde. Wenn `i` gleich -1 ist, wird nur `n` inkrementiert. Die **`:::no-loc(break):::`** -Anweisung, die auf die `n++;`-Anweisung folgt, führt dazu, dass die Ausführungssteuerung aus dem Anweisungstext übergeben wird und die übrigen Anweisungen übersprungen werden. Wenn `i` gleich 0 ist, wird dementsprechend nur `z` erhöht. Wenn `i` gleich 1 ist, wird nur `p` erhöht. Die abschließende **`:::no-loc(break):::`** -Anweisung ist nicht unbedingt erforderlich, da die Steuerung am Ende der Verbundanweisung aus dem Text übergeben wird. Aus Konsistenzgründen ist sie jedoch enthalten.

Eine einzelne Anweisung kann wie das folgende Beispiel zeigt mehrere **`:::no-loc(case):::`** -Bezeichnungen tragen:

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'a' :
    :::no-loc(case)::: 'b' :
    :::no-loc(case)::: 'c' :
    :::no-loc(case)::: 'd' :
    :::no-loc(case)::: 'e' :
    :::no-loc(case)::: 'f' :  convert_hex(c);
}
```

In diesem Beispiel wird im Fall, dass *constant-expression* einem beliebigen Buchstaben zwischen `'a'` und `'f'` entspricht, die `convert_hex`-Funktion aufgerufen.

### <a name="microsoft-specific"></a>Microsoft-spezifisch

In Microsoft C wird die Anzahl von **`:::no-loc(case):::`** -Werten in einer **`:::no-loc(switch):::`** -Anweisung nicht beschränkt. Die Anzahl wird nur durch den verfügbaren Speicher beschränkt. ANSI C erfordert, dass mindestens 257 **`:::no-loc(case):::`** -Abschnitte in einer **`:::no-loc(switch):::`** -Anweisung zulässig sind.

Bei Microsoft C sind die Microsoft-Erweiterungen in der :::no-loc(default):::-Einstellung aktiviert. Verwenden Sie die [/Za](../build/reference/za-ze-disable-language-extensions.md)-Compileroption, um diese Erweiterungen zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[:::no-loc(switch):::-Anweisung (C++)](../cpp/:::no-loc(switch):::-statement-cpp.md)
