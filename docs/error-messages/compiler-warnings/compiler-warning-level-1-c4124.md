---
title: Compilerwarnung (Stufe 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 59860bef108a3cd3e8bbbc6ff0790e17dbdaa0d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214489"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilerwarnung (Stufe 1) C4124

__fastcall mit Stapel Überprüfung ist ineffizient

Das **`__fastcall`** Schlüsselwort wurde mit aktivierter Stapel Überprüfung verwendet.

Die **`__fastcall`** Konvention generiert schnelleren Code, aber die Stapel Überprüfung verursacht langsameren Code. Deaktivieren Sie bei Verwendung **`__fastcall`** von die Stapel Überprüfung mit dem **check_stack** -Pragma oder/GS.

Diese Warnung wird nur für die erste, unter diesen Bedingungen deklarierte Funktion ausgegeben.
