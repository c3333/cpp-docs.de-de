---
title: Zusammenfassung der Präprozessorgrammatik (C/C++)
description: Definiert und beschreibt die Syntax der präprozessorgrammatik von Microsoft C/C++ Compiler (MSVC).
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 68e5f09acfc6444afb46bcbc0f7e9db10b04afed
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076877"
---
# <a name="preprocessor-grammar-summary-cc"></a>Zusammenfassung der Präprozessorgrammatik (C/C++)

In diesem Artikel wird die formale Grammatik des C- C++ und des Präprozessors beschrieben. Es behandelt die Syntax von Vorverarbeitungs Direktiven und Operatoren. Weitere Informationen finden Sie unter [Präprozessordirektiven](../preprocessor/preprocessor.md) und [pragma-Direktiven und das __Pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="definitions-for-the-grammar-summary"></a><a name="definitions"></a>Definitionen für die Grammatik Zusammenfassung

Bei Terminalen handelt es sich um Endpunkte in einer Syntaxdefinition. Es ist keine andere Auflösung möglich. Terminale enthalten den Satz reservierter Wörter und benutzerdefinierter Bezeichner.

Bei Nichtterminalen handelt es sich um Platzhalter in der Syntax. Die meisten sind an anderer Stelle in dieser Syntaxzusammenfassung definiert. Definitionen können rekursiv sein. Die folgenden nicht Terminals sind im Abschnitt " [lexikalische Konventionen](../cpp/lexical-conventions.md) " der  *C++ Sprachreferenz*definiert:

*Constant*, *Constant-Expression*, *Identifier*, *Schlüsselwort*, *Operator*, *Satzzeichen*

Eine optionale Komponente wird durch das tiefgestellte <sub>opt</sub> angegeben. Beispielsweise gibt die folgende Syntax einen optionalen Ausdruck an, der in geschweiften Klammern eingeschlossen ist:

**{** *Expression*<sub>opt</sub> **}**

## <a name="document-conventions"></a><a name="conventions"></a>Dokument Konventionen

Die Konventionen verwenden verschiedene Schriftartattribute für unterschiedliche Syntaxkomponenten. Die Symbole und die Schriftarten lauten wie folgt:

| attribute | BESCHREIBUNG |
|---------------|-----------------|
| *nonterminal* | Kursivschrift gibt Nichtterminale an. |
| **#include** | Fett formatierte Terminale sind literale, reservierte Symbole und Wörter, die wie gezeigt eingegeben werden müssen. Bei Zeichen in diesem Kontext wird immer die Groß-/Kleinschreibung beachtet. |
| <sub>opt</sub> | Nichtterminale, auf die <sub>opt</sub> folgt, sind immer optional.|
| Standardschriftart | Zeichen des in dieser Schriftart beschriebenen oder aufgeführten Satzes können als Terminale in C-Anweisungen verwendet werden. |

Ein Doppelpunkt ( **:** ) nach einem Nichtterminal führt ihre Definition ein. Alternative Definitionen werden in separaten Zeilen aufgeführt.

In Code Syntax Blöcken haben diese Symbole in der Standard Schriftart eine besondere Bedeutung:

| Symbol | BESCHREIBUNG |
|---|---|
| \[ ] | Eckige Klammern umgeben ein optionales Element. |
| {\|} | Geschweifte Klammern umschließen Alternative Elemente, die durch vertikale Balken voneinander getrennt sind. |
| ... | Gibt an, dass das vorherige Element Muster wiederholt werden kann. |

In Code Syntax Blöcken sind Kommas (`,`), Punkte (`.`), Semikolons (`;`), Doppelpunkte (`:`), Klammern (`( )`), doppelte Anführungszeichen (`"`) und einfache Anführungszeichen (`'`) Literale.

## <a name="preprocessor-grammar"></a><a name="grammar"></a>Präprozessorgrammatik

*Steuerungs Zeile*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *Bezeichnertoken* *-Zeichen*folgen<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *Bezeichner* **(** *bezeichneropt*<sub>opt</sub> **...** **,** *bezeichneropt*<sub>opt</sub> **)** *Tokenzeichenfolge*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _path-spec_ **"** \
&nbsp;&nbsp; **&nbsp;&nbsp;#include\<** _Pfadspezifikationen_>\
&nbsp;&nbsp;&nbsp;&nbsp; **#Line** **"** _Dateiname_ **"** <sub>opt</sub> der *Ziffern Sequenz*\
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *Bezeichners*\
&nbsp;&nbsp;&nbsp;&nbsp; **#Error** *Tokenzeichenfolge*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *Tokenzeichenfolge*

*Constant-Expression*: \
&nbsp;&nbsp;&nbsp;&nbsp;**definiert (** *Bezeichner* **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**definierten** *Bezeichner*\
&nbsp;&nbsp;&nbsp;&nbsp;eines beliebigen anderen konstanten Ausdrucks

*bedingt*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-Part* *elif-Parts*<sub>opt</sub> *else-Part*<sub>opt</sub> *EndIf-Line*

*if-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-Line-* *Text*

*if-Line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *Konstante Ausdruck*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *Bezeichners*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *Bezeichner*

*elif-Parts*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif-Line-* *Text*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-Parts* *elif-Line* *Text*

*elif-Line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *konstanter Ausdruck*

*else-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-Line-* *Text*

*else-Zeile*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*EndIf-Zeile*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#EndIf**

*Ziffern Sequenz*: \
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffer*\
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffern Sequenz* *digit*

*Ziffer*: eine von \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*Tokenzeichenfolge*: \
&nbsp;&nbsp;&nbsp;&nbsp;Zeichenfolge von Token

*Token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*Schlüsselwort*\
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichners*\
&nbsp;&nbsp;&nbsp;&nbsp;*Konstante*\
&nbsp;&nbsp;&nbsp;&nbsp;*Operator*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*Dateiname*: \
&nbsp;&nbsp;&nbsp;&nbsp;gültiger Betriebssystem-Dateiname

*Pfadspezifikation*: \
&nbsp;&nbsp;&nbsp;&nbsp;Gültiger Dateipfad

*Text*: \
&nbsp;&nbsp;&nbsp;&nbsp;eine beliebige Text Sequenz aus.

> [!NOTE]
> Die folgenden nicht terminale werden im Abschnitt " [lexikalische Konventionen](../cpp/lexical-conventions.md) " der  *C++ Sprachreferenz*erweitert: *Konstante*, *konstanter Ausdruck*, *Bezeichner*, *Schlüsselwort*, *Operator*und *interpunktator*.

## <a name="see-also"></a>Weitere Informationen

[C/C++ präprozessorverweis](../preprocessor/c-cpp-preprocessor-reference.md)
