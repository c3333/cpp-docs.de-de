---
title: OLE-Common-Dialogfeldklassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: b44a7b203c17f09f872cfedbb05798affb57f0f9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447677"
---
# <a name="ole-common-dialog-classes"></a>OLE-Common-Dialogfeldklassen

Diese Klassen behandeln allgemeine OLE-Aufgaben, indem eine Reihe von Standard-OLE-Dialogfeldern implementiert wird. Sie stellen auch eine konsistente Benutzeroberfläche für OLE-Funktionen bereit.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Wird vom Framework verwendet, um allgemeine Implementierungen für alle OLE-Dialogfelder zu enthalten. Alle Dialogfeld Klassen in der Benutzeroberflächen Kategorie werden von dieser Basisklasse abgeleitet. `COleDialog` kann nicht direkt verwendet werden.

[Coleingesertdialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Zeigt das Dialogfeld Objekt einfügen, die Standardbenutzer Oberfläche für das Einfügen von neuen OLE-verknüpften oder eingebetteten Elementen an.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Zeigt das Dialogfeld "spezielles einfügen" an, die Standardbenutzer Oberfläche für die Implementierung des Befehls "speziellen einfügen".

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Zeigt das Dialogfeld Links bearbeiten an, der Standardbenutzer Oberfläche zum Ändern von Informationen zu verknüpften Elementen.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Zeigt das Dialogfeld Symbol ändern, die Standardbenutzer Oberfläche zum Ändern des Symbols an, das einem OLE Embedded-oder verknüpften Element zugeordnet ist.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Zeigt das Dialogfeld Konvertieren an, die Standardbenutzer Oberfläche zum Konvertieren von OLE-Elementen von einem Typ in einen anderen.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Kapselt das allgemeine Windows-OLE-Eigenschaften Dialogfeld. Allgemeine OLE-Eigenschaften (Dialogfelder) bieten eine einfache Möglichkeit zum Anzeigen und Ändern der Eigenschaften eines OLE-Dokument Elements auf eine Weise, die mit Windows-Standards konsistent ist.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Zeigt das Dialogfeld Aktualisieren an, die Standardbenutzer Oberfläche zum Aktualisieren aller Links in einem Dokument. Das Dialogfeld enthält eine Statusanzeige, die angibt, wie die Aktualisierung der Aktualisierung abgeschlossen werden soll.

[Colechangesourcedialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Zeigt das Dialogfeld Quelle ändern an, die Standardbenutzer Oberfläche zum Ändern des Ziels oder der Quelle eines Links.

[Colebusydialog](../mfc/reference/colebusydialog-class.md)<br/>
Zeigt die Dialogfelder Server ausgelastet und Server reagiert nicht an, der Standardbenutzer Oberfläche für die Verarbeitung von Aufrufen von ausgelasteten Anwendungen. Wird normalerweise automatisch von der `COleMessageFilter`-Implementierung angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
