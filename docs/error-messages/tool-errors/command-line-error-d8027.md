---
title: Befehlszeilenfehler D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196884"
---
# <a name="command-line-error-d8027"></a>Befehlszeilenfehler D8027

' Komponente ' kann nicht ausgeführt werden.

Der Compiler konnte die angegebene Compilerkomponente oder den angegebenen Linker nicht ausführen.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Nicht genügend Arbeitsspeicher zum Laden der Komponente. Wenn NMAKE den Compiler aufgerufen hat, führen Sie den Compiler außerhalb der Makefile aus.

1. Die Komponente konnte vom aktuellen Betriebssystem nicht ausgeführt werden. Stellen Sie sicher, dass der Pfad auf die ausführbaren Dateien verweist, die für Ihr Betriebssystem geeignet sind.

1. Die Komponente wurde beschädigt. Verwenden Sie das Setup Programm, um die Komponente von den Verteilungs Datenträgern neu zu verteilen.

1. Eine Option wurde falsch angegeben. Beispiel:

    ```
    cl /B1 file1.c
    ```
