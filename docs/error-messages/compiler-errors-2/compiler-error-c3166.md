---
title: Compilerfehler C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 1915d58f73ce8d16135951b359c3f0fd48aea3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230869"
---
# <a name="compiler-error-c3166"></a>Compilerfehler C3166

> ' Pointer ': ein Zeiger auf einen inneren __gc Zeiger kann nicht als Member von ' type ' deklariert werden.

Der Compiler hat eine ungültige Zeiger Deklaration gefunden (einen **`__nogc`** Zeiger auf einen **`__gc`** Zeiger).

C3166 ist nur mit der veralteten Compileroption erreichbar **`/clr:oldSyntax`** .
