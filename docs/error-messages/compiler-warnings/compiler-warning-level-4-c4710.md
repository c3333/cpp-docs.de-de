---
title: Compilerwarnung (Stufe 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c39848b9b3e94e35c4d0c0937a0974b717c6bd8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198175"
---
# <a name="compiler-warning-level-4-c4710"></a>Compilerwarnung (Stufe 4) C4710

"Function": Funktion nicht Inline

Die angegebene Funktion wurde für die Inline Erweiterung ausgewählt, aber der Compiler hat das Inlining nicht durchgeführt.

Inlining wird nach dem Ermessen des Compilers ausgeführt. Das **Inline** Schlüsselwort wird wie das **Register** -Schlüsselwort als Hinweis für den Compiler verwendet. Der Compiler bestimmt mithilfe von Heuristik, ob er eine bestimmte Funktion Inline verwenden soll, um den Code bei der Kompilierung der Geschwindigkeit zu beschleunigen, oder ob er eine bestimmte Funktion Inline verwenden soll, um den Code bei der Kompilierung für Leerzeichen zu verkleinern. Beim Kompilieren von Leerzeichen werden nur sehr kleine Funktionen vom Compiler Inline eingebunden.

In einigen Fällen wird der Compiler eine bestimmte Funktion aus mechanischen Gründen nicht Inline Inline. Unter [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) finden Sie eine Liste der Gründe, warum der Compiler eine Funktion nicht Inline Inline durchführen kann.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .
