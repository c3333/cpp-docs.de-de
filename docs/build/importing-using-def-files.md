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
ms.openlocfilehash: e4ac48dc013874c240411f78a733d32e116df25d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223966"
---
# <a name="importing-using-def-files"></a>Importieren mithilfe von DEF-Dateien

Wenn Sie **`__declspec(dllimport)`** zusammen mit einer DEF-Datei verwenden, sollten Sie die DEF-Datei so anpassen, dass diese DATA anstelle von CONSTANT verwendet, um die Wahrscheinlichkeit zu verringern, dass ein Problem durch falsche Codierung entsteht:

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

Wenn Sie **`__declspec(dllimport)`** und CONSTANT verwenden, werden sowohl die `imp`-Version als auch der undekorierte Name in der .lib-DLL-Importbibliothek aufgelistet, die so erstellt wird, dass sie explizite Bindung zulässt. Wenn Sie **`__declspec(dllimport)`** und DATA verwenden, wird nur die `imp`-Version des Namens aufgeführt.

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

Der aktuelle MSVC-Linker gibt eine Warnung aus, wenn er CONSTANT in der DEF-Datei entdeckt, um auf diesen Fall hinzuweisen. Der einzig wahre Grund für die Verwendung von CONSTANT ist der Fall, dass Sie einige Objektdateien nicht erneut kompilieren können, bei denen die Headerdatei **`__declspec(dllimport)`** im Prototyp nicht aufgelistet hat.

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)
