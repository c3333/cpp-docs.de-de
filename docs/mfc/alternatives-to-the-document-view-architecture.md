---
title: Alternativen zur Dokument-/Ansichtsarchitektur
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 66325d1ae087b29f59f37197fb8695504bbddbc6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619757"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativen zur Dokument-/Ansichtarchitektur

MFC-Anwendungen verwenden normalerweise die Dokument-/Ansichtarchitektur, um Informationen, Dateiformate und die visuelle Darstellung von Daten für Benutzer zu verwalten. Bei den meisten Desktop Anwendungen ist die Dokument-/Ansichtsarchitektur eine geeignete und effiziente Anwendungsarchitektur. Diese Architektur trennt Daten von der Anzeige und vereinfacht in den meisten Fällen die Anwendung und verringert redundanten Code.

Allerdings ist die Dokument-/Ansichtarchitektur für einige Situationen nicht geeignet. Beachten Sie diese Beispiele:

- Wenn Sie eine in C für Windows geschriebene Anwendung portieren, empfiehlt es sich, Ihren Port abzuschließen, bevor Sie der Anwendung Unterstützung für Dokumente/Sichten hinzufügen können.

- Wenn Sie ein Lightweight-Hilfsprogramm schreiben, stellen Sie möglicherweise fest, dass Sie ohne die Dokument-/Ansichtarchitektur vorgehen können.

- Wenn Ihr ursprünglicher Code bereits die Datenverwaltung mit Datenanzeige kombiniert, ist der Aufwand für das Verschieben des Codes in das Dokument-/sichtenmodell nicht von Wert, da Sie beide trennen müssen. Möglicherweise bevorzugen Sie den Code unverändert zu lassen.

Zum Erstellen einer Anwendung, in der die Dokument-/Ansichtarchitektur nicht verwendet wird, deaktivieren Sie das Kontrollkästchen **Unterstützung für Dokument-/Ansichtarchitektur** in Schritt 1 des MFC-Anwendungs-Assistenten. Weitere Informationen finden Sie unter [MFC-Anwendungs-Assistent](reference/mfc-application-wizard.md) .

> [!NOTE]
> Vom MFC-Anwendungs-Assistenten erstellte Dialogfeld basierte Anwendungen verwenden die Dokument-/Ansichtarchitektur nicht, sodass das Kontrollkästchen **Unterstützung für Dokument-/Ansichtarchitektur** deaktiviert ist, wenn Sie den Anwendungstyp "Dialog" auswählen.

Die Visual C++-Assistenten sowie die Quell-und Dialog-Editoren arbeiten mit der generierten Anwendung genauso wie mit jeder anderen vom Assistenten generierten Anwendung. Die Anwendung kann Symbolleisten, Bild Lauf leisten und eine Statusleiste **mit** einem Info Feld unterstützen. Die Anwendung registriert keine Dokumentvorlagen und enthält keine Dokument Klasse.

Beachten Sie, dass die generierte Anwendung über eine von abgeleitete Ansichts Klasse verfügt `CChildView` `CWnd` . MFC erstellt eine Instanz der Ansichts Klasse in den von der Anwendung erstellten Frame Fenstern und positioniert diese. MFC erzwingt weiterhin die Verwendung eines Ansichts Fensters, da dadurch die Positionierung und Verwaltung des Anwendungs Inhalts vereinfacht wird. Sie können dem-Member dieser Klasse Zeichnungs Code hinzufügen `OnPaint` . Der Code sollte der Ansicht Scrollleisten anstatt dem Frame hinzufügen.

Da die von MFC bereitgestellte Dokument-/Ansichtarchitektur für die Implementierung vieler der grundlegenden Funktionen einer Anwendung verantwortlich ist, bedeutet das Fehlen in Ihrem Projekt, dass Sie für die Implementierung vieler wichtiger Features Ihrer Anwendung verantwortlich sind:

- Wie vom MFC-Anwendungs-Assistenten bereitgestellt, enthält das Menü für die Anwendung nur die Befehle " **New** " und " **Exit** " im Menü " **Datei** ". (Der **neue** Befehl wird nur für MDI-Anwendungen unterstützt, nicht für SDI-Anwendungen ohne Unterstützung von Dokumenten/Ansichten.) Die generierte Menü Ressource unterstützt keine MRU-Liste (zuletzt verwendet).

- Sie müssen Handlerfunktionen und-Implementierungen für alle Befehle hinzufügen, die von Ihrer Anwendung unterstützt werden, einschließlich **Öffnen** und **Speichern** im Menü **Datei** . MFC stellt normalerweise Code zur Unterstützung dieser Funktionen bereit. diese Unterstützung ist jedoch eng an die Dokument-/Ansichtarchitektur gebunden.

- Die Symbolleiste für die Anwendung ist, wenn Sie eine angefordert haben, minimal.

Es wird dringend empfohlen, dass Sie den MFC-Anwendungs-Assistenten verwenden, um Anwendungen ohne die Dokument-/Ansichtarchitektur zu erstellen, da der Assistent eine korrekte MFC-Architektur gewährleistet. Wenn Sie den Assistenten jedoch vermeiden müssen, finden Sie im folgenden verschiedene Ansätze zum Umgehen der Dokument-/Ansichtarchitektur in Ihrem Code:

- Behandeln Sie das Dokument als nicht verwendetes Appendage, und implementieren Sie den Daten Verwaltungs Code in der Ansichts Klasse, wie oben vorgeschlagen. Der Aufwand für das Dokument ist relativ gering. Bei einem einzelnen [CDocument](reference/cdocument-class.md) -Objekt wird ein kleiner Aufwand allein und der kleinere Aufwand der `CDocument` Basisklassen, [CCmdTarget](reference/ccmdtarget-class.md) und [CObject](reference/cobject-class.md)verursacht. Beide der letzteren Klassen sind klein.

   Deklariert in `CDocument` :

  - Zwei- `CString` Objekte.

  - Drei **boolesche**s.

  - Ein- `CDocTemplate` Zeiger.

  - Ein- `CPtrList` Objekt, das eine Liste der Dokument Sichten enthält.

  Außerdem ist für das Dokument die Zeitspanne erforderlich, mit der das Dokument Objekt, seine Ansichts Objekte, ein Rahmen Fenster und ein Dokumentvorlagen Objekt erstellt werden.

- Behandeln Sie sowohl das Dokument als auch die Ansicht als nicht verwendete appendages. Platzieren Sie den Daten Verwaltungs-und Zeichnungs Code im Rahmen Fenster anstelle der Ansicht. Dieser Ansatz geht näher an das Programmiermodell der Programmiersprache C.

- Überschreiben Sie die Teile des MFC-Frameworks, die das Dokument und die Ansicht erstellen, um die Erstellung überhaupt nicht zu vermeiden. Der Dokument Erstellungs Prozess beginnt mit einem-Befehl `CWinApp::AddDocTemplate` . Entfernen Sie diesen-Befehl aus der Member-Funktion Ihrer Anwendungsklasse `InitInstance` , und erstellen Sie stattdessen ein Rahmen Fenster in `InitInstance` sich selbst. Platzieren Sie den Daten Verwaltungs Code in der Rahmen Fenster Klasse. Der Erstellungs Vorgang für Dokumente/Sichten wird unter [Erstellen von Dokumenten/Ansichten](document-view-creation.md)veranschaulicht. Dies ist mehr Arbeit und erfordert ein besseres Verständnis des Frameworks, aber Sie erhalten vollständige Informationen zum Dokument-/ansichtaufwand.

Der Artikel [MFC: Verwenden von Datenbankklassen ohne Dokumente und Sichten](../data/mfc-using-database-classes-without-documents-and-views.md) bietet konkretere Beispiele für Dokumente/Ansichts Alternativen im Kontext von Datenbankanwendungen.

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
