---
title: Compilerfehler C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: 624b3ab47ccb1c934b612ec8648b5eee0d233690
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176974"
---
# <a name="compiler-error-c2919"></a>Compilerfehler C2919

'type': Operatoren können nicht direkt auf der veröffentlichten Oberfläche eines WinRT-Typs verwendet werden.

Das Windows-Runtime-Typsystem unterstützt nicht die Operatormemberfunktionen auf der veröffentlichten Oberfläche eines Typs. Dies liegt daran, weil nicht alle Sprachen Operatormemberfunktionen verwenden können. Sie können private oder interne Operatormemberfunktionen erstellen, die über C++-Code in derselben Klasse oder Kompilationskomponente aufgerufen werden können.

Entfernen Sie zum Beheben dieses Problems die Operatormemberfunktion aus der öffentlichen Schnittstelle, oder ändern Sie sie in eine benannte Memberfunktion. Benennen Sie die Memberfunktion beispielsweise anstelle von `operator==` in `Equals` um.
