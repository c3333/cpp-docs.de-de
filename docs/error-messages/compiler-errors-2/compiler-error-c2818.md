---
title: Compilerfehler C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212669"
---
# <a name="compiler-error-c2818"></a>Compilerfehler C2818

Anwendung des überladenen Operators "Operator->" ist durch den Typ "Typ" rekursiv

Eine Neudefinition des Klassenmember-Zugriffs Operators enthält eine rekursive **`return`** Anweisung. Wenn Sie den `->` Operator mit Rekursion neu definieren möchten, müssen Sie die rekursive Routine in eine separate Funktion verschieben, die von der Operator Überschreibungs Funktion aufgerufen wird.
