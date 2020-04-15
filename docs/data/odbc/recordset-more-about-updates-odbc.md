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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368674"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset: Weitere Informationen zu Aktualisierungen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Wie sich andere Vorgänge, z. B. Transaktionen, auf Aktualisierungen auswirken.](#_core_how_transactions_affect_updates)

- [Ihre Updates und die anderer Benutzer](#_core_your_updates_and_the_updates_of_other_users).

- [Weitere Informationen zu den Mitgliedsfunktionen Aktualisieren und Löschen](#_core_more_about_update_and_delete).

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Abrufen von Massenzeilen implementiert haben, gelten einige der Informationen nicht. Sie können z. `AddNew`B. `Delete`die `Update` Funktionen , `Edit`, und Member nicht aufrufen. Sie können jedoch Transaktionen durchführen. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Auswirkungen anderer Vorgänge auf Updates

Ihre Aktualisierungen werden von Transaktionen beeinflusst, die zum Zeitpunkt der Aktualisierung wirksam waren, indem Sie das Recordset schließen, bevor eine Transaktion abgeschlossen wird, und durch Scrollen vor Abschluss einer Transaktion.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Auswirkungen von Transaktionen auf Aktualisierungen

Neben dem `AddNew` `Edit`Verständnis, `Delete` wie , und arbeiten, `BeginTrans` `CommitTrans`ist `Rollback` es wichtig zu verstehen, wie die , und Memberfunktionen von [CDatabase](../../mfc/reference/cdatabase-class.md) mit den Aktualisierungsfunktionen von [CRecordset](../../mfc/reference/crecordset-class.md)arbeiten.

Standardmäßig wird die `AddNew` `Edit` Datenquelle sofort beim Aufrufen `Update`von aufrufen und beeinflusst. `Delete`Anrufe sofort wirksam werden. Sie können jedoch eine Transaktion einrichten und einen Batch solcher Aufrufe ausführen. Die Aktualisierungen sind erst dann dauerhaft, wenn Sie sie festsetzen. Wenn Sie Ihre Meinung ändern, können Sie die Transaktion zurücksetzen, anstatt sie zu übertragen.

Weitere Informationen zu Transaktionen finden Sie unter [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>So wirkt sich das Schließen des Recordsets auf Updates aus

Wenn Sie ein Recordset oder `CDatabase` das zugehörige Objekt mit einer laufenden Transaktion schließen (Sie haben [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) oder [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)nicht aufgerufen), wird die Transaktion automatisch zurückgesetzt (es sei denn, Ihr Datenbank-Backend ist das Microsoft Jet-Datenbankmodul).

> [!CAUTION]
> Wenn Sie das Microsoft Jet-Datenbankmodul verwenden, führt das Schließen eines Recordsets innerhalb einer expliziten Transaktion nicht dazu, dass eine der geänderten Zeilen oder Sperren freigegeben wird, die so lange platziert wurden, bis die explizite Transaktion festgeschrieben oder zurückgesetzt wurde. Es wird empfohlen, Recordsets innerhalb oder außerhalb einer expliziten Jet-Transaktion immer zu öffnen und zu schließen.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Auswirkungen auf das Scrollen von Updates

Wenn Sie [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) in einem Recordset durchführen, wird der Bearbeitungspuffer mit jedem neuen aktuellen Datensatz gefüllt (der vorherige Datensatz wird nicht zuerst gespeichert). Beim Scrollen werden zuvor gelöschte Datensätze übersprungen. Wenn Sie nach `AddNew` `Edit` einem Oder-Aufruf ohne Aufruf `Update`von , `CommitTrans`oder `Rollback` zuerst scrollen, gehen alle Änderungen verloren (ohne Warnung für Sie), da ein neuer Datensatz in den Bearbeitungspuffer eingefügt wird. Der Bearbeitungspuffer wird mit dem Datensatz gefüllt, zu dem gescrollt wird, der gespeicherte Datensatz wird freigegeben, und an der Datenquelle wird keine Änderung durchgeführt. Dies gilt für `AddNew` und `Edit`.

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Ihre Updates und Updates anderer Benutzer

Wenn Sie ein Recordset zum Aktualisieren von Daten verwenden, wirken sich Ihre Aktualisierungen auf andere Benutzer aus. Ebenso wirken sich die Aktualisierungen anderer Benutzer während der Lebensdauer des Recordsets auf Sie aus.

In einer Mehrbenutzerumgebung können andere Benutzer Recordsets öffnen, die einige der gleichen Datensätze enthalten, die Sie in Ihrem Recordset ausgewählt haben. Änderungen an einem Datensatz, bevor Sie ihn abrufen, werden in Ihrem Recordset widergespiegelt. Da Dynasets jedes Mal einen Datensatz abrufen, wenn Sie zu diesem Bild scrollen, spiegeln Dynasets Änderungen jedes Mal wider, wenn Sie zu einem Datensatz scrollen. Snapshots rufen einen Datensatz ab, wenn Sie zum ersten Mal zu diesem Datensatz scrollen, sodass Snapshots nur die Änderungen widerspiegeln, die auftreten, bevor Sie zu dem Datensatz zunächst scrollen.

Datensätze, die von anderen Benutzern nach dem Öffnen des Recordsets hinzugefügt wurden, werden nicht in Ihrem Recordset angezeigt, es sei denn, Sie senknachfragen erneut. Wenn es sich bei Ihrem Recordset um ein Dynaset handelt, werden Die Bearbeitungen an vorhandenen Datensätzen anderer Benutzer in Ihrem Dynaset angezeigt, wenn Sie zum betroffenen Datensatz scrollen. Wenn es sich bei Ihrem Recordset um einen Snapshot handelt, werden die Bearbeitungen erst angezeigt, wenn Sie den Snapshot erneut abfragen. Wenn Sie Datensätze anzeigen möchten, die von anderen Benutzern in Ihrem Snapshot hinzugefügt oder gelöscht wurden, oder Datensätze, die von anderen Benutzern in Ihrem Dynaset hinzugefügt wurden, rufen Sie [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) auf, um das Recordset neu zu erstellen. (Beachten Sie, dass die Löschungen anderer Benutzer in Ihrem Dynaset angezeigt werden.) Sie können `Requery` auch aufrufen, um Datensätze anzuzeigen, die Sie hinzufügen, aber nicht, um Ihre Löschungen anzuzeigen.

> [!TIP]
> Um die Zwischenspeicherung eines gesamten Snapshots auf einmal zu erzwingen, rufen Sie sofort nach dem Öffnen des Snapshots auf. `MoveLast` Rufen `MoveFirst` Sie dann an, um mit der Arbeit mit den Datensätzen zu beginnen. `MoveLast`ist gleichbedeutend mit einem Bildlauf über alle Datensätze, aber es ruft sie alle auf einmal ab. Beachten Sie jedoch, dass dies die Leistung beeinträchtigen kann und für einige Treiber möglicherweise nicht erforderlich ist.

Die Auswirkungen Ihrer Updates auf andere Benutzer sind ähnlich wie ihre Auswirkungen auf Sie.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Weitere Informationen zum Aktualisieren und Löschen

Dieser Abschnitt enthält zusätzliche Informationen, `Update` `Delete`die Sie bei der Arbeit mit und unterstützen.

### <a name="update-success-and-failure"></a>Update-Erfolg und -Fehler

Wenn `Update` dies `AddNew` erfolgreich `Edit` ist, endet der oder-Modus. Um einen `AddNew` `Edit` oder einen `AddNew` Modus `Edit`erneut zu starten, rufen Sie oder an.

Wenn `Update` fehlert (FALSE zurückoder eine `AddNew` Ausnahme `Edit` auslöst), bleiben Sie im Modus oder im Modus, je nachdem, welche Funktion Sie zuletzt aufgerufen haben. Sie können dann einen der folgenden Schritte ausführen:

- Ändern Sie ein Felddatenelement, und versuchen Sie es `Update` erneut.

- Rufen `AddNew` Sie auf, um die Felddatenmember auf Null zurückzusetzen, `Update` legen Sie die Werte der Felddatenmember fest, und rufen Sie dann erneut auf.

- Rufen `Edit` Sie auf, um die Werte, die sich `AddNew` `Edit`vor dem ersten Aufruf an oder im `Update` Recordset befanden, neu zu laden, legen Sie die Werte der Felddatenmember fest, und rufen Sie dann erneut auf. Nach einem `Update` erfolgreichen Aufruf `AddNew` (außer nach einem Aufruf) behalten die Felddatenmember ihre neuen Werte bei.

- Aufruf `Move` (einschließlich `Move` eines Parameters von AFX_MOVE_REFRESH oder 0), der `AddNew` alle `Edit` Änderungen löscht und einen beliebigen oder modus beendet.

### <a name="update-and-delete"></a>Aktualisieren und Löschen

Dieser Abschnitt gilt `Update` `Delete`für beide und .

Bei `Update` einem `Delete` oder einem Vorgang sollte ein und nur ein Datensatz aktualisiert werden. Dieser Datensatz ist der aktuelle Datensatz, der den Datenwerten in den Feldern des Recordsets entspricht. Wenn aus irgendeinem Grund keine Datensätze betroffen sind oder mehr als ein Datensatz betroffen ist, wird eine Ausnahme ausgelöst, die einen der folgenden **RETCODE-Werte** enthält:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Wenn diese Ausnahmen ausgelöst werden, `AddNew` bleiben `Edit` Sie in dem `Update` Zustand, in dem Sie sich beim Aufruf oder `Delete`aufwaren. Im Folgenden finden Sie die häufigsten Szenarien, in denen diese Ausnahmen angezeigt werden. Sie sehen am ehesten:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, wenn Sie den optimistischen Sperrmodus verwenden und ein anderer Benutzer den Datensatz so geändert hat, dass das Framework den richtigen Datensatz zum Aktualisieren oder Löschen nicht identifiziert.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, wenn die Tabelle, die Sie aktualisieren, keinen Primärschlüssel oder eindeutigen Index hat und Sie nicht über genügend Spalten im Recordset verfügen, um eine Tabellenzeile eindeutig zu identifizieren.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Datensatzauswahl durch Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Ausnahmen: Datenbankausnahmen](../../mfc/exceptions-database-exceptions.md)
