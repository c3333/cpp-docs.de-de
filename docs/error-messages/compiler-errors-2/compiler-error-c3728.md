---
title: Compilerfehler C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165873"
---
# <a name="compiler-error-c3728"></a>Compilerfehler C3728

"Ereignis": das Ereignis hat keine Raise-Methode.

Metadaten, die mit einer Sprache erstellt werden C#, z. b., die nicht zulässt, dass ein Ereignis von außerhalb der Klasse, in der Sie definiert wurde, ausgelöst werden, in der [#using](../../preprocessor/hash-using-directive-cpp.md) -Direktive enthalten waren und ein visuelles C++ Programm, das die CLR-Programmierung verwendet, versuchte, das Ereignis zu erhöhen

Zum Auslösen eines Ereignisses in einem Programm C#, das in einer Sprache wie z. b. entwickelt wurde, muss die Klasse, die das Ereignis enthält, auch eine öffentliche Methode definieren, die das Ereignis auslöst.
