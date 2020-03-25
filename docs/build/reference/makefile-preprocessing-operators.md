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
ms.openlocfilehash: 2276f6a3c28c6f2fac509ef0e4bc14cce9932582
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170462"
---
# <a name="makefile-preprocessing-operators"></a>Operatoren für den Präprozessorlauf eines Makefiles

Makefile-Vorverarbeitungsausdrücke können Operatoren verwenden, die auf konstante Werte, Exitcodes von Befehlen, Zeichenfolgen, Makros und Dateisystempfade angewendet werden. Zum Auswerten des Ausdrucks erweitert der Präprozessor zuerst Makros, führt dann Befehle aus und führt anschließend die Vorgänge durch. Vorgänge werden in der Reihenfolge der expliziten Gruppierung in Klammern ausgewertet und dann in der Reihenfolge der Operatorrangfolge. Das Ergebnis ist ein konstanter Wert.

Der **definierte** Operator ist ein logischer Operator, der auf einen Makronamen angewendet wird. Der **definierte Ausdruck (** _macroname_ **)** ist true, wenn *macroname* definiert ist, selbst wenn ihm kein Wert zugewiesen ist. **Definiert** in Kombination mit **! Wenn** oder **! Andernfalls, wenn** gleich ist **. Ifdef** oder **! Else ifdef**. Anders als diese Direktiven kann jedoch **definiert** in komplexen Ausdrücken verwendet werden.

Der **exist** -Operator ist ein logischer Operator, der auf einem Dateisystempfad agiert. **Exist (** _Pfad_ **)** ist true, wenn der *Pfad* vorhanden ist. Das Ergebnis von **exist** kann in binären Ausdrücken verwendet werden. Wenn der *Pfad* Leerzeichen enthält, müssen Sie ihn in doppelte Anführungszeichen einschließen.

Um zwei Zeichen folgen zu vergleichen, verwenden Sie den Gleichheits Operator ( **==** ) oder den Ungleichheits Operator ( **! =** ). Schließen Sie Zeichenfolgen in doppelte Anführungszeichen ein.

Ganzzahlige Konstanten können die unären Operatoren für numerische Negation ( **-** ), das Einerkomplement ( **~** ) und die logische Negation ( **!** ) verwenden.

Ausdrücke können die folgenden Operatoren verwenden. Die Operatoren mit gleichem Rang werden zusammengruppiert, und die Gruppen werden absteigender Rangfolge aufgelistet. Unäre Operatoren werden dem Operanden rechts zugeordnet. Binäre Operatoren mit gleichem Rang werden den Operanden von links nach rechts zugeordnet.

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|**Definiert (** *macroname* **)**|Erzeugt einen logischen Wert für den aktuellen Definitions Status von " *macroname*".|
|**Vorhanden (** *Pfad* **)**|Erzeugt einen logischen Wert für das vorhanden sein einer Datei im *Pfad*.|
|||
|**!**|Unäres logisches NOT.|
|**~**|Unäres Einerkomplement.|
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
> Der bitweise XOR-Operator ( **^** ) ist identisch mit dem Escapezeichen und muss mit Escapezeichen versehen werden (wie **^^** ), wenn er in einem Ausdruck verwendet wird.

## <a name="see-also"></a>Weitere Informationen

- [Ausdrücke für die Vorverarbeitung eines Makefiles](expressions-in-makefile-preprocessing.md)
