---
title: Linkertoolfehler LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183799"
---
# <a name="linker-tools-error-lnk1245"></a>Linkertoolfehler LNK1245

das angegebene Subsystem ' Subsystem ' ist ungültig. /Subsystem muss Windows, WindowsCE oder Console sein.

[/CLR](../../build/reference/clr-common-language-runtime-compilation.md) wurde verwendet, um das Objekt zu kompilieren, und eine der folgenden Bedingungen war true:

- Ein benutzerdefinierter Einstiegspunkt wurde definiert ([/Entry](../../build/reference/entry-entry-point-symbol.md)), sodass der Linker kein Subsystem ableiten konnte.

- Ein Wert wurde an die [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) -Linkeroption übermittelt, die für/CLR-Objekte nicht gültig ist.

In beiden Situationen besteht die Lösung darin, einen gültigen Wert für die/Subsystem Linker-Option anzugeben.
