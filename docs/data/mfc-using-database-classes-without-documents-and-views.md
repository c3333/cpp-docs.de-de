---
title: 'MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213355"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten

In manchen Fällen möchten Sie die Dokument-/Ansichtarchitektur des Frameworks in ihren Datenbankanwendungen nicht verwenden. In diesem Thema wird Folgendes erläutert:

- [Wenn Sie keine Dokumente wie die](#_core_when_you_don.92.t_need_documents) Dokumentserialisierung verwenden müssen.

- [Optionen des Anwendungs-Assistenten](#_core_appwizard_options_for_documents_and_views) zur Unterstützung von Anwendungen ohne Serialisierung und ohne Dokument bezogene **Datei** Menübefehle wie " **neu**", " **Öffnen**", " **Speichern**" und " **Speichern**unter".

- [Arbeiten mit einer Anwendung, die ein minimales Dokument verwendet](#_core_applications_with_minimal_documents).

- [Struktur einer Anwendung ohne Dokument oder Sicht](#_core_applications_with_no_document).

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Wenn Sie keine Dokumente benötigen

Einige Anwendungen verfügen über ein eindeutiges Konzept eines Dokuments. Diese Anwendungen laden in der Regel alle oder die meisten Dateien aus dem Speicher in den Arbeitsspeicher mit einem Befehl zum **Öffnen von Dateien** . Sie schreiben die aktualisierte Datei mit dem Befehl **Datei speichern** oder **Speichern** unter in den Speicher. Was dem Benutzer angezeigt wird, ist eine Datendatei.

Einige Kategorien von Anwendungen erfordern jedoch kein Dokument. Datenbankanwendungen arbeiten in Bezug auf Transaktionen. Die Anwendung wählt Datensätze aus einer Datenbank aus und präsentiert Sie dem Benutzer, häufig nacheinander. Was dem Benutzer angezeigt wird, ist normalerweise ein einzelner Aktueller Datensatz, bei dem es sich möglicherweise um den einzigen im Arbeitsspeicher handelt.

Wenn für Ihre Anwendung kein Dokument zum Speichern von Daten erforderlich ist, können Sie die Dokument-/Ansichtsarchitektur des Frameworks auf einige oder alle Anwendungen verzichten. Die Menge, die Sie ausgeben, hängt von dem bevorzugten Ansatz ab. Sie können Folgendes tun:

- Verwenden Sie ein minimales Dokument als Speicherort, um eine Verbindung mit der Datenquelle zu speichern, und verwenden Sie normale Dokument Funktionen wie z. b. die Serialisierung. Dies ist hilfreich, wenn Sie mehrere Ansichten der Daten synchronisieren möchten und alle Sichten synchronisieren und alle Sichten gleichzeitig aktualisieren möchten.

- Verwenden Sie ein Rahmen Fenster, in das Sie direkt zeichnen, anstatt eine Ansicht zu verwenden. In diesem Fall lassen Sie das Dokument aus, und speichern Sie alle Daten oder Datenverbindungen im Rahmen Fenster Objekt.

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Optionen des Anwendungs-Assistenten für Dokumente und Ansichten

Der MFC-Anwendungs-Assistent bietet **Unterstützung für Datenbanken auswählen**verschiedene Optionen, die in der folgenden Tabelle aufgeführt sind. Wenn Sie den MFC-Anwendungs-Assistenten zum Erstellen einer Anwendung verwenden, werden mit all diesen Optionen Anwendungen mit Dokumenten und Ansichten erstellt. Einige Optionen bieten Dokumente und Sichten, die nicht benötigte Dokument Funktionen weglassen. Weitere Informationen finden Sie unter [Datenbankunterstützung, MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md).

|Option|Sicht|Dokument|
|------------|----------|--------------|
|**None**|Abgeleitet von `CView`.|Bietet keine Unterstützung für Datenbanken. Dies ist die Standardoption.<br /><br /> Wenn Sie auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent](../mfc/reference/application-type-mfc-application-wizard.md) die Option **Unterstützung für Dokument-/Ansichtarchitektur** auswählen, erhalten Sie vollständige Dokument Unterstützung einschließlich der Befehle Serialisierung und **neu**, **Öffnen**, **Speichern**und **Speichern** unter im Menü **Datei** . Weitere Informationen finden Sie [unter Anwendungen ohne Dokument](#_core_applications_with_no_document).|
|**Nur Header Dateien**|Abgeleitet von `CView`.|Stellt die grundlegende Ebene der Datenbankunterstützung für Ihre Anwendung bereit.<br /><br /> Schließt AFXDB. h ein. Fügt Verknüpfungs Bibliotheken hinzu, erstellt jedoch keine datenbankspezifischen Klassen. Sie können später Recordsets erstellen und verwenden, um Datensätze zu überprüfen und zu aktualisieren.|
|**Daten Bank Ansicht ohne Dateiunterstützung**|Abgeleitet von `CRecordView`|Bietet Dokument Unterstützung, aber keine Unterstützung für die Serialisierung. Dokumente können Recordsets speichern und mehrere Sichten koordinieren. unterstützt keine Serialisierung oder die Befehle " **New**", " **Open**", " **Save**" und " **Speichern** unter". Weitere [Informationen finden Sie unter Anwendungen mit minimalen Dokumenten](#_core_applications_with_minimal_documents). Wenn Sie eine Daten Bank Sicht einschließen, müssen Sie die Quelle der Daten angeben.<br /><br /> Umfasst Daten Bank Header Dateien, Linkbibliotheken, eine Daten Satz Ansicht und ein Recordset. (Nur verfügbar für Anwendungen, bei denen die **Unterstützung für Dokument-/Ansichtarchitektur** auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent ausgewählt ist](../mfc/reference/application-type-mfc-application-wizard.md) .)|
|**Daten Bank Ansicht mit Dateiunterstützung**|Abgeleitet von `CRecordView`|Bietet vollständige Dokument Unterstützung, einschließlich Serialisierungs-und Dokument bezogener **Datei** Menübefehle. Datenbankanwendungen arbeiten in der Regel pro Datensatz und nicht auf Datei Basis, sodass keine Serialisierung erforderlich ist. Möglicherweise haben Sie jedoch eine besondere Verwendung für die Serialisierung. Weitere [Informationen finden Sie unter Anwendungen mit minimalen Dokumenten](#_core_applications_with_minimal_documents). Wenn Sie eine Daten Bank Sicht einschließen, müssen Sie die Quelle der Daten angeben.<br /><br /> Umfasst Daten Bank Header Dateien, Linkbibliotheken, eine Daten Satz Ansicht und ein Recordset. (Nur verfügbar für Anwendungen, bei denen die **Unterstützung für Dokument-/Ansichtarchitektur** auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent ausgewählt ist](../mfc/reference/application-type-mfc-application-wizard.md) .)|

Eine Erörterung von Alternativen zur Serialisierung und alternativen Verwendungsmöglichkeiten für die Serialisierung finden Sie unter [Serialisierung: Serialisierung im Vergleich zur Daten Bank Eingabe/-Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Anwendungen mit minimalen Dokumenten

Der MFC-Anwendungs-Assistent bietet zwei Optionen, die Formular basierte Datenzugriffs Anwendungen unterstützen. Jede Option erstellt eine `CRecordView`abgeleitete Ansichts Klasse und ein Dokument. Sie unterscheiden sich darin, was Sie aus dem Dokument verlassen.

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Dokumente ohne Dateiunterstützung

Wählen Sie die Datenbankoption Daten Bank Ansicht des Anwendungs-Assistenten **ohne Dateiunterstützung** aus, wenn Sie keine Dokumentserialisierung benötigen. Das Dokument dient den folgenden nützlichen Zwecken:

- Es ist ein guter Ort zum Speichern eines `CRecordset` Objekts.

   Diese Verwendung ähnelt normalen Dokument Konzepten: das Dokument speichert die Daten (oder in diesem Fall eine Gruppe von Datensätzen), und die Sicht ist eine Ansicht des Dokuments.

- Wenn Ihre Anwendung mehrere Sichten (z. b. mehrere Daten Satz Sichten) anzeigt, unterstützt ein Dokument das Koordinieren der Ansichten.

   Wenn die gleichen Daten in mehreren Ansichten angezeigt werden, können Sie die `CDocument::UpdateAllViews` Member-Funktion verwenden, um Updates für alle Sichten zu koordinieren, wenn die Daten von einer Ansicht geändert werden.

In der Regel verwenden Sie diese Option für einfache Formular basierte Anwendungen. Der Anwendungs-Assistent unterstützt automatisch eine bequeme Struktur für solche Anwendungen.

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument mit Dateiunterstützung

Wählen Sie die Datenbankoption Daten Bank Sicht der Anwendungs-Assistent **mit Dateiunterstützung** aus, wenn Sie für die Dokument bezogenen **Datei** Menübefehle und die Dokumentserialisierung eine Alternative verwenden möchten. Für den Datenzugriffs Teil des Programms können Sie das Dokument auf die gleiche Weise wie in [Dokument ohne Dateiunterstützung](#_core_a_document_without_file_support)beschrieben verwenden. Sie können z. b. die Serialisierungsfunktion des Dokuments verwenden, um ein serialisiertes Benutzerprofil Dokument zu lesen und zu schreiben, in dem die Benutzereinstellungen oder andere nützliche Informationen gespeichert werden. Weitere Ideen finden Sie unter [Serialisierung: Serialisierung im Vergleich zur Daten Bank Eingabe/-Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

Diese Option wird vom Anwendungs-Assistenten unterstützt, Sie müssen jedoch den Code schreiben, der das Dokument serialisiert. Speichert die serialisierten Informationen in dokumentdatenmembern.

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Anwendungen ohne Dokument

Manchmal möchten Sie möglicherweise eine Anwendung schreiben, die keine Dokumente oder Sichten verwendet. Ohne Dokumente speichern Sie Ihre Daten (z. b. ein `CRecordset` Objekt) in der Rahmen Fenster Klasse oder Ihrer Anwendungsklasse. Alle zusätzlichen Anforderungen hängen davon ab, ob die Anwendung eine Benutzeroberfläche darstellt.

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Datenbankunterstützung mit einer Benutzeroberfläche

Wenn Sie über eine Benutzeroberfläche verfügen (z. b. eine Konsolen-Befehlszeilenschnittstelle), wird Ihre Anwendung direkt in den Client Bereich des Frame Fensters und nicht in eine Ansicht gezeichnet. Eine solche Anwendung verwendet `CRecordView`, `CFormView`oder `CDialog` nicht für die Hauptbenutzer Oberfläche, sondern verwendet normalerweise `CDialog` für normale Dialoge.

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Schreiben von Anwendungen ohne Dokumente

Da der Anwendungs-Assistent keine Unterstützung für das Erstellen von Anwendungen ohne Dokumente bietet, müssen Sie eine eigene `CWinApp`abgeleitete Klasse schreiben und bei Bedarf auch eine `CFrameWnd` oder `CMDIFrameWnd` Klasse erstellen. Überschreiben Sie `CWinApp::InitInstance` und deklarieren Sie ein Anwendungs Objekt wie folgt:

```cpp
CYourNameApp theApp;
```

Das Framework stellt weiterhin den Nachrichten Zuordnungs Mechanismus und viele weitere Funktionen bereit.

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Datenbankunterstützung getrennt von der Benutzeroberfläche

Einige Anwendungen benötigen keine Benutzeroberfläche oder nur eine minimale Benutzeroberfläche. Nehmen Sie beispielsweise an, dass Sie Folgendes schreiben:

- Ein zwischen Datenzugriffs Objekt, das von anderen Anwendungen (Clients) für die spezielle Verarbeitung von Daten zwischen der Anwendung und der Datenquelle aufgerufen wird.

- Eine Anwendung, die Daten ohne Benutzereingriff verarbeitet, z. b. eine Anwendung, die Daten aus einem Datenbankformat in einen anderen verschiebt, oder eine Anwendung, die Berechnungen ausführt und Batch Aktualisierungen ausführt.

Da kein Dokument das `CRecordset` Objekt besitzt, möchten Sie es wahrscheinlich als eingebetteten Datenmember in der von `CWinApp`abgeleiteten Anwendungsklasse speichern. Zu den Alternativen gehören:

- Beibehalten eines permanenten `CRecordset` Objekts überhaupt nicht. Sie können NULL an die Recordset-Klassenkonstruktoren übergeben. In diesem Fall erstellt das Framework ein temporäres `CDatabase` Objekt mithilfe der Informationen in der `GetDefaultConnect` Member-Funktion des Recordsets. Dies ist die wahrscheinlichste Alternative Methode.

- Festlegen des `CRecordset` Objekts zu einer globalen Variablen. Bei dieser Variablen sollte es sich um einen Zeiger auf ein Recordset-Objekt handeln, das Sie in der `CWinApp::InitInstance` Außerkraftsetzung dynamisch erstellen. Dadurch wird vermieden, dass versucht wird, das Objekt zu erstellen, bevor das Framework initialisiert wird.

- Verwenden von Recordset-Objekten wie im Kontext eines Dokuments oder einer Ansicht. Erstellen Sie Recordsets in den Element Funktionen Ihrer Anwendung oder von Rahmen Fenster Objekten.

## <a name="see-also"></a>Weitere Informationen

[MFC-Datenbankklassen](../data/mfc-database-classes-odbc-and-dao.md)
