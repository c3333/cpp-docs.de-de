---
title: Compilerfehler C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202370"
---
# <a name="compiler-error-c2708"></a>Compilerfehler C2708

"Bezeichner": die tatsächliche Parameter Länge in Bytes unterscheidet sich vom vorherigen Rückruf oder Verweis.

Einer [__stdcall](../../cpp/stdcall.md) Funktion muss ein Prototyp vorangestellt sein. Andernfalls interpretiert der Compiler den ersten Aufrufe der Funktion als Prototyp. dieser Fehler tritt auf, wenn der Compiler auf einen nicht abgeglichen-Befehl trifft.

Fügen Sie einen Funktionsprototyp hinzu, um diesen Fehler zu beheben.
