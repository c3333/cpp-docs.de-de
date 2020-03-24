---
title: Mögliche Änderungen am Standardcode (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 7ea616caf176cd1e9e2f26bee1339640067b4e3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213460"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Mögliche Änderungen am Standardcode (MFC-Datenzugriff)

Der [MFC-Anwendungs-Assistent](../mfc/reference/database-support-mfc-application-wizard.md) schreibt eine Recordset-Klasse für Sie, die alle Datensätze in einer einzelnen Tabelle auswählt. Dieses Verhalten können Sie häufig auf eine oder mehrere der folgenden Arten ändern:

- Legen Sie einen Filter oder eine Sortierreihenfolge für das Recordset fest. Führen Sie dies in `OnInitialUpdate` aus, nachdem das Recordset-Objekt erstellt wurde, aber bevor seine `Open` Member-Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Recordset: Filtern von Datensätzen (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) und [Recordset: Sortieren von Datensätzen (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametrisieren Sie das Recordset. Geben Sie den tatsächlichen Laufzeit-Parameterwert nach dem Filter an. Weitere Informationen finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md) .

- Übergeben Sie eine angepasste SQL-Zeichenfolge an die [Open](../mfc/reference/crecordset-class.md#open) Member-Funktion. Eine Erläuterung dazu, was Sie mit dieser Technik erreichen können, finden Sie unter [SQL: Anpassen der SQL-Anweisung ihres Recordsets (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden einer Daten Satz Ansicht](../data/using-a-record-view-mfc-data-access.md)
