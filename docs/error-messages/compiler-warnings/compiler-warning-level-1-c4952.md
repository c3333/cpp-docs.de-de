---
title: Compilerwarnung (Stufe 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: 560705edeb0bbdd6be760736a8d4a19d914133d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174569"
---
# <a name="compiler-warning-level-1-c4952"></a>Compilerwarnung (Stufe 1) C4952

> "*Funktion*": in der Programmdatenbank "*pgd_file*" wurden keine Profildaten gefunden.

Bei der Verwendung von [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)hat der Compiler ein Eingabemodul erkannt, das nach `/LTCG:PGINSTRUMENT` erneut kompiliert wurde und eine neue Funktion (*Funktion*) aufweist.

Diese Warnung dient nur zu Informationszwecken. Um diese Warnung zu beheben, führen Sie `/LTCG:PGINSTRUMENT`aus, wiederholen alle Testläufe und führen `/LTCG:PGOPTIMIZE`aus.

Bei Verwendung von `/LTCG:PGOPTIMIZE` würde diese Warnung durch einen Fehler ersetzt.
