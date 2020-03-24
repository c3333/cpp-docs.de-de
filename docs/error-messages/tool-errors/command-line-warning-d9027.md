---
title: Befehlszeilenwarnung D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196676"
---
# <a name="command-line-warning-d9027"></a>Befehlszeilenwarnung D9027

die Quelldatei "\<filename >" wird ignoriert.

CL. exe hat die Eingabe Quelldatei ignoriert.

Diese Warnung kann durch ein Leerzeichen zwischen der Option/FO und einem Ausgabe Dateinamen in einer Befehlszeile mit der Option/c verursacht werden. Beispiel:

```
cl /c /Fo output.obj input.c
```

Da ein Leerzeichen zwischen/FO und `output.obj`vorhanden ist, nimmt CL. exe `output.obj` als Namen der Eingabedatei an. Entfernen Sie den Speicherplatz, um das Problem zu beheben:

```
cl /c /Fooutput.obj input.c
```
