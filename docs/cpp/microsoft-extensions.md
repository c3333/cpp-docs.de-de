---
title: Microsoft-Erweiterungen
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: 4b2ed06b31ffefb0d64d09864004256251a9b6cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223667"
---
# <a name="microsoft-extensions"></a>Microsoft-Erweiterungen

*`asm-statement`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***`assembly-instruction`* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***`assembly-instruction-list`* **`} ;`** <sub>opt</sub>  

*`assembly-instruction-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assembly-instruction`***`;`** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assembly-instruction`***`;`** *`assembly-instruction-list`* **`;`** <sub>opt</sub>

*`ms-modifier-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`ms-modifier`**`ms-modifier-list`* <sub>opt</sub>

*`ms-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__cdecl`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__fastcall`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__stdcall`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__syscall`**(für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__oldcall`**(für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__unaligned`**(für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`based-modifier`*

*`based-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__based (`** *`based-type`* **`)`**

*`based-type`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`name`*
