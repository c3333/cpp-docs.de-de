---
title: Ausdrucksauswertungsfehler CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184462"
---
# <a name="expression-evaluator-error-cxx0064"></a>Ausdrucksauswertungsfehler CXX0064

Haltepunkt kann nicht für gebundene virtuelle Element Funktion festgelegt werden.

Ein Haltepunkt wurde für eine virtuelle Element Funktion durch einen Zeiger auf ein Objekt festgelegt, z. b.:

```
pClass->vfunc( int );
```

Ein Haltepunkt kann für eine virtuelle Funktion festgelegt werden, indem die-Klasse eingegeben wird, z. b.:

```
Class::vfunc( int );
```

Dieser Fehler ist mit CAN0064 identisch.
