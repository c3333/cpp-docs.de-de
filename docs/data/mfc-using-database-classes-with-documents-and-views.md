---
title: 'MFC: Verwenden von Datenbankklassen mit Dokumenten und Ansichten'
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213381"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Verwenden von Datenbankklassen mit Dokumenten und Ansichten

Sie können die MFC-Datenbankklassen mit oder ohne die Dokument-/Ansichtarchitektur verwenden. In diesem Thema wird die Arbeit mit Dokumenten und Ansichten hervorgehoben. Es wird Folgendes erläutert:

- So [schreiben Sie eine Formular basierte Anwendung](#_core_writing_a_form.2d.based_application) mit einem `CRecordView`-Objekt als Hauptansicht Ihres Dokuments.

- [Verwenden von Recordset-Objekten in Ihren Dokumenten und Sichten](#_core_using_recordsets_in_documents_and_views).

- [Weitere Überlegungen](#_core_other_factors).

Alternativen finden Sie unter [MFC: Verwenden von Datenbankklassen ohne Dokumente und Sichten](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Schreiben einer Formular basierten Anwendung

Viele Datenzugriffs Anwendungen basieren auf Formularen. Die Benutzeroberfläche ist ein Formular, das Steuerelemente enthält, in denen der Benutzerdaten untersucht, eingibt oder bearbeitet. Verwenden Sie zum Erstellen des Anwendungs Formulars die Klasse `CRecordView`. Wenn Sie den MFC-Anwendungs-Assistenten ausführen und auf der Seite **Datenbankunterstützung** den Typ **ODBC** -Client auswählen, verwendet das Projekt `CRecordView` für die Ansichts Klasse.

In einer Formular basierten Anwendung speichert jedes Daten Satz Ansichts Objekt einen Zeiger auf ein `CRecordset` Objekt. Der RFX-Mechanismus (Record Field Exchange) des Frameworks tauscht Daten zwischen dem Recordset und der Datenquelle aus. Der DDX-Mechanismus (Dialog Datenaustausch) tauscht Daten zwischen den Felddatenmembern des Recordset-Objekts und den Steuerelementen im Formular aus. `CRecordView` bietet auch Standard Befehls Handler-Funktionen für die Navigation von Datensatz zu Datensatz im Formular.

Informationen zum Erstellen einer Formular basierten Anwendung mit dem Anwendungs-Assistenten finden Sie unter [Erstellen einer Formular basierten MFC-Anwendung](../mfc/reference/creating-a-forms-based-mfc-application.md) und [Datenbankunterstützung, MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md).

Eine vollständige Erläuterung der Formulare finden Sie unter [Daten Satz Ansichten](../data/record-views-mfc-data-access.md).

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Verwenden von Recordsets in Dokumenten und Ansichten

Viele einfache Formular basierte Anwendungen benötigen keine Dokumente. Wenn Ihre Anwendung komplexer ist, sollten Sie ein Dokument als Proxy für die Datenbank verwenden und ein `CDatabase` Objekt speichern, das eine Verbindung mit der Datenquelle herstellt. Formular basierte Anwendungen speichern in der Regel einen Zeiger auf ein Recordset-Objekt in der Ansicht. Andere Arten von Datenbankanwendungen speichern Recordsets und `CDatabase` Objekt im Dokument. Im folgenden finden Sie einige Möglichkeiten für die Verwendung von Dokumenten in Datenbankanwendungen:

- Wenn Sie auf ein Recordset in einem lokalen Kontext zugreifen, erstellen Sie nach Bedarf ein `CRecordset` Objekt lokal in den Element Funktionen des Dokuments oder der Ansicht.

   Deklarieren Sie ein Recordset-Objekt als lokale Variable in einer Funktion. Übergeben Sie NULL an den-Konstruktor, der bewirkt, dass das Framework ein temporäres `CDatabase` Objekt erstellt und öffnet. Übergeben Sie als Alternative einen Zeiger auf ein `CDatabase` Objekt. Verwenden Sie das Recordset innerhalb der-Funktion, und lassen Sie es beim Beenden der Funktion automatisch zerstören.

   Wenn Sie NULL an einen recordsetkonstruktor übergeben, verwendet das Framework Informationen, die von der `GetDefaultConnect` Member-Funktion des Recordsets zurückgegeben werden, um ein `CDatabase` Objekt zu erstellen und zu öffnen. Die Assistenten implementieren `GetDefaultConnect` für Sie.

- Wenn Sie während der Lebensdauer Ihres Dokuments auf ein Recordset zugreifen, Betten Sie mindestens ein `CRecordset`-Objekt in das Dokument ein.

   Erstellen Sie die Recordset-Objekte, entweder wenn Sie das Dokument initialisieren oder nach Bedarf. Sie können eine Funktion schreiben, die einen Zeiger auf das Recordset zurückgibt, wenn Sie bereits vorhanden ist, oder das Recordset erstellt und öffnet, wenn es noch nicht vorhanden ist. Schließen, löschen und erstellen Sie das Recordset nach Bedarf, oder erstellen Sie die `Requery` Member-Funktion, um die Datensätze zu aktualisieren.

- Wenn Sie während der Lebensdauer des Dokuments auf eine Datenquelle zugreifen, Betten Sie ein `CDatabase` Objekt ein, oder speichern Sie einen Zeiger auf ein `CDatabase` Objekt darin.

   Das `CDatabase`-Objekt verwaltet eine Verbindung mit Ihrer Datenquelle. Das-Objekt wird während der Dokument Erstellung automatisch erstellt, und Sie können seine `Open` Member-Funktion aufzurufen, wenn Sie das Dokument initialisieren. Beim Erstellen von recordsetobjekten in Dokument Element Funktionen übergeben Sie einen Zeiger auf das `CDatabase` Objekt des Dokuments. Dadurch wird jedes Recordset mit seiner Datenquelle verknüpft. Das Datenbankobjekt wird in der Regel zerstört, wenn das Dokument geschlossen wird. Die Recordset-Objekte werden in der Regel zerstört, wenn Sie den Gültigkeitsbereich einer Funktion beenden.

##  <a name="other-factors"></a><a name="_core_other_factors"></a>Weitere Faktoren

Formular basierte Anwendungen werden häufig nicht für den dokumentserialisierungsmechanismus des Frameworks verwendet, sodass Sie die Befehle " **New** " und " **Open** " im Menü " **Datei** " entfernen, deaktivieren oder ersetzen können. Weitere Informationen finden Sie im Artikel [Serialisierung: Serialisierung im Vergleich zur Daten Bank Eingabe/-Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

Möglicherweise möchten Sie auch die zahlreichen Möglichkeiten der Benutzeroberfläche nutzen, die das Framework unterstützen kann. Beispielsweise können Sie mehrere `CRecordView` Objekte in einem Splitter Fenster verwenden, mehrere Recordsets in untergeordneten MDI-Fenstern (Multiple Document Interface) öffnen usw.

Möglicherweise möchten Sie den Druck von anderen in der Ansicht implementieren, unabhängig davon, ob es sich um ein mit `CRecordView` implementiertes Formular handelt. Als von `CFormView`abgeleitete Klassen unterstützt `CRecordView` keinen Druck, aber Sie können die `OnPrint` Member-Funktion überschreiben, um das Drucken zuzulassen. Weitere Informationen finden Sie unter [CFormView](../mfc/reference/cformview-class.md)-Klasse.

Möglicherweise möchten Sie überhaupt keine Dokumente und Sichten verwenden. Weitere Informationen finden Sie unter [MFC: Verwenden von Datenbankklassen ohne Dokumente und Sichten](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Weitere Informationen

[MFC-Datenbankklassen](../data/mfc-database-classes-odbc-and-dao.md)
