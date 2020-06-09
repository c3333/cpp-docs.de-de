---
title: OLE-Steuerelementklassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 5aa3899dca5a42cf789dc6dfd4701547495ec618
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617768"
---
# <a name="ole-control-classes"></a>OLE-Steuerelementklassen

Dies sind die primären Klassen, die Sie beim Schreiben von OLE-Steuerelementen verwenden. Die- `COleControlModule` Klasse in einem OLE-Steuerungs Modul ähnelt der [CWinApp](reference/cwinapp-class.md) -Klasse in einer Anwendung. Jedes Modul implementiert ein oder mehrere OLE-Steuerelemente. Diese Steuerelemente werden durch- `COleControl` Objekte dargestellt. Diese Steuerelemente kommunizieren mit ihren Containern mithilfe von- `CConnectionPoint` Objekten.

Die `CPictureHolder` `CFontHolder` Klassen und Kapseln com-Schnittstellen für Bilder und Schriftarten, während die `COlePropertyPage` `CPropExchange` Klassen und Sie dabei unterstützen, Eigenschaften Seiten und Eigenschafts Persistenz für das Steuerelement zu implementieren.

[COleControlModule](reference/colecontrolmodule-class.md)<br/>
Ersetzt die- `CWinApp` Klasse für das OLE-Steuerungs Modul. Ableiten von der- `COleControlModule` Klasse, um ein OLE-Steuerelement Modul-Objekt zu entwickeln. Sie stellt Member-Funktionen zum Initialisieren des Moduls des OLE-Steuer Elements bereit.

[COleControl](reference/colecontrol-class.md)<br/>
Ableiten von der- `COleControl` Klasse zum Entwickeln eines OLE-Steuer Elements. `CWnd`Diese Klasse wird von abgeleitet und erbt die gesamte Funktionalität eines Windows-Fenster Objekts sowie zusätzliche OLE-spezifische Funktionen, wie z. b. das Auslösen von Ereignissen und die Möglichkeit zur Unterstützung von Methoden und Eigenschaften.

[CConnectionPoint](reference/cconnectionpoint-class.md)<br/>
Die- `CConnectionPoint` Klasse definiert einen speziellen Schnittstellentyp, der für die Kommunikation mit anderen OLE-Objekten verwendet wird, die als Verbindungspunkt bezeichnet werden. Ein Verbindungspunkt implementiert eine ausgehende Schnittstelle, die Aktionen für andere Objekte initiieren kann, z. b. das Auslösen von Ereignissen und Änderungs Benachrichtigungen.

[CPictureHolder](reference/cpictureholder-class.md)<br/>
Kapselt die Funktionalität eines Windows-Bildobjekts und der `IPicture` com-Schnittstelle, die zum Implementieren der benutzerdefinierten Bild Eigenschaft eines OLE-Steuer Elements verwendet wird.

[CFontHolder](reference/cfontholder-class.md)<br/>
Kapselt die Funktionalität eines Windows-Schriftart Objekts und der `IFont` com-Schnittstelle; wird verwendet, um die Eigenschaft "Stock Font" eines OLE-Steuer Elements zu implementieren.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Zeigt die Eigenschaften eines OLE-Steuer Elements in einer grafischen Benutzeroberfläche ähnlich einem Dialogfeld an.

[CPropExchange](reference/cpropexchange-class.md)<br/>
Unterstützt die Implementierung der Eigenschafts Persistenz für die OLE-Steuerelemente. Analog zu [CDataExchange](reference/cdataexchange-class.md) für Dialogfelder.

[CMonikerFile](reference/cmonikerfile-class.md)<br/>
Nimmt einen Moniker oder eine Zeichen folgen Darstellung, die er in einem Moniker erstellen kann, an und bindet ihn synchron an den Datenstrom, für den der Moniker ein Name ist.

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)<br/>
Funktioniert ähnlich wie, `CMonikerFile` bindet den Moniker jedoch asynchron an den Datenstrom, für den der Moniker einen Namen hat.

[CDataPathProperty](reference/cdatapathproperty-class.md)<br/>
Implementiert eine OLE-Steuerelementeigenschaft, die asynchron geladen werden kann.

[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)<br/>
Implementiert eine asynchron übertragene und in einer Arbeitsspeicherdatei zwischengespeicherte OLE-Steuerelementeigenschaft.

[COleCmdUI](reference/colecmdui-class.md)<br/>
Ermöglicht einem aktiven Dokument das Empfangen von Befehlen, die aus der Benutzeroberfläche seines Containers stammen (z. b. Datei-, Öffnungs-, Druck-usw.) und ermöglicht einem Container das Empfangen von Befehlen, die aus der Benutzeroberfläche des aktiven Dokuments stammen.

[COleSafeArray](reference/colesafearray-class.md)<br/>
Kann mit Arrays beliebiger Typen und Dimensionen verwendet werden.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
