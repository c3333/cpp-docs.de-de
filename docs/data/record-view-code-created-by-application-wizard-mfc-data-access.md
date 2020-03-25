---
title: Vom Anwendungs-Assistenten erstellter Datensatzansichts-Code (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69bebe978d03e5777f20765ac0bcf9a344f69320
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209156"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Vom Anwendungs-Assistenten erstellter Datensatzansichts-Code (MFC-Datenzugriff)

Der [MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md) überschreibt die `OnInitialUpdate`-und `OnGetRecordset` Member-Funktionen der Ansicht. Nachdem das Framework das Rahmenfenster, Dokument und die Ansicht erstellt hat, wird `OnInitialUpdate` aufgerufen, um die Ansicht zu initialisieren. `OnInitialUpdate` erhält einen Zeiger auf das Recordset aus dem Dokument. Ein Aufrufder [CView:: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) -Basisklasse öffnet das Recordset. Der folgende Code zeigt diesen Prozess für eine `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Beim Öffnen des Recordsets werden Datensätze ausgewählt. [CRecordset:: Open](../mfc/reference/crecordset-class.md#open) macht den ersten Datensatz zum aktuellen Datensatz, und DDX verschiebt Daten aus den Felddatenmembern des Recordsets in die entsprechenden Formular Steuerelemente in der Ansicht. Weitere Informationen zu RFX finden Sie unter [Daten Satz Feld Austausch (RFX)](../data/odbc/record-field-exchange-rfx.md). Weitere Informationen über DDX finden Sie unter [Dialogdatenaustausch und -validierung](../mfc/dialog-data-exchange-and-validation.md). Weitere Informationen zum Erstellen von Dokumenten/Ansichten finden Sie unter [Verwenden der Klassen zum Schreiben von Anwendungen für Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Sie sollten den Endbenutzern die Möglichkeit geben, die Steuerelemente der Datensatzansicht vom Recordset zu aktualisieren. Ohne diese Funktion kann der Benutzer den aktuellen Datensatz möglicherweise nicht verlassen, wenn er als Wert für ein Steuerelement einen unzulässigen Wert eingibt. Um die Steuerelemente zu aktualisieren, müssen Sie die `CWnd` Member-Funktion [UpdateData](../mfc/reference/cwnd-class.md#updatedata) mit dem Parameter false aufrufen.

## <a name="see-also"></a>Weitere Informationen

[Verwenden einer Daten Satz Ansicht](../data/using-a-record-view-mfc-data-access.md)
