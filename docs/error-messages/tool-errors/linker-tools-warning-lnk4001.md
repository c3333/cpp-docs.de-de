---
title: Linkertoolwarnung LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194407"
---
# <a name="linker-tools-warning-lnk4001"></a>Linkertoolwarnung LNK4001

Es wurden keine Objektdateien angegeben. verwendete Bibliotheken

An den Linker wurden mindestens eine LIB-Datei, aber keine OBJ-Dateien weitergeleitet.

Da der Linker nicht in der Lage ist, auf Informationen in einer LIB-Datei zuzugreifen, auf die in einer OBJ-Datei zugegriffen werden kann, weist diese Warnung darauf hin, dass Sie explizit andere Linkeroptionen angeben müssen. Möglicherweise müssen Sie z. b. die Optionen [/Machine](../../build/reference/machine-specify-target-platform.md), [/out](../../build/reference/out-output-file-name.md)oder [/Entry](../../build/reference/entry-entry-point-symbol.md) angeben.
