---
title: Datensatzansichten (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 31dbd92219f263c625050524279b97ef38ba9ba1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209130"
---
# <a name="record-views--mfc-data-access"></a>Datensatzansichten (MFC-Datenzugriff)

Dieser Abschnitt gilt nur für die MFC-ODBC-Klassen. Informationen zu OLE DB-Daten Satz Sichten finden Sie unter [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) und [Verwenden von OLE DB Daten Satz Sichten](../data/oledb/using-ole-db-record-views.md).

Zur Unterstützung von Formular basierten Anwendungen für den Datenzugriff stellt die Klassenbibliothek [CRecordView](../mfc/reference/crecordview-class.md)-Klasse bereit. Eine Daten Satz Ansicht ist ein Formular Ansichts Objekt, dessen Steuerelemente direkt den Felddatenmembern eines [Recordset](../data/odbc/recordset-odbc.md) -Objekts (und indirekt den entsprechenden Spalten in einem Abfrageergebnis oder einer Tabelle in der Datenquelle) zugeordnet werden. Wie die Basisklasse [CFormView](../mfc/reference/cformview-class.md)basiert `CRecordView` auf einer Dialogfeld Vorlagen Ressource.

## <a name="form-uses"></a>Verwendungszwecke für Formulare

Formulare eignen sich für eine Vielzahl von Datenzugriffsaufgaben:

- Eingeben von Daten

- Durchführen von schreibgeschützten Prüfung von Daten

- Aktualisieren von Daten

## <a name="further-reading-about-record-views"></a>Weitere Informationen zu Datensatzansichten

Die Informationen in diesen Themen gelten für die ODBC-basierten und DAO-basierte Klassen. Verwenden Sie `CRecordView` für ODBC und `CDaoRecordView` für DAO.

Dabei werden folgende Themen behandelt:

- [Funktionen von Daten Satz Ansichts Klassen](../data/features-of-record-view-classes-mfc-data-access.md)

- [Datenaustausch für Daten Satz Ansichten](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Ihre Rolle beim Arbeiten mit einer Daten Satz Ansicht](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Entwerfen und Erstellen einer Daten Satz Ansicht](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Verwenden einer Daten Satz Ansicht](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Weitere Informationen

[Datenzugriffsprogrammierung (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Liste der ODBC-Treiber](../data/odbc/odbc-driver-list.md)
