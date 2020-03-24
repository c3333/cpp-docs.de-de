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
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212874"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset: Datensatzaktualisierung durch Recordsets (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Mit der Möglichkeit, Datensätze aus einer Datenquelle auszuwählen, können Recordsets (optional) die ausgewählten Datensätze aktualisieren oder löschen oder neue Datensätze hinzufügen. Drei Faktoren bestimmen die Aktualisierbarkeit eines Recordsets: gibt an, ob die verbundene Datenquelle aktualisierbar ist, welche Optionen Sie angeben, wenn Sie ein Recordset-Objekt erstellen, und die SQL-Datenbank, die erstellt wird.

> [!NOTE]
>  Der SQL-Server, auf dem das `CRecordset` Objekt basiert, kann die Aktualisierbarkeit Ihres Recordsets beeinflussen. Wenn Ihr SQL z. b. eine Join-oder **Group by** -Klausel enthält, legt MFC die Aktualisierbarkeit auf false fest.

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

In diesem Thema wird Folgendes erläutert:

- [Ihre Rolle beim Aktualisieren von Recordsets](#_core_your_role_in_recordset_updating) und die Funktionsweise des Frameworks.

- [Das Recordset als Bearbeitungs Puffer](#_core_the_edit_buffer) und die [Unterschiede zwischen Dynasets und Momentaufnahmen](#_core_dynasets_and_snapshots).

[Recordset: wie AddNew, Edit und delete work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) beschreibt die Aktionen dieser Funktionen aus der Sicht des Recordsets.

[Recordset: Weitere Informationen zu Aktualisierungen (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) schließt das Recordset-Update aus, indem erläutert wird, wie sich Transaktionen auf Updates auswirken, wie sich das Schließen eines Recordsets oder Bildlaufs auf aktuell ausgeführte Updates auswirkt und wie Ihre Updates mit den Updates anderer Benutzer interagieren.

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Ihre Rolle beim Aktualisieren von Recordsets

In der folgenden Tabelle wird die Rolle für die Verwendung von Recordsets zum Hinzufügen, bearbeiten oder Löschen von Datensätzen zusammen mit den Funktionen des Frameworks gezeigt.

### <a name="recordset-updating-you-and-the-framework"></a>Recordset-Aktualisierung: Sie und das Framework

|Sie|Das Framework|
|---------|-------------------|
|Bestimmen Sie, ob die Datenquelle aktualisierbar (oder angefügt) werden kann.|Stellt [CDatabase](../../mfc/reference/cdatabase-class.md) -Element Funktionen zum Testen der Aktualisierbarkeit oder der angehörbarkeit der Datenquelle bereit.|
|Öffnen Sie ein Aktualisier bares Recordset (beliebiger Typ).||
|Bestimmen Sie, ob das Recordset aktualisierbar ist, indem Sie `CRecordset` Update Funktionen aufrufen, z. b. `CanUpdate` oder `CanAppend`.||
|Ruft recordsetmember-Funktionen zum Hinzufügen, bearbeiten und Löschen von Datensätzen auf.|Verwaltet die Mechanismen zum Austauschen von Daten zwischen dem Recordset-Objekt und der Datenquelle.|
|Verwenden Sie optional Transaktionen, um den Aktualisierungsprozess zu steuern.|Stellt `CDatabase`-Element Funktionen zur Unterstützung von Transaktionen bereit.|

Weitere Informationen zu Transaktionen finden Sie unter [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Der Bearbeitungs Puffer

Zusammengefasst fungieren die Felddatenmember eines Recordsets als Bearbeitungs Puffer, der einen Datensatz enthält – den aktuellen Datensatz. Aktualisierungs Vorgänge verwenden diesen Puffer, um auf dem aktuellen Datensatz zu arbeiten.

- Wenn Sie einen Datensatz hinzufügen, wird der Bearbeitungs Puffer zum Erstellen eines neuen Datensatzes verwendet. Wenn Sie das Hinzufügen des Datensatzes abgeschlossen haben, wird der zuvor aktuelle Datensatz wieder aktuell.

- Wenn Sie einen Datensatz aktualisieren (Bearbeiten), wird der Bearbeitungs Puffer verwendet, um die Felddatenmember des Recordsets auf neue Werte festzulegen. Wenn Sie die Aktualisierung abgeschlossen haben, ist der aktualisierte Datensatz weiterhin aktuell.

Wenn Sie " [AddNew](../../mfc/reference/crecordset-class.md#addnew) " oder " [Edit](../../mfc/reference/crecordset-class.md#edit)" aufruft, wird der aktuelle Datensatz gespeichert, sodass er später nach Bedarf wieder hergestellt werden kann. Wenn Sie [Delete](../../mfc/reference/crecordset-class.md#delete)aufzurufen, wird der aktuelle Datensatz nicht gespeichert, aber als gelöscht markiert, und Sie müssen einen Bildlauf zu einem anderen Datensatz durchführen.

> [!NOTE]
>  Der Bearbeitungs Puffer spielt keine Rolle beim Löschen von Datensätzen. Wenn Sie den aktuellen Datensatz löschen, wird der Datensatz als gelöscht markiert, und das Recordset ist nicht in einem Datensatz, bis Sie einen Bildlauf zu einem anderen Datensatz durchführen.

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets und Momentaufnahmen

[Dynasets](../../data/odbc/dynaset.md) aktualisieren Sie den Inhalt eines Datensatzes, während Sie einen Bildlauf zum Datensatz durchführen. [Momentaufnahmen](../../data/odbc/snapshot.md) sind statische Darstellungen der Datensätze, sodass der Inhalt eines Datensatzes nur dann aktualisiert wird, wenn Sie " [Requery](../../mfc/reference/crecordset-class.md#requery)" aufgerufen haben. Um die gesamte Funktionalität von Dynasets zu nutzen, müssen Sie mit einem ODBC-Treiber arbeiten, der der richtigen Ebene der ODBC-API-Unterstützung entspricht. Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Funktionsweise von AddNew, Edit und Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
