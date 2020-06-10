---
title: Gerätekontexte
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: a5be2e57302e597e9c65b7bc966a5ff0ecaf855a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620365"
---
# <a name="device-contexts"></a>Gerätekontexte

Ein Gerätekontext ist eine Windows-Datenstruktur, die Informationen über die Zeichnungs Attribute eines Geräts (z. b. eine Anzeige oder einen Drucker) enthält. Alle Zeichnungs Aufrufe werden über ein Gerätekontext Objekt durchgeführt, das die Windows-APIs zum Zeichnen von Linien, Formen und Text kapselt. Geräte Kontexte ermöglichen eine geräteunabhängige Zeichnung in Windows. Geräte Kontexte können verwendet werden, um auf den Bildschirm, den Drucker oder eine Metadatei zu zeichnen.

[CPaintDC](reference/cpaintdc-class.md) -Objekte kapseln das gängige Idiom von Fenstern, den Aufruf der `BeginPaint` Funktion, das anschließende zeichnen im Gerätekontext und das anschließende Aufrufen der `EndPaint` Funktion. Der `CPaintDC` Konstruktor ruft `BeginPaint` für Sie auf, und der Dekonstruktor Ruft auf `EndPaint` . Der vereinfachte Prozess besteht darin, das [CDC](reference/cdc-class.md) -Objekt zu erstellen, zu zeichnen und dann das Objekt zu zerstören `CDC` . Im Rahmen des Frameworks ist ein Großteil dieses Prozesses auch automatisiert. Insbesondere `OnDraw` wird ihrer Funktion ein `CPaintDC` bereits vorbereitetes (via)-Wert übermittelt `OnPrepareDC` , und Sie zeichnen sich einfach darauf aus. Sie wird durch das Framework zerstört, und der zugrunde liegende Gerätekontext wird für Windows bei Rückgabe des Aufrufes der Funktion freigegeben `OnDraw` .

[CClientDC](reference/cclientdc-class.md) -Objekte kapseln das Arbeiten mit einem Gerätekontext, der nur den Client Bereich eines Fensters darstellt. Der `CClientDC` Konstruktor ruft die `GetDC` -Funktion auf, und der Dekonstruktor Ruft die- `ReleaseDC` Funktion auf. [Cwindowdc](reference/cwindowdc-class.md) -Objekte Kapseln einen Gerätekontext, der das gesamte Fenster einschließlich seines Frames darstellt.

[Cmetafiledc](reference/cmetafiledc-class.md) -Objekte kapseln das Zeichnen in eine Windows-Metadatendatei. Im Gegensatz zu der `CPaintDC` an übergebenen `OnDraw` muss in diesem Fall [OnPrepareDC](reference/cview-class.md#onpreparedc) selbst aufgerufen werden.

## <a name="mouse-drawing"></a>Maus Zeichnung

Die meisten Zeichen in einem Framework-Programm – und damit die meisten Gerätekontext arbeiten – werden in der Member-Funktion der Sicht ausgeführt `OnDraw` . Sie können jedoch weiterhin Gerätekontext Objekte für andere Zwecke verwenden. Um z. b. nach Verfolgungs Feedback für die Mausbewegung in einer Ansicht bereitzustellen, müssen Sie direkt in die Ansicht ziehen, ohne darauf warten `OnDraw` zu müssen, dass aufgerufen wird.

In einem solchen Fall können Sie ein [CClientDC](reference/cclientdc-class.md) -Gerätekontext Objekt verwenden, um direkt in die Ansicht zu zeichnen.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Geräte Kontexte (Definition)](/windows/win32/gdi/device-contexts)

- [Zeichnen in einer Ansicht](drawing-in-a-view.md)

- [Interpretieren der Benutzereingaben in einer Ansicht](interpreting-user-input-through-a-view.md)

- [Linien und Kurven](/windows/win32/gdi/lines-and-curves)

- [Gefüllte Formen](/windows/win32/gdi/filled-shapes)

- [Schriftarten und Text](/windows/win32/gdi/fonts-and-text)

- [Farben](/windows/win32/gdi/colors)

- [Koordinaten Bereiche und Transformationen](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Siehe auch

[Fensterobjekte](window-objects.md)
