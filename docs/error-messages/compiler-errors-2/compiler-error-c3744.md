---
title: Compilerfehler C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 8db81afc348434e9ea2f57c991962fb15dc6bf98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220157"
---
# <a name="compiler-error-c3744"></a>Compilerfehler C3744

__unhook müssen mindestens 3 Argumente für verwaltete Ereignisse aufweisen.

Die [`__unhook`](../../cpp/unhook.md) Funktion muss drei Parameter annehmen, wenn Sie in einem Programm verwendet wird, das für Managed Extensions for C++ kompiliert wird.

**`__hook`** und **`__unhook`** sind nicht mit der- **`/clr`** Programmierung kompatibel. Verwenden Sie stattdessen die Operatoren + = und-=.

C3744 ist nur mit der veralteten Compileroption erreichbar **`/clr:oldSyntax`** .
