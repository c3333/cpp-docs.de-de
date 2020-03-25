---
title: Verwenden einer Datensatzansicht (MFC-Datenzugriff)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209026"
---
# <a name="using-a-record-view--mfc-data-access"></a>Verwenden einer Datensatzansicht (MFC-Datenzugriff)

In diesem Thema wird erläutert, wie Sie normalerweise den Standardcode für Datensatzansichten anpassen können, den der Assistent für Sie schreibt. In der Regel möchten Sie die Daten Satz Auswahl mit einem [Filter](../data/odbc/recordset-filtering-records-odbc.md) oder [Parametern](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)einschränken, ggf. die Datensätze [Sortieren](../data/odbc/recordset-sorting-records-odbc.md) und die SQL-Anweisung anpassen.

Die Verwendung von `CRecordView` ist mit der Verwendung von [CFormView](../mfc/reference/cformview-class.md)identisch. Grundsätzlich wird die Datensatzansicht zum Anzeigen und ggf. zum Aktualisieren der Datensätze eines einzelnen Recordsets verwendet. Darüber hinaus möchten Sie möglicherweise auch andere Recordsets verwenden, wie unter [Daten Satz Ansichten: Füllen eines Listen Felds aus einem zweiten Recordset](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)erläutert.

## <a name="see-also"></a>Weitere Informationen

[Datensatzansichten (MFC-Datenzugriff)](../data/record-views-mfc-data-access.md)<br/>
[Liste der ODBC-Treiber](../data/odbc/odbc-driver-list.md)
