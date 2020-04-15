---
title: Erstellen eines aktualisierbaren Anbieters
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365558"
---
# <a name="creating-an-updatable-provider"></a>Erstellen eines aktualisierbaren Anbieters

Visual C++ unterstützt aktualisierbare Anbieter oder Anbieter, die den Datenspeicher aktualisieren (schreiben) können. In diesem Thema wird erläutert, wie Sie aktualisierbare Anbieter mithilfe von OLE DB-Vorlagen erstellen.

In diesem Thema wird davon ausgegangen, dass Sie mit einem praktikabelen Anbieter beginnen. Es gibt zwei Schritte zum Erstellen eines aktualisierbaren Anbieters. Sie müssen zunächst entscheiden, wie der Anbieter Änderungen am Datenspeicher vornimmt. insbesondere, ob Änderungen sofort oder aufgeschoben werden sollen, bis ein Aktualisierungsbefehl ausgegeben wird. Der Abschnitt "[Making Providers Updatable](#vchowmakingprovidersupdatable)" beschreibt die Änderungen und Einstellungen, die Sie im Anbietercode vornehmen müssen.

Als Nächstes müssen Sie sicherstellen, dass Ihr Anbieter alle Funktionen enthält, um alles zu unterstützen, was der Verbraucher von ihm anfordert. Wenn der Consumer den Datenspeicher aktualisieren möchte, muss der Anbieter Code enthalten, der Daten im Datenspeicher verbleibt. Sie können z. B. die C-Laufzeitbibliothek oder MFC verwenden, um solche Vorgänge in Ihrer Datenquelle auszuführen. Im Abschnitt "[Schreiben in die Datenquelle](#vchowwritingtothedatasource)" wird beschrieben, wie in die Datenquelle geschrieben, NULL- und Standardwerte behandelt und Spaltenflags festgelegt werden.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ist ein Beispiel für einen aktualisierbaren Anbieter. UpdatePV ist das gleiche wie MyProv, aber mit aktualisierbarer Unterstützung.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Anbieter updatable machen

Der Schlüssel, um einen Anbieter aufrüstbar zu machen, besteht darin, zu verstehen, welche Vorgänge Ihr Anbieter im Datenspeicher ausführen soll und wie der Anbieter diese Vorgänge ausführen soll. Insbesondere ist die Hauptfrage, ob Aktualisierungen des Datenspeichers sofort oder zurückgestellt (Batched) durchgeführt werden sollen, bis ein Aktualisierungsbefehl ausgegeben wird.

Sie müssen zuerst entscheiden, ob `IRowsetChangeImpl` `IRowsetUpdateImpl` Sie von oder in Ihrer Rowset-Klasse erben möchten. Je nachdem, welche dieser Methoden Sie implementieren möchten, wird `SetData` `InsertRows`die `DeleteRows`Funktionalität von drei Methoden beeinträchtigt: , und .

- Wenn Sie von [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)erben, ändert das Aufrufen dieser drei Methoden sofort den Datenspeicher.

- Wenn Sie von [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)erben, verschieben die Methoden Änderungen am `Update` `GetOriginalData`Datenspeicher, bis Sie , oder `Undo`aufrufen. Wenn die Aktualisierung mehrere Änderungen beinhaltet, werden sie im Batchmodus durchgeführt (beachten Sie, dass Batching-Änderungen einen erheblichen Speicheraufwand verursachen können).

Beachten `IRowsetUpdateImpl` Sie, dass `IRowsetChangeImpl`die ableitet von . Somit `IRowsetUpdateImpl` erhalten Sie Änderungsfähigkeit plus Batch-Fähigkeit.

### <a name="to-support-updatability-in-your-provider"></a>Unterstützung der Updatability in Ihrem Provider

1. Erben Sie in Ihrer Rowset-Klasse von `IRowsetChangeImpl` oder `IRowsetUpdateImpl`. Diese Klassen bieten geeignete Schnittstellen zum Ändern des Datenspeichers:

   **Hinzufügen von IRowsetChange**

   Fügen `IRowsetChangeImpl` Sie Ihrer Vererbungskette mithilfe dieses Formulars hinzu:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Fügen `COM_INTERFACE_ENTRY(IRowsetChange)` Sie `BEGIN_COM_MAP` auch dem Abschnitt in der Rowset-Klasse hinzu.

   **Hinzufügen von IRowsetUpdate**

   Fügen `IRowsetUpdate` Sie Ihrer Vererbungskette mithilfe dieses Formulars hinzu:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Sie sollten `IRowsetChangeImpl` die Zeile aus der Vererbungskette entfernen. Diese eine Ausnahme von der bereits erwähnten Richtlinie muss den Code für `IRowsetChangeImpl`enthalten.

1. Fügen Sie Ihrer COM-Karte Folgendes hinzu (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  Wenn Sie   |           Zur COM-Karte hinzufügen             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Wenn Sie | Hinzufügen einer Eigenschaftssatzzuordnung |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Fügen Sie in Ihrem Befehl Folgendes zu`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`Ihrer Eigenschaftensatzzuordnung hinzu ( ):

   |  Wenn Sie   |                                             Hinzufügen einer Eigenschaftssatzzuordnung                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. In der Eigenschaftssatzzuordnung sollten Sie auch alle folgenden Einstellungen in die folgenden Einstellungen einschließen:

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   Sie können die in diesen Makroaufrufen verwendeten Werte finden, indem Sie in Atldb.h nach den Eigenschaften-IDs und -Werten suchen (wenn Atldb.h sich von der Onlinedokumentation unterscheidet, ersetzt Atldb.h die Dokumentation).

   > [!NOTE]
   > Viele der `VARIANT_FALSE` `VARIANT_TRUE` und Einstellungen sind für die OLE DB-Vorlagen erforderlich. Die OLE DB-Spezifikation sagt, dass sie gelesen/geschrieben werden können, aber die OLE DB-Vorlagen können nur einen Wert unterstützen.

   **Wenn Sie IRowsetChangeImpl implementieren**

   Wenn Sie `IRowsetChangeImpl`implementieren, müssen Sie die folgenden Eigenschaften für Ihren Anbieter festlegen. Diese Eigenschaften werden hauptsächlich zum `ICommandProperties::SetProperties`Anfordern von Schnittstellen über verwendet.

   - `DBPROP_IRowsetChange`: Einstellung dieser `DBPROP_IRowsetChange`automatisch gesetzt .

   - `DBPROP_UPDATABILITY`: Eine Bitmaske, die `IRowsetChange`die `SetData` `DeleteRows`unterstützten `InsertRow`Methoden für : , , oder angibt.

   - `DBPROP_CHANGEINSERTEDROWS`: Der `IRowsetChange::DeleteRows` Verbraucher `SetData` kann neu eingefügte Zeilen aufrufen oder neu eingefügt haben.

   - `DBPROP_IMMOBILEROWS`: Rowset ordnet eingefügte oder aktualisierte Zeilen nicht neu an.

   **Wenn Sie IRowsetUpdateImpl implementieren**

   Wenn Sie `IRowsetUpdateImpl`implementieren, müssen Sie die folgenden Eigenschaften für Ihren Anbieter `IRowsetChangeImpl` festlegen, zusätzlich zum Festlegen aller Eigenschaften für zuvor aufgeführte Eigenschaften:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OWNUPDATEDELETE`: Muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OTHERINSERT`: Muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OTHERUPDATEDELETE`: Muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_REMOVEDELETED`: Muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Wenn Sie Benachrichtigungen unterstützen, verfügen Sie möglicherweise auch über einige andere Eigenschaften. siehe Abschnitt `IRowsetNotifyCP` weiter für diese Liste.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Schreiben in die Datenquelle

Um aus der Datenquelle zu `Execute` lesen, rufen Sie die Funktion auf. Um in die Datenquelle zu `FlushData` schreiben, rufen Sie die Funktion auf. (Im allgemeinen Sinne bedeutet Flush, dass Änderungen, die Sie an einer Tabelle oder einem Index vornehmen, auf dem Datenträger gespeichert werden.)

```cpp
FlushData(HROW, HACCESSOR);
```

Mit den Argumenten Zeilenhandle (HROW) und Accessor handle (HACCESSOR) können Sie den zu schreibenden Bereich angeben. In der Regel schreiben Sie ein einzelnes Datenfeld gleichzeitig.

Die `FlushData` Methode schreibt Daten in dem Format, in dem sie ursprünglich gespeichert wurde. Wenn Sie diese Funktion nicht überschreiben, funktioniert Ihr Anbieter ordnungsgemäß, aber Änderungen werden nicht in den Datenspeicher geleert.

### <a name="when-to-flush"></a>Wann zu Flush

Die Anbietervorlagen rufen FlushData auf, wenn Daten in den Datenspeicher geschrieben werden müssen. Dies geschieht in der Regel (aber nicht immer) als Folge von Aufrufen der folgenden Funktionen:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`(wenn neue Daten in die Zeile eingefügt werden müssen)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Funktionsweise

Der Consumer ruft einen Aufruf ab, der eine Leerung erfordert (z. B. Update), und dieser Aufruf wird an den Anbieter weitergeleitet, der immer folgendes tut:

- Ruft `SetDBStatus` immer dann auf, wenn Sie einen Statuswert gebunden haben.

- Überprüft Spaltenflags.

- Aufruf von `IsUpdateAllowed`.

Diese drei Schritte sorgen für Sicherheit. Dann ruft `FlushData`der Anbieter an.

### <a name="how-to-implement-flushdata"></a>Implementieren von FlushData

Um `FlushData`zu implementieren, müssen Sie mehrere Probleme berücksichtigen:

Stellen Sie sicher, dass der Datenspeicher Änderungen verarbeiten kann.

Umgang mit NULL-Werten.

### <a name="handling-default-values"></a>Behandeln von Standardwerten.

Um Ihre `FlushData` eigene Methode zu implementieren, müssen Sie:

- Wechseln Sie zu Ihrer Rowset-Klasse.

- Setzen Sie in die rowset-Klasse die Deklaration von:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Stellen Sie `FlushData`eine Implementierung von bereit.

Eine gute `FlushData` Implementierung von speichert nur die Zeilen und Spalten, die tatsächlich aktualisiert werden. Sie können die Parameter HROW und HACCESSOR verwenden, um die aktuelle Zeile und Spalte zu bestimmen, die zur Optimierung gespeichert werden.

In der Regel besteht die größte Herausforderung darin, mit Ihrem eigenen nativen Datenspeicher zu arbeiten. Versuchen Sie nach Möglichkeit:

- Halten Sie die Methode zum Schreiben in Ihren Datenspeicher so einfach wie möglich.

- Behandeln Sie NULL-Werte (optional, aber empfohlen).

- Behandeln Sie Standardwerte (optional, aber empfohlen).

Am besten müssen Sie tatsächlich angegebene Werte in Ihrem Datenspeicher für NULL- und Standardwerte haben. Es ist am besten, wenn Sie diese Daten extrapolieren können. Wenn dies nicht der Fall ist, wird empfohlen, NULL- und Standardwerte nicht zuzulassen.

Das folgende Beispiel `FlushData` zeigt, `RUpdateRowset` wie in `UpdatePV` der Klasse im Beispiel implementiert wird (siehe Rowset.h im Beispielcode):

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>Handhabung von Änderungen

Damit Ihr Anbieter Änderungen verarbeiten kann, müssen Sie zunächst sicherstellen, dass Ihr Datenspeicher (z. B. eine Textdatei oder eine Videodatei) über Funktionen verfügt, mit denen Sie Änderungen daran vornehmen können. Ist dies nicht der Fall, sollten Sie diesen Code getrennt vom Anbieterprojekt erstellen.

### <a name="handling-null-data"></a>Umgang mit NULL-Daten

Es ist möglich, dass ein Endbenutzer NULL-Daten sendet. Wenn Sie NULL-Werte in Felder in der Datenquelle schreiben, kann es zu potenziellen Problemen kommen. Stellen Sie sich eine Auftragsanwendung vor, die Werte für Stadt und Postleitzahl akzeptiert; sie könnte einen oder beide Werte akzeptieren, aber nicht weder, weil in diesem Fall eine Lieferung unmöglich wäre. Sie müssen daher bestimmte Kombinationen von NULL-Werten in Feldern einschränken, die für Ihre Anwendung sinnvoll sind.

Als Anbieterentwickler müssen Sie berücksichtigen, wie Sie diese Daten speichern, wie Sie diese Daten aus dem Datenspeicher lesen und wie Sie diese für den Benutzer angeben. Insbesondere müssen Sie überlegen, wie Sie den Datenstatus von Rowset-Daten in der Datenquelle ändern können (z. B. DataStatus = NULL). Sie entscheiden, welcher Wert zurückgegeben werden soll, wenn ein Consumer auf ein Feld mit einem NULL-Wert zugreift.

Sehen Sie sich den Code im UpdatePV-Beispiel an. Es wird veranschaulicht, wie ein Anbieter NULL-Daten verarbeiten kann. In UpdatePV speichert der Anbieter NULL-Daten, indem er die Zeichenfolge "NULL" im Datenspeicher schreibt. Wenn NULL-Daten aus dem Datenspeicher gelesen werden, wird diese Zeichenfolge und anschließendder Puffer geleert, wodurch eine NULL-Zeichenfolge erstellt wird. Es verfügt auch über `IRowsetImpl::GetDBStatus` eine Außerkraftsetzung, in der es DBSTATUS_S_ISNULL zurückgibt, wenn dieser Datenwert leer ist.

### <a name="marking-nullable-columns"></a>Markieren von nullierbaren Spalten

Wenn Sie auch Schemarowsets `IDBSchemaRowsetImpl`implementieren (siehe ), sollte Ihre Implementierung im DBSCHEMA_COLUMNS Rowset (in der Regel in Ihrem Anbieter durch CxxxSchemaColSchemaRowset markiert) angeben, dass die Spalte nullist.

Sie müssen auch angeben, dass alle NULL-Spalten den `GetColumnInfo`DBCOLUMNFLAGS_ISNULLABLE Wert in Ihrer Version des enthalten.

Wenn Sie in der OLE DB-Vorlagenimplementierung Spalten nicht als nullwert markieren, geht der Anbieter davon aus, dass sie einen Wert enthalten müssen, und lässt den Consumer nicht zu, dass er NULL-Werte sendet.

Das folgende Beispiel `CommonGetColInfo` zeigt, wie die Funktion in CUpdateCommand (siehe UpProvRS.cpp) in UpdatePV implementiert wird. Beachten Sie, wie die Spalten diese DBCOLUMNFLAGS_ISNULLABLE für NULL-Spalten haben.

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>Standardwerte

Wie bei NULL-Daten sind Sie dafür verantwortlich, sich mit sich ändernden Standardwerten zu befassen.

Der Standardwert von `FlushData` und `Execute` ist die Rückgabe S_OK. Wenn Sie diese Funktion nicht überschreiben, scheinen die Änderungen erfolgreich zu sein (S_OK werden zurückgegeben), werden aber nicht an den Datenspeicher übertragen.

Im `UpdatePV` Beispiel (in Rowset.h) behandelt die `SetDBStatus` Methode Die Standardwerte wie folgt:

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>Spaltenflags

Wenn Sie Standardwerte für Ihre Spalten unterstützen, müssen \<Sie\>sie mithilfe von Metadaten in der SchemaRowset-Klasse der Anbieterklasse festlegen. Legen Sie `m_bColumnHasDefault = VARIANT_TRUE` fest.

Sie haben auch die Verantwortung, die Spaltenflags festzulegen, die mit dem aufgezählten TYP DBCOLUMNFLAGS angegeben werden. Die Spaltenflags beschreiben Spaltenmerkmale.

In der `CUpdateSessionColSchemaRowset` Klasse in `UpdatePV` (in Session.h) wird z. B. die erste Spalte auf folgende Weise eingerichtet:

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

Dieser Code gibt unter anderem an, dass die Spalte den Standardwert 0 unterstützt, dass sie schreibbar ist und dass alle Daten in der Spalte die gleiche Länge haben. Wenn die Daten in einer Spalte eine variable Länge haben sollen, sollten Sie dieses Flag nicht festlegen.

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB-Anbieters](creating-an-ole-db-provider.md)
