---
title: Momentaufnahme
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366908"
---
# <a name="snapshot"></a>Momentaufnahme

Ein Snapshot ist ein Recordset, das eine statische Ansicht der Daten widerspiegelt, wie sie zum Zeitpunkt der Erstellung des Snapshots vorhanden war. Wenn Sie den Snapshot öffnen und zu allen Datensätzen wechseln, ändern sich der darin enthaltene Datensatzsatz und deren Werte erst, wenn Sie den Snapshot durch Aufrufen neu `Requery`erstellen.

> [!NOTE]
> Dieses Thema bezieht sich auf die MFC-ODBC-Klassen. Wenn Sie die MFC DAO-Klassen anstelle der MFC ODBC-Klassen verwenden, finden Sie unter [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) eine Beschreibung von Snapshot-Typ-Recordsets.

Sie können aktualisierbare oder schreibgeschützte Snapshots mit den Datenbankklassen erstellen. Im Gegensatz zu einem Dynaset spiegelt ein aktualisierbarer Snapshot keine Änderungen an Datensatzwerten wider, die von anderen Benutzern vorgenommen wurden, aber er spiegelt Aktualisierungen und Löschungen wider, die von Ihrem Programm vorgenommen wurden. Datensätze, die einem Snapshot hinzugefügt werden, werden `Requery`für den Snapshot erst sichtbar, wenn Sie aufrufen.

> [!TIP]
> Ein Snapshot ist ein statischer ODBC-Cursor. Statische Cursor erhalten erst dann eine Datenzeile, wenn Sie zu diesem Datensatz scrollen. Um sicherzustellen, dass alle Datensätze sofort abgerufen werden, können Sie zum Ende des Recordsets scrollen und dann zum ersten Datensatz scrollen, den Sie anzeigen möchten. Beachten Sie jedoch, dass ein Bildlauf bis zum Ende einen zusätzlichen Overhead mit sich bringt und die Leistung beeinträchtigen kann.

Snapshots sind am wertvollsten, wenn sie die Daten während des Arbeitsablaufs reparieren lassen müssen, z. B. wenn Sie einen Bericht generieren oder Berechnungen durchführen. Dennoch kann die Datenquelle erheblich von Ihrem Snapshot abweichen, sodass Sie ihn von Zeit zu Zeit neu erstellen möchten.

Die Snapshot-Unterstützung basiert auf der ODBC-Cursorbibliothek, die statische Cursor und positionierte Aktualisierungen (erforderlich für die Aktualisierungsfähigkeit) für jeden Level 1-Treiber bereitstellt. Die Cursorbibliotheks-DLL muss für diese Unterstützung in den Arbeitsspeicher geladen werden. Wenn Sie `CDatabase` ein Objekt `OpenEx` erstellen und seine Memberfunktion aufrufen, müssen Sie die `CDatabase::useCursorLib` Option des Parameters *dwOptions* angeben. Wenn Sie `Open` die Memberfunktion aufrufen, wird die Cursorbibliothek standardmäßig geladen. Wenn Sie Dynasets anstelle von Snapshots verwenden, möchten Sie nicht dazu führen, dass die Cursorbibliothek geladen wird.

Snapshots sind nur verfügbar, wenn die ODBC-Cursorbibliothek beim Erstellen des `CDatabase` Objekts geladen wurde oder der ODBC-Treiber, den Sie verwenden, statische Cursor unterstützt.

> [!NOTE]
> Bei einigen ODBC-Treibern können Snapshots (statische Cursor) möglicherweise nicht aktualisiert werden. Überprüfen Sie die Treiberdokumentation auf unterstützte Cursortypen und die von ihnen unterstützten Parallelitätstypen. Um aktualisierbare Snapshots zu gewährleisten, stellen Sie `CDatabase` sicher, dass Sie die Cursorbibliothek beim Erstellen eines Objekts in den Speicher laden. Weitere Informationen finden Sie unter [ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Wenn Sie sowohl Snapshots als auch Dynasets verwenden möchten, müssen Sie sie auf zwei verschiedenen `CDatabase` Objekten (zwei verschiedene Verbindungen) basieren.

Weitere Informationen zu den Eigenschaften, die Snapshots für alle Recordsets freigeben, finden Sie unter [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Weitere Informationen zu ODBC und Snapshots, einschließlich der ODBC-Cursorbibliothek, finden Sie unter [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Siehe auch

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
