---
title: Zusammenfassung der Deklarationen
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170435"
---
# <a name="summary-of-declarations"></a>Zusammenfassung der Deklarationen

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarationsspezifizierer* *Attribut-setq*<sub>opt</sub> *Init-declarator-List*<sub>opt</sub> **;**

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;von *Storage-Class-specifier* *Declaration-Specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklaration-Spezifizierer*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Type-Qualifizierer* *Deklaration-Spezifizierer*<sub>opt</sub>

*Attribut-* *&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifischer \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Attribute* *-Attribut-"-* <sub>abwählen</sub> "

*Attribut* : eine der&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifischen \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-List* **,** *Init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator* **=** *Initialisierer* /\* für skalare Initialisierungs \*/

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-modifier-LQ* **)**  /\* Microsoft-spezifischen \*/

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* Microsoft-spezifischer \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* Microsoft-spezifischer \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* Microsoft-spezifischer \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* Microsoft-spezifischer \*/<br/>
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
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *Deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *Constant-Expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Deklarator* **(** *Parameter-Type-List* **)**  /\* \*neuer Deklarator /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Deklarator* **(** *Identifier-List*<sub>opt</sub> **)**  /\* \*veralteter Deklarator /

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Type-Qualifizierer-List*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Type-Qualifizierer-List-* <sub>opt</sub> - *Zeiger*

*parameter-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* Die Parameterliste \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameter-List* **..** .

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Parameter-List* **,** *Parameter-Declaration*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Type-Qualifizierer-List* *Type-Qualifizierer*

*enum-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerator-List* **}** von **Enumeration** - *Bezeichner*<sub>opt</sub> **{**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Enumeration** - *Bezeichner*

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerator-List* **,** *Enumerator*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumeration-Constant* **=** *Constant-Expression*

*enumeration-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder Union* *identifier*-ID<sub>opt</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktur-oder Union-* *Bezeichner*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-Deklaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-Qualifizierer-List* *struct-declarator-List* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-Qualifizierer-List*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Type-Qualifizierer* - *Qualifizierer-List*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator* *-Struktur-declarator-List* **,** *struct-declarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typspezifizierer* *Deklarator*<sub>opt</sub> **:** *Constant-Expression*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarationsspezifizierer* *Deklarator* /\* benannte Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarationsspezifizierer* *abstract-Deklarator*<sub>opt</sub> /\* anonymer Deklarator \*/

*identifier-list*: /\* Für alten Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezeichnerliste* **,** *Bezeichner*

*abstract-declarator*: /\* Verwendet mit anonymen Deklaratoren \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zeiger*<sub>opt</sub> *Direct-Abstract-declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Abstract-declarator*<sub>opt</sub> **[** *Constant-Expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-Abstract-declarator*<sub>opt</sub> **(** *Parameter-Type-List*<sub>opt</sub> **)**

*initializer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **}**  /\* für Aggregat Initialisierungs \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-List* **,}**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisierer-List* **,** *Initialisierer*

*type-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-Qualifizierer-List* *abstract-declarator*<sub>opt</sub>

*typedef-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*Extended-decl-modifier-* &nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifischen \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier-* " *Extended-decl-modifier* "

*Extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifischen \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Weitere Informationen

[Aufrufkonventionen](../cpp/calling-conventions.md)<br/>
[Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)<br/>
[Veraltete Aufrufkonventionen](../cpp/obsolete-calling-conventions.md)
