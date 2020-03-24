---
title: Compilerwarnung (Stufe 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 2956758a6bdd074d7fc902c6ebac60af19e34b54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186763"
---
# <a name="compiler-warning-level-1-c4445"></a>Compilerwarnung (Stufe 1) C4445

'Funktion' : Eine virtuelle Methode kann in einem WinRT- oder verwalteten Typ nicht privat sein.

Wenn eine virtuelle Funktion privat ist, kann über einen abgeleiteten Typ nicht auf diese zugegriffen werden. Um diesen Fehler zu beheben, ändern Sie den Zugriff auf die virtuelle Memberfunktion in „Protected“ oder „Public“.
