---
title: Compilerfehler C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: c3aff142215286a94a261a1f0fcb411296b57d5a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230778"
---
# <a name="compiler-error-c3715"></a>Compilerfehler C3715

' Pointer ': muss ein Zeiger auf ' class ' sein.

Sie haben einen Zeiger in [`__hook`](../../cpp/hook.md) oder angegeben [`__unhook`](../../cpp/unhook.md) , der nicht auf eine gültige Klasse verweist. Um diesen Fehler zu beheben, stellen Sie sicher, dass Ihre **`__hook`** -und- **`__unhook`** Aufrufe Zeiger auf gültige Klassen angeben.
