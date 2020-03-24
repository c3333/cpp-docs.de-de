---
title: Compilerwarnung (Stufen 1 und 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 7e39e8c837d94776a804da2bf38643b453edb949
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198041"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Compilerwarnung (Stufen 1 und 4) C4115

'Typ': Benannte Typdefinition in runden Klammern

Das angegebene Symbol wird verwendet, um eine Struktur, Union oder einen Aufzählungstyp innerhalb eines Klammerausdrucks zu definieren. Der Gültigkeitsbereich der Definition ist möglicherweise unerwartet.

Bei einem C-Funktionsaufruf weist die Definition einen globalen Gültigkeitsbereich auf. In einem C++-Aufruf weist die Definition denselben Gültigkeitsbereich wie die aufgerufene Funktion auf.

Diese Warnung kann auch durch Deklaratoren in Klammern (z. B. Prototypen) verursacht werden, die keine Ausdrücke in Klammern sind.

Dies ist eine Warnung der Stufe 1 für C++- und C#-Programme, die mit ANSI-Kompatibilität (/Za) kompiliert werden. Andernfalls handelt es sich um eine Warnung der Stufe 3.
