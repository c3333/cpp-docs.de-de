---
title: Schließen von Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617232"
---
# <a name="closing-files"></a>Schließen von Dateien

Wie in e/a-Vorgängen üblich, müssen Sie, sobald Sie mit einer Datei fertig sind, Sie schließen.

#### <a name="to-close-a-file"></a>So schließen Sie eine Datei

1. Verwenden Sie die **Close** Member-Funktion. Diese Funktion schließt die Dateisystem Datei und leert bei Bedarf Puffer.

Wenn Sie das [CFile](reference/cfile-class.md) -Objekt dem Frame zugeordnet haben (wie in dem Beispiel, das beim [Öffnen von Dateien](opening-files.md)angezeigt wird), wird das Objekt automatisch geschlossen und dann zerstört, wenn es den Gültigkeitsbereich verlässt. Beachten Sie, dass durch das Löschen des `CFile` Objekts nicht die physische Datei im Dateisystem gelöscht wird.

## <a name="see-also"></a>Siehe auch

[Dateien](files-in-mfc.md)
