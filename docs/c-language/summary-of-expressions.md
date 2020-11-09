---
title: Zusammenfassung der Ausdrücke
description: Erfahren Sie mehr über die Standardgrammatik von C für Ausdrücke entsprechend der Implementierung durch den C-/C++-Compiler von Microsoft.
ms.date: 10/30/2020
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 317f7c26e89e2741a5496c5a091100f0c2d8a21a
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238446"
---
# <a name="summary-of-expressions"></a>Zusammenfassung der Ausdrücke

*`primary-expression`* :\
&emsp;*`identifier`*\
&emsp;*`constant`*\
&emsp;*`string-literal`*\
&emsp;**`(`** *`expression`* **`)`**\
&emsp;*`generic-selection`*

*`generic-selection`* :\
&emsp;**`_Generic`** **`(`** *`assignment-expression`* **`,`** *`generic-assoc-list`* **`)`**

*`generic-assoc-list`* :\
&emsp;*`generic-association`*\
&emsp;*`generic-assoc-list`* **`,`** *`generic-association`*

*`generic-association`* :\
&emsp;*`type-name`* **`:`** *`assignment-expression`*\
&emsp;**`default`** **`:`** *`assignment-expression`*

*`postfix-expression`* :\
&emsp;*`primary-expression`*\
&emsp;*`postfix-expression`* **`[`** *`expression`* **`]`**\
&emsp; *`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`** \
&emsp;*`postfix-expression`* **`.`** *`identifier`*\
&emsp;*`postfix-expression`* **`->`** *`identifier`*\
&emsp;*`postfix-expression`* **`++`**\
&emsp;*`postfix-expression`* **`--`**\
&emsp;**`(`** *`type-name`* **`)`** **`{`** *`initializer-list`* **`}`**\
&emsp;**`(`** *`type-name`* **`)`** **`{`** *`initializer-list`* **`,`** **`}`**

*`argument-expression-list`* :\
&emsp;*`assignment-expression`*\
&emsp;*`argument-expression-list`* **`,`** *`assignment-expression`*

*`unary-expression`* :\
&emsp;*`postfix-expression`*\
&emsp;**`++`** *`unary-expression`*\
&emsp;**`--`** *`unary-expression`*\
&emsp;*`unary-operator`* *`cast-expression`*\
&emsp;**`sizeof`** *`unary-expression`*\
&emsp;**`sizeof`** **`(`** *`type-name`* **`)`** &emsp;**`_Alignof`** **`(`** *`type-name`* **`)`**

*`unary-operator`* : eines der folgenden Zeichen\
&emsp;**`&`** **`*`** **`+`** **`-`** **`~`** **`!`**

*`cast-expression`* :\
&emsp;*`unary-expression`*\
&emsp;**`(`** *`type-name`* **`)`** *`cast-expression`*

*`multiplicative-expression`* :\
&emsp;*`cast-expression`*\
&emsp;*`multiplicative-expression`* **`*`** *`cast-expression`*\
&emsp;*`multiplicative-expression`* **`/`** *`cast-expression`*\
&emsp;*`multiplicative-expression`* **`%`** *`cast-expression`*

*`additive-expression`* :\
&emsp;*`multiplicative-expression`*\
&emsp;*`additive-expression`* **`+`** *`multiplicative-expression`*\
&emsp;*`additive-expression`* **`-`** *`multiplicative-expression`*

*`shift-expression`* :\
&emsp;*`additive-expression`*\
&emsp;*`shift-expression`* **`<<`** *`additive-expression`*\
&emsp;*`shift-expression`* **`>>`** *`additive-expression`*

*`relational-expression`* :\
&emsp;*`shift-expression`*\
&emsp;*`relational-expression`* **`<`** *`shift-expression`*\
&emsp;*`relational-expression`* **`>`** *`shift-expression`*\
&emsp;*`relational-expression`* **`<=`** *`shift-expression`*\
&emsp;*`relational-expression`* **`>=`** *`shift-expression`*

*`equality-expression`* :\
&emsp;*`relational-expression`*\
&emsp;*`equality-expression`* **`==`** *`relational-expression`*\
&emsp;*`equality-expression`* **`!=`** *`relational-expression`*

*`AND-expression`* :\
&emsp;*`equality-expression`*\
&emsp;*`AND-expression`* **`&`** *`equality-expression`*

*`exclusive-OR-expression`* :\
&emsp;*`AND-expression`*\
&emsp;*`exclusive-OR-expression`* **`^`** *`AND-expression`*

*`inclusive-OR-expression`* :\
&emsp;*`exclusive-OR-expression`*\
&emsp;*`inclusive-OR-expression`* **`|`** *`exclusive-OR-expression`*

*`logical-AND-expression`* :\
&emsp;*`inclusive-OR-expression`*\
&emsp;*`logical-AND-expression`* **`&&`** *`inclusive-OR-expression`*

*`logical-OR-expression`* :\
&emsp;*`logical-AND-expression`*\
&emsp;*`logical-OR-expression`* **`||`** *`logical-AND-expression`*

*`conditional-expression`* :\
&emsp;*`logical-OR-expression`*\
&emsp;*`logical-OR-expression`* **`?`** *`expression`* **`:`** *`conditional-expression`*

*`assignment-expression`* :\
&emsp;*`conditional-expression`*\
&emsp;*`unary-expression`* *`assignment-operator`* *`assignment-expression`*

*`assignment-operator`* : eines der folgenden Zeichen\
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`** **`&=`** **`^=`** **`|=`**

*`expression`* :\
&emsp;*`assignment-expression`*\
&emsp;*`expression`* **`,`** *`assignment-expression`*

*`constant-expression`* :\
&emsp;*`conditional-expression`*

## <a name="see-also"></a>Siehe auch

- [Phrasenstrukturgrammatik](../c-language/phrase-structure-grammar.md)
