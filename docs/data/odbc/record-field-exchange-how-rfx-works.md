---
title: 'Datensatzfeldaustausch: Funktionsweise von RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367170"
---
# <a name="record-field-exchange-how-rfx-works"></a>Datensatzfeldaustausch: Funktionsweise von RFX

In diesem Thema wird der RFX-Prozess erläutert. Dies ist ein fortgeschrittenes Thema, das Folgendes abdeckt:

- [RFX und das Recordset](#_core_rfx_and_the_recordset)

- [Der RFX-Prozess](#_core_the_record_field_exchange_process)

> [!NOTE]
> Dieses Thema bezieht sich auf aus `CRecordset` abgeleitete Klassen, in denen gesammeltes Abrufen (Massenabrufen) von Zeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX und das Recordset

Die Felddatenmember des Recordset-Objekts bilden zusammen genommen einen Bearbeitungspuffer, der die ausgewählten Spalten eines Datensatzes enthält. Wenn das Recordset zum ersten Mal geöffnet wird und den ersten Datensatz lesen soll, bindet RFX jede ausgewählte Spalte an die Adresse des entsprechenden Felddatenelements. Wenn das Recordset einen Datensatz aktualisiert, ruft RFX ODBC-API-Funktionen auf, um eine SQL **UPDATE-** oder **INSERT-Anweisung** an den Treiber zu senden. RFX verwendet seine Kenntnisse der Felddatenmember, um die zu schreibenden Spalten anzugeben.

Das Framework sichert den Bearbeitungspuffer in bestimmten Phasen, sodass der Inhalt bei Bedarf wiederhergestellt werden kann. RFX unterstützt den Bearbeitungspuffer, bevor ein neuer Datensatz hinzugefügt und ein vorhandener Datensatz bearbeitet wird. In einigen Fällen wird der Bearbeitungspuffer wiederhergestellt, z. B. nach einem `Update` Aufruf nach `AddNew`. Der Bearbeitungspuffer wird nicht wiederhergestellt, wenn Sie einen neu geänderten Bearbeitungspuffer `Update`aufgeben, indem Sie z. B. vor dem Aufruf zu einem anderen Datensatz wechseln.

Neben dem Datenaustausch zwischen der Datenquelle und den Felddatenmembern des Recordsets verwaltet RFX Bindungsparameter. Wenn das Recordset geöffnet wird, werden alle Parameterdatenmember in der Reihenfolge der `CRecordset::Open` "?"-Platzhalter in der SQL-Anweisung gebunden, die erstellt wird. Weitere Informationen finden Sie unter [Recordset: Parametrieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Die Außerkraftsetzung der `DoFieldExchange` Recordset-Klasse durch die Recordset-Klasse führt alle Arbeiten aus und verschiebt Daten in beide Richtungen. Wie Dialogdatenaustausch (DDX) benötigt RFX Informationen über die Datenmember Ihrer Klasse. Der Assistent stellt die erforderlichen Informationen bereit, `DoFieldExchange` indem er eine Recordset-spezifische Implementierung für Sie schreibt, basierend auf den Felddatenmembernamen und Datentypen, die Sie mit dem Assistenten angeben.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Datensatzfeldaustauschprozess

In diesem Abschnitt wird die Reihenfolge der RFX-Ereignisse beschrieben, wenn ein Recordset-Objekt geöffnet wird und datensätze hinzugefügt, aktualisiert und gelöscht werden. Die Tabelle [Sequenz von RFX-Operationen während Der Recordset-Öffnung](#_core_sequence_of_rfx_operations_during_recordset_open) und die Tabelle [Sequenz von RFX-Operationen während des Scrollens](#_core_sequence_of_rfx_operations_during_scrolling) in diesem Thema zeigen den Prozess, wie RFX einen `Move` Befehl im Recordset verarbeitet und als RFX ein Update verwaltet. Während dieser Prozesse wird [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) aufgerufen, um viele verschiedene Vorgänge auszuführen. Das `m_nOperation` Datenmember des [CFieldExchange-Objekts](../../mfc/reference/cfieldexchange-class.md) bestimmt, welcher Vorgang angefordert wird. Es könnte hilfreich sein, [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) und [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) zu lesen, bevor Sie dieses Material lesen.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Anfängliche Bindung von Spalten und Parametern

Die folgenden RFX-Aktivitäten treten in der angezeigten Reihenfolge auf, wenn Sie die [Open-Memberfunktion](../../mfc/reference/crecordset-class.md#open) eines Recordset-Objekts aufrufen:

- Wenn das Recordset Über Parameterdatenmember `DoFieldExchange` verfügt, ruft das Framework auf, um die Parameter an Parameterplatzhalter in der SQL-Anweisungszeichenfolge des Recordsets zu binden. Für jeden Platzhalter, der in der **SELECT-Anweisung** gefunden wird, wird eine datentypabhängige Darstellung des Parameters verwendet. Dies geschieht, nachdem die SQL-Anweisung vorbereitet wurde, aber bevor sie ausgeführt wird. Informationen zur Anweisungsvorbereitung `::SQLPrepare` finden Sie in der Funktion in der *ODBC-Programmiererreferenz*.

- Das Framework `DoFieldExchange` ruft ein zweites Mal auf, um die Werte ausgewählter Spalten an die entsprechenden Felddatenmember im Recordset zu binden. Dadurch wird das Recordset-Objekt als Bearbeitungspuffer eingerichtet, der die Spalten des ersten Datensatzes enthält.

- Das Recordset führt die SQL-Anweisung aus, und die Datenquelle wählt den ersten Datensatz aus. Die Spalten des Datensatzes werden in die Felddatenmember des Recordsets geladen.

Die folgende Tabelle zeigt die Reihenfolge der RFX-Vorgänge beim Öffnen eines Recordsets.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Sequenz der RFX-Operationen während Der Recordset-Eröffnung

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Datenbank-/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. Öffnen Sie Recordset.|||
||2. Erstellen Sie eine SQL-Anweisung.||
|||3. Senden Sie die SQL.|
||4. Binden Sie Parameterdatenmember.||
||5. Binden Sie Felddatenelemente an Spalten.||
|||6. ODBC macht die Verschiebung und füllt die Daten aus.|
||7. Befestigen Sie die Daten für C++.||

Recordsets verwenden die vorbereitete Ausführung von ODBC, um eine schnelle erneute Abfrage mit derselben SQL-Anweisung zu ermöglichen. Weitere Informationen zur vorbereiteten Ausführung finden Sie in der *ODBC SDK-Programmiererreferenz* in der MSDN-Bibliothek.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Scrollen

Wenn Sie von einem Datensatz zu `DoFieldExchange` einem anderen scrollen, ruft das Framework auf, um die zuvor in den Felddatenmembern gespeicherten Werte durch Werte für den neuen Datensatz zu ersetzen.

Die folgende Tabelle zeigt die Reihenfolge der RFX-Vorgänge, wenn der Benutzer von Datensatz zu Datensatz wechselt.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Sequenz der RFX-Operationen während des Scrollens

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Datenbank-/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Rufen Sie eine der anderen Move-Funktionen auf.|||
|||2. ODBC macht die Verschiebung und füllt die Daten aus.|
||3. Korrigieren Sie die Daten für C++.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Hinzufügen neuer Datensätze und Bearbeiten vorhandener Datensätze

Wenn Sie einen neuen Datensatz hinzufügen, dient das Recordset als Bearbeitungspuffer, um den Inhalt des neuen Datensatzes aufzubauen. Wie beim Hinzufügen von Datensätzen umfasst das Bearbeiten von Datensätzen das Ändern der Werte der Felddatenmember des Recordsets. Aus RFX-Sicht ist die Reihenfolge wie folgt:

1. Wenn Sie die [AddNew-](../../mfc/reference/crecordset-class.md#addnew) oder [Edit-Memberfunktion](../../mfc/reference/crecordset-class.md#edit) des Recordsets aufrufen, wird rFX den aktuellen Bearbeitungspuffer gespeichert, damit er später wiederhergestellt werden kann.

1. `AddNew`oder `Edit` bereitet die Felder im Bearbeitungspuffer vor, damit RFX geänderte Felddatenmember erkennen kann.

   Da ein neuer Datensatz keine vorherigen Werte zum `AddNew` Vergleichen neuer Werte enthält, wird der Wert jedes Felddatenelements auf einen PSEUDO_NULL Wert festgelegt. Später, wenn `Update`Sie aufrufen, vergleicht RFX den Wert jedes Datenmembers mit dem wert PSEUDO_NULL. Wenn es einen Unterschied gibt, wurde das Datenelement festgelegt. (PSEUDO_NULL nicht mit einer Datensatzspalte mit einem echten Nullwert identisch ist, noch ist eine dieser Beiden mit C++ NULL identisch.)

   Im `Update` Gegensatz `AddNew`zum `Update` Aufruf `Edit` für vergleicht der Aufruf für aktualisierte Werte mit zuvor gespeicherten Werten, anstatt PSEUDO_NULL zu verwenden. Der Unterschied `AddNew` besteht darin, dass zuvor keine Werte zum Vergleich gespeichert wurden.

1. Sie legen direkt die Werte von Felddatenelementen fest, deren Werte Sie bearbeiten oder die für einen neuen Datensatz ausgefüllt werden sollen. Dies kann `SetFieldNull`auch den Aufruf von umfassen.

1. Ihr Aufruf an [Update](../../mfc/reference/crecordset-class.md#update) prüft nach geänderten Felddatenmembern, wie in Schritt 2 beschrieben (siehe Tabelle [Sequenz der RFX-Vorgänge während des Scrollens](#_core_sequence_of_rfx_operations_during_scrolling)). Wenn sich keine `Update` geändert hat, wird 0 zurückgegeben. Wenn sich einige Felddatenmember geändert haben, `Update` wird eine SQL **INSERT-Anweisung** vorbereitet und ausgeführt, die Werte für alle aktualisierten Felder im Datensatz enthält.

1. Für schließt sie mit der Wiederherstellung der zuvor gespeicherten Werte des Datensatzes, der vor dem `AddNew` Aufruf aktuell war. `AddNew` `Update` Für `Edit`bleiben die neuen, bearbeiteten Werte erhalten.

Die folgende Tabelle zeigt die Reihenfolge der RFX-Vorgänge, wenn Sie einen neuen Datensatz hinzufügen oder einen vorhandenen Datensatz bearbeiten.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Reihenfolge der RFX-Operationen während AddNew und Edit

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Datenbank-/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Rufen `Edit`Sie an oder .|||
||2. Sichern Sie den Bearbeitungspuffer.||
||3. `AddNew`Markieren Sie für Felddatenmember als "sauber" und Null.||
|4. Weisen Sie Den Datensatzfelddatenelementen Werte zu.|||
|5. `Update`Rufen Sie an.|||
||6. Überprüfen Sie, ob die Felder geändert wurden.||
||7. Erstellen Sie `AddNew` die SQL `Edit` **INSERT-Anweisung** für oder die **UPDATE-Anweisung** für .||
|||8. Senden Sie die SQL.|
||9. `AddNew`Stellen Sie für den Bearbeitungspuffer in seinem gesicherten Inhalt wieder her. Löschen `Edit`Sie für die Sicherung.||

### <a name="rfx-deleting-existing-records"></a>RFX: Löschen vorhandener Datensätze

Wenn Sie einen Datensatz löschen, legt RFX alle Felder auf NULL fest, um daran zu erinnern, dass der Datensatz gelöscht wird und Sie ihn entfernen müssen. Sie benötigen keine weiteren RFX-Sequenzinformationen.

## <a name="see-also"></a>Siehe auch

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
