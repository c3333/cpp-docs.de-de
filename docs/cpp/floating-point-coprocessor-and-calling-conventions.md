---
title: Gleitkomma-Coprozessor und Aufrufkonventionen
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188620"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Gleitkomma-Coprozessor und Aufrufkonventionen

Wenn Sie Assemblyroutinen für den Gleit Komma-Coprozessor schreiben, müssen Sie das Gleit Komma Steuerwort beibehalten und den Coprozessor-Stapel bereinigen, es sei denn, Sie geben einen **float** -oder **Double** -Wert zurück, der von der Funktion in St (0) zurückgegeben werden soll.

## <a name="see-also"></a>Weitere Informationen

[Aufrufkonventionen](../cpp/calling-conventions.md)
