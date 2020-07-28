---
title: Compilerfehler C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: 9cf414200dcfad8ae617e16e111bd26b19a315a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220430"
---
# <a name="compiler-error-c2129"></a>Compilerfehler C2129

die statische Funktion "Function" wurde deklariert, aber nicht definiert.

Ein vorwärts Verweis erfolgt auf eine **`static`** Funktion, die nie definiert ist.

Eine **`static`** Funktion muss im Datei Gültigkeitsbereich definiert werden. Wenn die Funktion in einer anderen Datei definiert ist, muss Sie als deklariert werden **`extern`** .
