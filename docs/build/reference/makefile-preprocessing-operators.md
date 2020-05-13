---
title: Operatoren für den Präprozessorlauf eines Makefiles
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336474"
---
# <a name="makefile-preprocessing-operators"></a>Operatoren für den Präprozessorlauf eines Makefiles

Makefile-Vorverarbeitungsausdrücke können Operatoren verwenden, die auf konstante Werte, Exitcodes von Befehlen, Zeichenfolgen, Makros und Dateisystempfade angewendet werden. Zum Auswerten des Ausdrucks erweitert der Präprozessor zuerst Makros, führt dann Befehle aus und führt anschließend die Vorgänge durch. Vorgänge werden in der Reihenfolge der expliziten Gruppierung in Klammern ausgewertet und dann in der Reihenfolge der Operatorrangfolge. Das Ergebnis ist ein konstanter Wert.

Der **DEFINED-Operator** ist ein logischer Operator, der auf einen Makronamen wirkt. Der Ausdruck **DEFINED(**_macroname_**)** ist true, wenn *macroname* definiert ist, auch wenn er keinen zugewiesenen Wert hat. **DEFINED** in Kombination mit **! IF** oder **! ELSE IF** entspricht **! IFDEF** oder **! ELSE IFDEF**. Im Gegensatz zu diesen Direktiven kann **DEFINED** jedoch in komplexen Ausdrücken verwendet werden.

Der **EXIST-Operator** ist ein logischer Operator, der auf einen Dateisystempfad einwirkt. **EXIST(**_Pfad_**)** ist true, wenn *Pfad* vorhanden ist. Das Ergebnis von **EXIST** kann in binären Ausdrücken verwendet werden. Wenn *der Pfad* Leerzeichen enthält, schließen Sie ihn in doppelte Anführungszeichen ein.

Um zwei Zeichenfolgen zu**==** vergleichen, verwenden Sie den Operator equality ( ) oder den Inequality (**!=**) Operator. Schließen Sie Zeichenfolgen in doppelte Anführungszeichen ein.

Ganzzahl-Konstanten können die unären Operatoren**-** für numerische Negation**~**( ) verwenden, die Komplementierung ( ), und logische Negation (**!**).

Ausdrücke können die folgenden Operatoren verwenden. Die Operatoren mit gleichem Rang werden zusammengruppiert, und die Gruppen werden absteigender Rangfolge aufgelistet. Unäre Operatoren werden dem Operanden rechts zugeordnet. Binäre Operatoren mit gleichem Rang werden den Operanden von links nach rechts zugeordnet.

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|**DEFINED(** *Makroname* **)**|Erzeugt einen logischen Wert für den aktuellen Definitionsstatus von *macroname*.|
|**EXIST(** *Pfad* **)**|Erzeugt einen logischen Wert für das Vorhandensein einer Datei im *Pfad*.|
|||
|**!**|Unäres logisches NOT.|
|**~**|Unary man ergänzung.|
|**-**|Unäre Negation.|
|||
|**&#42;**|Multiplikation.|
|**/**|Division.|
|**%**|Modul (Rest).|
|||
|**+**|Addition.|
|**-**|Subtraktion.|
|||
|**\<\<**|Bitweise Verschiebung links.|
|**>>**|Bitweise Verschiebung rechts.|
|||
|**\<=**|Kleiner oder gleich.|
|**>=**|Größer oder gleich.|
|**\<**|Kleiner als.|
|**>**|Größer als.|
|||
|**==**|Gleichheit.|
|**!=**|Ungleichheit.|
|||
|**&**|Bitweises AND.|
|**^**|Bitweises XOR.|
|**&#124;**|Bitweises OR.|
|||
|**&&**|Logisches AND.|
|||
|**&#124;&#124;**|Logisches OR.|

> [!NOTE]
> Der bitweise XOR-Operator (**^**) ist identisch mit dem **^^** Escapezeichen und muss bei Verwendung in einem Ausdruck mit escape (as ) versehen werden.

## <a name="see-also"></a>Siehe auch

- [Ausdrücke für den Präprozessorlauf eines Makefiles](expressions-in-makefile-preprocessing.md)
