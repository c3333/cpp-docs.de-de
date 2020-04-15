---
title: 'TN045: MFC-Datenbank-Unterstützung für Long Varchar-Varbinary'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: f67d159fb600dcacd8eedd40e672edf18bddee9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365509"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: MFC- und Datenbankunterstützung für LONGVARCHAR und LONGVARBINARY

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem Hinweis wird beschrieben, wie die ODBC-SQL_LONGVARCHAR und **SQL_LONGVARBINARY** Datentypen mithilfe der MFC-Datenbankklassen abgerufen und gesendet werden. **SQL_LONGVARCHAR**

## <a name="overview-of-long-varcharvarbinary-support"></a>Übersicht über Long Varchar/Varbinary Support

Die **ODBC-SQL_LONG_VARCHAR** und **SQL_LONGBINARY** Datentypen (hier als lange Datenspalten bezeichnet) können riesige Datenmengen enthalten. Es gibt 3 Möglichkeiten, mit diesen Daten umzugehen:

- Binden Sie `CString` / `CByteArray`es an eine .

- Binden Sie `CLongBinary`es an eine .

- Binden Sie es überhaupt nicht und rufen Sie den langen Datenwert unabhängig von den Datenbankklassen manuell ab und senden Sie ihn.

Jede der drei Methoden hat Vor- und Nachteile.

Lange Datenspalten werden für Parameter für eine Abfrage nicht unterstützt. Sie werden nur für outputColumns unterstützt.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Binden einer Long Data Column an ein CString/CByteArray

Vorteile:

Dieser Ansatz ist einfach zu verstehen, und Sie arbeiten mit vertrauten Klassen. Der Rahmen `CFormView` unterstützt `CString` `DDX_Text`mit . Sie verfügen über viele allgemeine Zeichenfolgen- oder Auflistungsfunktionen mit dem `CString` und-Klassen, `CByteArray` und Sie können die Lokale Speichermenge steuern, die für den Datenwert reserviert ist. Das Framework verwaltet eine alte `Edit` Kopie `AddNew` von Felddaten während oder Funktionsaufrufen, und das Framework kann automatisch Änderungen an den Daten für Sie erkennen.

> [!NOTE]
> Da `CString` für die Arbeit an `CByteArray` Zeichendaten und für die Arbeit an Binärdaten entwickelt wurde, wird empfohlen, die `CByteArray`Zeichendaten (**SQL_LONGVARCHAR**) in `CString`und die Binärdaten (**SQL_LONGVARBINARY**) in ein .

Die RFX-Funktionen für `CString` und `CByteArray` verfügen über ein zusätzliches Argument, mit dem Sie die Standardgröße des zugewiesenen Speichers überschreiben können, um den abgerufenen Wert für die Datenspalte zu enthalten. Beachten Sie das Argument nMaxLength in den folgenden Funktionsdeklarationen:

```
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

Wenn Sie eine lange Datenspalte in einem `CString` oder `CByteArray`abrufen, beträgt die maximale zurückgegebene Datenmenge standardmäßig 255 Byte. Alles, was darüber hinausgeht, wird ignoriert. In diesem Fall löst das Framework die Ausnahme **AFX_SQL_ERROR_DATA_TRUNCATED**aus. Glücklicherweise können Sie nMaxLength explizit auf höhere Werte bis **maxINT**erhöhen.

> [!NOTE]
> Der Wert von nMaxLength wird von MFC verwendet, um den lokalen Puffer der `SQLBindColumn` Funktion festzulegen. Dies ist der lokale Puffer für die Speicherung der Daten und hat keinen Einfluss auf die Menge der vom ODBC-Treiber zurückgegebenen Daten. `RFX_Text`und `RFX_Binary` führen Sie `SQLFetch` nur einen Aufruf durch, bei dem die Daten aus der Back-End-Datenbank abgerufen werden. Jeder ODBC-Treiber hat eine andere Einschränkung für die Datenmenge, die er in einem einzigen Abruf zurückgeben kann. Dieser Grenzwert kann viel kleiner sein als der in nMaxLength festgelegte Wert, in diesem Fall wird die Ausnahme **AFX_SQL_ERROR_DATA_TRUNCATED** ausgelöst. Wechseln Sie unter diesen `RFX_LongBinary` Umständen `RFX_Text` `RFX_Binary` zur Verwendung anstelle oder so, dass alle Daten abgerufen werden können.

ClassWizard bindet **SQL_LONGVARCHAR** eine SQL_LONGVARCHAR `CString`an eine , `CByteArray` oder eine **SQL_LONGVARBINARY** an einen für Sie. Wenn Sie mehr als 255 Bytes zuweisen möchten, in die Sie Ihre lange Datenspalte abrufen, können Sie einen expliziten Wert für nMaxLength angeben.

Wenn eine lange Datenspalte `CString` an `CByteArray`eine oder gebunden ist, funktioniert das Aktualisieren des Felds genauso wie bei einer SQL_**VARCHAR** oder SQL_**VARBINARY**. Während `Edit`wird der Datenwert weggespeichert und `Update` später verglichen, wenn aufgerufen wird, um Änderungen am Datenwert zu erkennen und die Fehler- und Nullwerte für die Spalte entsprechend festzulegen.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Binden einer Long Data-Spalte an eine CLongBinary

Wenn Ihre lange Datenspalte möglicherweise mehr **MAXINT-Bytes** an Daten enthält, sollten Sie diese wahrscheinlich in eine `CLongBinary`abrufen.

Vorteile:

Dadurch wird eine ganze lange Datenspalte bis zum verfügbaren Speicher abgerufen.

Nachteile:

Die Daten werden im Speicher gespeichert. Dieser Ansatz ist auch für sehr große Datenmengen unerschwinglich teuer. Sie müssen `SetFieldDirty` das gebundene Datenelement aufrufen, um `Update` sicherzustellen, dass das Feld in einen Vorgang einbezogen wird.

Wenn Sie lange Datenspalten `CLongBinary`in einem abrufen, überprüfen die Datenbankklassen die Gesamtgröße der langen Datenspalte und weisen dann ein `HGLOBAL` Speichersegment zu, das groß genug ist, um den gesamten Datenwert zu speichern. Die Datenbankklassen rufen dann den gesamten `HGLOBAL`Datenwert in die zugeordnete ab.

Wenn die Datenquelle die erwartete Größe der langen Datenspalte nicht zurückgeben kann, löst das Framework die Ausnahme **AFX_SQL_ERROR_SQL_NO_TOTAL**aus. Wenn der Versuch, `HGLOBAL` die Fehler zuzuweisen, fehlschlägt, wird eine Standardspeicherausnahme ausgelöst.

ClassWizard bindet eine **SQL_LONGVARCHAR** oder `CLongBinary` **SQL_LONGVARBINARY** an einen für Sie. Wählen `CLongBinary` Sie im Dialogfeld Elementvariable hinzufügen als Variablentyp aus. ClassWizard fügt dann `RFX_LongBinary` einen `DoFieldExchange` Aufruf zu Ihrem Anruf hinzu und erhöht die Gesamtzahl der gebundenen Felder.

Um lange Datenspaltenwerte zu aktualisieren, `HGLOBAL` stellen Sie zunächst sicher, dass die zugewiesenen Daten groß `CLongBinary`genug sind, um Ihre neuen Daten zu halten, indem Sie **::GlobalSize** auf dem *m_hData* Member des aufrufen. Wenn es zu klein `HGLOBAL` ist, lassen Sie die los und weisen Sie eine die entsprechende Größe zu. Legen Sie *dann m_dwDataLength* fest, um die neue Größe widerzuspiegeln.

Andernfalls können Sie die , wenn *m_dwDataLength* größer als die Größe der zu `HGLOBAL`ersetzenden Daten ist, entweder frei und neu zuordnen oder sie zuweisen. Stellen Sie sicher, dass Die Anzahl der Bytes angegeben wird, die tatsächlich in *m_dwDataLength*verwendet werden.

## <a name="how-updating-a-clongbinary-works"></a>So funktioniert das Aktualisieren eines CLongBinary

Es ist nicht notwendig zu `CLongBinary` verstehen, wie das Aktualisieren einer funktioniert, aber es kann als Beispiel für das Senden langer Datenwerte an eine Datenquelle nützlich sein, wenn Sie diese dritte Methode auswählen, die unten beschrieben wird.

> [!NOTE]
> Damit ein `CLongBinary` Feld in eine Aktualisierung einbezogen werden `SetFieldDirty` kann, müssen Sie das Feld explizit aufrufen. Wenn Sie Änderungen an einem Feld vornehmen, einschließlich `SetFieldDirty`der Einstellung Null, müssen Sie aufrufen. Sie müssen `SetFieldNull`auch aufrufen, wobei der zweite Parameter **FALSE**ist, um das Feld als wertmarkiert zu markieren.

Beim Aktualisieren `CLongBinary` eines Felds verwenden die Datenbankklassen **den DATA_AT_EXEC** Mechanismus `SQLSetPos`von ODBC (siehe ODBC-Dokumentation zum argument rgbValue von 's). Wenn das Framework die Insert- oder Update-Anweisung `HGLOBAL` vorbereitet, anstatt auf `CLongBinary` die zu zeigen, die die Daten enthält, wird die *Adresse* des stattdessen als *Wert* der Spalte festgelegt, und der Längenindikator wird auf **SQL_DATA_AT_EXEC**festgelegt. Wenn die Updateanweisung später an die `SQLExecDirect` Datenquelle gesendet wird, wird **SQL_NEED_DATA**zurückgegeben. Dadurch wird der Rahmen darauf hinangezeigt, dass der Wert `CLongBinary`des Params für diese Spalte tatsächlich die Adresse einer ist. Das Framework `SQLGetData` ruft einmal mit einem kleinen Puffer auf, in dem erwartet wird, dass der Treiber die tatsächliche Länge der Daten zurückgibt. Wenn der Treiber die tatsächliche Länge des binären großen Objekts (bLOB) zurückgibt, ordnet MFC so viel Speicherplatz wie nötig neu zu, um das BLOB abzurufen. Wenn die Datenquelle **SQL_NO_TOTAL**zurückgibt, was darauf hinweist, dass die Größe des BLOB nicht bestimmt werden kann, erstellt MFC kleinere Blöcke. Die Standardanfangsgröße ist 64K, und nachfolgende Blöcke sind doppelt so groß. z. B. ist die zweite 128K, die dritte ist 256K, und so weiter. Die Anfangsgröße ist konfigurierbar.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Nicht bindungsfrei: Abrufen/Senden von Daten direkt aus ODBC mit SQLGetData

Mit dieser Methode umgehen Sie die Datenbankklassen vollständig und beschäftigen sich selbst mit der langen Datenspalte.

Vorteile:

Sie können Bei Bedarf Daten auf dem Datenträger zwischenspeichern oder dynamisch entscheiden, wie viele Daten abgerufen werden sollen.

Nachteile:

Sie erhalten weder die `Edit` Frameworks noch `AddNew` die Unterstützung, und Sie`Delete` müssen Code selbst schreiben, um grundlegende Funktionen auszuführen (funktioniert jedoch, da es sich nicht um einen Vorgang auf Spaltenebene handelt).

In diesem Fall muss sich die lange Datenspalte in der Auswahlliste des Recordsets befinden, sollte jedoch nicht an das Framework gebunden sein. Eine Möglichkeit, dies zu tun, `GetDefaultSQL` besteht darin, Ihre eigene `CRecordset`SQL-Anweisung über oder als lpszSQL-Argument für die `Open` Funktion von zu liefern und die zusätzliche Spalte nicht mit einem RFX_-Funktionsaufruf zu binden. ODBC erfordert, dass ungebundene Felder rechts von gebundenen Feldern angezeigt werden, daher fügen Sie Ihre ungebundene Spalte oder Spalten am Ende der Auswahlliste hinzu.

> [!NOTE]
> Da Ihre lange Datenspalte nicht an das Framework gebunden ist, `CRecordset::Update` werden Änderungen an ihr nicht mit Aufrufen behandelt. Sie müssen die erforderlichen SQL **INSERT-** und **UPDATE-Anweisungen** selbst erstellen und senden.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
