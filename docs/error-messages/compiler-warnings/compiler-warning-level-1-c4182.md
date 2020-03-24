---
title: Compilerwarnung (Stufe 1) C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: a438373b7fda04a6e8d1f76e2ef38208c3e557a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175947"
---
# <a name="compiler-warning-level-1-c4182"></a>Compilerwarnung (Stufe 1) C4182

\#die Schachtelungs Ebene einschließen ist "Number" Deep; mögliche unendliche Rekursion

Dem Compiler stand aufgrund der Anzahl geschachtelter Includedateien kein Heapspeicherplatz mehr zur Verfügung. Eine Includedatei, die aus einer anderen Includedatei eingefügt wird, ist geschachtelt.

Diese Meldung dient zur Information und wird vor dem Fehler [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)ausgegeben.
