---
title: Aufgaben bei der Arbeit mit Datensatzansichten (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: 351aa2d5ce950017aa8c1b3d99c8d297a423ad9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209000"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Aufgaben bei der Arbeit mit Datensatzansichten (MFC-Datenzugriff)

Die folgende Tabelle zeigt, was Sie in der Regel tun müssen, um mit einer Datensatzansicht zu arbeiten, und wie das Framework Sie unterstützt.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Arbeiten mit einer Datensatzansicht: Sie und das Framework

|Sie|Das Framework|
|---------|-------------------|
|Verwenden Sie zum Entwerfen des Formulars den Visual C++-Dialog-Editor.|Erstellt eine Dialogfeldvorlagen-Ressource mit Steuerelementen.|
|Verwenden Sie den [MFC-Anwendungs-Assistenten](../mfc/reference/database-support-mfc-application-wizard.md) zum Erstellen von Klassen, die von [CRecordView](../mfc/reference/crecordview-class.md) und [CRecordset](../mfc/reference/crecordset-class.md)abgeleitet werden.|Schreibt die Klassen für Sie.|
|Weisen Sie Datensatzansichts-Steuerelemente Recordset-Felddatenmembern zu.|Stellt DDX zwischen den Steuerelementen und den Recordset-Feldern bereit.|
||Stellt Standard Befehls Handler für " **zuerst verschieben**", " **Letzte verschieben**", "weiter **verschieben**" und " **vorherige Befehle verschieben** " aus Menüs oder Symbolleisten-Schaltflächen bereit|
||Aktualisiert Änderungen in der Datenbank.|
|[Optional] Schreiben Sie Code, um Listen- oder Kombinationsfelder oder andere Steuerelemente mit Daten aus einem zweiten Recordset zu füllen.||
|[Optional] Schreiben Sie Code für spezielle Validierungen.||
|[Optional] Schreiben Sie Code zum Hinzufügen oder Löschen von Datensätzen.||

Formularbasierte Programmierung ist nur eine Herangehensweise für die Arbeit mit einer Datenbank. Informationen zu Anwendungen, die eine andere Benutzeroberfläche oder keine Benutzeroberfläche verwenden, finden Sie unter [MFC: Verwenden von Datenbankklassen mit Dokumenten und Sichten](../data/mfc-using-database-classes-with-documents-and-views.md) und [MFC: Verwenden von Datenbankklassen ohne Dokumente und Sichten](../data/mfc-using-database-classes-without-documents-and-views.md). Alternative Ansätze zum Anzeigen von Datenbankdaten Sätzen finden Sie Unterklassen [CListView](../mfc/reference/clistview-class.md) und [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Weitere Informationen

[Datensatzansichten (MFC-Datenzugriff)](../data/record-views-mfc-data-access.md)<br/>
[Liste der ODBC-Treiber](../data/odbc/odbc-driver-list.md)
