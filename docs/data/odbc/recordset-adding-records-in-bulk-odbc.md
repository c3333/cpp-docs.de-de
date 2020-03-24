---
title: 'Recordset: Hinzufügen von Datensätzen in einer Sammeloperation (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213017"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Recordset: Hinzufügen von Datensätzen in einer Sammeloperation (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Die MFC [CRecordset](../../mfc/reference/crecordset-class.md) -Klasse verfügt über eine neue Optimierung, die die Effizienz verbessert, wenn Sie einer Tabelle neue Datensätze in einem Massen Vorgang hinzufügen.

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Eine neue Option für den *dwOptions* -Parameter der [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) -Member-Funktion, `optimizeBulkAdd`, verbessert die Leistung, wenn Sie mehrere Datensätze nacheinander hinzufügen, ohne `Requery` oder `Close`aufrufen zu müssen. Nur die Felder, die vor dem ersten `Update` Aufruf geändert werden, werden für nachfolgende `AddNew`/`Update` Aufrufe als geändert markiert.

Wenn Sie die-Datenbankklassen verwenden, um die `::SQLSetPos` ODBC-API-Funktion zum Hinzufügen, bearbeiten und Löschen von Datensätzen zu nutzen, ist diese Optimierung nicht erforderlich.

Wenn die ODBC-Cursor Bibliothek geladen wird oder der ODBC-Treiber das Hinzufügen, bearbeiten und Löschen über `::SQLSetPos`nicht unterstützt, sollte diese Optimierung die Leistung beim Massen hinzufügen verbessern. Um diese Optimierung zu aktivieren, legen Sie den *dwOptions* -Parameter im `Open`-aufrufsbefehl für das Recordset auf Folgendes fest:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
