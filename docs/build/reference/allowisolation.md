---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440369"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Gibt das Verhalten bei der Manifestsuche an.

## <a name="syntax"></a>Syntax

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Bemerkungen

**/ALLOWISOLATION** bewirkt, dass das Betriebssystem Manifeste suchen und lädt.

**/ALLOWISOLATION** ist die Standardeinstellung.

**/ALLOWISOLATION: No** gibt an, dass ausführbare Dateien geladen werden, als ob kein Manifest vorhanden wäre, und bewirkt, dass der [EDITBIN-Verweis](editbin-reference.md) das `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` Bit im `DllCharacteristics` Feld des optionalen Headers festgelegt.

Wenn die Isolation für eine ausführbare Datei deaktiviert ist, führt das Windows-Ladeprogramm keine Suche nach dem Anwendungsmanifest für den neu erstellen Prozess durch. Der neue Prozess verfügt über keinen Standard Aktivierungs Kontext, auch wenn ein Manifest in der ausführbaren Datei selbst vorhanden ist, oder wenn ein Manifest mit dem Namen " *ausführbare Datei*Name. exe. Manifest" vorhanden ist.

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)<br/>
[/ALLOWISOLATION (Manifestsuche)](allowisolation-manifest-lookup.md)<br/>
[Manifest-Dateireferenz](/windows/win32/SbsCs/manifest-files-reference)
