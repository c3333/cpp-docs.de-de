---
title: Compilerfehler C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: a3e2268bfc5597668e8689d093a0c2bb7f18e037
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207284"
---
# <a name="compiler-error-c2129"></a>Compilerfehler C2129

die statische Funktion "Function" wurde deklariert, aber nicht definiert.

Ein vorwärts Verweis erfolgt auf eine `static` Funktion, die nie definiert ist.

Eine `static` Funktion muss im Datei Gültigkeitsbereich definiert werden. Wenn die Funktion in einer anderen Datei definiert ist, muss Sie als `extern`deklariert werden.
