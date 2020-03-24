---
title: Compilerwarnung (Stufe 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198119"
---
# <a name="compiler-warning-level-4-c4960"></a>Compilerwarnung (Stufe 4) C4960

"function" ist zu groß, um ein Profil zu erstellen

Bei Verwendung von [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)hat der Compiler ein Eingabemodul mit einer Funktion mit mehr als 65.535 Anweisungen erkannt. Eine so große Funktion ist für profilgesteuerte Optimierungen nicht verfügbar.

Verkleinern Sie die Funktion, um die Warnung aufzuheben.
