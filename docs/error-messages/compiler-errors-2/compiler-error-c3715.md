---
title: Compilerfehler C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 13befc17b94fdf2c22cb84bc64ed55b9375b3473
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165911"
---
# <a name="compiler-error-c3715"></a>Compilerfehler C3715

' Pointer ': muss ein Zeiger auf ' class ' sein.

Sie haben einen Zeiger in [__hook](../../cpp/hook.md) oder [__unhook](../../cpp/unhook.md) angegeben, die nicht auf eine gültige Klasse zeigen. Um diesen Fehler zu beheben, stellen Sie sicher, dass die `__hook`-und `__unhook` Aufrufe Zeiger auf gültige Klassen angeben.
