---
title: Compilerwarnung (Stufe 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199541"
---
# <a name="compiler-warning-level-1-c4651"></a>Compilerwarnung (Stufe 1) C4651

"Definition" für den vorkompilierten Header, aber nicht für die aktuelle Kompilierung angegeben

Die Definition wurde beim Generieren des vorkompilierten Headers angegeben, jedoch nicht in dieser Kompilierung.

Die Definition ist innerhalb des vorkompilierten Headers, aber nicht im Rest des Codes wirksam.

Wenn ein vorkompilierter Header mit/DSYMBOL erstellt wurde, generiert der Compiler diese Warnung, wenn die/Yu-Kompilierung nicht über/DSYMBOL.  Durch das Hinzufügen von/DSYMBOL zur/Yu-Befehlszeile wird diese Warnung aufgelöst.
