---
title: Namensergänzung
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: 6a43b952b2f8f9bcbb5e835bf8e20682c99f2935
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218038"
---
# <a name="name-decoration"></a>Namensergänzung

Namensergänzungen beziehen in der Regel auf C++-Benennungskonventionen, können jedoch auch auf eine Vielzahl von C-Fällen zutreffen. Standardmäßig verwendet C++ den Funktionsnamen, Parameter und den Rückgabetyp, um einen Linkernamen für die Funktion zu erstellen. Beachten Sie die folgende Funktionsdeklaration:

`void CALLTYPE test(void);`

In der folgenden Tabelle ist der Linkername für verschiedene Aufrufkonventionen dargestellt.

|Aufrufkonvention|`extern "C"`oder- `.c` Datei|`.cpp`, `.cxx` oder`/TP`|
|------------------------|---------------------------|------------------------|
|C-Benennungs Konvention ( **`__cdecl`** )|`_test`|`?test@@ZAXXZ`|
|Benennungs Konvention für schnelles anrufen ( **`__fastcall`** )|`@test@0`|`?test@@YIXXZ`|
|Standard mäßige Benennungs Konvention für Aufrufe ( **`__stdcall`** )|`_test@0`|`?test@@YGXXZ`|
|Benennungs Konvention für Vektor Aufrufe ( **`__vectorcall`** )|`test@@0`|`?test@@YQXXZ`|

Verwenden `extern "C"` Sie, um eine C-Funktion von C++ aufzurufen. `extern "C"`erzwingt die Verwendung der C-Benennungs Konvention für nicht-Klassen-C++-Funktionen. Beachten Sie die Compilerschalter **/TC** oder **/tp**, die den Compiler anweisen, die Dateinamenerweiterung zu ignorieren und die Datei als C bzw. C++ zu kompilieren. Diese Optionen können zu nicht erwarteten Linker-Namen führen.

Funktionsprototypen mit nicht übereinstimmenden Parametern können auch zu diesem Fehler führen. Namensergänzungen fügen die Parameter einer Funktion in den endgültigen ergänzten Funktionsnamen ein. Das Aufrufen einer Funktion mit den Parametertypen, die nicht mit denen in der Funktionsdeklaration identisch sind, kann auch LNK2001 verursachen.

Zurzeit gibt es keine Standards für C++ Naming zwischen compileranbietern oder sogar zwischen verschiedenen Versionen eines Compilers. Das Verknüpfen von Objektdateien, die von anderen Compilern kompiliert werden, erzeugt möglicherweise nicht dasselbe Benennungs Schema und kann zu nicht aufgelösten externalen führen.

## <a name="see-also"></a>Weitere Informationen

[Linker-Tools-Fehler LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
