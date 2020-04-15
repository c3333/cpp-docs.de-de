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
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368901"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Verwenden von Datenbankklassen mit Dokumenten und Ansichten

Sie können die MFC-Datenbankklassen mit oder ohne Dokument-/Ansichtsarchitektur verwenden. In diesem Thema wird das Arbeiten mit Dokumenten und Ansichten hervorgehoben. Es erklärt:

- [Schreiben einer formularbasierten Anwendung](#_core_writing_a_form.2d.based_application) mithilfe `CRecordView` eines Objekts als Hauptansicht im Dokument.

- [So verwenden Sie Recordset-Objekte in Dokumenten und Ansichten](#_core_using_recordsets_in_documents_and_views).

- [Sonstige Überlegungen](#_core_other_factors).

Alternativen finden Sie unter [MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Schreiben einer formularbasierten Anwendung

Viele Datenzugriffsanwendungen basieren auf Formularen. Die Benutzeroberfläche ist ein Formular, das Steuerelemente enthält, in denen der Benutzer Daten untersucht, eingibt oder benimmt. Um ihr Antragsformular basierend `CRecordView`zu machen, verwenden Sie die Klasse . Wenn Sie den MFC-Anwendungs-Assistenten ausführen und **den ODBC-Clienttyp** auf der Seite **Datenbanksupport** auswählen, wird das Projekt für die Ansichtsklasse verwendet. `CRecordView`

In einer formularbasierten Anwendung speichert jedes Datensatzansichtsobjekt `CRecordset` einen Zeiger auf ein Objekt. Der RFX-Mechanismus (Record Field Exchange) des Frameworks tauscht Daten zwischen dem Recordset und der Datenquelle aus. Der Dialogdatenaustauschmechanismus (DDX) tauscht Daten zwischen den Felddatenmembern des Recordset-Objekts und den Steuerelementen im Formular aus. `CRecordView`bietet auch Standardbefehlshandlerfunktionen für die Navigation von Datensatz zu Datensatz im Formular.

Informationen zum Erstellen einer formularbasierten Anwendung mit dem Anwendungsassistenten finden Sie unter [Erstellen einer formularbasierten MFC-Anwendung](../mfc/reference/creating-a-forms-based-mfc-application.md) und [Datenbankunterstützung, MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md).

Eine ausführliche Erläuterung der Formulare finden Sie unter [Datensatzansichten](../data/record-views-mfc-data-access.md).

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Verwenden von Recordsets in Dokumenten und Ansichten

Viele einfache formularbasierte Anwendungen benötigen keine Dokumente. Wenn Ihre Anwendung komplexer ist, möchten Sie wahrscheinlich ein Dokument als `CDatabase` Proxy für die Datenbank verwenden und ein Objekt speichern, das eine Verbindung mit der Datenquelle herstellt. Formularbasierte Anwendungen speichern in der Regel einen Zeiger auf ein Recordsetobjekt in der Ansicht. Andere Arten von Datenbankanwendungen `CDatabase` speichern Recordsets und Objekte im Dokument. Hier sind einige Möglichkeiten zur Verwendung von Dokumenten in Datenbankanwendungen:

- Wenn Sie in einem lokalen Kontext auf ein `CRecordset` Recordset zugreifen, erstellen Sie bei Bedarf ein Objekt lokal in Denelementfunktionen des Dokuments oder der Ansicht.

   Deklarieren Sie ein Recordset-Objekt als lokale Variable in einer Funktion. Übergeben Sie NULL an den Konstruktor, wodurch `CDatabase` das Framework ein temporäres Objekt erstellt und geöffnet hat. Alternativ können Sie einen Zeiger `CDatabase` auf ein Objekt übergeben. Verwenden Sie das Recordset innerhalb der Funktion und lassen Sie es automatisch zerstört werden, wenn die Funktion beendet wird.

   Wenn Sie NULL an einen Recordsetkonstruktor übergeben, verwendet das `GetDefaultConnect` Framework Informationen, `CDatabase` die von der Memberfunktion des Recordsets zurückgegeben werden, um ein Objekt zu erstellen und zu öffnen. Die Assistenten `GetDefaultConnect` implementieren für Sie.

- Wenn Sie während der Lebensdauer des Dokuments auf ein Recordset zugreifen, betten Sie ein oder mehrere `CRecordset` Objekte in das Dokument ein.

   Erstellen Sie die Recordset-Objekte entweder, wenn Sie das Dokument initialisieren, oder nach Bedarf. Sie können eine Funktion schreiben, die einen Zeiger auf das Recordset zurückgibt, wenn es bereits vorhanden ist oder das Recordset erstellt und öffnet, wenn es noch nicht vorhanden ist. Schließen, löschen und erstellen Sie das Recordset `Requery` nach Bedarf neu, oder rufen Sie die Memberfunktion auf, um die Datensätze zu aktualisieren.

- Wenn Sie während der Lebensdauer des Dokuments auf eine `CDatabase` Datenquelle zugreifen, betten `CDatabase` Sie ein Objekt ein, oder speichern Sie einen Zeiger auf ein Objekt darin.

   Das `CDatabase` Objekt verwaltet eine Verbindung mit der Datenquelle. Das Objekt wird während der Dokumenterstellung `Open` automatisch erstellt, und Sie rufen seine Memberfunktion auf, wenn Sie das Dokument initialisieren. Wenn Sie Recordset-Objekte in Dokumentmemberfunktionen erstellen, übergeben Sie `CDatabase` einen Zeiger an das Dokumentobjekt. Dadurch wird jedes Recordset seiner Datenquelle zugeordnet. Das Datenbankobjekt wird normalerweise zerstört, wenn das Dokument geschlossen wird. Die Recordset-Objekte werden in der Regel zerstört, wenn sie den Bereich einer Funktion verlassen.

## <a name="other-factors"></a><a name="_core_other_factors"></a>Andere Faktoren

Formularbasierte Anwendungen werden häufig nicht für den Dokumentserialisierungsmechanismus des Frameworks verwendet, daher sollten Sie die Befehle **Neu** und **Öffnen** im Menü **Datei** entfernen, deaktivieren oder ersetzen. Siehe den Artikel [Serialisierung: Serialisierung vs. Datenbankeingabe/-ausgabe](../mfc/serialization-serialization-vs-database-input-output.md).

Sie können auch die vielen Benutzeroberflächenmöglichkeiten nutzen, die das Framework unterstützen kann. Sie können z. `CRecordView` B. mehrere Objekte in einem Splitterfenster verwenden, mehrere Recordsets in verschiedenen untergeordneten MDI-Fenstern (Multiple Document Interface) öffnen usw.

Sie können das Drucken von allem, was in Ihrer Ansicht `CRecordView` ist, implementieren, unabhängig davon, ob es sich um ein Formular handelt, das mit implementiert wurde, oder um etwas anderes. Da von `CFormView` `CRecordView` abgeleitete Klassen das Drucken nicht unterstützen, können Sie jedoch die `OnPrint` Memberfunktion überschreiben, um das Drucken zu ermöglichen. Weitere Informationen finden Sie unter Klasse [CFormView](../mfc/reference/cformview-class.md).

Möglicherweise möchten Sie dokumente und ansichten überhaupt nicht verwenden. In diesem Fall finden Sie weitere Informationen unter [MFC: Verwenden von Datenbankklassen ohne Dokumente und Ansichten](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Siehe auch

[MFC-Datenbankklassen](../data/mfc-database-classes-odbc-and-dao.md)
