---
title: Schwerwiegender Fehler C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202864"
---
# <a name="fatal-error-c1853"></a>Schwerwiegender Fehler C1853

> die vorkompilierte Header Datei "*filename*" ist aus einer früheren Version des Compilers, oder der vorkompilierte Header ist C++ , und Sie verwenden ihn von C (oder umgekehrt).

Mögliche Ursachen:

- Der vorkompilierte Header wurde mit einer früheren Compilerversion kompiliert. Versuchen Sie, den Header mit dem aktuellen Compiler neu zu kompilieren.

- Der vorkompilierte Header C++ ist, und Sie verwenden ihn von c. versuchen Sie, den Header für die Verwendung mit c neu zu kompilieren, indem Sie eine der [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) -Compileroptionen angeben oder das Suffix der Quelldatei in "c" ändern. Weitere Informationen finden Sie unter [zwei Optionen für das Vorkompilieren von Code](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
