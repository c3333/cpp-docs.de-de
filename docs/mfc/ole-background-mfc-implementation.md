---
title: 'OLE-Hintergrund: MFC-Implementierung'
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 1dffdafbd02697db5aec341fec253c84217a0faf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619875"
---
# <a name="ole-background-mfc-implementation"></a>OLE-Hintergrund: MFC-Implementierung

Aufgrund der Größe und Komplexität der unformatierten OLE-API kann das direkte Aufrufen zum Schreiben von OLE-Anwendungen sehr zeitaufwändig sein. Das Ziel der Microsoft Foundation Class-Bibliothek Implementierung von OLE besteht darin, den Arbeitsaufwand zu reduzieren, den Sie zum Schreiben von OLE-fähigen Anwendungen mit vollem Funktionsumfang ausführen müssen.

In diesem Artikel werden die Teile der OLE-API erläutert, die in MFC nicht implementiert wurden. Außerdem wird erläutert, wie das implementierte dem OLE-Abschnitt der Windows SDK zugeordnet wird.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Von der Klassenbibliothek nicht implementierte Teile von OLE

Einige Schnittstellen und Features von OLE werden von MFC nicht direkt bereitgestellt. Wenn Sie diese Features verwenden möchten, können Sie die OLE-API direkt aufzurufen.

IMoniker-Schnittstelle die `IMoniker` Schnittstelle wird von der Klassenbibliothek implementiert (z. b. die- `COleServerItem` Klasse), wurde aber noch nicht für den Programmierer verfügbar gemacht. Weitere Informationen zu dieser Schnittstelle finden Sie unter OLE-Monikerimplementierungen im OLE-Abschnitt der Windows SDK. Weitere Informationen finden Sie unter " [CMonikerFile](reference/cmonikerfile-class.md) " und " [CAsyncMonikerFile](reference/casyncmonikerfile-class.md)".

IUnknown-und IMarshal-Schnittstellen die `IUnknown` Schnittstelle wird von der Klassenbibliothek implementiert, aber für den Programmierer nicht verfügbar gemacht. Die- `IMarshal` Schnittstelle wird nicht von der-Klassenbibliothek implementiert, sondern intern verwendet. Für Automation-Server, die mithilfe der-Klassenbibliothek erstellt wurden, sind bereits Marshallingfunktionen integriert.

Docfiles-Verbund Dateien (Verbund Dateien) werden teilweise von der-Klassenbibliothek unterstützt. Keine der Funktionen, die Verbund Dateien direkt außerhalb der Erstellung bearbeiten, werden unterstützt. MFC verwendet die-Klasse `COleFileStream` , um die Bearbeitung von Streams mit Standarddatei Funktionen zu unterstützen. Weitere Informationen finden Sie im Artikel [Container: Verbund Dateien](containers-compound-files.md).

Prozess interne Server und Objekt Handler in-Process-Server und Objekt Handler ermöglichen die Implementierung von visuellen Bearbeitungsdaten oder voll Component Object Model (com)-Objekten in einer Dynamic Link Library (dll). Zu diesem Zweck können Sie die dll implementieren, indem Sie die OLE-API direkt aufrufen. Wenn Sie jedoch einen Automatisierungsserver schreiben und der Server keine Benutzeroberfläche besitzt, können Sie mit AppWizard Ihren Server zu einem Prozess internen Server machen und ihn vollständig in eine DLL einfügen. Weitere Informationen zu diesen Themen finden Sie unter [Automation Servers (Automatisierungsserver](automation-servers.md)).

> [!TIP]
> Die einfachste Möglichkeit, einen Automatisierungsserver zu implementieren, besteht darin, ihn in eine DLL zu versetzen. MFC unterstützt diese Vorgehensweise.

Weitere Informationen zur Implementierung von OLE-Schnittstellen durch die OLE-Klassen von Microsoft Foundation finden Sie unter Technische Hinweise zu MFC [38](tn038-mfc-ole-iunknown-implementation.md), [39](tn039-mfc-ole-automation-implementation.md)und [40](tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Siehe auch

[OLE-Hintergrund](ole-background.md)<br/>
[OLE-Hintergrund: Implementierungsstrategien](ole-background-implementation-strategies.md)
