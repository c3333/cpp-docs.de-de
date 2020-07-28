---
title: Compilerwarnung (Stufe 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214333"
---
# <a name="compiler-warning-level-4-c4611"></a>Compilerwarnung (Stufe 1) C4600

die Interaktion zwischen "Function" und der C++-Objekt Zerstörung ist nicht portabel.

Auf einigen Plattformen unterstützen Funktionen, die enthalten, **`catch`** möglicherweise keine C++-Objekt Semantik der Zerstörung, wenn außerhalb des gültigen Bereichs.

Um unerwartetes Verhalten zu vermeiden, sollten Sie nicht **`catch`** in Funktionen verwenden, die über Konstruktoren und debugtoren verfügen.

Diese Warnung wird nur einmal ausgegeben. siehe [pragma warning](../../preprocessor/warning.md).
