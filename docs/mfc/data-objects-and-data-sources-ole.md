---
title: Datenobjekte und Datenquellen (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: dfe400dddfecce3e52337f7f449e975dff2ca83e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616222"
---
# <a name="data-objects-and-data-sources-ole"></a>Datenobjekte und Datenquellen (OLE)

Wenn Sie eine Datenübertragung entweder mithilfe der Zwischenablage oder Drag & Drop durchführen, verfügen die Daten über eine Quelle und ein Ziel. Eine Anwendung stellt die Daten zum Kopieren bereit, und eine andere Anwendung nimmt Sie zum Einfügen an. Jede Seite der Übertragung muss verschiedene Vorgänge für dieselben Daten durchführen, damit die Übertragung erfolgreich ist. Die MFC-Bibliothek (Microsoft Foundation Class) stellt zwei Klassen bereit, die jede Seite dieser Übertragung darstellen:

- Datenquellen (wie von `COleDataSource` Objekten implementiert) stellen die Quellseite der Datenübertragung dar. Sie werden von der Quell Anwendung erstellt, wenn Daten in die Zwischenablage kopiert werden sollen, oder wenn Daten für einen Drag & Drop-Vorgang bereitgestellt werden.

- Datenobjekte (wie von `COleDataObject` Objekten implementiert) stellen die Zielseite der Datenübertragung dar. Sie werden erstellt, wenn in der Zielanwendung Daten abgelegt werden, oder wenn Sie aufgefordert werden, einen Einfügevorgang aus der Zwischenablage auszuführen.

In den folgenden Artikeln wird erläutert, wie Sie Datenobjekte und Datenquellen in Ihren Anwendungen verwenden. Diese Informationen gelten für Container-und Server Anwendungen, da beide möglicherweise aufgerufen werden, um Daten zu kopieren und einzufügen.

- [Datenobjekte und Datenquellen: Erstellen und Zerstören](data-objects-and-data-sources-creation-and-destruction.md)

- [Datenobjekte und Datenquellen: Bearbeitung](data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>In diesem Abschnitt

[Drag & Drop](drag-and-drop-ole.md)

[Zwischenablage](clipboard.md)

## <a name="see-also"></a>Siehe auch

[OLE](ole-in-mfc.md)<br/>
[COleDataObject-Klasse](reference/coledataobject-class.md)<br/>
[COleDataSource-Klasse](reference/coledatasource-class.md)
