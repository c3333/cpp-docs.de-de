---
title: '##define-Anweisung (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: e9e5b7a02ee55c05aa44278fbceb9c42f372c443
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506663"
---
# <a name="define-directive-cc"></a>#define-Direktive (C/C++)

Der **#define** erstellt ein- *Makro*, das die Zuordnung eines Bezeichners oder eines parametrisierten Bezeichners zu einer Tokenzeichenfolge ist. Nachdem das Makro definiert wurde, kann der Compiler die Tokenzeichenkette für jedes Vorkommen des Bezeichners in der Quelldatei ersetzen.

## <a name="syntax"></a>Syntax

> **#define** *Bezeichnertoken* *-Zeichen*folgen<sub>opt</sub>\
> **#define** *Bezeichner* **(** *identifier*<sub>bezeichneropt</sub>**,** ... **,** *bezeichneropt*<sub>opt</sub> **)** *Token-Zeichen*folgen<sub>opt</sub>

## <a name="remarks"></a>Bemerkungen

Die **#define** -Direktive bewirkt, dass der Compiler *Tokenzeichenfolgen* für jedes Vorkommen des *Bezeichners* in der Quelldatei ersetzt. Der *Bezeichner* wird nur ersetzt, wenn er ein Token bildet. Das heißt, dass der *Bezeichner* nicht ersetzt wird, wenn er in einem Kommentar, in einer Zeichenfolge oder als Teil eines längeren Bezeichners erscheint. Weitere Informationen finden Sie unter [Tokens](../cpp/character-sets.md).

Das *Tokenzeichenfolgen-* Argument besteht aus einer Reihe von Token, wie z. b. Schlüsselwörtern, Konstanten oder Complete-Anweisungen. Ein oder mehrere Leerzeichen müssen eine *Tokenzeichenfolge* vom *Bezeichner*trennen. Diese Leerstelle und alle weiteren Leerstellen nach dem letzten Token des Texts werden nicht als Teil des ersetzten Texts betrachtet.

Ein `#define` ohne *Tokenzeichenfolge* entfernt das Vorkommen des *Bezeichners* aus der Quelldatei. Der *Bezeichner* bleibt definiert und kann mithilfe der `#if defined` Direktiven und getestet werden `#ifdef` .

Durch das zweite Syntaxformat wird ein funktionsähnliches Makro mit Parametern definiert. Dieses Formular akzeptiert eine optionale Liste von Parametern, die in Klammern angegeben sein müssen. Nachdem das Makro definiert wurde, wird jedes nachfolgende Vorkommen des *Bezeichners*( *bezeichneropt*<sub>opt</sub>,..., *identifier*<sub>bezeichneropt</sub> ) durch eine Version des *tokenzeichenfolgenarguments* ersetzt, das über tatsächliche Argumente für formale Parameter verfügt.

Formale Parameternamen werden in *Tokenzeichenfolge* angezeigt, um die Orte zu markieren, an denen tatsächliche Werte ersetzt werden. Jeder Parameter Name kann in der *Tokenzeichenfolge*mehrmals vorkommen, und die Namen können in beliebiger Reihenfolge angezeigt werden. Die Anzahl von Argumenten im Aufruf muss mit der Anzahl von Parametern in der Makrodefinition übereinstimmen. Mit der großzügigen Verwendung von Klammern wird sichergestellt, dass komplexe tatsächliche Argumente richtig interpretiert werden.

Die formalen Parameter in der Liste werden durch Kommas getrennt. Jeder Name in der Liste muss eindeutig sein und die Liste muss in Klammern eingeschlossen werden. Der *Bezeichner* und die öffnende Klammer können von keinem Leerzeichen getrennt werden. Verwenden Sie die Zeilen Verkettung – platzieren Sie einen umgekehrten Schrägstrich ( `\` ) direkt vor dem Zeilen Umleitungs Zeichen – für lange Direktiven in mehreren Quellzeilen. Der Gültigkeitsbereich eines formalen Parameter namens wird auf die neue Zeile erweitert, die *Tokenzeichenfolge*beendet.

Wenn ein Makro im zweiten Syntaxformat definiert wurde, geben nachfolgende Textinstanzen, auf die eine Argumentliste folgt, einen Makro-Aufruf an. Die tatsächlichen Argumente, die auf eine Instanz des *Bezeichners* in der Quelldatei folgen, werden mit den entsprechenden formalen Parametern in der Makro Definition abgeglichen. Jedem formalen Parameter in einer *Tokenzeichenfolge* , dem kein `#` `#@` Zeichen folgen Operator (), Zeichen folgen Operator () oder tokeneinfügenden `##` Operator () oder nicht gefolgt von einem `##` Operator vorangestellt wird, wird durch das entsprechende tatsächliche Argument ersetzt. Alle Makros im tatsächlichen Argument werden erweitert, bevor die Anweisung den formalen Parameter ersetzt. (Die Operatoren werden in [Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)beschrieben.)

In den folgenden Beispielen für Makros mit Argumenten wird die zweite Form der **#define** Syntax veranschaulicht:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

Argumente mit Nebeneffekten können dazu führen, dass Makros unerwartete Ergebnisse erzeugen. Ein bestimmter formaler Parameter kann mehrmals in der *Tokenzeichenfolge*angezeigt werden. Wenn der formale Parameter durch einen Ausdruck mit Nebeneffekten ersetzt wird, dann wird der Ausdruck samt seinen Nebeneffekten evtl. mehrmals ausgewertet. (Weitere Informationen finden Sie in den Beispielen unter [Operator zum Einfügen von Token (# #)](../preprocessor/token-pasting-operator-hash-hash.md).)

Die `#undef`-Anweisung führt dazu, dass die Präprozessordefinition eines Bezeichners übergangen wird. Weitere Informationen finden Sie in [der #undef-Direktive](../preprocessor/hash-undef-directive-c-cpp.md) .

Wenn der Name des zu definierenden Makros in der *Tokenzeichenfolge* auftritt (auch als Ergebnis einer anderen Makro Erweiterung), wird er nicht erweitert.

Eine zweite **#define** für ein Makro mit demselben Namen generiert eine Warnung, es sei denn, die zweite tokensequenz ist mit der ersten identisch.

**Microsoft-spezifisch**

Mit Microsoft C/C++ können Sie ein Makro neu definieren, wenn die neue Definition mit der ursprünglichen Definition syntaktisch identisch ist. Das bedeutet, dass die beiden Definitionen über unterschiedliche Parameternamen verfügen können. Dieses Verhalten unterscheidet sich von ANSI C, was erfordert, dass die beiden Definitionen lexikalisch identisch sind.

Beispielsweise sind die folgenden beiden Makros identisch, abgesehen von den Parameternamen. ANSI c lässt eine solche Neudefinition nicht zu, aber Microsoft C/C++ kompiliert es ohne Fehler.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

Andererseits sind die folgenden beiden Makros nicht identisch und generieren in Microsoft C/C++ eine Warnung.

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**Ende Microsoft-spezifisch**

In diesem Beispiel wird die **#define** -Direktive veranschaulicht:

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

Die erste Anweisung definiert den Bezeichner `WIDTH` als die ganzzahlige Konstante 80 und definiert `LENGTH` hinsichtlich `WIDTH` und der ganzzahligen Konstante 10. Jedes Vorkommen von `LENGTH` wird ersetzt durch (`WIDTH + 10`). Im Gegenzug wird jedes Vorkommen von `WIDTH + 10` durch den Ausdruck (`80 + 10`) ersetzt. Die Klammern um `WIDTH + 10` sind wichtig, da sie die Interpretation in Anweisungen steuern, z. B.:

```C
var = LENGTH * 20;
```

Nach der Vorverarbeitungsphase wird die Anweisung:

```C
var = ( 80 + 10 ) * 20;
```

zu 1800 ausgewertet. Ohne Klammern wird das Ergebnis:

```C
var = 80 + 10 * 20;
```

Dies ergibt 280.

**Microsoft-spezifisch**

Das Definieren von Makros und Konstanten mit der [/D](../build/reference/d-preprocessor-definitions.md) -Compileroption hat dieselbe Auswirkung wie die Verwendung einer **#define** Vorverarbeitungs Direktive am Anfang der Datei. Maximal 30 Makros können mit der /D-Option definiert werden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Präprozessoranweisungen](../preprocessor/preprocessor-directives.md)
