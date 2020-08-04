---
title: Zusammenfassung der Deklarationen
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: 894ed5e39ac8019048b6730d5e3b34de22f3a0c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220846"
---
# <a name="summary-of-declarations"></a>Zusammenfassung der Deklarationen

*`declaration`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`attribute-seq`* <sub>opt</sub> *`init-declarator-list`* <sub>opt</sub> **`;`**

*`declaration-specifiers`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`storage-class-specifier`* *`declaration-specifiers`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-specifier`* *`declaration-specifiers`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-qualifier`* *`declaration-specifiers`* <sub>opt</sub>

*`attribute-seq`* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`attribute`* *`attribute-seq`* <sub>opt</sub>

*`attribute`* : one of&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[`__asm`](../assembler/inline/asm.md) [`__clrcall`](../cpp/clrcall.md) [`__stdcall`](../cpp/stdcall.md) [`__based`](../cpp/based-grammar.md) [`__fastcall`](../cpp/fastcall.md) [`__thiscall`](../cpp/thiscall.md) [`__cdecl`](../cpp/cdecl.md) [`__inline`](../cpp/inline-functions-cpp.md) [`__vectorcall`](../cpp/vectorcall.md)

*`init-declarator-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`init-declarator-list`*  **`,`**  *`init-declarator`*

*`init-declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declarator`*  **`=`**  *`initializer`*  /\* Für eine skalare Initialisierung \*/

*`storage-class-specifier`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`auto`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`register`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`static`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`extern`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`typedef`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__declspec (`** *`extended-decl-modifier-seq`* **`)`**  /\* Microsoft-spezifisch \*/

*`type-specifier`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int8`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int16`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int32`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`__int64`**  /\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-or-union-specifier`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`enum-specifier`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`typedef-name`*

*`type-qualifier`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`const`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`volatile`**

*`declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`pointer`* <sub>opt</sub> *`direct-declarator`*

*`direct-declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`identifier`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`(`** *`declarator`* **`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-declarator`* **`[`** *`constant-expression`* <sub>opt</sub> **`]`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-declarator`* **`(`** *`parameter-type-list`* **`)`**  /\* Deklarator im neuen Format \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-declarator`* **`(`** *`identifier-list`* <sub>opt</sub> **`)`**  /\* Deklarator im veralteten Format \*/

*`pointer`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>`*`</strong> *`type-qualifier-list`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>`*`</strong> *`type-qualifier-list`* <sub>opt</sub> *`pointer`*

*`parameter-type-list`* :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* Die Parameterliste \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`* **`, ...`**

*`parameter-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`parameter-list`* **`,`** *`parameter-declaration`*

*`type-qualifier-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-qualifier`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-qualifier-list`* *`type-qualifier`*

*`enum-specifier`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`enum`** *`identifier`* <sub>opt</sub> **`{`** *`enumerator-list`* **`}`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`enum`** *`identifier`*

*`enumerator-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`enumerator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`enumerator-list`* **`,`** *`enumerator`*

*`enumerator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`enumeration-constant`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`enumeration-constant`* **`=`** *`constant-expression`*

*`enumeration-constant`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`identifier`*

*`struct-or-union-specifier`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-or-union`* *`identifier`* <sub>opt</sub> **`{`** *`struct-declaration-list`* **`}`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-or-union`* *`identifier`*

*`struct-or-union`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`struct`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`union`**

*`struct-declaration-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-declaration-list`* *`struct-declaration`*

*`struct-declaration`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`specifier-qualifier-list`* *`struct-declarator-list`* **`;`**

*`specifier-qualifier-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-specifier`* *`specifier-qualifier-list`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-qualifier`* *`specifier-qualifier-list`* <sub>opt</sub>

*`struct-declarator-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`struct-declarator`* *`struct-declarator-list`* **`,`** *`struct-declarator`*

*`struct-declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`type-specifier`* *`declarator`* <sub>opt</sub> **`:`** *`constant-expression`*

*`parameter-declaration`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`declarator`*  /\* Benannter Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`declaration-specifiers`* *`abstract-declarator`* <sub>opt</sub> /\* Anonymer Deklarator \*/

*`identifier-list`* : /\* Für Deklarator im veralteten Format \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`identifier`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`identifier-list`* **`,`** *`identifier`*

*`abstract-declarator`* : /\* Verwendet mit anonymen Deklaratoren \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`pointer`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`pointer`* <sub>opt</sub> *`direct-abstract-declarator`*

*`direct-abstract-declarator`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`(`** *`abstract-declarator`* **`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-abstract-declarator`* <sub>opt</sub> **`[`** *`constant-expression`* <sub>opt</sub> **`]`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`direct-abstract-declarator`* <sub>opt</sub> **`(`** *`parameter-type-list`* <sub>opt</sub> **`)`**

*`initializer`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`assignment-expression`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`{`** *`initializer-list`* **`}`**  /\* Für Aggregatinitialisierung \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`{`** *`initializer-list`* **`, }`**

*`initializer-list`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`initializer`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`initializer-list`* **`,`** *`initializer`*

*`type-name`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`specifier-qualifier-list`* *`abstract-declarator`* <sub>opt</sub>

*`typedef-name`* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`identifier`*

*`extended-decl-modifier-seq`* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`extended-decl-modifier`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`extended-decl-modifier-seq`* *`extended-decl-modifier`*

*`extended-decl-modifier`* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft-spezifisch \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`dllexport`**

## <a name="see-also"></a>Siehe auch

[Aufrufkonventionen](../cpp/calling-conventions.md)<br/>
[Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)<br/>
[Veraltete Aufrufkonventionen](../cpp/obsolete-calling-conventions.md)
