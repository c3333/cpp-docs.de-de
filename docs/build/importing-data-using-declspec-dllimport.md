---
title: Importieren von Daten mithilfe von __declspec(dllimport)
description: Verwenden von __declspec(dllimport) zum Importieren von DLL-Daten.
ms.date: 09/03/2020
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: cb9850306d6e73b88e2926a6f068ae21f8d32530
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609122"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importieren von Daten mit `__declspec(dllimport)`

Bei Daten ist **`__declspec(dllimport)`** ein praktisches Element, das eine Dereferenzierungsstufe entfernt. Wenn Sie Daten aus einer DLL importieren, müssen Sie immer noch die Importadresstabelle durchlaufen. Vor **`__declspec(dllimport)`** bedeutete dies, dass beim Zugriff auf Daten, die aus der DLL exportiert wurden, eine zusätzliche Dereferenzierungsstufe erforderlich war:

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Anschließend exportieren Sie die Daten in Ihrer DEF-Datei:

```DEF
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

und greifen außerhalb der DLL auf sie zu:

```C
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Wenn Sie die Daten als **`__declspec(dllimport)`** markieren, generiert der Compiler automatisch den Dereferenzierungscode für Sie. Sie müssen sich keine Gedanken mehr über die oben beschriebenen Schritte machen. Wie bereits erwähnt, sollten Sie bei der Erstellung der DLL die **`__declspec(dllimport)`** -Deklaration nicht für die Daten verwenden. Funktionen innerhalb der DLL verwenden nicht die Importadresstabelle für den Zugriff auf das Datenobjekt, und daher verfügen Sie nicht über die zusätzliche Dereferenzierungsstufe.

Um die Daten automatisch aus der DLL zu exportieren, verwenden Sie die folgende Deklaration:

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   __declspec(dllexport) ULONG ulDataInDLL;

#else         // If accessing the data from outside the DLL
   __declspec(dllimport) ULONG ulDataInDLL;
#endif
```

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)
