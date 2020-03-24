---
title: Compilerfehler C2873
ms.date: 11/04/2016
f1_keywords:
- C2873
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
ms.openlocfilehash: a77c4294d697d915a77b5aa244579860f860cf21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201655"
---
# <a name="compiler-error-c2873"></a>Compilerfehler C2873

' Symbol ': das Symbol kann nicht in einer using-Deklaration verwendet werden.

In einer `using`-Direktive fehlt ein [Namespace](../../cpp/namespaces-cpp.md) Schlüsselwort. Dies bewirkt, dass der Compiler den Code nicht als using- [Direktive](../../cpp/namespaces-cpp.md#using_directives), sondern als [using-Deklaration](../../cpp/using-declaration.md) interpretiert.
