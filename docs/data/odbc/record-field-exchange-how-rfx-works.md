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
ms.openlocfilehash: 0661e61bceeedc0dd049ef47f5a0a0b71a8d82ed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213069"
---
# <a name="record-field-exchange-how-rfx-works"></a>Datensatzfeldaustausch: Funktionsweise von RFX

In diesem Thema wird der RFX-Prozess erläutert. Dies ist ein erweitertes Thema, das Folgendes behandelt:

- [RFX und das Recordset](#_core_rfx_and_the_recordset)

- [Der RFX-Prozess](#_core_the_record_field_exchange_process)

> [!NOTE]
>  Dieses Thema bezieht sich auf aus `CRecordset` abgeleitete Klassen, in denen gesammeltes Abrufen (Massenabrufen) von Zeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX und das Recordset

Die Felddatenmember des Recordset-Objekts bilden zusammen einen Bearbeitungs Puffer, der die ausgewählten Spalten eines Datensatzes enthält. Wenn das Recordset zum ersten Mal geöffnet wird und im Begriff ist, den ersten Datensatz zu lesen, bindet RFX jede ausgewählte Spalte an die Adresse des entsprechenden Felddatenmembers. Wenn das Recordset einen Datensatz aktualisiert, ruft RFX ODBC-API-Funktionen auf, um eine SQL **Update** -oder **Insert** -Anweisung an den Treiber zu senden. RFX verwendet seine Kenntnisse der Felddatenmember, um die zu schreibenden Spalten anzugeben.

Das Framework sichert den Bearbeitungs Puffer in bestimmten Phasen, damit dessen Inhalt bei Bedarf wieder hergestellt werden kann. RFX sichert vor dem Hinzufügen eines neuen Datensatzes und vor der Bearbeitung eines vorhandenen Datensatzes den Bearbeitungs Puffer. Der Bearbeitungs Puffer wird in einigen Fällen wieder hergestellt, z. b. nach einem `Update`-Rückruf nach `AddNew`. Der Bearbeitungs Puffer wird nicht wieder hergestellt, wenn Sie einen neu geänderten Bearbeitungs Puffer verwerfen, indem Sie z. b. in einen anderen Datensatz verschieben, bevor Sie `Update`aufrufen.

Neben dem Austauschen von Daten zwischen der Datenquelle und den Felddatenmembern des Recordsets werden die Bindungs Parameter von RFX verwaltet. Wenn das Recordset geöffnet wird, werden alle Parameter Datenmember in der Reihenfolge der "?"-Platzhalter in der SQL-Anweisung gebunden, die `CRecordset::Open` Konstrukte. Weitere Informationen finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Die außer Kraft setzung der Recordset-Klasse von `DoFieldExchange` führt alle Aufgaben durch und verschiebt Daten in beide Richtungen. Wie beim Dialog Datenaustausch (DDX) benötigt RFX Informationen zu den Datenmembern ihrer Klasse. Der Assistent stellt die erforderlichen Informationen bereit, indem er eine recordsetspezifische Implementierung der `DoFieldExchange` für Sie basierend auf den Felddatenmember-Namen und Datentypen schreibt, die Sie mit dem Assistenten angeben.

##  <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Prozess für Daten Satz Feld Austausch

In diesem Abschnitt wird die Abfolge von RFX-Ereignissen beschrieben, wenn ein Recordset-Objekt geöffnet wird und Sie Datensätze hinzufügen, aktualisieren und löschen. Die Tabellen [Sequenz von RFX-Vorgängen beim Öffnen von Recordset](#_core_sequence_of_rfx_operations_during_recordset_open) und die Tabellen [Sequenz von RFX-Vorgängen während des Bildlaufs](#_core_sequence_of_rfx_operations_during_scrolling) in diesem Thema zeigen den Prozess, bei dem RFX einen `Move` Befehl im Recordset verarbeitet und ein Update von RFX verwaltet wird. Während dieser Prozesse wird [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) aufgerufen, um viele verschiedene Vorgänge auszuführen. Der `m_nOperation` Datenmember des [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) -Objekts bestimmt, welcher Vorgang angefordert wird. Möglicherweise ist es hilfreich, [Recordset zu lesen: Wie Recordsets Datensätze (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) und [Recordset auswählen: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) , bevor Sie dieses Material lesen.

###  <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: anfängliche Bindung von Spalten und Parametern

Die folgenden RFX-Aktivitäten treten in der angezeigten Reihenfolge auf, wenn Sie die [Open](../../mfc/reference/crecordset-class.md#open) -Member-Funktion eines Recordset-Objekts aufzurufen:

- Wenn das Recordset Parameter Datenmember enthält, ruft das Framework `DoFieldExchange` auf, um die Parameter an die Parameter Platzhalter in der SQL-Anweisungs Zeichenfolge des Recordsets zu binden. Eine Datentyp abhängige Darstellung des Werts des-Parameters wird für jeden in der **Select** -Anweisung gefundenen Platzhalter verwendet. Dies tritt auf, nachdem die SQL-Anweisung vorbereitet wurde, aber bevor Sie ausgeführt wird. Weitere Informationen zur Anweisungs Vorbereitung finden Sie in der `::SQLPrepare`-Funktion in der ODBC *Programmer es Reference*.

- Das Framework ruft `DoFieldExchange` ein zweites Mal auf, um die Werte ausgewählter Spalten an die entsprechenden Felddatenmember im Recordset zu binden. Dadurch wird das Recordset-Objekt als Bearbeitungs Puffer festgelegt, der die Spalten des ersten Datensatzes enthält.

- Das Recordset führt die SQL-Anweisung aus, und die Datenquelle wählt den ersten Datensatz aus. Die Spalten des Datensatzes werden in die Felddatenmember des Recordsets geladen.

In der folgenden Tabelle wird die Abfolge der RFX-Vorgänge beim Öffnen eines Recordsets angezeigt.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Abfolge von RFX-Vorgängen beim Öffnen des Recordsets

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Database/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. Öffnen Sie das Recordset.|||
||2. Erstellen Sie eine SQL-Anweisung.||
|||3. senden Sie den SQL-Server.|
||4. binden Sie Parameter Datenmember.||
||5. binden Sie Felddatenmember an Spalten.||
|||6. ODBC führt die Verschiebung durch und füllt die Daten aus.|
||7. beheben Sie die Daten für C++.||

Recordsets verwenden die vorbereitete ODBC-Ausführung, um eine schnelle Anforderung mit derselben SQL-Anweisung zuzulassen. Weitere Informationen zur vorbereiteten Ausführung finden Sie in der ODBC SDK *-Programmier Referenz* in der MSDN Library.

###  <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Scrollen

Wenn Sie einen Bildlauf von einem Datensatz zu einem anderen durchführen, ruft das Framework `DoFieldExchange` auf, um die zuvor in den Felddatenmembern gespeicherten Werte durch Werte für den neuen Datensatz zu ersetzen.

In der folgenden Tabelle wird die Abfolge von RFX-Vorgängen angezeigt, wenn der Benutzer vom Datensatz in den Datensatz wechselt.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Abfolge von RFX-Vorgängen beim Scrollen

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Database/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` oder eine der anderen Verschiebungs Funktionen aufzurufen.|||
|||2. ODBC führt die Verschiebung durch und füllt die Daten aus.|
||3. beheben Sie die Daten für C++.||

###  <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Hinzufügen neuer Datensätze und Bearbeiten vorhandener Datensätze

Wenn Sie einen neuen Datensatz hinzufügen, wird das Recordset als Bearbeitungs Puffer betrieben, um den Inhalt des neuen Datensatzes zu erstellen. Wie beim Hinzufügen von Datensätzen umfasst das Bearbeiten von Datensätzen das Ändern der Werte der Felddatenmember des Recordsets. Aus der RFX-Sicht sieht die Sequenz wie folgt aus:

1. Wenn Sie die Funktion [AddNew](../../mfc/reference/crecordset-class.md#addnew) oder [Edit](../../mfc/reference/crecordset-class.md#edit) Member des Recordsets aufzurufen, speichert RFX den aktuellen Bearbeitungs Puffer, sodass er später wieder hergestellt werden kann.

1. `AddNew` oder `Edit` bereitet die Felder im Bearbeitungs Puffer vor, damit RFX geänderte Felddatenmember erkennen kann.

   Da ein neuer Datensatz keine vorherigen Werte aufweist, mit denen neue Werte verglichen werden, legt `AddNew` den Wert der einzelnen Felddatenmember auf einen PSEUDO_NULL Wert fest. Wenn Sie später `Update`aufzurufen, vergleicht RFX den Wert jedes Datenmembers mit dem PSEUDO_NULL Wert. Wenn es einen Unterschied gibt, wurde das Datenmember festgelegt. (PSEUDO_NULL ist nicht mit einer Daten Satz Spalte identisch, bei der es sich C++ um einen true-NULL-Wert handelt.

   Im Gegensatz zum `Update`-Aufrufe für `AddNew`vergleicht der `Update`-Befehl für `Edit` aktualisierte Werte mit zuvor gespeicherten Werten, anstatt PSEUDO_NULL zu verwenden. Der Unterschied besteht darin, dass `AddNew` zuvor keine Werte für den Vergleich enthält.

1. Sie legen die Werte von Felddatenmembern, deren Werte Sie bearbeiten möchten oder die Sie für einen neuen Datensatz ausfüllen möchten, direkt fest. Dies kann das Aufrufen von `SetFieldNull`einschließen.

1. Ihr [Aktualisierungs Update](../../mfc/reference/crecordset-class.md#update) überprüft, wie in Schritt 2 beschrieben (siehe die Tabellen [Sequenz von RFX-Vorgängen während des Bildlaufs](#_core_sequence_of_rfx_operations_during_scrolling)). Wenn keine Änderungen vorgenommen wurden, gibt `Update` 0 zurück. Wenn sich einige Felddatenmember geändert haben, `Update` eine SQL **Insert** -Anweisung vorbereitet und ausgeführt, die Werte für alle aktualisierten Felder im Datensatz enthält.

1. Für `AddNew`wird `Update` beendet, indem die zuvor gespeicherten Werte des Datensatzes wieder hergestellt werden, der vor dem `AddNew` aufgerufen wurde. Bei `Edit`bleiben die neuen, bearbeiteten Werte bestehen.

In der folgenden Tabelle wird die Abfolge von RFX-Vorgängen angezeigt, wenn Sie einen neuen Datensatz hinzufügen oder einen vorhandenen Datensatz bearbeiten.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Abfolge von RFX-Vorgängen während AddNew und Edit

|Bei Ihrem Vorgang|DoFieldExchange-Vorgang|Database/SQL-Vorgang|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` oder `Edit`aufgerufen.|||
||2. Sichern Sie den Bearbeitungs Puffer.||
||3. Markieren Sie für `AddNew`Felddatenmember als "Clean" und NULL.||
|4. weisen Sie den Recordset-Felddatenmembern Werte zu.|||
|5. `Update`abrufen.|||
||6. Überprüfen Sie die geänderten Felder.||
||7. Erstellen einer SQL- **Insert** -Anweisung für eine `AddNew`-oder **Update** -Anweisung für `Edit`.||
|||8. senden Sie den SQL-Server.|
||9. Stellen Sie für `AddNew`den Bearbeitungs Puffer in seinem gesicherten Inhalt wieder her. Löschen Sie die Sicherung für `Edit`.||

### <a name="rfx-deleting-existing-records"></a>RFX: Löschen vorhandener Datensätze

Wenn Sie einen Datensatz löschen, werden alle Felder von RFX als Erinnerung auf NULL festgelegt, um zu vergessen, dass der Datensatz gelöscht wurde, und Sie müssen ihn entfernen. Sie benötigen keine weiteren RFX-Sequenz Informationen.

## <a name="see-also"></a>Weitere Informationen

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
