---
title: Microsoft-Erweiterungen
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: a2d0846e55122f177b4868c2e80c4f1d27267f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179405"
---
# <a name="microsoft-extensions"></a>Microsoft-Erweiterungen

*ASM-Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm***Assemblyanweisung* **;** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *Assembly-Instruction-List* **};** <sub>opt</sub>

*Assembly-Instruction-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Assemblyanweisung* **;** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Assemblyanweisung* **;** *Assembly-Instruction-List* **;** <sub>opt</sub>

*MS-Modifier-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*MS-Modifier* *MS-Modifier-List*<sub>opt</sub>

*MS-Modifizierer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__syscall** (für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__oldcall** (für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__unaligned** (für zukünftige Implementierungen reserviert)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*basierten Modifizierer*

*basierter-Modifizierer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__based (** *Basistyp* **)**

*based-Type*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Namen*
