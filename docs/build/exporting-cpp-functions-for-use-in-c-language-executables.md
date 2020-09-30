---
title: Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: 38b13c1fc9c57354ba8160f6dbe0df6546fe7b5f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506602"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien

Falls eine DLL in C++ geschriebene Funktionen enthält und auf diese Funktionen über ein C-Sprachmodul zugegriffen werden soll, sollten Sie diese Funktionen mit C-Bindung anstatt mit C++-Bindung deklarieren. Sofern nicht anders angegeben, verwendet der C++-Compiler die typsichere Namensgebung (auch Namensergänzung genannt) sowie die Aufrufkonventionen von C++, wodurch ein von C durchgeführter Aufruf sich schwierig gestalten kann.

Geben Sie `extern "C"` für Ihre Funktionsdeklarationen an, um die C-Bindung anzugeben. Zum Beispiel:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von DEF-Dateien](exporting-from-a-dll-using-def-files.md)

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Dekorierte Namen](reference/decorated-names.md)

- [Verwenden von "extern" zur Angabe der Verknüpfung](../cpp/extern-cpp.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
