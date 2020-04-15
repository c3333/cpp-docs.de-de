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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364533"
---
# <a name="ole-background-mfc-implementation"></a>OLE-Hintergrund: MFC-Implementierung

Aufgrund der Größe und Komplexität der OLE-API kann das direkte Aufrufen zum Schreiben von OLE-Anwendungen sehr zeitaufwändig sein. Das Ziel der Implementierung der Microsoft Foundation-Klassenbibliothek von OLE besteht darin, die Menge an Arbeit zu reduzieren, die Sie für das Schreiben voll funktionsfähiger OLE-fähiger Anwendungen leisten müssen.

In diesem Artikel werden die Teile der OLE-API erläutert, die nicht in MFC implementiert wurden. In der Diskussion wird auch erläutert, wie die Implementierung dem OLE-Abschnitt des Windows SDK zugeordnet ist.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Teile von OLE, die nicht von der Klassenbibliothek implementiert wurden

Einige Schnittstellen und Funktionen von OLE werden nicht direkt von MFC bereitgestellt. Wenn Sie diese Funktionen verwenden möchten, können Sie die OLE-API direkt aufrufen.

IMoniker-Schnittstelle `IMoniker` Die Schnittstelle wird von der Klassenbibliothek (z. B. der `COleServerItem` Klasse) implementiert, wurde aber zuvor nicht für den Programmierer verfügbar gemacht. Weitere Informationen zu dieser Schnittstelle finden Sie unter OLE Moniker-Implementierungen im Abschnitt OLE des Windows SDK. Siehe aber auch Klasse [CMonikerFile](../mfc/reference/cmonikerfile-class.md) und [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

IUnknown und IMarshal `IUnknown` Interfaces Die Schnittstelle wird von der Klassenbibliothek implementiert, aber nicht für den Programmierer verfügbar gemacht. Die `IMarshal` Schnittstelle wird nicht von der Klassenbibliothek implementiert, sondern intern verwendet. Automatisierungsserver, die mit der Klassenbibliothek erstellt wurden, verfügen bereits über integrierte Marshallingfunktionen.

Docfiles (Compound Files) Zusammengesetzte Dateien werden teilweise von der Klassenbibliothek unterstützt. Keine der Funktionen, die zusammengesetzte Dateien über die Erstellung hinaus direkt bearbeiten, wird unterstützt. MFC verwendet `COleFileStream` Klasse, um die Manipulation von Streams mit Standarddateifunktionen zu unterstützen. Weitere Informationen finden Sie im Artikel [Container: Zusammengesetzte Dateien](../mfc/containers-compound-files.md).

In-Process-Server und Objekthandler In-Process-Server und Objekthandler ermöglichen die Implementierung von visuellen Bearbeitungsdaten oder COM-Objekten (Com) in einer Dynamic-Link-Bibliothek (DLL). Dazu können Sie Ihre DLL implementieren, indem Sie die OLE-API direkt aufrufen. Wenn Sie jedoch einen Automatisierungsserver schreiben und Ihr Server über keine Benutzeroberfläche verfügt, können Sie AppWizard verwenden, um den Server zu einem In-Process-Server zu machen und ihn vollständig in eine DLL einzuteilen. Weitere Informationen zu diesen Themen finden Sie unter [Automatisierungsserver](../mfc/automation-servers.md).

> [!TIP]
> Die einfachste Möglichkeit, einen Automatisierungsserver zu implementieren, besteht darin, ihn in einer DLL zu platzieren. MFC unterstützt diesen Ansatz.

Weitere Informationen zum Implementieren von OLE-Schnittstellen durch die Microsoft Foundation-OLE-Klassen finden Sie in den MFC Technical Notes [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md)und [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Siehe auch

[OLE-Hintergrund](../mfc/ole-background.md)<br/>
[OLE-Hintergrund: Implementierungsstrategien](../mfc/ole-background-implementation-strategies.md)
