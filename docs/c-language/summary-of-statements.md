---
title: Zusammenfassung der Anweisungen
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 1a230ca7d998316d2ec96e76b54ac60575acd2ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856994"
---
# <a name="summary-of-statements"></a>Zusammenfassung der Anweisungen

*Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*compound-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*selection-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteration-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-Anweisung* /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-Anweisung* /\* Microsoft-spezifisch \*/

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *Bezeichner*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**continue ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *Ausdruck*<sub>opt</sub> **;**

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Deklarationsliste*<sub>opt</sub> *Anweisungsliste*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsliste* *Deklaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Anweisungsliste* *Anweisung*

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ausdruck*<sub>opt</sub> **;**

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *Ausdruck*  **)**  *Anweisung*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**do**  *Anweisung*  **while (**  *Ausdruck*  **) ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (**  *Ausdruck*<sub>opt</sub> **;** *Ausdruck*<sub>opt</sub> **;** *Ausdruck*<sub>opt</sub> **)** *Anweisung*

*selection-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (**  *Ausdruck*  **)**  *Anweisung*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (**  *Ausdruck*  **)**  *Anweisung*  **else**  *Anweisung*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**switch (**  *Ausdruck*  **)**  *Anweisung*

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner*  **:**  *Anweisung*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *konstanter-Ausdruck*  **:**  *Anweisung*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default :**  *Anweisung*

*try-except-Anweisung*:   /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try**  *Verbundanweisung* **__except (**  *Ausdruck*  **)**  *Verbundanweisung*

*try-finally-Anweisung*:   /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try**  *Verbundanweisung* **__finally**  *Verbundanweisung*

## <a name="see-also"></a>Siehe auch

[Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)
