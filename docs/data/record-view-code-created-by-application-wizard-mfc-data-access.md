---
title: Vom Anwendungs-Assistenten erstellter Datensatzansichts-Code (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376023"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Vom Anwendungs-Assistenten erstellter Datensatzansichts-Code (MFC-Datenzugriff)

Der [MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md) überschreibt `OnInitialUpdate` `OnGetRecordset` die Funktionen der Ansicht und des Members. Nachdem das Framework das Rahmenfenster, Dokument und die Ansicht erstellt hat, wird `OnInitialUpdate` aufgerufen, um die Ansicht zu initialisieren. `OnInitialUpdate` erhält einen Zeiger auf das Recordset aus dem Dokument. Ein Aufruf der Basisklasse [CView::OnInitialUpdate-Funktion](../mfc/reference/cview-class.md#oninitialupdate) öffnet das Recordset. Der folgende Code zeigt `CRecordView`diesen Prozess für eine:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Beim Öffnen des Recordsets werden Datensätze ausgewählt. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) erstellt den ersten Datensatz zum aktuellen Datensatz, und DDX verschiebt Daten aus den Felddatenelementen des Recordsets in die entsprechenden Formularsteuerelemente in der Ansicht. Weitere Informationen zu RFX finden Sie unter [Datensatzfeldaustausch (RFX)](../data/odbc/record-field-exchange-rfx.md). Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../mfc/dialog-data-exchange-and-validation.md). Informationen zum Dokument-/Ansichtserstellungsprozess finden Sie unter [Verwenden der Klassen zum Schreiben](../mfc/using-the-classes-to-write-applications-for-windows.md)von Anwendungen für Windows .

> [!NOTE]
> Sie sollten den Endbenutzern die Möglichkeit geben, die Steuerelemente der Datensatzansicht vom Recordset zu aktualisieren. Ohne diese Funktion kann der Benutzer den aktuellen Datensatz möglicherweise nicht verlassen, wenn er als Wert für ein Steuerelement einen unzulässigen Wert eingibt. Um die Steuerelemente zu `CWnd` aktualisieren, rufen Sie die Memberfunktion [UpdateData](../mfc/reference/cwnd-class.md#updatedata) mit dem Parameter FALSE auf.

## <a name="see-also"></a>Siehe auch

[Verwenden einer Datensatzansicht](../data/using-a-record-view-mfc-data-access.md)
