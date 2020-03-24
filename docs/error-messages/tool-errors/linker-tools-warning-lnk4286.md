---
title: Linkertoolwarnung LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173867"
---
# <a name="linker-tools-warning-lnk4286"></a>Linkertoolwarnung LNK4286

> das Symbol '*Symbol*', das in '*filename_1. obj*' definiert ist, wird von '*filename_2. obj*' importiert.

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) wurde für das *Symbol* angegeben, obwohl das Symbol in der Objektdatei *filename_1. obj* im gleichen Bild definiert ist. Entfernen Sie den `__declspec(dllimport)` Modifizierer, um diese Warnung zu beheben.

## <a name="remarks"></a>Bemerkungen

Warnung LNK4286 ist eine allgemeinere Version der [Linker-Tool Warnung Linkertoolwarnung LNK4217](linker-tools-warning-lnk4217.md). Der Linker generiert eine Warnung LNK4286, wenn er feststellen kann, in welcher Objektdatei auf das Symbol verwiesen wurde, jedoch nicht welche Funktion.

Entfernen Sie zum Auflösen von LNK4286 den Modifizierer `__declspec(dllimport)` Deklaration aus der vorwärts Deklaration des *Symbols* , auf das in *filename_2. obj*verwiesen wird.

Obwohl sich der endgültige generierte Code ordnungsgemäß verhält, ist der Code, der zum Aufrufen einer importierten Funktion generiert wurde, weniger effizient, als die Funktion direkt aufzurufen. Diese Warnung wird nicht angezeigt, wenn Sie mit der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Option kompilieren.

Weitere Informationen zum Importieren und Exportieren von Datendeklarationen finden Sie unter [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Weitere Informationen

[Warnmeldungen für Linker-Tools Linkertoolwarnung LNK4049](linker-tools-warning-lnk4049.md) \
[Warnmeldungen für Linker-Tools Linkertoolwarnung LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
