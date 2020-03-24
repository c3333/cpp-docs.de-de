---
title: Compilerfehler C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: f76515d58f020b414e6b79a7737463af80bd2d07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200814"
---
# <a name="compiler-error-c3398"></a>Compilerfehler C3398

'Operator': Konvertierung von 'function_signature' in 'function_pointer' nicht möglich. Der Quellausdruck muss ein Funktionssymbol sein.

Wenn die [__clrcall](../../cpp/clrcall.md) -Aufrufkonvention bei der Kompilierung mit **/clr**nicht angegeben ist, generiert der Compiler zwei Einstiegspunkte (Adressen) für jede Funktion, einen systemeigener Einstiegspunkt und einen verwalteten Einstiegspunkt.

Standardmäßig gibt der Compiler den systemeigenen Einstiegspunkt zurück, aber es gibt einige Fälle, in denen der verwaltete Einstiegspunkt erwünscht ist (z. B. beim Zuweisen der Adresse zu einem `__clrcall` -Funktionszeiger). Damit der Compiler den verwalteten Einstiegspunkt in einer Zuordnung zuverlässig auswählen kann, muss die rechte Seite ein Funktionssymbol sein.
