---
title: Compilerwarnung (Stufe 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 6b0ca74bbd03682f91206c21c3413d4ad168b60a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185866"
---
# <a name="compiler-warning-level-1-c4727"></a>Compilerwarnung (Stufe 1) C4727

"PCH Named Pch_file mit demselben Zeitstempel in obj_file_1 und obj_file_2.  Verwenden des ersten PCH.

> [!NOTE]
> In Visual Studio 2017 und früheren Versionen heißt der vorkompilierte Header standardmäßig *stdafx. h* , und in Visual Studio 2019 und höher wird der vorkompilierte Header standardmäßig als " *PCH. h* " bezeichnet.

C4727 tritt auf, wenn mehrere Kompilierungen mit **/Yc**kompiliert werden und der Compiler alle OBJ-Dateien mit demselben PCH-Zeitstempel markieren konnte.

Um das Problem zu beheben, kompilieren Sie eine Quelldatei mit **/Yc/c** (erstellt PCH), und die anderen kompilieren separat mit **/Yu/c** (verwendet PCH) und verknüpfen Sie dann miteinander.

Wenn Sie also die folgenden Schritte durchgeführt haben, generiert C4727:

::: moniker range="<=vs-2017"

**cl/clr/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

Gehen Sie stattdessen wie folgt vor:

**cl/clr/GL a. cpp/Ycstdafx.h/c**

**cl/clr/GL b. cpp c. cpp/Yustdafx.h/Link a. obj**

::: moniker-end

::: moniker range=">=vs-2019"

**cl/clr/GL a. cpp b. cpp c. cpp/Ycpch.h**

Gehen Sie stattdessen wie folgt vor:

**cl/clr/GL a. cpp/Ycpch.h/c**

**cl/clr/GL b. cpp c. cpp/Yupch.h/Link a. obj**

::: moniker-end

Weitere Informationen finden Sie unter

- [/Yc (Vorkompilierte Headerdatei erstellen)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Vorkompilierte Headerdatei verwenden)](../../build/reference/yu-use-precompiled-header-file.md)
