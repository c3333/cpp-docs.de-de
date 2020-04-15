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
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360671"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten

Manchmal möchten Sie die Dokument-/Ansichtsarchitektur des Frameworks in Ihren Datenbankanwendungen möglicherweise nicht verwenden. In diesem Thema wird Folgendes erläutert:

- [Wenn Sie keine Dokumente](#_core_when_you_don.92.t_need_documents) wie die Dokumentserialisierung verwenden müssen.

- [Anwendungs-Assistenten-Optionen](#_core_appwizard_options_for_documents_and_views) zur Unterstützung von Anwendungen ohne Serialisierung und ohne dokumentbezogene **Dateimenübefehle** wie **Neu**, **Öffnen**, **Speichern**und **Speichern unter**.

- [So arbeiten Sie mit einer Anwendung, die ein Minimaledokument verwendet.](#_core_applications_with_minimal_documents)

- [Strukturieren einer Anwendung ohne Dokument oder Ansicht](#_core_applications_with_no_document).

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Wenn Sie keine Dokumente benötigen

Einige Anwendungen haben ein eigenes Konzept für ein Dokument. Diese Anwendungen laden in der Regel die gesamte oder den größten Teil einer Datei aus dem Speicher in den Speicher mit einem **File Open-Befehl.** Sie schreiben die aktualisierte Datei mit einem Befehl **Datei speichern** oder **Speichern unter** auf einmal in den Speicher zurück. Was der Benutzer sieht, ist eine Datendatei.

Für einige Anwendungskategorien ist jedoch kein Dokument erforderlich. Datenbankanwendungen arbeiten in Bezug auf Transaktionen. Die Anwendung wählt Datensätze aus einer Datenbank aus und stellt sie dem Benutzer vor, oft nacheinander. Was der Benutzer sieht, ist in der Regel ein einzelner aktueller Datensatz, der möglicherweise der einzige im Speicher ist.

Wenn Ihre Anwendung kein Dokument zum Speichern von Daten benötigt, können Sie auf einige oder die gesamte Dokument-/Ansichtsarchitektur des Frameworks verzichten. Wie viel Sie verzichten, hängt von dem Ansatz ab, den Sie bevorzugen. Sie können:

- Verwenden Sie ein minimales Dokument als Ort, um eine Verbindung mit Ihrer Datenquelle zu speichern, verzichten Sie jedoch auf normale Dokumentfeatures wie die Serialisierung. Dies ist nützlich, wenn Sie mehrere Ansichten der Daten wünschen und alle Ansichten synchronisieren, sie alle auf einmal aktualisieren möchten usw.

- Verwenden Sie ein Rahmenfenster, in das Sie direkt zeichnen, anstatt eine Ansicht zu verwenden. In diesem Fall lassen Sie das Dokument weg und speichern alle Daten- oder Datenverbindungen im Framefensterobjekt.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Anwendungs-Assistenten-Optionen für Dokumente und Ansichten

Der MFC-Anwendungs-Assistent verfügt über mehrere Optionen unter **Datenbankunterstützung auswählen**, die in der folgenden Tabelle aufgeführt sind. Wenn Sie den MFC-Anwendungs-Assistenten zum Erstellen einer Anwendung verwenden, erstellen alle diese Optionen Anwendungen mit Dokumenten und Ansichten. Einige Optionen bieten Dokumente und Ansichten, die nicht benötigte Dokumentfunktionen auslassen. Weitere Informationen finden Sie unter [Datenbanksupport, MFC-Anwendungsassistent](../mfc/reference/database-support-mfc-application-wizard.md).

|Option|Sicht|Dokument|
|------------|----------|--------------|
|**None**|Abgeleitet von `CView`.|Bietet keine Datenbankunterstützung. Dies ist die Standardoption.<br /><br /> Wenn Sie auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent](../mfc/reference/application-type-mfc-application-wizard.md) die Option **Dokument-/Ansichtsarchitektur unterstützen,** erhalten Sie im Menü **Datei** vollständige Dokumentunterstützung einschließlich Serialisierung und **New**, **Open**, **Save**und **Save As.For** The., MFC Application Wizard. Siehe [Anwendungen ohne Dokument](#_core_applications_with_no_document).|
|**Nur Headerdateien**|Abgeleitet von `CView`.|Bietet die grundlegende Ebene der Datenbankunterstützung für Ihre Anwendung.<br /><br /> Inklusive Afxdb.h. Fügt Verknüpfungsbibliotheken hinzu, erstellt jedoch keine datenbankspezifischen Klassen. Sie können später Recordsets erstellen und diese zum Überprüfen und Aktualisieren von Datensätzen verwenden.|
|**Datenbankansicht ohne Dateiunterstützung**|Abgeleitet von`CRecordView`|Bietet Dokumentunterstützung, aber keine Serialisierungsunterstützung. Das Dokument kann Recordset speichern und mehrere Ansichten koordinieren. unterstützt keine Serialisierung oder die Befehle **New**, **Open**, **Save**und **Save As.** Siehe [Anwendungen mit minimalen Dokumenten](#_core_applications_with_minimal_documents). Wenn Sie eine Datenbankansicht einschließen, müssen Sie die Quelle der Daten angeben.<br /><br /> Enthält Datenbankheaderdateien, Linkbibliotheken, eine Datensatzansicht und ein Recordset. (Nur für Anwendungen verfügbar, für die die **Unterstützungsoption Dokument-/Ansichtsarchitektur** auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent](../mfc/reference/application-type-mfc-application-wizard.md) ausgewählt wurde.)|
|**Datenbankansicht mit Dateiunterstützung**|Abgeleitet von`CRecordView`|Bietet vollständige Dokumentunterstützung, einschließlich Serialisierung **File** und dokumentbezogenen Dateimenübefehlen. Datenbankanwendungen arbeiten in der Regel pro Datensatz und nicht pro Datei und müssen daher nicht serialisiert werden. Möglicherweise haben Sie jedoch eine spezielle Verwendung für die Serialisierung. Siehe [Anwendungen mit minimalen Dokumenten](#_core_applications_with_minimal_documents). Wenn Sie eine Datenbankansicht einschließen, müssen Sie die Quelle der Daten angeben.<br /><br /> Enthält Datenbankheaderdateien, Linkbibliotheken, eine Datensatzansicht und ein Recordset. (Nur für Anwendungen verfügbar, für die die **Unterstützungsoption Dokument-/Ansichtsarchitektur** auf der Seite [Anwendungstyp, MFC-Anwendungs-Assistent](../mfc/reference/application-type-mfc-application-wizard.md) ausgewählt wurde.)|

Eine Erläuterung von Alternativen zur Serialisierung und alternativen Verwendungen für die Serialisierung finden Sie unter [Serialisierung: Serialisierung vs. Datenbankein-/Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Anwendungen mit minimalen Dokumenten

Der MFC-Anwendungs-Assistent verfügt über zwei Optionen, die formularbasierte Datenzugriffsanwendungen unterstützen. Jede Option `CRecordView`erstellt eine -abgeleitete Ansichtsklasse und ein Dokument. Sie unterscheiden sich in dem, was sie aus dem Dokument herauslassen.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Dokument ohne Dateiunterstützung

Wählen Sie die Datenbankoption des Anwendungsassistenten **Datenbankansicht ohne Dateiunterstützung** aus, wenn Sie keine Dokumentserialisierung benötigen. Das Dokument dient folgenden nützlichen Zwecken:

- Es ist ein bequemer `CRecordset` Ort, um ein Objekt zu speichern.

   Diese Verwendung parallel zu gewöhnlichen Dokumentkonzepten: Das Dokument speichert die Daten (oder in diesem Fall eine Gruppe von Datensätzen) und die Ansicht ist eine Ansicht des Dokuments.

- Wenn Ihre Anwendung mehrere Ansichten (z. B. mehrere Datensatzansichten) enthält, unterstützt ein Dokument die Koordination der Ansichten.

   Wenn mehrere Ansichten dieselben Daten anzeigen, `CDocument::UpdateAllViews` können Sie die Memberfunktion verwenden, um Aktualisierungen aller Ansichten zu koordinieren, wenn eine Ansicht die Daten ändert.

Normalerweise verwenden Sie diese Option für einfache formularbasierte Anwendungen. Der Anwendungsassistent unterstützt automatisch eine praktische Struktur für solche Anwendungen.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument mit Dateiunterstützung

Wählen Sie die Datenbankoption des Anwendungsassistenten **Datenbankansicht mit Dateiunterstützung** aus, wenn Sie eine alternative Verwendung für die dokumentbezogenen **Menübefehle "Datei"** und die Dokumentserialisierung verwenden. Für den Datenzugriffsteil Ihres Programms können Sie das Dokument auf die gleiche Weise verwenden, wie unter [Dokument ohne Dateiunterstützung](#_core_a_document_without_file_support)beschrieben. Sie können die Serialisierungsfunktion des Dokuments verwenden, z. B. zum Lesen und Schreiben eines serialisierten Benutzerprofildokuments, in dem die Einstellungen des Benutzers oder andere nützliche Informationen gespeichert werden. Weitere Ideen finden Sie unter [Serialisierung: Serialisierung vs. Datenbankein-/Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

Der Anwendungsassistent unterstützt diese Option, Sie müssen jedoch den Code schreiben, der das Dokument serialisiert. Speichern Sie die serialisierten Informationen in Dokumentdatenmembern.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Anwendungen ohne Dokument

Manchmal möchten Sie eine Anwendung schreiben, die keine Dokumente oder Ansichten verwendet. Ohne Dokumente speichern Sie Ihre Daten `CRecordset` (z. B. ein Objekt) in Ihrer Frame-Fenster-Klasse oder in Ihrer Anwendungsklasse. Zusätzliche Anforderungen hängen davon ab, ob die Anwendung eine Benutzeroberfläche bietet.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Datenbankunterstützung mit Benutzeroberfläche

Wenn Sie über eine Benutzeroberfläche (außer z. B. einer Konsolenbefehlszeilenschnittstelle) verfügen, wird die Anwendung direkt in den Clientbereich des Rahmenfensters und nicht in eine Ansicht gezeichnet. Eine solche Anwendung `CRecordView`verwendet `CFormView`nicht `CDialog` , oder für ihre Hauptbenutzeroberfläche, aber sie verwendet `CDialog` normalerweise für normale Dialoge.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Schreiben von Anwendungen ohne Dokumente

Da der Anwendungsassistent das Erstellen von Anwendungen ohne `CWinApp`Dokumente nicht unterstützt, müssen Sie `CFrameWnd` eine `CMDIFrameWnd` eigene -abgeleitete Klasse schreiben und bei Bedarf auch eine oder eine Klasse erstellen. Überschreiben `CWinApp::InitInstance` und deklarieren Sie ein Anwendungsobjekt wie:

```cpp
CYourNameApp theApp;
```

Das Framework stellt weiterhin den Message-Map-Mechanismus und viele andere Features bereit.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Datenbankunterstützung Getrennt von der Benutzeroberfläche

Einige Anwendungen benötigen keine Oder nur eine minimale Benutzeroberfläche. Angenommen, Sie schreiben:

- Ein Zwischenobjekt für den Datenzugriff, das von anderen Anwendungen (Clients) für eine spezielle Verarbeitung von Daten zwischen der Anwendung und der Datenquelle gefordert wird.

- Eine Anwendung, die Daten ohne Benutzereingriff verarbeitet, z. B. eine Anwendung, die Daten von einem Datenbankformat in ein anderes verschiebt oder eine, die Berechnungen durchführt und Batchaktualisierungen durchführt.

Da kein Dokument `CRecordset` Eigentümer des Objekts ist, möchten Sie es `CWinApp`wahrscheinlich als eingebettetes Datenmember in Ihrer -derived-Anwendungsklasse speichern. Alternativen sind:

- Kein Dauerobjekt `CRecordset` zu halten. Sie können NULL an Ihre Recordset-Klassenkonstruktoren übergeben. In diesem Fall erstellt das `CDatabase` Framework ein temporäres Objekt `GetDefaultConnect` unter Verwendung der Informationen in der Memberfunktion des Recordsets. Dies ist der wahrscheinlichste alternative Ansatz.

- Das `CRecordset` Objekt zu einer globalen Variable machen. Diese Variable sollte ein Zeiger auf ein Recordset-Objekt `CWinApp::InitInstance` sein, das Sie dynamisch in der Außerkraftsetzung erstellen. Dadurch wird vermieden, dass versucht wird, das Objekt zu erstellen, bevor das Framework initialisiert wird.

- Verwenden von Recordset-Objekten wie im Kontext eines Dokuments oder einer Ansicht. Erstellen Sie Recordsets in den Memberfunktionen Ihrer Anwendung oder Frame-Fenster-Objekte.

## <a name="see-also"></a>Siehe auch

[MFC-Datenbankklassen](../data/mfc-database-classes-odbc-and-dao.md)
