---
title: C-Bezeichner
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: 1f3abf304e6fda52e2571d0bccb8d4db5a414dfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325662"
---
# <a name="c-identifiers"></a>C-Bezeichner

"Bezeichner" oder "Symbole" sind die Namen, die Sie für Variablen, Typen, Funktionen und Beschriftungen im Programm angeben. Bezeichnernamen müssen sich bezüglich der Schreibweise und der Groß-/Kleinschreibung von allen Schlüsselwörtern unterscheiden. Sie können Schlüsselwörter (entweder C oder Microsoft) nicht als Bezeichner verwenden. Sie sind zur besonderen Verwendung reserviert. Sie erstellen einen Bezeichner, indem Sie ihn in der Deklaration einer Variablen, eines Typs oder einer Funktion festlegen. In diesem Beispiel ist `result` ein Bezeichner für eine ganzzahlige Variable. `main` und `printf` sind Bezeichnernamen für Funktionen.

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

Sobald der Bezeichner deklariert wurde, können Sie ihn in späteren Programmanweisungen verwenden, um auf den zugeordneten Wert zu verweisen.

Eine besondere Art von Bezeichnern, die als Anweisungsmarken bezeichnet werden, kann in `goto`-Anweisungen verwendet werden. (Deklarationen werden unter [Deklarationen und Typen](../c-language/declarations-and-types.md) und Anweisungsmarken unter [goto-Anweisungen und Anweisungen mit Bezeichnung](../c-language/goto-and-labeled-statements-c.md) erläutert.)

## <a name="syntax"></a>Syntax

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner* *keine Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner* *Ziffer*

*nondigit*: eins von<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **_ a b c d e f g h i j k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T U V W X Y Z**

*digit*: eine von<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

Das erste Zeichen eines Bezeichnernamens muss ein `nondigit`-Wert sein (das heißt, dass das erste Zeichen ein Unterstrich oder ein Groß- oder Kleinbuchstabe sein muss). ANSI ermöglicht die Eingabe von sechs signifikanten Zeichen im Namen eines externen Bezeichners und von 31 signifikanten Zeichen für Namen interner Bezeichner (in einer Funktion). Externe Bezeichner (solche, die im globalen Gültigkeitsbereich oder mit der `extern`-Speicherklasse deklariert wurden) unterliegen möglicherweise zusätzlichen Benennungseinschränkungen, da diese Bezeichner von anderer Software wie Linker verarbeitet werden müssen.

**Microsoft-spezifisch**

Obwohl ANSI 6 signifikante Zeichen in den externen Bezeichnernamen und 31 signifikante Zeichen für Namen interner Bezeichner (in einer Funktion) zulässt, ermöglicht der Microsoft C-Compiler die Eingabe von 247 Zeichen in einen internen oder externen Bezeichnernamen. Wenn ANSI-Kompatibilität nicht erforderlich ist, können Sie diese Vorgabe in eine kleinere oder größere Zahl ändern, indem Sie die Option "/H" (Längenbeschränkung externer Namen) verwenden.

**Ende Microsoft-spezifisch**

Der C-Compiler berücksichtigt Groß- und Kleinbuchstaben als unterschiedliche Zeichen. Dieses Merkmal der "Berücksichtigung der Groß-/Kleinschreibung" ermöglicht es Ihnen, eindeutige Bezeichner zu erstellen, die dieselbe Schreibweise, jedoch eine unterschiedliche Groß- und Kleinschreibung für einzelne Buchstaben aufweisen. Beispielsweise ist jeder der folgenden Bezeichner eindeutig:

```
add
ADD
Add
aDD
```

**Microsoft-spezifisch**

Wählen Sie keinen Namen für Bezeichner aus, die mit zwei Unterstrichen oder mit einem Unterstrich gefolgt von einem Großbuchstaben beginnen. Mit dem ANSI C-Standard können Bezeichnernamen, die mit diesen Zeichenkombinationen beginnen, für die Verwendung durch den Compiler reserviert werden. Bezeichner mit Gültigkeit auf Dateiebene sollten nicht mit einem Unterstrich und einem nachfolgenden Kleinbuchstaben beginnen. Bezeichnernamen, die mit diesen Zeichen beginnen, sind ebenfalls reserviert. Gemäß der Konvention verwendet Microsoft einen Unterstrich und einen Großbuchstaben am Anfang von Makronamen und doppelte Unterstriche für Microsoft-spezifische Schlüsselwortnamen. Um Namenskonflikte zu vermeiden, wählen Sie stets Bezeichnernamen aus, die nicht mit einem oder zwei Unterstrichen beginnen, oder Namen, die mit einem Unterstrich und einem nachfolgenden Großbuchstaben beginnen.

**Ende Microsoft-spezifisch**

Im Folgenden finden Sie Beispiele für gültige Bezeichner, die entweder den ANSI- oder Microsoft-Benennungseinschränkungen entsprechen:

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Microsoft-spezifisch**

Obwohl Bezeichner in den Quelldateien standardmäßig die Groß- und Kleinschreibung berücksichtigen, ist dies bei Symbolen in den Objektdateien nicht der Fall. Microsoft C beachtet die Groß-/Kleinschreibung bei Bezeichnern innerhalb einer Kompilierungseinheit.

Der Microsoft-Linker beachtet die Groß-/Kleinschreibung. Sie müssen alle Bezeichner entsprechend der Groß-/Kleinschreibung einheitlich festlegen.

Beim Quellzeichensatz handelt es sich um einen Satz zulässiger Zeichen, die in den Quelldateien auftreten können. In Microsoft C ist der Quellsatz der ASCII-Standardzeichensatz. Der Quell- und Ausführungszeichensatz enthält die ASCII-Zeichen, die als Escapesequenzen verwendet werden. Weitere Informationen zum Ausführungszeichensatz finden Sie unter [Zeichenkonstanten](../c-language/c-character-constants.md).

**Ende Microsoft-spezifisch**

Ein Bezeichner hat einen "Bereich", bei dem es sich um die Region des Programms handelt, in der es bekannt ist, sowie eine "Bindung", die bestimmt, ob derselbe Name in einem anderen Bereich auf denselben Bezeichner verweist. Diese Themen werden unter [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md) erläutert.

## <a name="see-also"></a>Siehe auch

[C-Elemente](../c-language/elements-of-c.md)
