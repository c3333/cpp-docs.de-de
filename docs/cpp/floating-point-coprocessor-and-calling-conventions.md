---
title: Gleitkomma-Coprozessor und Aufrufkonventionen
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 09358ee36da7e5a86c214789fa7fd0687e9b8825
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231194"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Gleitkomma-Coprozessor und Aufrufkonventionen

Wenn Sie Assemblyroutinen für den Gleit Komma-Coprozessor schreiben, müssen Sie das Gleit Komma Steuerwort beibehalten und den Coprozessor-Stapel bereinigen, es sei denn, Sie geben einen-Wert oder einen-Wert zurück, den **`float`** **`double`** die Funktion in St (0) zurückgeben soll.

## <a name="see-also"></a>Siehe auch

[Aufrufkonventionen](../cpp/calling-conventions.md)
