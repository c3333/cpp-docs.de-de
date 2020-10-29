---
title: Supporting Schema Rowsets
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 156fe9c7a2b15f7254fb0c83f8b25982aa5ad09a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924308"
---
# <a name="supporting-schema-rowsets"></a>Supporting Schema Rowsets

Schemarowsets ermöglichen es Consumern, Informationen zu einem Datenspeicher abzurufen, ohne Kenntnis über die zugrunde liegende Struktur oder das Schema zu besitzen. Beispielsweise kann ein Datenspeicher Tabellen umfassen, die in einer benutzerdefinierten Hierarchie strukturiert sind. Es gibt in diesem Fall nur die Möglichkeit, Kenntnis über das Schema zu erlangen, indem es gelesen wird. (Ein weiteres Beispiel ist, dass die Visual C++-Assistenten Schemarowsets verwenden, um Accessoren für den Consumer zu generieren.) Damit der Consumer dies tun kann, macht das Sitzungs Objekt des Anbieters Methoden für die [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) -Schnittstelle verfügbar. In Visual C++-Anwendungen verwenden Sie die Klasse [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) zur Implementierung von `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` unterstützt die folgenden Methoden:

- [CheckRestrictions](./idbschemarowsetimpl-class.md#checkrestrictions) überprüft die Gültigkeit von Einschränkungen anhand eines Schemarowsets.

- [CreateSchemaRowset](./idbschemarowsetimpl-class.md#createschemarowset) implementiert eine Funktion zur COM-Objekterstellung für das über den Vorlagenparameter angegebene Objekt.

- [SetRestrictions](./idbschemarowsetimpl-class.md#setrestrictions) gibt an, welche Einschränkungen Sie für ein bestimmtes Schemarowset unterstützen.

- [IDBSchemaRowset::GetRowset](./idbschemarowsetimpl-class.md#getrowset) gibt ein (von der Schnittstelle geerbtes) Schemarowset zurück.

- [GetSchemas](./idbschemarowsetimpl-class.md#getschemas) gibt eine Liste mit Schemarowsets zurück, die für `IDBSchemaRowsetImpl::GetRowset` (von der Schnittstelle geerbt) zugänglich sind.

## <a name="atl-ole-db-provider-wizard-support"></a>Unterstützung für den ATL-OLE DB-Anbieter-Assistenten

::: moniker range="msvc-160"

Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Der **ATL-OLE DB-Anbieter-Assistent** erstellt drei Schemaklassen in der Sitzungsheaderdatei:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Diese Klassen antworten auf Consumeranforderungen von Schemainformationen. Beachten Sie, dass die OLE DB-Spezifikation erfordert, dass diese drei Schemarowsets unterstützt werden müssen:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** verarbeitet Anforderungen von Tabelleninformationen (DBSCHEMA_TABLES-Schemarowset).

- **C**<em>ShortName</em>**SessionColSchemaRowset** verarbeitet Anforderungen von Spalteninformationen (DBSCHEMA_COLUMNS-Schemarowset). Der Assistent stellt Beispielimplementierungen für diese Klassen bereit, die Schemainformationen für einen DOS-Anbieter zurückgeben.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** verarbeitet Anforderungen von Schemainformationen zum Anbietertyp (DBSCHEMA_PROVIDER_TYPES-Schemarowset). Die vom Assistenten bereitgestellte Standardimplementierung gibt S_OK zurück.

Sie können diese Klassen anpassen, um Schemainformationen in geeigneter Weise für Ihren Anbieter zu verarbeiten:

- In **C**<em>ShortName</em>**SessionTRSchemaRowset** müssen Sie Felder für Katalog, Tabelle und Beschreibung ausfüllen (`trData.m_szType`, `trData.m_szTable` und `trData.m_szDesc`). Das vom Assistenten generierte Beispiel verwendet nur eine Zeile (Tabelle). Andere Anbieter können mehr als eine Tabelle zurückgeben.

- In **C**<em>ShortName</em>**SessionColSchemaRowset** übergeben Sie den Namen der Tabelle als `DBID`.

::: moniker-end

## <a name="setting-restrictions"></a>Festlegen von Einschränkungen

Ein wichtiges Konzept bei der Unterstützung von Schemarowsets ist das Festlegen von Einschränkungen. Die Festlegung erfolgt über `SetRestrictions`. Einschränkungen ermöglichen es Consumern, nur die übereinstimmende Zeilen abzurufen (z. B. Suche nach allen Spalten in der Tabelle „MyTable“). Einschränkungen sind optional, und wenn keine unterstützt werden (Standardeinstellung), werden immer alle Daten zurückgegeben. Ein Beispiel für einen Anbieter mit Unterstützung von Einschränkungen finden Sie in [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV).

## <a name="setting-up-the-schema-map"></a>Einrichten der Schemazuordnung

Richten Sie eine Schemazuordnung wie die folgende in „Session.h“ in UpdatePV ein:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Um `IDBSchemaRowset` zu unterstützen, müssen Sie DBSCHEMA_TABLES, DBSCHEMA_COLUMNS und DBSCHEMA_PROVIDER_TYPES unterstützen. Sie können nach eigenem Ermessen weitere Schemarowsets hinzufügen.

Deklarieren Sie eine Schemarowsetklasse mit einer `Execute`-Methode wie z.B. `CUpdateSessionTRSchemaRowset` in `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` erbt von `IDBSchemaRowsetImpl` und verfügt deshalb über alle zugehörigen Methoden für die Einschränkungsverarbeitung. Deklarieren Sie unter Verwendung von `CSchemaRowsetImpl` drei untergeordnete Klassen (diese werden in der Schemazuordnung oben aufgeführt): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset` und `CUpdateSessionPTSchemaRowset`. Jede dieser untergeordneten Klassen umfasst eine `Execute`-Methode, die den zugehörigen Satz an Einschränkungen (Suchkriterien) verarbeitet. Jede `Execute`-Methode vergleicht die Werte der Parameter *cRestrictions* und *rgRestrictions* . Eine Beschreibung dieser Parameter finden Sie in [SetRestrictions](./idbschemarowsetimpl-class.md#setrestrictions).

Weitere Informationen dazu, welche Einschränkungen einem bestimmten Schemarowset entsprechen, finden Sie in der Tabelle der Schemarowset-GUIDs in [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der **OLE DB-Programmierreferenz** im Windows SDK.

Wenn Sie beispielsweise die TABLE_NAME-Einschränkung für DBSCHEMA_TABLES unterstützen, gehen Sie folgendermaßen vor:

Im ersten Schritt suchen Sie nach DBSCHEMA_TABLES und sehen, dass es vier Einschränkungen (in der Reihenfolge) unterstützt.

|Schemarowseteinschränkung|Einschränkungswert|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (binär: 1)|
|TABLE_SCHEMA|0x2 (binär: 10)|
|table_name|0x4 (binär: 100)|
|TABLE_TYPE|0x8 (binär: 1000)|

Es ist ein Bit für jede Einschränkung vorhanden. Sie möchten nur TABLE_NAME unterstützen, deshalb geben Sie im `rgRestrictions`-Element 0x4 zurück. Wenn Sie TABLE_CATALOG und TABLE_NAME unterstützen möchten, geben Sie 0x5 (binär: 101) zurück.

Standardmäßig gibt die Implementierung 0 für eine Anforderung zurück (keine Unterstützung von Einschränkungen). UpdatePV ist ein Beispiel für einen Anbieter, der Einschränkungen unterstützt.

### <a name="example"></a>Beispiel

Dieser Code stammt aus dem [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)-Beispiel. `UpdatePv` unterstützt die drei erforderlichen Schemarowsets: DBSCHEMA_TABLES, DBSCHEMA_COLUMNS und DBSCHEMA_PROVIDER_TYPES. Als Beispiel für eine Implementierung der Schemaunterstützung in Ihrem Anbieter werden Sie in diesem Thema durch die Implementierung des DBSCHEMA_TABLE-Rowsets geleitet.

> [!NOTE]
> Der Beispielcode unterscheidet sich möglicherweise vom hier gezeigten Code. Betrachten Sie den Beispielcode als die aktuellere Codeversion.

Im ersten Schritt beim Hinzufügen von Schemaunterstützung müssen Sie bestimmen, welche Einschränkungen Sie unterstützen möchten. Um zu ermitteln, welche Einschränkungen für Ihr Schemarowset verfügbar sind, sehen Sie sich die OLE DB-Spezifikation für die Definition von `IDBSchemaRowset` an. Nach der Hauptdefinition sehen Sie eine Tabelle mit dem Namen des Schemarowsets, der Anzahl von Einschränkungen und den Einschränkungsspalten. Wählen Sie das Schemarowset aus, das Sie unterstützen möchten, und notieren Sie sich die Anzahl von Einschränkungen und Einschränkungsspalten. DBSCHEMA_TABLES unterstützt beispielsweise vier Einschränkungen (TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME und TABLE_TYPE):

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

Ein Bit repräsentiert jede Einschränkungsspalte. Wenn Sie eine Einschränkung unterstützen (d.h. eine Abfrage mithilfe der Einschränkung ausführen) möchten, legen Sie das Bit auf 1 fest. Wenn Sie eine Einschränkung nicht unterstützen möchten, legen Sie das Bit auf 0 fest. Im Code oben unterstützt `UpdatePV` die Einschränkungen TABLE_NAME und TABLE_TYPE für das DBSCHEMA_TABLES-Rowset. Dies sind die dritte (Bitmaske 100) und die vierte (Bitmaske 1000) Einschränkung. Die Bitmaske für `UpdatePv` lautet deshalb 1100 (oder 0x0C):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

Die folgende `Execute`-Funktion ähnelt denen in regulären Rowsets. Sie verfügen über drei Argumente: *pcRowsAffected* , *cRestrictions* und *rgRestrictions* . Die Variable *pcRowsAffected* ist ein Ausgabeparameter, mit dem der Anbieter die Anzahl von Zeilen im Schemarowset zurückgeben kann. Der *cRestrictions* -Parameter ist ein Eingabeparameter, der die Anzahl von Einschränkungen enthält, die vom Consumer an den Anbieter übergeben werden. Der Parameter *rgRestrictions* ist ein Array aus VARIANT-Werten, die die Einschränkungswerte enthalten.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

Die Variable *cRestrictions* basiert auf der Gesamtzahl an Einschränkungen für ein Schemarowset, unabhängig davon, ob der Anbieter sie unterstützt. UpdatePV unterstützt zwei Einschränkungen (die 3. und die 4.), deshalb sucht dieser Code nur nach einem *cRestrictions* -Wert größer oder gleich 3.

Der Wert für die TABLE_NAME-Einschränkung ist in *rgRestrictions[2]* gespeichert (die 3. Einschränkung in einem 0-basierten Array ist 2). Stellen Sie sicher, dass die Einschränkung nicht VT_EMPTY lautet, um sie tatsächlich zu unterstützen. Beachten Sie, dass VT_NULL nicht gleichbedeutend ist mit VT_EMPTY. VT_NULL gibt einen gültigen Einschränkungswert an.

Die `UpdatePv`-Definition eines Tabellennamens ist ein vollqualifizierter Pfadname zu einer Textdatei. Extrahieren Sie den Einschränkungswert, und versuchen Sie dann, die Datei zu öffnen, um sicherzustellen, dass sie tatsächlich vorhanden ist. Wenn die Datei nicht vorhanden ist, geben Sie S_OK zurück. Dies mag ein wenig rückwärts gerichtet erscheinen, aber tatsächlich informiert der Code den Consumer darüber, dass keine unterstützten Tabellen mit dem angegebenen Namen vorhanden waren. Die Rückgabe von S_OK bedeutet, dass der Code korrekt ausgeführt wurde.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

Die Unterstützung der vierten Einschränkung (TABLE_TYPE) ähnelt der für die dritte Einschränkung. Führen Sie eine Überprüfung durch, um sicherzustellen, dass der Wert nicht VT_EMPTY lautet. Diese Einschränkung gibt nur den Tabellentyp, TABLE, zurück. Die gültigen Werte für DBSCHEMA_TABLES finden Sie in **Anhang B** der **OLE DB-Programmierreferenz** im Abschnitt zum TABLES-Rowset.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

Hier erstellen Sie tatsächlich einen Zeileneintrag für das Rowset. Die Variable `trData` entspricht `CTABLESRow`, einer in den OLE DB-Anbietervorlagen definierten Struktur. `CTABLESRow` entspricht der TABLES-Rowsetdefinition in **Anhang B** der OLE DB-Spezifikation. Sie müssen nur eine Zeile hinzufügen, weil Sie nur jeweils eine Tabelle unterstützen können.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` legt nur drei Spalten fest: table_name, TABLE_TYPE und Beschreibung. Notieren Sie sich die Spalten, für die Sie Informationen zurückgeben. Sie benötigen diese Informationen bei der Implementierung von `GetDBStatus`:

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

Die Funktion `GetDBStatus` ist wichtig für die ordnungsgemäße Funktion des Schemarowsets. Sie geben nicht für jede Spalte im TABLES-Rowset Daten zurück, deshalb müssen Sie angeben, für welche Spalten Sie Daten zurückgeben und für welche nicht.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

Ihre `Execute`-Funktion gibt Daten für die Felder TABLE_NAME, TABLE_TYPE und DESCRIPTION aus dem TABLES-Rowset zurück, deshalb können Sie anhand von **Anhang B** der OLE DB-Spezifikation (durch Zählen von oben nach unten) feststellen, dass es sich um die Ordinalzahlen 3, 4 und 6 handelt. Geben Sie für jede dieser Spalten DBSTATUS_S_OK zurück. Für alle anderen Spalten geben Sie DBSTATUS_S_ISNULL zurück. Es ist wichtig, diesen Status zurückzugeben, weil ein Consumer möglicherweise nicht versteht, dass der zurückgegebene Wert NULL oder etwas anderes ist. Zur Erinnerung: NULL ist nicht gleichbedeutend mit leer.

Weitere Informationen zur OLE DB-Schemarowset-Schnittstelle finden Sie im Abschnitt zur [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md)-Schnittstelle in der **OLE DB-Programmierreferenz** .

Informationen dazu, wie Consumer `IDBSchemaRowset`-Methoden verwenden können, finden Sie unter [Abrufen von Metadaten mit Schemarowsets](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Ein Beispiel für einen Anbieter, der Schemarowsets unterstützt, finden Sie im [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)-Beispiel.

## <a name="see-also"></a>Siehe auch

[Erweiterte Anbieter Techniken](../../data/oledb/advanced-provider-techniques.md)
