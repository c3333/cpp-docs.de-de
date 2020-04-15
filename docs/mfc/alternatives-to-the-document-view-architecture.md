---
title: Alternativen zur Document-View-Architektur
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370802"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativen zur Dokument-/Ansichtarchitektur

MFC-Anwendungen verwenden normalerweise die Dokument-/Ansichtsarchitektur, um Informationen, Dateiformate und die visuelle Darstellung von Daten für Benutzer zu verwalten. Für die meisten Desktopanwendungen ist die Dokument-/Ansichtsarchitektur eine geeignete und effiziente Anwendungsarchitektur. Diese Architektur trennt Daten von der Anzeige und vereinfacht in den meisten Fällen Ihre Anwendung und reduziert redundanten Code.

Die Dokument-/Ansichtsarchitektur ist jedoch für einige Situationen nicht geeignet. Betrachten Sie diese Beispiele:

- Wenn Sie eine in C für Windows geschriebene Anwendung portieren, sollten Sie den Port abschließen, bevor Sie Ihrer Anwendung Dokument-/Ansichtsunterstützung hinzufügen.

- Wenn Sie ein leichtes Dienstprogramm schreiben, können Sie möglicherweise auf die Dokument-/Ansichtsarchitektur verzichten.

- Wenn der ursprüngliche Code bereits die Datenverwaltung mit der Datenanzeige vermischt, lohnt sich das Verschieben des Codes in das Dokument-/Ansichtsmodell nicht, da Sie die beiden datentrennen müssen. Möglicherweise möchten Sie den Code so belassen, wie er ist.

Um eine Anwendung zu erstellen, die die Dokument-/Ansichtsarchitektur nicht verwendet, deaktivieren Sie das Kontrollkästchen **Dokument-/Ansichtsarchitekturunterstützung** in Schritt 1 des MFC-Anwendungs-Assistenten. Weitere Informationen finden Sie im [MFC-Anwendungs-Assistenten.](../mfc/reference/mfc-application-wizard.md)

> [!NOTE]
> Dialogbasierte Anwendungen, die vom MFC-Anwendungs-Assistenten erstellt wurden, verwenden nicht die Dokument-/Ansichtsarchitektur, daher ist das Kontrollkästchen **Dokument-/Ansichtsarchitekturunterstützung** deaktiviert, wenn Sie den Dialogfeldanwendungstyp auswählen.

Die Visual C++-Assistenten sowie die Quell- und Dialog-Editoren arbeiten mit der generierten Anwendung genauso wie mit jeder anderen vom Assistenten generierten Anwendung. Die Anwendung kann Symbolleisten, Bildlaufleisten und eine **About** Statusleiste unterstützen und verfügt über ein Info-Feld. Ihre Anwendung registriert keine Dokumentvorlagen und enthält keine Dokumentklasse.

Beachten Sie, dass die generierte Anwendung über eine Ansichtsklasse verfügt, `CChildView`, abgeleitet von `CWnd`. MFC erstellt und positioniert eine Instanz der Ansichtsklasse innerhalb der von Der Anwendung erstellten Rahmenfenster. MFC wird weiterhin mithilfe eines Ansichtsfensters erzwungen, da es das Positionieren und Verwalten des Anwendungsinhalts vereinfacht. Sie können dem `OnPaint` Member dieser Klasse Malcode hinzufügen. Der Code sollte Bildlaufleisten zur Ansicht und nicht zum Rahmen hinzufügen.

Da die von MFC bereitgestellte Dokument-/Ansichtsarchitektur für die Implementierung vieler grundlegender Funktionen einer Anwendung verantwortlich ist, bedeutet das Fehlen im Projekt, dass Sie für die Implementierung vieler wichtiger Funktionen Ihrer Anwendung verantwortlich sind:

- Wie vom MFC-Anwendungs-Assistenten bereitgestellt, enthält das Menü für Ihre Anwendung nur **Neue** und **Exit-Befehle** im Menü **Datei.** (Der Befehl **"Neu"** wird nur für MDI-Anwendungen und nicht für SDI-Anwendungen ohne Document/View-Unterstützung unterstützt.) Die generierte Menüressource unterstützt keine MRU-Liste (zuletzt verwendet).

- Sie müssen Handlerfunktionen und Implementierungen für alle Befehle hinzufügen, die Von Ihrer Anwendung unterstützt werden, einschließlich **Öffnen** und **Speichern** im Menü **Datei.** MFC stellt normalerweise Code zur Unterstützung dieser Features bereit, aber diese Unterstützung ist eng an die Dokument-/Ansichtsarchitektur gebunden.

- Die Symbolleiste für Ihre Anwendung, wenn Sie eine angefordert haben, ist minimal.

Es wird dringend empfohlen, den MFC-Anwendungs-Assistenten zum Erstellen von Anwendungen ohne dokument-/ansichtsarchitektur zu verwenden, da der Assistent eine korrekte MFC-Architektur garantiert. Wenn Sie jedoch die Verwendung des Assistenten vermeiden müssen, finden Sie hier mehrere Ansätze zum Umgehen der Dokument-/Ansichtsarchitektur im Code:

- Behandeln Sie das Dokument als nicht verwendetes Anhängseln, und implementieren Sie Ihren Datenverwaltungscode in der Ansichtsklasse, wie oben beschrieben. Der Overhead für das Dokument ist relativ gering. Ein einzelnes [CDocument-Objekt](../mfc/reference/cdocument-class.md) verursacht einen geringen Overhead für sich, zuzüglich des geringen Overheads der `CDocument`Basisklassen [CCmdTarget](../mfc/reference/ccmdtarget-class.md) und [CObject](../mfc/reference/cobject-class.md). Beide letzteren Klassen sind klein.

   Deklariert `CDocument`in :

  - Zwei `CString` Objekte.

  - Drei **BOOL**s.

  - Ein `CDocTemplate` Zeiger.

  - Ein `CPtrList` Objekt, das eine Liste der Ansichten des Dokuments enthält.

  Darüber hinaus benötigt das Dokument die Zeit zum Erstellen des Dokumentobjekts, seiner Ansichtsobjekte, eines Rahmenfensters und eines Dokumentvorlagenobjekts.

- Behandeln Sie sowohl das Dokument als auch die Ansicht als nicht verwendete Anhänge. Setzen Sie den Datenverwaltungs- und Zeichnungscode in das Rahmenfenster und nicht in die Ansicht. Dieser Ansatz ist näher am Programmiermodell für C-Sprachen.

- Überschreiben Sie die Teile des MFC-Frameworks, die das Dokument und die Ansicht erstellen, um das Erstellen zu vermeiden. Der Dokumenterstellungsprozess beginnt mit `CWinApp::AddDocTemplate`einem Aufruf von . Beseitigen Sie diesen Aufruf aus `InitInstance` der Memberfunktion Ihrer Anwendungsklasse, `InitInstance` und erstellen Sie stattdessen ein Rahmenfenster in Sich selbst. Setzen Sie Ihren Datenverwaltungscode in die Rahmenfensterklasse. Der Dokument-/Ansichtserstellungsprozess wird in [Dokument-/Ansichtserstellung](../mfc/document-view-creation.md)veranschaulicht. Dies ist mehr Arbeit und erfordert ein tieferes Verständnis des Frameworks, aber es gibt Ihnen vollständig den Dokument-/Ansichtsaufwand.

Der Artikel [MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten](../data/mfc-using-database-classes-without-documents-and-views.md) enthält konkretere Beispiele für Dokument-/Ansichtsalternativen im Kontext von Datenbankanwendungen.

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtsarchitektur](../mfc/document-view-architecture.md)
