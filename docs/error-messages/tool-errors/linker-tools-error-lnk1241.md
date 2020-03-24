---
title: Linkertoolfehler LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183812"
---
# <a name="linker-tools-error-lnk1241"></a>Linkertoolfehler LNK1241

die Ressourcen Datei "Resource File" wurde bereits angegeben.

Dieser Fehler wird generiert, wenn Sie **CVTRES** manuell von der Befehlszeile ausführen und die resultierende OBJ-Datei zusätzlich zu anderen RES-Dateien an den Linker übergeben.

Wenn Sie mehrere RES-Dateien angeben möchten, übergeben Sie diese als res-Dateien an den Linker, nicht innerhalb von. obj-Dateien, die von **CVTRES**erstellt wurden.
