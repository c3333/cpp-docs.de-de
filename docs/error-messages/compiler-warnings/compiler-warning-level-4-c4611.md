---
title: Compilerwarnung (Stufe 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198301"
---
# <a name="compiler-warning-level-4-c4611"></a>Compilerwarnung (Stufe 1) C4600

die Interaktion zwischen "Function" C++ und der Objekt Zerstörung ist nicht portabel.

Auf einigen Plattformen unterstützen C++ Funktionen, die **catch** enthalten, möglicherweise keine Objekt Semantik der Zerstörung, wenn Sie außerhalb des gültigen Bereichs liegen.

Um unerwartetes Verhalten zu vermeiden, sollten Sie **catch** in-Funktionen vermeiden, die über Konstruktoren und debugtoren verfügen.

Diese Warnung wird nur einmal ausgegeben. siehe [pragma warning](../../preprocessor/warning.md).
