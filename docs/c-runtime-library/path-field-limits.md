---
title: Begrenzungen für Pfadfelder
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 8db9961bd2d5b5b3ea9d3addad3c26737b4f5199
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171397"
---
# <a name="path-field-limits"></a>Begrenzungen für Pfadfelder

## <a name="syntax"></a>Syntax

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Bemerkungen

Diese Konstanten definieren die maximale Länge für den Pfad und die einzelnen Felder in diesem Pfad.

|Dauerhaft|Bedeutung|
|--------------|-------------|
|`_MAX_DIR`|Maximale Länge der Verzeichniskomponente|
|`_MAX_DRIVE`|Maximale Länge der Laufwerkskomponente|
|`_MAX_EXT`|Maximale Länge der Erweiterungskomponente|
|`_MAX_FNAME`|Maximale Länge der Dateinamenkomponente|
|`_MAX_PATH`|Maximale Länge des vollständigen Pfads|

> [!NOTE]
> Die C-Laufzeit unterstützt Pfadlängen bis zu 32.768 Zeichen, aber es hängt vom Betriebssystem, insbesondere vom Dateisystem ab, ob diese längeren Pfade unterstützt werden. Zur vollständigen Abwärtskompatibilität mit FAT32-Dateisystemen sollte die Summe der Felder `_MAX_PATH` nicht überschreiten. Das Windows-NTFS-Dateisystem unterstützt Pfadlängen bis zu 32768 Zeichen, aber nur bei Verwendung von Unicode-APIs. Wenn Sie lange Pfadnamen verwenden, stellen Sie dem Pfad die Zeichen „\\\\?\“ als Präfix voran, und verwenden Sie die Unicode-Versionen der C-Laufzeit-Funktionen.

## <a name="see-also"></a>Weitere Informationen

[Global Constants (Globale Konstanten)](../c-runtime-library/global-constants.md)
