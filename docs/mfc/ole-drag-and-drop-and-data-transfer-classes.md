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
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447614"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE-Drag &amp; Drop- und Datenübertragungs-Klassen

Diese Klassen werden in OLE-Datenübertragungen verwendet. Sie ermöglichen das Übertragen von Daten zwischen Anwendungen mithilfe der Zwischenablage oder per Drag & Drop.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Steuert den Drag & Drop-Vorgang von Anfang bis Ende. Diese Klasse bestimmt, wann der Zieh Vorgang beginnt und wann er endet. Außerdem wird während des Drag & Drop-Vorgangs Cursor Feedback angezeigt.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Wird verwendet, wenn eine Anwendung Daten für eine Datenübertragung bereitstellt. `COleDataSource` können als objektorientiertes Zwischenablage Objekt angezeigt werden.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Stellt das Ziel eines Drag & Drop-Vorgangs dar. Ein `COleDropTarget`-Objekt entspricht einem Fenster auf dem Bildschirm. Es bestimmt, ob Daten, die auf ihm abgelegt werden, akzeptiert und der tatsächliche Drop-Vorgang implementiert wird.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Wird als Empfängerseite zum `COleDataSource`verwendet. `COleDataObject`-Objekte ermöglichen den Zugriff auf die Daten, die von einem `COleDataSource`-Objekt gespeichert werden.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
