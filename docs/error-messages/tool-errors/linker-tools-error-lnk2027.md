---
title: Linkertoolfehler LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 0c531f70f98a017e8b75cceddc684f99d33bc554
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194594"
---
# <a name="linker-tools-error-lnk2027"></a>Linkertoolfehler LNK2027

nicht aufgelöstes Modul Verweis "Module"

Eine Datei, die an den Linker weitergegeben wurde, weist eine Abhängigkeit von einem Modul auf, das weder mit **/ASSEMBLYMODULE** angegeben noch direkt an den Linker weitergegeben wurde.

Führen Sie zum Auflösen von Linkertoolfehler LNK2027 einen der folgenden Schritte aus:

- Übergeben Sie die Datei mit der Modul Abhängigkeit nicht an den Linker.

- Geben Sie das Modul mit **/ASSEMBLYMODULE**an.

- Wenn das Modul ein sicheres. netmodule ist, übergeben Sie das Modul direkt an den Linker.

Weitere Informationen finden Sie unter [/ASSEMBLYMODULE (ein MSIL-Modul zur Assembly hinzufügen)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) und [NETMODULE-Dateien als Eingabe](../../build/reference/netmodule-files-as-linker-input.md)für den Linker.
