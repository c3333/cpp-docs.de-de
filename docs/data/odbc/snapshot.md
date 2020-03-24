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
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212692"
---
# <a name="snapshot"></a>Momentaufnahme

Eine Momentaufnahme ist ein Recordset, das eine statische Ansicht der Daten darstellt, die zum Zeitpunkt der Erstellung der Momentaufnahme vorhanden waren. Wenn Sie die Momentaufnahme öffnen und zu allen Datensätzen wechseln, ändern sich die darin enthaltenen Datensätze und deren Werte erst, nachdem Sie die Momentaufnahme durch Aufrufen von `Requery`neu erstellt haben.

> [!NOTE]
>  Dieses Thema bezieht sich auf die MFC-ODBC-Klassen. Wenn Sie die MFC-DAO-Klassen anstelle der MFC-ODBC-Klassen verwenden, finden Sie weitere Informationen unter [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) für eine Beschreibung von Recordsets vom Typ "Snapshot".

Mit den Datenbankklassen können Sie aktualisierbare oder schreibgeschützte Momentaufnahmen erstellen. Anders als bei einem Dynaset gibt eine aktualisierbare Momentaufnahme keine Änderungen an den Daten Satz Werten an, die von anderen Benutzern vorgenommen wurden, sondern spiegelt Updates und Löschungen, die von Ihrem Programm vorgenommen werden. Datensätze, die einer Momentaufnahme hinzugefügt werden, werden erst dann für die Momentaufnahme sichtbar, wenn Sie `Requery`

> [!TIP]
>  Eine Momentaufnahme ist ein statischer ODBC-Cursor. Statische Cursor erhalten erst dann eine Zeile mit Daten, wenn Sie einen Bildlauf zu diesem Datensatz durchführen. Um sicherzustellen, dass alle Datensätze sofort abgerufen werden, können Sie einen Bildlauf zum Ende des Recordsets durchführen und dann einen Bildlauf zum ersten Datensatz durchführen, den Sie anzeigen möchten. Beachten Sie jedoch, dass der Bildlauf zum Ende zu einem zusätzlichen Aufwand führt und die Leistung verringern kann.

Momentaufnahmen sind besonders wertvoll, wenn die Daten während der Vorgänge korrigiert bleiben müssen, so als wenn Sie einen Bericht erstellen oder Berechnungen ausführen. Auch wenn sich die Datenquelle erheblich von der Momentaufnahme unterscheiden kann, sollten Sie Sie von Zeit zu Zeit neu erstellen.

Die momentaufnahmenunterstützung basiert auf der ODBC-Cursor Bibliothek, die statische Cursor und positionierte Updates (die für Aktualisierbarkeit erforderlich ist) für alle Treiber der Ebene 1 bereitstellt. Die Cursor-Bibliotheks-DLL muss für diese Unterstützung in den Arbeitsspeicher geladen werden. Wenn Sie ein `CDatabase` Objekt erstellen und seine `OpenEx` Member-Funktion aufrufen, müssen Sie die `CDatabase::useCursorLib`-Option des *dwOptions* -Parameters angeben. Wenn Sie die `Open` Member-Funktion aufzurufen, wird die Cursor Bibliothek standardmäßig geladen. Wenn Sie Dynasets anstelle von Momentaufnahmen verwenden, möchten Sie nicht, dass die Cursor Bibliothek geladen wird.

Momentaufnahmen sind nur verfügbar, wenn die ODBC-Cursor Bibliothek geladen wurde, als das `CDatabase` Objekt erstellt wurde, oder der von Ihnen verwendete ODBC-Treiber unterstützt statische Cursor.

> [!NOTE]
>  Für einige ODBC-Treiber sind Momentaufnahmen (statische Cursor) möglicherweise nicht aktualisierbar. Überprüfen Sie die Treiber Dokumentation auf unterstützte Cursor Typen und die von Ihnen unterstützten neben läufigkeits Typen. Um aktualisierbare Momentaufnahmen zu gewährleisten, stellen Sie sicher, dass Sie die Cursor Bibliothek in den Arbeitsspeicher laden, wenn Sie ein `CDatabase` Weitere Informationen finden Sie unter [ODBC: die ODBC-Cursor Bibliothek](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Wenn Sie sowohl Momentaufnahmen als auch Dynasets verwenden möchten, müssen Sie Sie auf zwei verschiedenen `CDatabase` Objekten (zwei unterschiedliche Verbindungen) aufbauen.

Weitere Informationen zur Freigabe von Eigenschaften Momentaufnahmen für alle Recordsets finden Sie unter [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Weitere Informationen zu ODBC und Momentaufnahmen, einschließlich der ODBC-Cursor Bibliothek, finden Sie unter [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
