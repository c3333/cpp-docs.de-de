---
title: Compilerfehler C2307
ms.date: 11/04/2016
f1_keywords:
- C2307
helpviewer_keywords:
- C2307
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
ms.openlocfilehash: a9d5addc18dd548e584a1cceed8b880cb62ed40d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206278"
---
# <a name="compiler-error-c2307"></a>Compilerfehler C2307

pragma ' pragma ' muss sich außerhalb der Funktion befinden, wenn inkrementelle Kompilierung aktiviert ist

Sie müssen das `data_seg`-Pragma zwischen den Funktionen platzieren, wenn Sie die inkrementelle Kompilierung verwenden.
