---
title: /MANIFESTINPUT (Angeben einer Manifesteingabedatei)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337490"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Angeben einer Manifesteingabedatei)

Gibt eine Manifesteingabedatei an, die dem Manifest hinzugefügt wird, das im Image eingebettet ist.

## <a name="syntax"></a>Syntax

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Die Manifestdatei, die dem eingebetteten Manifest hinzuzufügen ist.

## <a name="remarks"></a>Bemerkungen

Die Option **/MANIFESTINPUT** gibt den Pfad einer Eingabedatei an, die zum Erstellen des eingebetteten Manifests in einem ausführbaren Abbild verwendet werden soll. Wenn Sie mehrere Manifesteingabedateien haben, verwenden Sie den Schalter mehrfach, einmal für jede Eingabedatei. Die Manifesteingabedateien werden zusammengeführt, um das eingebettete Manifest zu erstellen. Für diese Option ist die Option **/MANIFEST:EMBED** erforderlich.

Diese Option kann nicht direkt in Visual Studio festgelegt werden. Verwenden Sie stattdessen die Eigenschaft **Zusätzliche Manifestdateien** des Projekts, um zusätzliche Manifestdateien anzugeben, die eingeschlossen werden sollen. Weitere Informationen finden Sie unter [Manifest Tool Property Pages](manifest-tool-property-pages.md).

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
