---
title: Compilerfehler C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: f6af217dbcd871ac4edd1852042144802388545b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216088"
---
# <a name="compiler-error-c2696"></a>Compilerfehler C2696

Ein temporäres Objekt vom verwalteten Typ "Type" kann nicht erstellt werden.

Verweise auf **`const`** in einem nicht verwalteten Programm bewirken, dass der Compiler den Konstruktor aufruft und ein temporäres Objekt auf dem Stapel erstellt. Eine verwaltete Klasse kann jedoch nie auf dem Stapel erstellt werden.

C2696 ist nur mit der veralteten Compileroption **/clr: oldSyntax**erreichbar.
