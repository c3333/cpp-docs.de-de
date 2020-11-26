---
title: Erweitern von Platzhalterargumenten
description: Verwenden einer Linkeroption zum Verarbeiten von Platzhalter-Befehlszeilenargumenten in Ihren Programmen.
ms.date: 11/20/2020
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.openlocfilehash: b847a5dd8af577a4e30edcd9bc7fc34add296c17
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483307"
---
# <a name="expanding-wildcard-arguments"></a>Erweitern von Platzhalterargumenten

Die Erweiterung des Platzhalterarguments ist spezifisch für Microsoft.

Wenn Sie ein C-Programm ausführen, können Sie einen von zwei Platzhaltern – das Fragezeichen ( **`?`** ) und das Sternchen ( **`*`** ) – verwenden, um Dateinamen- und Pfadargumente in der Befehlszeile anzugeben.

Standardmäßig werden Platzhalter in Befehlszeilenargumenten nicht erweitert. Sie können die normale `argv`-Laderoutine für den Argumentvektor durch eine Version ersetzen, die Platzhalter durch eine Verknüpfung mit der Datei *`setargv.obj`* oder *`wsetargv.obj`* erweitert. Wenn das Programm eine `main`-Funktion verwendet, stellen Sie eine Verknüpfung mit *`setargv.obj`* her. Wenn das Programm eine `wmain`-Funktion verwendet, stellen Sie eine Verknüpfung mit *`wsetargv.obj`* her. Beide weisen das gleiche Verhalten auf. 

Verwenden Sie die Option **`/link`** , um mit *`setargv.obj`* oder *`wsetargv.obj`* zu verknüpfen. Beispiel:

**`cl example.c /link setargv.obj`**

Die Platzhalter werden auf dieselbe Weise wie Betriebssystembefehle erweitert.

## <a name="see-also"></a>Siehe auch

[Linkoptionen](../c-runtime-library/link-options.md)\
[`main`-Funktion und Programmausführung](../c-language/main-function-and-program-execution.md)
