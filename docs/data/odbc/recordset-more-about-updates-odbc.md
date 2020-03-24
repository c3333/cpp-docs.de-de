---
title: 'Recordset: Weitere Informationen zu Aktualisierungen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: f11c723e4589cb28a3f38100050a69a78fc0809e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212848"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset: Weitere Informationen zu Aktualisierungen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Wie andere Vorgänge, wie z. b. Transaktionen, Auswirkungen auf Updates haben](#_core_how_transactions_affect_updates).

- [Ihre Updates und die anderen Benutzer](#_core_your_updates_and_the_updates_of_other_users).

- [Weitere Informationen zu den Funktionen zum Aktualisieren und Löschen von](#_core_more_about_update_and_delete)Membern.

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, sind einige der Informationen nicht anwendbar. Beispielsweise können Sie die Funktionen `AddNew`, `Edit`, `Delete`und `Update` Member nicht aufzurufen. Sie können jedoch Transaktionen ausführen. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Auswirkungen anderer Vorgänge auf Updates

Ihre Aktualisierungen werden von Transaktionen beeinflusst, die zum Zeitpunkt des Updates wirksam sind, indem das Recordset vor dem Abschließen einer Transaktion geschlossen wird, und durch einen Bildlauf vor dem Abschließen einer Transaktion.

###  <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Auswirkungen von Transaktionen auf Aktualisierungen

Wenn Sie wissen, wie `AddNew`, `Edit`und `Delete` funktionieren, ist es wichtig zu verstehen, wie die `BeginTrans`-, `CommitTrans`-und `Rollback` Member-Funktionen von [CDatabase](../../mfc/reference/cdatabase-class.md) mit den Update Funktionen von [CRecordset](../../mfc/reference/crecordset-class.md)funktionieren.

Standardmäßig wirken sich Aufrufe von `AddNew` und `Edit` sofort auf die Datenquelle aus, wenn Sie `Update`aufrufen. `Delete` Aufrufe treten sofort in Kraft. Sie können jedoch eine Transaktion einrichten und einen Batch solcher Aufrufe ausführen. Die Updates sind erst permanent, wenn Sie einen Commit für Sie durchlaufen. Wenn Sie Ihre Meinung ändern, können Sie für die Transaktion ein Rollback ausführen, anstatt Sie zu committen.

Weitere Informationen zu Transaktionen finden Sie unter [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Auswirkungen der Schließung des Recordsets auf Updates

Wenn Sie ein Recordset oder das zugeordnete `CDatabase` Objekt schließen, während eine Transaktion ausgeführt wird (Sie haben nicht [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) oder [CDatabase:: Rollback](../../mfc/reference/cdatabase-class.md#rollback)aufgerufen), wird für die Transaktion automatisch ein Rollback ausgeführt (es sei denn, das Datenbank-Back-End ist die Microsoft Jet-Datenbank-Engine).

> [!CAUTION]
>  Wenn Sie die Microsoft Jet-Datenbank-Engine verwenden, führt das Schließen eines Recordsets innerhalb einer expliziten Transaktion nicht dazu, dass die geänderten Zeilen oder sperren, die für die explizite Transaktion oder das Rollback der expliziten Transaktion platziert wurden, freigegeben werden. Es wird empfohlen, Recordsets immer innerhalb oder außerhalb einer expliziten Jet-Transaktion zu öffnen und zu schließen.

###  <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Auswirkungen des Bildlaufs auf Updates

Wenn Sie [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) in einem Recordset ausführen, wird der Bearbeitungs Puffer mit jedem neuen aktuellen Datensatz gefüllt (der vorherige Datensatz wird zuerst nicht gespeichert). Beim Scrollen werden die zuvor gelöschten Datensätze überspringt. Wenn Sie nach einem `AddNew` oder `Edit` Aufruf scrollen, ohne `Update`, `CommitTrans`oder `Rollback` aufzurufen, gehen alle Änderungen verloren (ohne Warnung), da ein neuer Datensatz in den Bearbeitungs Puffer eingefügt wird. Der Bearbeitungs Puffer wird mit dem Datensatz, in dem ein Bildlauf durchgeführt wurde, aufgefüllt, der gespeicherte Datensatz wird freigegeben, und es erfolgt keine Änderung in der Datenquelle. Dies gilt für `AddNew` und `Edit`.

##  <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Ihre Updates und Updates anderer Benutzer

Wenn Sie ein Recordset zum Aktualisieren von Daten verwenden, wirken sich die Updates auf andere Benutzer aus. Ebenso wirken sich die Aktualisierungen anderer Benutzer während der Lebensdauer des Recordsets auf Sie aus.

In einer mehr Benutzerumgebung können andere Benutzer Recordsets öffnen, die einige der gleichen Datensätze enthalten, die Sie in Ihrem Recordset ausgewählt haben. Änderungen an einem Datensatz, bevor Sie ihn abrufen, werden in Ihrem Recordset widergespiegelt. Da Dynasets jedes Mal, wenn Sie einen Bildlauf durchführen, einen Datensatz abrufen, spiegeln Dynasets bei jedem Bildlauf zu einem Datensatz Änderungen wider. Momentaufnahmen rufen einen Datensatz ab, wenn Sie zum ersten Mal einen Bildlauf durchführen, sodass Momentaufnahmen nur die Änderungen widerspiegeln, die vor dem ersten Bildlauf zum Datensatz stattfinden.

Datensätze, die nach dem Öffnen des Recordsets von anderen Benutzern hinzugefügt wurden, werden nicht in Ihrem Recordset angezeigt, es sei denn, Sie Fragen sich. Wenn Ihr Recordset ein Dynaset ist, werden Änderungen an vorhandenen Datensätzen durch andere Benutzer in Ihrem Dynaset angezeigt, wenn Sie einen Bildlauf zum betroffenen Datensatz durchführen. Wenn Ihr Recordset eine Momentaufnahme ist, werden Änderungen erst angezeigt, wenn Sie die Momentaufnahme angefordert haben. Wenn Sie Datensätze anzeigen möchten, die von anderen Benutzern in der Momentaufnahme hinzugefügt oder gelöscht wurden, oder Datensätze, die von anderen Benutzern im Dynaset hinzugefügt wurden, können Sie [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) zum erneuten Erstellen des Recordsets abrufen. (Beachten Sie, dass die Löschungen anderer Benutzer in Ihrem Dynaset angezeigt werden.) Sie können auch `Requery` aufrufen, um Datensätze anzuzeigen, die Sie hinzufügen, aber nicht, um die Löschungen anzuzeigen.

> [!TIP]
>  Um das Zwischenspeichern einer vollständigen Momentaufnahme gleichzeitig zu erzwingen, müssen Sie `MoveLast` sofort nach dem Öffnen der Momentaufnahme anrufen. Wenden Sie dann `MoveFirst` an, um mit den Datensätzen zu arbeiten. `MoveLast` entspricht dem Scrollen über alle Datensätze, ruft Sie aber alle gleichzeitig ab. Beachten Sie jedoch, dass dies die Leistung verringern kann und für einige Treiber möglicherweise nicht erforderlich ist.

Die Auswirkungen ihrer Updates auf andere Benutzer ähneln ihren Auswirkungen auf Sie.

##  <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Weitere Informationen zu Update und DELETE

Dieser Abschnitt enthält zusätzliche Informationen, die Ihnen bei der Arbeit mit `Update` und `Delete`helfen.

### <a name="update-success-and-failure"></a>Erfolgreiche und fehlgeschlagene Updates

Wenn `Update` erfolgreich ist, wird der `AddNew`-oder `Edit` Modus beendet. Um erneut einen `AddNew` oder `Edit`-Modus zu starten, müssen Sie `AddNew` oder `Edit`aufzurufen.

Wenn `Update` fehlschlägt (gibt false zurück oder löst eine Ausnahme aus), verbleiben Sie in `AddNew` oder `Edit` Modus, je nachdem, welche Funktion Sie zuletzt aufgerufen haben. Sie können dann einen der folgenden Schritte ausführen:

- Ändern Sie einen Felddatenmember, und wiederholen Sie den `Update`.

- Ruft `AddNew` auf, um die Felddatenmember auf NULL zurückzusetzen, die Werte der Felddatenmember festzulegen und `Update` erneut aufzurufen.

- Ruft `Edit` auf, um die Werte des Recordsets vor dem ersten `AddNew` oder `Edit`zu laden, die Werte der Felddatenmember festzulegen und dann `Update` erneut aufzurufen. Nach einem erfolgreichen `Update`-Aufruf(außer nach einem `AddNew`-Aufrufvorgang) behalten die Felddatenmember ihre neuen Werte bei.

- Aufrufen `Move` (einschließlich `Move` mit einem Parameter von AFX_MOVE_REFRESH oder 0), der alle Änderungen leert und alle im Endeffekt `AddNew` oder `Edit` Modus beendet.

### <a name="update-and-delete"></a>Aktualisieren und löschen

Dieser Abschnitt gilt für `Update` und `Delete`.

Bei einem `Update`-oder `Delete` Vorgang sollte nur ein Datensatz aktualisiert werden. Dieser Datensatz ist der aktuelle Datensatz, der den Datenwerten in den Feldern des Recordsets entspricht. Wenn aus irgendeinem Grund keine Datensätze betroffen sind oder mehr als ein Datensatz betroffen ist, wird eine Ausnahme ausgelöst, die einen der folgenden **retcodewerte** enthält:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Wenn diese Ausnahmen ausgelöst werden, verbleiben Sie in der `AddNew` oder `Edit` Zustand, in dem Sie sich befanden, als Sie `Update` oder `Delete`aufgerufen haben. Im folgenden finden Sie die gängigsten Szenarien, in denen diese Ausnahmen angezeigt werden. Sie sehen höchstwahrscheinlich Folgendes:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, wenn Sie den Modus für optimistische Sperren verwenden und ein anderer Benutzer den Datensatz auf eine Weise geändert hat, die verhindert, dass das Framework den richtigen Datensatz identifiziert, der aktualisiert oder gelöscht werden soll.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, wenn die zu aktualisierbare Tabelle keinen Primärschlüssel oder eindeutigen Index aufweist und Sie nicht über genügend Spalten im Recordset verfügen, um eine Tabellenzeile eindeutig zu identifizieren.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Wie Recordsets Datensätze auswählen (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Ausnahmen: Datenbankausnahmen](../../mfc/exceptions-database-exceptions.md)
