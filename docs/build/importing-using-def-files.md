---
title: Importieren mithilfe von DEF-Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273416"
---
# <a name="importing-using-def-files"></a>Importieren mithilfe von DEF-Dateien

Wenn Sie sich dafür entscheiden, **__declspec(dllimport)** zusammen mit einer DEF-Datei zu verwenden, sollten Sie die DEF-Datei so anpassen, dass diese DATA anstelle von CONSTANT verwendet, um die Wahrscheinlichkeit zu reduzieren, dass ein Problem durch falsche Codierung entsteht:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

In der folgenden Tabelle wird der Grund dafür erläutert.

|Stichwort|Ausgabe in der Importbibliothek|Exports|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Wenn Sie **__declspec(dllimport)** und CONSTANT verwenden, werden sowohl die `imp`-Version als auch der undekorierte Name in der .lib-DLL-Importbibliothek aufgelistet, die so erstellt wird, dass sie eine explizite Verknüpfung zulässt. Wenn Sie **__declspec(dllimport)** und DATA verwenden, wird nur die `imp`-Version des Namens aufgeführt.

Wenn Sie CONSTANT verwenden, kann eines der folgenden Codekonstrukte verwendet werden, um auf `ulDataInDll` zuzugreifen:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- oder -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Wenn Sie in Ihrer DEF-Datei jedoch DATA verwenden, kann nur Code, der mit der folgenden Definition kompiliert wurde, auf die Variable `ulDataInDll` zugreifen:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Die Verwendung von CONSTANT ist riskanter. Wenn Sie nämlich vergessen, die zusätzliche Dereferenzierung zu verwenden, greifen Sie möglicherweise auf den Zeiger der Importadresstabelle auf die Variable und nicht auf die Variable selbst zu. Diese Art von Problem kann sich oft als Zugriffsverletzung erweisen, da die Importadresstabelle derzeit durch den Compiler und den Linker schreibgeschützt ist.

Der aktuelle MSVC-Linker gibt eine Warnung aus, wenn er CONSTANT in der DEF-Datei entdeckt, um auf diesen Fall hinzuweisen. Der einzig wahre Grund für die Verwendung von CONSTANT ist der Fall, dass Sie einige Objektdateien nicht kompilieren können, bei denen die Headerdatei **__declspec(dllimport)** nicht auf dem Prototyp aufgelistet hat.

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)
