---
title: Linkertoolfehler LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194810"
---
# <a name="linker-tools-error-lnk2011"></a>Linkertoolfehler LNK2011

Vorkompiliertes Objekt nicht verknüpft in; Image kann möglicherweise nicht ausgeführt werden

Wenn Sie vorkompilierte Header verwenden, erfordert Link, dass alle mit vorkompilierten Headern erstellten Objektdateien in verknüpft werden müssen. Wenn Sie über eine Quelldatei verfügen, die Sie verwenden, um einen vorkompilierten Header zur Verwendung mit anderen Quelldateien zu generieren, müssen Sie jetzt die Objektdatei einschließen, die zusammen mit dem vorkompilierten Header erstellt wurde.

Wenn Sie z. b. eine Datei mit dem Namen "Stub. cpp" kompilieren, um einen vorkompilierten Header für die Verwendung mit anderen Quelldateien zu erstellen, müssen Sie eine Verknüpfung mit "Stub. obj" herstellen. andernfalls wird dieser Fehler angezeigt. In den folgenden Befehlszeilen wird Zeile 1 verwendet, um einen vorkompilierten Header (Common. pch) zu erstellen, der mit PROG1. cpp und PROG2. cpp in den Zeilen 2 und 3 verwendet wird. Die Datei Stub. cpp enthält nur `#include` Zeilen (dieselben `#include` Zeilen wie in PROG1. cpp und PROG2. cpp) und wird nur zum Generieren von vorkompilierten Headern verwendet. In der letzten Zeile muss Stub. obj in verknüpft werden, um Linkertoolfehler LNK2011 zu vermeiden.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
