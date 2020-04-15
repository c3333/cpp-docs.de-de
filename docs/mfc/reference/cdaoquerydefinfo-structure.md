---
title: CDaoQueryDefInfo-Struktur
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368940"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo-Struktur

Die `CDaoQueryDefInfo` Struktur enthält Informationen zu einem querydef-Objekt, das für Datenzugriffsobjekte (DAO) definiert ist.

## <a name="syntax"></a>Syntax

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>Parameter

*m_strName*<br/>
Benennt das querydef-Objekt eindeutig. Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe. Rufen Sie [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) auf, um diese Eigenschaft direkt abzurufen.

*m_nType*<br/>
Ein Wert, der den Betriebstyp eines querydef-Objekts angibt. Der Wert kann in folgenden Formen vorliegen:

- `dbQSelect`Wählen Sie diese Option aus: Die Abfrage wählt Datensätze aus.

- `dbQAction`Aktion – Die Abfrage verschiebt oder ändert Daten, gibt jedoch keine Datensätze zurück.

- `dbQCrosstab`Crosstab – Die Abfrage gibt Daten in einem tabellenähnlichen Format zurück.

- `dbQDelete`Löschen – Die Abfrage löscht eine Reihe von angegebenen Zeilen.

- `dbQUpdate`Aktualisieren – Die Abfrage ändert eine Gruppe von Datensätzen.

- `dbQAppend`Anfügen – Die Abfrage fügt neue Datensätze am Ende einer Tabelle oder Abfrage hinzu.

- `dbQMakeTable`Make-Table – Die Abfrage erstellt eine neue Tabelle aus einem Recordset.

- `dbQDDL`Datendefinition – Die Abfrage wirkt sich auf die Struktur von Tabellen oder deren Teilen aus.

- `dbQSQLPassThrough`Pass-Through – Die SQL-Anweisung wird ohne Zwischenverarbeitung direkt an das Datenbank-Backend übergeben.

- `dbQSetOperation`Union – Die Abfrage erstellt ein Recordset-Objekt vom Typ Snapshot, das Daten aus allen angegebenen Datensätzen in zwei oder mehr Tabellen enthält, wobei alle doppelten Datensätze entfernt wurden. Um die Duplikate einzuschließen, fügen Sie das Schlüsselwort **ALL** in der SQL-Anweisung der querydef hinzu.

- `dbQSPTBulk`Wird `dbQSQLPassThrough` mit verwendet, um eine Abfrage anzugeben, die keine Datensätze zurückgibt.

> [!NOTE]
> Um eine SQL-Pass-Through-Abfrage zu `dbQSQLPassThrough` erstellen, legen Sie die Konstante nicht fest. Dies wird automatisch vom Microsoft Jet-Datenbankmodul festgelegt, wenn Sie ein querydef-Objekt erstellen und die Connect-Eigenschaft festlegen.

Weitere Informationen finden Sie im Thema "Typeigenschaft" in der DAO-Hilfe.

*m_dateCreated*<br/>
Das Datum und die Uhrzeit, zu der die Querydef erstellt wurde. Um das Datum, an dem die querydef erstellt wurde, `CDaoTableDef` direkt abzurufen, rufen Sie die [GetDateCreated-Memberfunktion](../../mfc/reference/cdaotabledef-class.md#getdatecreated) des der Tabelle zugeordneten Objekts auf. Weitere Informationen finden Sie unter Kommentare unten. Siehe auch das Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

*m_dateLastUpdated*<br/>
Das Datum und die Uhrzeit der letzten Änderung an der querydef. Um das Datum, an dem die Tabelle zuletzt aktualisiert wurde, direkt abzurufen, rufen Sie die [GetDateLastUpdated-Memberfunktion](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) der querydef auf. Weitere Informationen finden Sie unter Kommentare unten. Und siehe das Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

*m_bUpdatable*<br/>
Gibt an, ob Änderungen an einem querydef-Objekt vorgenommen werden können. Wenn diese Eigenschaft TRUE ist, ist die querydef updatable. andernfalls ist dies nicht der Fall. Updatable bedeutet, dass die Abfragedefinition des querydef-Objekts geändert werden kann. Die Updatable-Eigenschaft eines querydef-Objekts wird auf TRUE festgelegt, wenn die Abfragedefinition aktualisiert werden kann, auch wenn das resultierende Recordset nicht aufrüstbar ist. Um diese Eigenschaft direkt abzurufen, rufen Sie die [CanUpdate-Memberfunktion](../../mfc/reference/cdaoquerydef-class.md#canupdate) der querydef auf. Weitere Informationen finden Sie im Thema "Updatable-Eigenschaft" in der DAO-Hilfe.

*m_bReturnsRecords*<br/>
Gibt an, ob eine SQL-Pass-Through-Abfrage an eine externe Datenbank Datensätze zurückgibt. Wenn diese Eigenschaft TRUE ist, gibt die Abfrage Datensätze zurück. Um diese Eigenschaft direkt abzurufen, rufen Sie [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)auf. Nicht alle SQL-Pass-Through-Abfragen an externe Datenbanken geben Datensätze zurück. Eine SQL **UPDATE-Anweisung** aktualisiert z. B. Datensätze, ohne Datensätze zurückzugeben, während eine SQL **SELECT-Anweisung** Datensätze zurückgibt. Weitere Informationen finden Sie im Thema "ReturnsRecords-Eigenschaft" in der DAO-Hilfe.

*m_strSQL*<br/>
Die SQL-Anweisung, die die Abfrage definiert, die von einem querydef-Objekt ausgeführt wird. Die SQL-Eigenschaft enthält die SQL-Anweisung, die bestimmt, wie Datensätze beim Ausführen der Abfrage ausgewählt, gruppiert und geordnet werden. Sie können die Abfrage verwenden, um Datensätze auszuwählen, die in ein Recordset-Objekt mit Dynaset- oder Snapshot-Typ eingeschlossen werden sollen. Sie können auch Massenabfragen definieren, um Daten zu ändern, ohne Datensätze zurückzugeben. Sie können den Wert dieser Eigenschaft direkt abrufen, indem Sie die [GetSQL-Memberfunktion](../../mfc/reference/cdaoquerydef-class.md#getsql) der querydef aufrufen.

*m_strConnect*<br/>
Enthält Informationen zur Quelle einer Datenbank, die in einer Pass-Through-Abfrage verwendet wird. Diese Informationen haben die Form einer Verbindungszeichenfolge. Weitere Informationen zu Verbindungszeichenfolgen und Informationen zum direkten Abrufen des Werts dieser Eigenschaft finden Sie in der [CDaoDatabase::GetConnect-Memberfunktion.](../../mfc/reference/cdaodatabase-class.md#getconnect)

*m_nODBCTimeout*<br/>
Die Anzahl der Sekunden, die das Microsoft Jet-Datenbankmodul wartet, bevor ein Timeoutfehler auftritt, wenn eine Abfrage in einer ODBC-Datenbank ausgeführt wird. Wenn Sie eine ODBC-Datenbank verwenden, z. B. Microsoft SQL Server, kann es aufgrund des Netzwerkverkehrs oder der starken Verwendung des ODBC-Servers zu Verzögerungen kommen. Anstatt auf unbestimmte Zeit zu warten, können Sie angeben, wie lange das Microsoft Jet-Modul wartet, bevor es einen Fehler verursacht. Der Standardtimeoutwert beträgt 60 Sekunden. Sie können den Wert dieser Eigenschaft direkt abrufen, indem Sie die [GetODBCTimeout-Memberfunktion](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) der querydef aufrufen. Weitere Informationen finden Sie im Thema "ODBCTimeout-Eigenschaft" in der DAO-Hilfe.

## <a name="remarks"></a>Bemerkungen

Die querydef ist ein Objekt der Klasse [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Die Verweise auf Primär, Sekundär und Alle oben geben an, wie die `CDaoDatabase`Informationen von der [GetQueryDefInfo-Memberfunktion](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) in der Klasse zurückgegeben werden.

Die von der [A-ZipNetDefInfo-Memberfunktion CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) abgerufenen Informationen werden in einer `CDaoQueryDefInfo` Struktur gespeichert. Aufruf `GetQueryDefInfo` für das Datenbankobjekt, in dessen QueryDefs-Auflistung das querydef-Objekt gespeichert ist. `CDaoQueryDefInfo`definiert auch `Dump` eine Memberfunktion in Debugbuilds. Sie können `Dump` den Inhalt eines `CDaoQueryDefInfo` Objekts absetzen. Die `CDaoDatabase` Klasse stellt auch Memberfunktionen für den direkten `CDaoQueryDefInfo` Zugriff auf alle in einem `GetQueryDefInfo`Objekt zurückgegebenen Eigenschaften bereit, sodass Sie wahrscheinlich selten aufrufen müssen.

Wenn Sie ein neues Feld- oder Parameterobjekt an die Fields- oder Parameters-Auflistung eines querydef-Objekts anfügen, wird eine Ausnahme ausgelöst, wenn die zugrunde liegende Datenbank den für das neue Objekt angegebenen Datentyp nicht unterstützt.

Die Datums- und Uhrzeiteinstellungen werden von dem Computer abgeleitet, auf dem die querydef erstellt oder zuletzt aktualisiert wurde. In einer Mehrbenutzerumgebung sollten Benutzer diese Einstellungen direkt vom Dateiserver mithilfe des Befehls **"Nettozeit"** abrufen, um Abweichungen in den Eigenschafteneinstellungen DateCreated und LastUpdated zu vermeiden.

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef-Klasse](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)
