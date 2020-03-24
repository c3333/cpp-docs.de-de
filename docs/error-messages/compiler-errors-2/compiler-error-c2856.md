---
title: Compilerfehler C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: c88610607083ecfaf5f20cd585b479991fa51b44
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201879"
---
# <a name="compiler-error-c2856"></a>Compilerfehler C2856

\#Pragma hdrstopps darf sich nicht innerhalb eines #If Blocks befinden.

Das `hdrstop`-Pragma kann nicht innerhalb des Texts eines Blocks für die bedingte Kompilierung platziert werden.

Verschieben Sie die `#pragma hdrstop`-Anweisung in einen Bereich, der nicht in einem `#if/#endif`-Block enthalten ist.
