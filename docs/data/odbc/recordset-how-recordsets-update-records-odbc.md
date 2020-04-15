---
title: 'Recordset: Datensatzaktualisierung durch Recordsets (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366976"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset: Datensatzaktualisierung durch Recordsets (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Neben der Möglichkeit, Datensätze aus einer Datenquelle auszuwählen, können Recordsets (optional) die ausgewählten Datensätze aktualisieren oder löschen oder neue Datensätze hinzufügen. Drei Faktoren bestimmen die Aktualisierungsfähigkeit eines Recordsets: ob die verbundene Datenquelle aktualisierbar ist, die Optionen, die Sie beim Erstellen eines Recordset-Objekts angeben, und die erstellte SQL.

> [!NOTE]
> Die SQL, `CRecordset` auf der Ihr Objekt basiert, kann sich auf die Aktualisierungsfähigkeit Ihres Recordsets auswirken. Wenn Ihr SQL beispielsweise eine Join- oder **GROUP BY-Klausel** enthält, legt MFC die Aktualisierungsfähigkeit auf FALSE fest.

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Abrufen von Massenzeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

In diesem Thema wird Folgendes erläutert:

- Ihre Rolle bei der [Recordset-Aktualisierung](#_core_your_role_in_recordset_updating) und was das Framework für Sie tut.

- [Das Recordset als Bearbeitungspuffer](#_core_the_edit_buffer) und die [Unterschiede zwischen Dynasets und Snapshots](#_core_dynasets_and_snapshots).

[Recordset: Wie AddNew, Edit, and Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) die Aktionen dieser Funktionen aus der Sicht des Recordsets beschreibt.

[Recordset: Mehr über Updates (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) schließt die Story für die Recordset-Aktualisierung ab, indem erläutert wird, wie sich Transaktionen auf Aktualisierungen auswirken, wie sich das Schließen eines Recordsets oder das Scrollen auf laufende Aktualisierungen auswirkt und wie Ihre Updates mit den Updates anderer Benutzer interagieren.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Ihre Rolle bei der Recordset-Aktualisierung

In der folgenden Tabelle wird ihre Rolle bei der Verwendung von Recordsets zum Hinzufügen, Bearbeiten oder Löschen von Datensätzen sowie zum Ausführen des Frameworks für Sie angezeigt.

### <a name="recordset-updating-you-and-the-framework"></a>Recordset-Aktualisierung: Sie und das Framework

|Sie|Das Framework|
|---------|-------------------|
|Bestimmen Sie, ob die Datenquelle aktualisierbar (oder anbeschreibbar) ist.|Stellt [CDatabase-Memberfunktionen](../../mfc/reference/cdatabase-class.md) zum Testen der Aktualisierungs- oder Anhängefähigkeit der Datenquelle bereit.|
|Öffnen Sie ein aufrüstbares Recordset (jeden Typs).||
|Bestimmen Sie, ob das Recordset `CRecordset` aufrüstbar `CanUpdate` `CanAppend`ist, indem Sie Aktualisierungsfunktionen wie oder aufrufen.||
|Rufen Sie Recordset-Memberfunktionen auf, um Datensätze hinzuzufügen, zu bearbeiten und zu löschen.|Verwaltet die Mechanik des Datenaustauschs zwischen dem Recordset-Objekt und der Datenquelle.|
|Optional können Sie Transaktionen verwenden, um den Aktualisierungsprozess zu steuern.|Stellt `CDatabase` Memberfunktionen zur Unterstützung von Transaktionen bereit.|

Weitere Informationen zu Transaktionen finden Sie unter [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Der Bearbeitungspuffer

Zusammengenommen dienen die Felddatenmember eines Recordsets als Bearbeitungspuffer, der einen Datensatz – den aktuellen Datensatz – enthält. Aktualisierungsvorgänge verwenden diesen Puffer, um mit dem aktuellen Datensatz zu arbeiten.

- Wenn Sie einen Datensatz hinzufügen, wird der Bearbeitungspuffer zum Erstellen eines neuen Datensatzes verwendet. Wenn Sie das Hinzufügen des Datensatzes abgeschlossen haben, wird der Datensatz, der zuvor aktuell war, wieder aktuell.

- Wenn Sie einen Datensatz aktualisieren (bearbeiten), wird der Bearbeitungspuffer verwendet, um die Felddatenmember des Recordsets auf neue Werte festzulegen. Wenn Sie die Aktualisierung abgeschlossen haben, ist der aktualisierte Datensatz immer noch aktuell.

Wenn Sie [AddNew](../../mfc/reference/crecordset-class.md#addnew) oder [Edit](../../mfc/reference/crecordset-class.md#edit)aufrufen, wird der aktuelle Datensatz gespeichert, sodass er später bei Bedarf wiederhergestellt werden kann. Wenn Sie [Delete](../../mfc/reference/crecordset-class.md#delete)aufrufen, wird der aktuelle Datensatz nicht gespeichert, sondern als gelöscht markiert, und Sie müssen zu einem anderen Datensatz scrollen.

> [!NOTE]
> Der Bearbeitungspuffer spielt beim Löschen von Aufzeichnungen keine Rolle. Wenn Sie den aktuellen Datensatz löschen, wird der Datensatz als gelöscht markiert, und das Recordset ist "nicht auf einem Datensatz", bis Sie zu einem anderen Datensatz scrollen.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets und Snapshots

[Dynasets](../../data/odbc/dynaset.md) aktualisieren den Inhalt eines Datensatzes, während Sie zum Datensatz scrollen. [Snapshots](../../data/odbc/snapshot.md) sind statische Darstellungen der Datensätze, sodass der Inhalt eines Datensatzes nur aktualisiert wird, wenn Sie [Requery](../../mfc/reference/crecordset-class.md#requery)aufrufen. Um alle Funktionen von Dynasets nutzen zu können, müssen Sie mit einem ODBC-Treiber arbeiten, der der richtigen Ebene der ODBC-API-Unterstützung entspricht. Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Funktionsweise von AddNew, Edit und Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
