---
title: Compilerfehler C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: e4d30ff0fbca7428fb1dcf252bcad50bd53488d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205693"
---
# <a name="compiler-error-c2410"></a>Compilerfehler C2410

' Identifier ': mehrdeutiger Elementname in ' context '

Der Bezeichner ist in diesem Kontext Mitglied von mehr als einer Struktur oder Union.

Verwenden Sie einen Struktur-oder Union-Spezifizierer für den Operanden, der den Fehler verursacht hat. Ein Struktur-oder Union-Spezifizierer ist ein Bezeichner des Typs `struct` oder `union` (ein `typedef` Name oder eine Variable desselben Typs wie die Struktur oder Union, auf die verwiesen wird). Der Spezifizierer muss der linke Operand des ersten Member-Selection-Operators (.) sein, um den Operanden zu verwenden.
