---
title: Compilerwarnung (Stufe 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176311"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilerwarnung (Stufe 1) C4124

__fastcall mit Stapel Überprüfung ist ineffizient

Das `__fastcall`-Schlüsselwort wurde mit aktivierter Stapel Überprüfung verwendet.

Die `__fastcall` Konvention generiert schnelleren Code, aber die Stapel Überprüfung verursacht langsameren Code. Wenn Sie `__fastcall`verwenden, deaktivieren Sie die Stapel Überprüfung mit dem **check_stack** -Pragma oder/GS.

Diese Warnung wird nur für die erste, unter diesen Bedingungen deklarierte Funktion ausgegeben.
