---
title: Import- und Exportfunktionen einer DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: 8d703045773e4d2c320eaef2aa80c4ce74d23472
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234246"
---
# <a name="dll-import-and-export-functions"></a>Import- und Exportfunktionen einer DLL

**Microsoft-spezifisch**

Die vollständigsten und aktuellsten Informationen zu diesem Thema finden Sie unter [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Die Speicherklassenmodifizierer **dllimport** und `dllexport` sind Microsoft-spezifische Erweiterungen der Sprache C. Diese Modifizierer definieren explizit die Schnittstelle der DLL mit dem Client (die ausführbare Datei oder eine andere DLL). Durch das Deklarieren von Funktionen als `dllexport` ist keine Moduldefinitionsdatei (.DEF) notwendig. Sie können auch die **dllimport**- und `dllexport`-Modifizierer mit Daten und Objekten verwenden.

Die **dllimport** und `dllexport`-Speicherklassenmodifizierer müssen mit dem erweiterten Schlüsselwort der Attributsyntax, `__declspec`, wie in diesem Beispiel gezeigt verwendet werden:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Spezifische Informationen zur Syntax für erweiterte Speicherklassenmodifizierer finden Sie unter [Erweiterte Speicherklassenattribute](../c-language/c-extended-storage-class-attributes.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
