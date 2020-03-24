---
title: Namensergänzung
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173516"
---
# <a name="name-decoration"></a>Namensergänzung

Namensergänzungen beziehen in der Regel auf C++-Benennungskonventionen, können jedoch auch auf eine Vielzahl von C-Fällen zutreffen. Standardmäßig verwendet C++ den Funktionsnamen, Parameter und den Rückgabetyp, um einen Linkernamen für die Funktion zu erstellen. Beachten Sie die folgende Funktionsdeklaration:

`void CALLTYPE test(void);`

In der folgenden Tabelle ist der Linkername für verschiedene Aufrufkonventionen dargestellt.

|Aufrufkonvention|Datei `extern "C"` oder `.c`|`.cpp`, `.cxx` oder `/TP`|
|------------------------|---------------------------|------------------------|
|C-Namenskonvention (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Benennungs Konvention für schnelles anrufen (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|Standard mäßige Benennungs Konvention für Aufrufe (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Benennungs Konvention für Vektor Aufrufe (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

Verwenden Sie `extern "C"`, um eine C- C++Funktion von aufzurufen. `extern "C"` erzwingt die Verwendung der C-Benennungs Konvention für C++ nicht-Klassen Funktionen. Beachten Sie die Compilerschalter **/TC** oder **/tp**, die den Compiler anweisen, die Dateinamenerweiterung zu ignorieren und die Datei C++als C bzw. zu kompilieren. Diese Optionen können zu nicht erwarteten Linker-Namen führen.

Funktionsprototypen mit nicht übereinstimmenden Parametern können auch zu diesem Fehler führen. Namensergänzungen fügen die Parameter einer Funktion in den endgültigen ergänzten Funktionsnamen ein. Das Aufrufen einer Funktion mit den Parametertypen, die nicht mit denen in der Funktionsdeklaration identisch sind, kann auch LNK2001 verursachen.

Zurzeit gibt es keine Standards C++ für die Benennung zwischen compileranbietern oder sogar zwischen verschiedenen Versionen eines Compilers. Das Verknüpfen von Objektdateien, die von anderen Compilern kompiliert werden, erzeugt möglicherweise nicht dasselbe Benennungs Schema und kann zu nicht aufgelösten externalen führen.

## <a name="see-also"></a>Weitere Informationen

[Linkertoolfehler LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
