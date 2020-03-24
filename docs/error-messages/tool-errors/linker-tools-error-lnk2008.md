---
title: Linkertoolfehler LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194823"
---
# <a name="linker-tools-error-lnk2008"></a>Linkertoolfehler LNK2008

Das fixupziel ist nicht als "symbol_name" ausgerichtet.

Link hat ein fixupziel in der Objektdatei gefunden, das nicht ordnungsgemäß ausgerichtet wurde.

Dieser Fehler kann durch eine benutzerdefinierte secton-Ausrichtung (z. b. #Pragma [Pack](../../preprocessor/pack.md)), einen [align](../../cpp/align-cpp.md) -Modifizierer oder durch die Verwendung von assemblysprachcode verursacht werden, der die Ausrichtung von secton ändert

Wenn der Code keine der oben genannten Optionen verwendet, kann dies durch den Compiler verursacht werden.
