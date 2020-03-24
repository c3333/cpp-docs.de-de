---
title: Linkertoolfehler LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194927"
---
# <a name="linker-tools-error-lnk1302"></a>Linkertoolfehler LNK1302

unterstützt nur das Verknüpfen von Safe. netmodules; Datei ". netmodule" kann nicht verknüpft werden.

Ein. netmodule (mit **/ln**kompiliert) wurde in einem Benutzer Versuch, MSIL-Verknüpfungen aufzurufen, an den Linker übermittelt.  Ein C++ Modul ist für MSIL-Verknüpfungen gültig, wenn es mit **/clr: Safe**kompiliert wird.

Um diesen Fehler zu beheben, kompilieren Sie mit **/clr: Safe** , um das MSIL-verknüpfen zu aktivieren, oder übergeben Sie die **/CLR** -oder **/clr: pure** . obj-Datei an den Linker anstatt an das Modul.

Weitere Informationen finden Sie unter

- [/LN (MSIL-Modul erstellen)](../../build/reference/ln-create-msil-module.md)

- [.NETMODULE-Dateien als Eingabe für den Linker](../../build/reference/netmodule-files-as-linker-input.md)
