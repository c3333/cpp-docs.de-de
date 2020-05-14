---
title: Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273572"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien

Wenn Sie über Funktionen in einer DLL verfügen, die in C geschrieben wurden und auf die Sie über eine C-Sprache oder ein C++Sprachmodul zugreifen möchten, sollten Sie das **__cplusplus**-Präprozessormakro verwenden, um zu bestimmen, welche Sprache kompiliert wird, und dann diese Funktionen mit einer C-Bindung deklarieren, wenn sie von einem C++-Sprachmodul verwendet werden. Wenn Sie diese Technik verwenden und Headerdateien für Ihre DLL bereitstellen, können diese Funktionen von C- und C++-Benutzern ohne Änderung verwendet werden.

Der folgende Code zeigt eine Headerdatei, die von C- und C++-Clientanwendungen verwendet werden kann:

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

Wenn Sie C-Funktionen mit Ihrer ausführbaren C++-Datei verknüpfen müssen und die Headerdateien der Funktionsdeklaration die oben genannte Technik nicht verwendet haben, gehen Sie in der C++-Quelldatei folgendermaßen vor, um zu verhindern, dass der Compiler die C-Funktionsnamen mit Attributen versieht:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von „AFX_EXT_CLASS“](exporting-and-importing-using-afx-ext-class.md)

- [Ermitteln, welche Exportmethode verwendet werden soll](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Dekorierte Namen](reference/decorated-names.md)

- [Verwenden von "extern" zur Angabe der Verknüpfung](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
