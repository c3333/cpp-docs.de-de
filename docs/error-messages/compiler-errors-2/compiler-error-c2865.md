---
title: Compilerfehler C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201695"
---
# <a name="compiler-error-c2865"></a>Compilerfehler C2865

"Funktion": Unzulässiger Vergleich für handle_or_pointer

Verweise auf [Klassen und Strukturen](../../extensions/classes-and-structs-cpp-component-extensions.md) oder verwaltete Verweis Typen können nur auf Gleichheit verglichen werden, um zu überprüfen, ob Sie auf dasselbe Objekt (= =) oder auf unterschiedliche Objekte (! =) verweisen.

Sie können Sie nicht für die Reihenfolge vergleichen, weil die .NET-Laufzeit möglicherweise verwaltete Objekte zu einem beliebigen Zeitpunkt verschiebt und das Ergebnis des Tests ändert.
