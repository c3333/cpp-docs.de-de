---
title: Zusammenfassung der Konstanten
ms.date: 11/04/2016
helpviewer_keywords:
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
ms.openlocfilehash: f927d977d818bed28c5fd7392f7933cd1a63ced3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157741"
---
# <a name="summary-of-constants"></a>Zusammenfassung der Konstanten

*Konstante*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*floating-point-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*integer-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*

*floating-point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bruchteilkonstante* *Exponententeil*<sub>opt</sub> *Gleitkommasuffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffernsequenz* *Exponententeil* *Gleitkommasuffix*<sub>opt</sub>

*fractional-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffernsequenz*<sub>opt</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffernsequenz*  **.**

*exponent-part*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *Zeichen*<sub>opt</sub> *Ziffernsequenz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *Zeichen*<sub>opt</sub> *Ziffernsequenz*

*sign*: eins der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **+ -**

*digit-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffernsequenz* *Ziffer*

*floating-suffix* : eins der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

*integer-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Dezimalkonstante* *Integer-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Binäronstante* *Integer-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Oktalonstante* *Integer-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Hexadezimalkonstante* *Integer-Suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Dezimalkonstante* *Ziffer*

*binary-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0b** *binäre-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0B** *binäre-Ziffer*

*octal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Oktalkonstante* *Oktalziffer*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  *hexadezimale-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0X**  *hexadezimale-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Hexadezimalkonstante* *Hexadezimalziffer*

*nonzero-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*octal-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*hexadecimal-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*unsigned-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*long-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*character-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **'** *c-char-Sequenz* **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *c-char-Sequenz* **'**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-Suffix* *long-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-Suffix* *unsigned-suffix*<sub>opt</sub>

*c-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*c-char-Sequenz* *c-char*

*c-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Alle Member des Quellzeichensatzes mit Ausnahme von einfachem Anführungszeichen ( **'** ), umgekehrtem Schrägstrich ( **\\** ) oder Zeilenumbruchzeichen „escape-sequence“

*escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*simple-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-escape-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-escape-sequence*

*simple-escape-sequence*: eins der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\a \b \f \n \r \t \v**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\\' \\" \\\ \\?**

*octal-escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\\** *oktale-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\\** *oktale-Ziffer* *oktale-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\\** *oktale-Ziffer* *oktale-Ziffer* *oktale-Ziffer*

*hexadecimal-escape-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\x** *hexadezimale-Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadezimale-Escapesequenz* *hexadezimale-Ziffer*

## <a name="see-also"></a>Siehe auch

[Lexikalische Grammatik](../c-language/lexical-grammar.md)<br/>
