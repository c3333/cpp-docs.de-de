---
title: Anweisungen für den Präprozessorlauf eines Makefiles
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170487"
---
# <a name="makefile-preprocessing-directives"></a>Anweisungen für den Präprozessorlauf eines Makefiles

Bei Vorverarbeitungs Anweisungen wird nicht zwischen Groß-und Kleinschreibung Das erste Ausrufezeichen (!) muss am Anfang der Zeile angezeigt werden. Nach dem Ausrufezeichen für den Einzug können NULL oder mehr Leerzeichen oder Tabstopps angezeigt werden.

- `!CMDSWITCHES` {`+` &#124; `-`}-*Option* ...

   Schaltet die einzelnen *Optionen* ein oder aus. Leerzeichen oder Tabstopps müssen vor dem `+` oder `-` Operator angezeigt werden. Es können keine zwischen dem Operator und den [options Buchstaben](running-nmake.md#nmake-options)angezeigt werden. Bei Buchstaben wird nicht zwischen Groß-und Kleinschreibung unterschieden, und Sie werden ohne Schrägstrich (`/` Um einige Optionen zu aktivieren und andere zu deaktivieren, verwenden Sie separate Spezifikationen `!CMDSWITCHES`.

   Nur/D,/I,/N und/S können in einem Makefile verwendet werden. In "Tools. ini" sind alle Optionen mit Ausnahme von/F,/Help,/nologo,/X und/? zulässig. Änderungen, die in einem Beschreibungsblock angegeben werden, werden bis zum nächsten Beschreibungsblock nicht wirksam. Diese Direktive aktualisiert **MAKEFLAGS**. Änderungen werden während der Rekursion geerbt, wenn **MAKEFLAGS** angegeben wird.

- `!ERROR` *Text*

   Zeigt *Text* in Error U1050 an und stoppt NMAKE, auch wenn/K,/I, `.IGNORE`, `!CMDSWITCHES`oder der Bindestrich (`-`) verwendet wird. Leerzeichen oder *Tabstopps vor Text* werden ignoriert.

- `!MESSAGE` *Text*

   Zeigt *Text* in Standardausgabe an. Leerzeichen oder *Tabstopps vor Text* werden ignoriert.

- `!INCLUDE` [`<`] *Dateiname* [`>`]

   Liest *filename* als Makefile und fährt dann mit dem aktuellen Makefile fort. NMAKE sucht zuerst im angegebenen oder aktuellen Verzeichnis nach *filename* , dann rekursiv durch Verzeichnisse aller übergeordneten Makefiles, dann, wenn der *Dateiname* durch spitzen Klammern (`< >`) eingeschlossen wird, in Verzeichnissen, die durch das **include** -Makro angegeben werden, das anfänglich auf die include-Umgebungsvariable festgelegt ist. Es ist hilfreich, `.SUFFIXES` Einstellungen, `.PRECIOUS`und Rückschluss Regeln an rekursive Makefiles zu übergeben.

- `!IF` *constant_expression*

   Verarbeitet Anweisungen zwischen `!IF` und der nächsten `!ELSE` oder `!ENDIF`, wenn *constant_expression* zu einem Wert ungleich 0 (null) ausgewertet wird.

- `!IFDEF` *macroname*

   Verarbeitet Anweisungen zwischen `!IFDEF` und der nächsten `!ELSE` oder `!ENDIF`, wenn *macroname* definiert ist. Ein NULL-Makro wird als definiert betrachtet.

- `!IFNDEF` *macroname*

   Verarbeitet Anweisungen zwischen `!IFNDEF` und der nächsten `!ELSE` oder `!ENDIF`, wenn *macroname* nicht definiert ist.

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *macroname* &#124; `IFNDEF` *macroname*]

   Verarbeitet Anweisungen zwischen `!ELSE` und der nächsten `!ENDIF`, wenn die vorherige `!IF`, `!IFDEF`oder `!IFNDEF` Anweisung auf NULL ausgewertet wurde. Die optionalen Schlüsselwörter stellen eine weitere Steuerung der Vorverarbeitung zur Verfügung.

- `!ELSEIF`

   Synonym für `!ELSE IF`.

- `!ELSEIFDEF`

   Synonym für `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonym für `!ELSE IFNDEF`.

- `!ENDIF`

   Markiert das Ende eines `!IF`-, `!IFDEF`-oder `!IFNDEF`-Blocks. Jeder Text nach `!ENDIF` in derselben Zeile wird ignoriert.

- `!UNDEF` *macroname*

   Definiert " *macroname*".

## <a name="see-also"></a>Weitere Informationen

- [Vorverarbeitung eines Makefiles](makefile-preprocessing.md)
