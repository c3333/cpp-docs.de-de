---
title: Compilerfehler C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 7e6e07fb90827fb28fcdde2f723a36c4529a1868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225487"
---
# <a name="compiler-error-c2410"></a>Compilerfehler C2410

' Identifier ': mehrdeutiger Elementname in ' context '

Der Bezeichner ist in diesem Kontext Mitglied von mehr als einer Struktur oder Union.

Verwenden Sie einen Struktur-oder Union-Spezifizierer für den Operanden, der den Fehler verursacht hat. Ein Struktur-oder Union-Spezifizierer ist ein Bezeichner des Typs **`struct`** oder **`union`** (ein **`typedef`** Name oder eine Variable desselben Typs wie die Struktur oder Union, auf die verwiesen wird). Der Spezifizierer muss der linke Operand des ersten Member-Selection-Operators (.) sein, um den Operanden zu verwenden.
