---
title: Compilerfehler C2873
ms.date: 11/04/2016
f1_keywords:
- C2873
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
ms.openlocfilehash: b1eabf71c4338a9ede275b58fd12f1be1a25029d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228881"
---
# <a name="compiler-error-c2873"></a>Compilerfehler C2873

' Symbol ': das Symbol kann nicht in einer using-Deklaration verwendet werden.

In einer- **`using`** Direktive fehlt ein [Namespace](../../cpp/namespaces-cpp.md) -Schlüsselwort. Dies bewirkt, dass der Compiler den Code nicht als using- [Direktive](../../cpp/namespaces-cpp.md#using_directives), sondern als [using-Deklaration](../../cpp/using-declaration.md) interpretiert.
