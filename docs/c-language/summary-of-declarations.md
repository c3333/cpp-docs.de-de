---
title: Zusammenfassung der Deklarationen
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170435"
---
# <a name="summary-of-declarations"></a>Zusammenfassung der Deklarationen

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer* *Attributsequenz*<sub>opt</sub> *Initialisierungsdeklaratorliste*<sub>opt</sub> **;**

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Speicherklassenspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarationsspezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Deklarationsspezifizierer*<sub>opt</sub>

*Attributsequenz* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Attribut* *Attributsequenz*<sub>opt</sub>

*Attribut* : eines der folgenden&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisierungsdeklaratorliste*  **,**  *Initialisierungsdeklarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*  **=**  *Initialisierer* /\* Für skalare Initialisierung \*/

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *erweiterte-Deklarationsmodifizierersequenz* **)**  /\* Microsoft-spezifisch \*/

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-qualifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direkter-Deklarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *Deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator* **[** *konstanter-Ausdruck*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator* **(** *Parametertypliste* **)**  /\* Neuer Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-Deklarator* **(** *Bezeichnerliste*<sub>opt</sub> **)**  /\* Veralteter Deklarator \*/

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typqualifiziererliste*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typqualifiziererliste*<sub>opt</sub> *Zeiger*

*Parametertypliste*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* Die Parameterliste \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameterliste* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameterliste* **,** *Parameterdeklaration*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifiziererliste* *Typqualifizierer*

*enum-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *Bezeichner*<sub>opt</sub> **{** *Enumeratorliste* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *Bezeichner*

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumeratorliste* **,** *Enumerator*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerationskonstante* **=** *konstanter-Ausdruck*

*enumeration-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*<sub>opt</sub> **{** *Strukturdeklarationsliste* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder-Union* *Bezeichner*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklarationsliste* *Strukturdeklaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Spezifizierer-/Qualifiziererliste* *Strukturdeklaratorliste* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typqualifizierer* *Spezifizierer-/Qualifiziererliste*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Strukturdeklarator* *Strukturdeklaratorliste* **,** *Strukturdeklarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarator*<sub>opt</sub> **:** *konstanter-Ausdruck*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer* *Deklarator* /\* Benannter Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarationsspezifizierer* *abstrakter-Deklarator*<sub>opt</sub> /\* Anonymer Deklarator \*/

*identifier-list*: /\* Für alten Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichnerliste* **,** *Bezeichner*

*abstract-declarator*: /\* Verwendet mit anonymen Deklaratoren \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direkter-abstrakter-Deklarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstrakter-Deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-abstrakter-Deklarator*<sub>opt</sub> **[** *konstanter-Ausdruck*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direkter-abstrakter-Deklarator*<sub>opt</sub> **(** *Parametertypliste*<sub>opt</sub> **)**

*initializer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Initialisiererliste* **}**  /\* Für Aggregatinitialisierung \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Initialisiererliste* **, }**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisiererliste* **,** *Initialisierer*

*type-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Spezifizierer-/Qualifiziererliste* *abstrakter-Deklarator*<sub>opt</sub>

*typedef-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*extended-decl-modifier-seq*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*erweiterte-Deklarationsmodifizierersequenz* *erweiterter-Deklarationsmodifizierer*

*extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Siehe auch

[Aufrufkonventionen](../cpp/calling-conventions.md)<br/>
[Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)<br/>
[Veraltete Aufrufkonventionen](../cpp/obsolete-calling-conventions.md)
