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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440448"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importieren von Daten mithilfe von "__declspec(dllimport)"

Im Fall von Daten ist die Verwendung von **__declspec (dllimport)** ein praktisches Element, das eine Dereferenzierungsebene entfernt. Wenn Sie Daten aus einer dll importieren, müssen Sie immer noch die Import Adress Tabelle durchlaufen. Vor **__declspec (dllimport)** bedeutete dies, dass Sie beim Zugriff auf Daten, die aus der dll exportiert wurden, eine zusätzliche dereferenzierungsstufe durchführen mussten:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Anschließend exportieren Sie die Daten in Ihrer. DEF-Datei:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

und auf diese außerhalb der dll zugreifen:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Wenn Sie die Daten als **__declspec (dllimport)** markieren, generiert der Compiler automatisch den dereferenzierungscode für Sie. Sie müssen sich keine Gedanken mehr über die oben beschriebenen Schritte machen. Wie bereits erwähnt, sollten Sie bei der Erstellung der dll keine **__declspec (dllimport)** -Deklaration für die Daten verwenden. Funktionen innerhalb der DLL verwenden die Import Adress Tabelle nicht für den Zugriff auf das Datenobjekt. Daher haben Sie keinen zusätzlichen Dereferenzierungsebene.

Um die Daten automatisch aus der dll zu exportieren, verwenden Sie diese Deklaration:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Weitere Informationen

[Importieren in eine Anwendung](importing-into-an-application.md)
