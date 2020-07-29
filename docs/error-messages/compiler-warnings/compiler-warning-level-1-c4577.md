---
title: Compilerwarnung C4577
description: Compilerwarnung C4577 Beschreibung und Projekt Mappe.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: fb9d412196e7764326a397a4bf6e76c8723ac2ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196252"
---
# <a name="compiler-warning-level-1-c4577"></a>Compilerwarnung (Stufe 1) C4577

> "noaußer" wird verwendet, ohne dass der Ausnahme Behandlungs Modus angegeben wurde. Beendigung bei Ausnahme ist nicht gewährleistet. /EHsc angeben

Der Compiler hat eine **`noexcept`** Spezifikation erkannt, aber die standardmäßige C++-Ausnahmebehandlung wurde nicht angegeben. Der Compiler unterstützt die Ausnahmebehandlung gemäß dem C++-Standard nur, wenn die [/EHsc](../../build/reference/eh-exception-handling-model.md) -Compileroption angegeben wird. Um dieses Problem zu beheben, legen Sie die **/EHsc** -Compileroption fest.

Diese Warnung ist neu in Visual Studio 2015 und ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.
