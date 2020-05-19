---
title: Zusammenfassung der Tokens
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345135"
---
# <a name="summary-of-tokens"></a>Zusammenfassung der Tokens

*token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*preprocessing-token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*header-name*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator punctuator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Alle Zeichen, die kein Leerzeichen sind und keines der oben erwähnten sein können

*header-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\<**  *Pfadspezifizierung*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **"**  *Pfadspezifizierung*  **"**

*path-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Gültiger Dateipfad

*pp-number*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Vorverarbeitungsnummer* *Ziffer* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Vorverarbeitungsnummer* *keine Ziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Vorverarbeitungsnummer*  **e**  *Zeichen*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Vorverarbeitungsnummer*  **E**  *Zeichen*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Vorverarbeitungsnummer*  **.**

## <a name="see-also"></a>Siehe auch

[Lexikalische Grammatik](../c-language/lexical-grammar.md)
