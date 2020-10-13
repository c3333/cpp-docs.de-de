---
title: Zusammenfassung der Ausdrücke
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 1660690c6d36aa1dbdc025d6afe92e19ff941463
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220833"
---
# <a name="summary-of-expressions"></a>Zusammenfassung der Ausdrücke

*primary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *Ausdruck*  **)**

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ausdruck*  **,**  *Zuweisungsausdruck*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logischer-OR-Ausdruck*  **?**  *Ausdruck*  **:**  *bedingter-Ausdruck*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unärer-Ausdruck* *Zuweisungsoperator* *Zuweisungsausdruck*

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **[**  *Ausdruck*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **(**  *argument-Ausdrucksliste*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **->**  *Bezeichner*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-Ausdrucksliste*  **,**  *Zuweisungsausdruck*

*unary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **++**  *unärer-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **--**  *unärer-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`sizeof`**  *unärer-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *Typname*  **)**

*unary-operator*: Einer von<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **&** **&#42;** **+** **-** **~** **!**

*cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *Typname*  **)**  *cast-Ausdruck*

*multiplicative-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Multiplikationsausdruck*  **&#42;**  *cast-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Multiplikationsausdruck*  **/**  *cast-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Multiplikationsausdruck*  **%**  *cast-Ausdruck*

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additiver-Ausdruck*  **+**  *multiplikativer-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additiver-Ausdruck*  **-**  *multiplikativer-Ausdruck*

*shift-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Verschiebeausdruck*  **\<\<**  *additive-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* Verschiebeausdruck*  **>>**  *additiver-Ausdruck*

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relationaler-Ausdruck*  **\<**  *shift-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relationaler-Ausdruck*  **>**  *Verschiebeausdruck*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relationaler-Ausdruck*  **\<=**  *shift-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relationaler-Ausdruck*  **>=**  *Verschiebeausdruck*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Gleichheitsausdruck*  **==**  *relationaler-Ausdruck*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Gleichheitsausdruck*  **!=**  *relationaler-Ausdruck*

*AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-Ausdruck*  **&**  *Gleichheitsausdruck*

*exclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exklusiver-OR-Ausdruck*  **^**  *AND-Ausdruck*

*inclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inklusiver-OR-Ausdruck*  **&#124;**  *exklusiver-OR-Ausdruck*

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logischer-AND-Ausdruck*  **&&**  *inklusiver-OR-Ausdruck*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logischer-OR-Ausdruck*  **&#124;&#124;**  *logischer-AND-Ausdruck*

## <a name="see-also"></a>Siehe auch

- [Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)
