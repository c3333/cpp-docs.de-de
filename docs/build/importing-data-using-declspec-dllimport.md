---
title: Importieren von Daten mithilfe von "__declspec(dllimport)"
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440448"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importieren von Daten mithilfe von "__declspec(dllimport)"

Im Fall von Daten ist **__declspec(dllimport)** ein praktisches Element, das eine Dereferenzierungsstufe entfernt. Wenn Sie Daten aus einer DLL importieren, müssen Sie immer noch die Importadresstabelle durchlaufen. Vor **__declspec(dllimport)** bedeutete dies, dass beim Zugriff auf Daten, die aus der DLL exportiert wurden, eine zusätzliche Dereferenzierungsstufe erforderlich war:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Anschließend exportieren Sie die Daten in Ihrer DEF-Datei:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

und greifen außerhalb der DLL auf sie zu:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Wenn Sie die Daten als **__declspec(dllimport)** markieren, generiert der Compiler automatisch den Dereferenzierungscode für Sie. Sie müssen sich keine Gedanken mehr über die oben beschriebenen Schritte machen. Wie bereits erwähnt, sollten Sie bei der Erstellung der DLL die **__declspec(dllimport)** -Deklaration nicht für die Daten verwenden. Funktionen innerhalb der DLL verwenden nicht die Importadresstabelle für den Zugriff auf das Datenobjekt, und daher verfügen Sie nicht über die zusätzliche Dereferenzierungsstufe.

Um die Daten automatisch aus der DLL zu exportieren, verwenden Sie die folgende Deklaration:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)
