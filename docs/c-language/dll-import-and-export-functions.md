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
ms.openlocfilehash: 753a51fa8e2c87b77a54e5e93522e5f11585b610
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200074"
---
# <a name="dll-import-and-export-functions"></a>Import- und Exportfunktionen einer DLL

**Microsoft-spezifisch**

Die vollständigsten und aktuellsten Informationen zu diesem Thema finden Sie unter [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Die Speicherklassenmodifizierer **`dllimport`** und `dllexport` sind Microsoft-spezifische Erweiterungen der Sprache C. Diese Modifizierer definieren explizit die Schnittstelle der DLL mit dem Client (die ausführbare Datei oder eine andere DLL). Durch das Deklarieren von Funktionen als `dllexport` ist keine Moduldefinitionsdatei (.DEF) notwendig. Sie können auch die **`dllimport`** - und `dllexport`-Modifizierer mit Daten und Objekten verwenden.

Die **`dllimport`** und `dllexport`-Speicherklassenmodifizierer müssen mit dem erweiterten Schlüsselwort der Attributsyntax, **`__declspec`** , wie in diesem Beispiel gezeigt verwendet werden:

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
