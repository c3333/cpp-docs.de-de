---
title: Extrahieren eines Bibliothekmembers
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439883"
---
# <a name="extracting-a-library-member"></a>Extrahieren eines Bibliothekmembers

Sie können lib verwenden, um eine Objektdatei (obj-Datei) zu erstellen, die eine Kopie eines Members einer vorhandenen Bibliothek enthält. Verwenden Sie die folgende Syntax, um eine Kopie eines Members zu extrahieren:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Mit diesem Befehl wird eine OBJ-Datei mit dem Namen " *ObjectFile* " erstellt, die eine Kopie einer `member` einer *Bibliothek*enthält. Beim `member` Namen wird die Groß-/Kleinschreibung beachtet. Sie können nur ein Element in einem einzelnen Befehl extrahieren. Die/out-Option ist erforderlich. Es ist kein Standardausgabe Name vorhanden. Wenn eine Datei mit dem Namen *ObjectFile* bereits im angegebenen Verzeichnis (oder im aktuellen Verzeichnis vorhanden ist, wenn kein Verzeichnis mit *ObjectFile*angegeben ist), wird die vorhandene Datei durch die extrahierte *ObjectFile* ersetzt.

## <a name="see-also"></a>Weitere Informationen

[LIB-Referenz](lib-reference.md)
