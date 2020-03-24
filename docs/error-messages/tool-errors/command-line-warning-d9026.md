---
title: Befehlszeilenwarnung D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196702"
---
# <a name="command-line-warning-d9026"></a>Befehlszeilenwarnung D9026

Optionen gelten für die gesamte Befehlszeile.

In einem Befehl wurde eine Option angegeben, nachdem ein Dateiname angegeben wurde. Die Option wurde auf die vorangegangene Datei angewendet.

Beispielsweise im Befehl

```
CL verdi.c /G5 puccini.c
```

die Datei "Verdi. c" wird mit der/G5-Option, nicht mit dem/G4-Standard kompiliert.

Dieses Verhalten unterscheidet sich von einigen früheren Versionen, die nur die vor dem Dateinamen angegebenen Optionen angewendet haben, was dazu führt, dass Verdi. c mit/G4 und Puccini. c kompiliert wird, die mit/G5. kompiliert werden.
