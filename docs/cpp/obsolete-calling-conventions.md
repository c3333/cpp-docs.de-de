---
title: Veraltete Aufrufkonventionen
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188557"
---
# <a name="obsolete-calling-conventions"></a>Veraltete Aufrufkonventionen

**Microsoft-spezifisch**

Die **__pascal**-, **__fortran**-und **__syscall** Aufruf Konventionen werden nicht mehr unterstützt. Sie können ihre Funktionalität emulieren, indem Sie eine der unterstützten Aufrufkonventionen und geeignete Linkeroptionen verwenden.

\<Windows. h > unterstützt jetzt das WinAPI-Makro, das in die entsprechende Aufruf Konvention für das Ziel übersetzt. Verwenden Sie WinAPI, wenn Sie zuvor Pascal oder **__far \__pascal**verwendet haben.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)
