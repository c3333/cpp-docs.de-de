---
title: OLE-Drag &amp; Drop- und Datenübertragungs-Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 530b1772dfb623689facd5b14eebe9ed1eacd4fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624142"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE-Drag &amp; Drop- und Datenübertragungs-Klassen

Diese Klassen werden in OLE-Datenübertragungen verwendet. Sie ermöglichen das Übertragen von Daten zwischen Anwendungen mithilfe der Zwischenablage oder per Drag & Drop.

[COleDropSource](reference/coledropsource-class.md)<br/>
Steuert den Drag & Drop-Vorgang von Anfang bis Ende. Diese Klasse bestimmt, wann der Zieh Vorgang beginnt und wann er endet. Außerdem wird während des Drag & Drop-Vorgangs Cursor Feedback angezeigt.

[COleDataSource](reference/coledatasource-class.md)<br/>
Wird verwendet, wenn eine Anwendung Daten für eine Datenübertragung bereitstellt. `COleDataSource`kann als objektorientiertes Zwischenablage Objekt angezeigt werden.

[COleDropTarget](reference/coledroptarget-class.md)<br/>
Stellt das Ziel eines Drag & Drop-Vorgangs dar. Ein- `COleDropTarget` Objekt entspricht einem Fenster auf dem Bildschirm. Es bestimmt, ob Daten, die auf ihm abgelegt werden, akzeptiert und der tatsächliche Drop-Vorgang implementiert wird.

[COleDataObject](reference/coledataobject-class.md)<br/>
Wird als Empfängerseite für verwendet `COleDataSource` . `COleDataObject`-Objekte ermöglichen den Zugriff auf die von einem-Objekt gespeicherten Daten `COleDataSource` .

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
