---
title: Compilerfehler C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202109"
---
# <a name="compiler-error-c2818"></a>Compilerfehler C2818

Anwendung des überladenen Operators "Operator->" ist durch den Typ "Typ" rekursiv

Eine Neudefinition des Klassenmember-Zugriffs Operators enthält eine rekursive `return` Anweisung. Wenn Sie den `->` Operator mit Rekursion neu definieren möchten, müssen Sie die rekursive Routine in eine separate Funktion verschieben, die von der Operator Überschreibungs Funktion aufgerufen wird.
