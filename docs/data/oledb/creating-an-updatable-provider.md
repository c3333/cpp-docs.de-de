---
title: Erstellen eines aktualisierbaren Anbieters
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211392"
---
# <a name="creating-an-updatable-provider"></a>Erstellen eines aktualisierbaren Anbieters

Visual C++ unterstützt aktualisierbare Anbieter oder Anbieter, die den Datenspeicher aktualisieren (schreiben) können. In diesem Thema wird erläutert, wie Sie aktualisierbare Anbieter mithilfe von OLE DB Vorlagen erstellen.

In diesem Thema wird davon ausgegangen, dass Sie mit einem funktionsfähigen Anbieter beginnen. Zum Erstellen eines aktualisierbaren Anbieters müssen zwei Schritte ausgeführt werden. Sie müssen zunächst entscheiden, wie der Anbieter Änderungen am Datenspeicher vornimmt. insbesondere, ob Änderungen sofort oder verzögert ausgeführt werden, bis ein Update-Befehl ausgegeben wird. Im Abschnitt "[Erstellen von Anbietern aktualisierbar](#vchowmakingprovidersupdatable)" werden die Änderungen und Einstellungen beschrieben, die Sie im Anbieter Code ausführen müssen.

Als nächstes müssen Sie sicherstellen, dass der Anbieter alle Funktionen enthält, die vom Consumer angefordert werden können. Wenn der Consumer den Datenspeicher aktualisieren möchte, muss der Anbieter Code enthalten, der Daten im Datenspeicher speichert. Beispielsweise können Sie die C-Lauf Zeit Bibliothek oder MFC verwenden, um solche Vorgänge für die Datenquelle auszuführen. Der Abschnitt "[Schreiben in die Datenquelle](#vchowwritingtothedatasource)" beschreibt, wie in die Datenquelle geschrieben wird, wie NULL-Werte und Standardwerte behandelt werden und wie Spalten Flags festgelegt werden.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ist ein Beispiel für einen aktualisierbaren Anbieter. UpdatePV ist identisch mit MyProv, aber mit aktualisierbarer Unterstützung.

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Festlegen der aktualisierbaren Anbieter

Der Schlüssel für einen aktualisierbaren Anbieter ist das Verständnis der Vorgänge, die der Anbieter für den Datenspeicher durchführen soll, und die Art und Weise, wie der Anbieter diese Vorgänge durchführen soll. Insbesondere besteht das wesentliche Problem darin, dass Updates des Datenspeicher sofort oder verzögert (in Batches) ausgeführt werden, bis ein Update-Befehl ausgegeben wird.

Sie müssen zuerst entscheiden, ob Sie von `IRowsetChangeImpl` oder `IRowsetUpdateImpl` in der Rowsetklasse erben möchten. Je nachdem, welche der Optionen Sie implementieren, wird die Funktionalität von drei Methoden beeinträchtigt: `SetData`, `InsertRows`und `DeleteRows`.

- Wenn Sie von [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)erben, wird der Datenspeicher durch Aufrufen dieser drei Methoden sofort geändert.

- Wenn Sie von [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)erben, verschieben die Methoden Änderungen am Datenspeicher, bis Sie `Update`, `GetOriginalData`oder `Undo`aufrufen. Wenn das Update mehrere Änderungen umfasst, werden Sie im Batch Modus ausgeführt (Beachten Sie, dass Änderungen an der Batch Verarbeitung zu einem beträchtlichen Speicher Aufwand führen können).

Beachten Sie, dass `IRowsetUpdateImpl` von `IRowsetChangeImpl`abgeleitet ist. `IRowsetUpdateImpl` bietet Ihnen somit die Möglichkeit, Funktionen und Batch Funktionen zu ändern.

### <a name="to-support-updatability-in-your-provider"></a>So unterstützen Sie die Aktualisierbarkeit in Ihrem Anbieter

1. Erben Sie in der Rowsetklasse von `IRowsetChangeImpl` oder `IRowsetUpdateImpl`. Diese Klassen stellen geeignete Schnittstellen zum Ändern des Datenspeicher bereit:

   **IRowsetChange wird hinzugefügt**

   Fügen Sie der Vererbungs Kette mithilfe dieses Formulars `IRowsetChangeImpl` hinzu:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Fügen Sie auch `COM_INTERFACE_ENTRY(IRowsetChange)` dem Abschnitt `BEGIN_COM_MAP` in der Rowsetklasse hinzu.

   **Hinzufügen von IRowsetUpdate**

   Fügen Sie der Vererbungs Kette mithilfe dieses Formulars `IRowsetUpdate` hinzu:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Sie sollten die `IRowsetChangeImpl` Zeile aus der Vererbungs Kette entfernen. Diese Ausnahme von der bereits erwähnten Direktive muss den Code für `IRowsetChangeImpl`enthalten.

1. Fügen Sie der com-Karte Folgendes hinzu (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  Wenn Sie implementieren   |           Zu COM-Zuordnung hinzufügen             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Wenn Sie implementieren | Zu Eigenschaften Satz Zuordnung hinzufügen |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Fügen Sie in Ihrem Befehl der Eigenschaften Satz Zuordnung (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`) Folgendes hinzu:

   |  Wenn Sie implementieren   |                                             Zu Eigenschaften Satz Zuordnung hinzufügen                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. In ihrer Eigenschaften Satz Zuordnung sollten Sie auch alle folgenden Einstellungen einschließen, wie Sie unten angezeigt werden:

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

   Sie können die in diesen Makro aufrufen verwendeten Werte suchen, indem Sie in "Atldb. h" nach den Eigenschaften-IDs und-Werten suchen (wenn "Atldb. h" von der Online Dokumentation abweicht, wird "Atldb. h" von der Dokumentation abgelöst).

   > [!NOTE]
   > Viele der `VARIANT_FALSE`-und `VARIANT_TRUE` Einstellungen sind für die OLE DB Vorlagen erforderlich. die OLE DB Spezifikation besagt, dass Sie Lese-/Schreibzugriff haben können, aber die OLE DB Vorlagen können nur einen Wert unterstützen.

   **Wenn Sie IRowsetChangeImpl implementieren**

   Wenn Sie `IRowsetChangeImpl`implementieren, müssen Sie die folgenden Eigenschaften für Ihren Anbieter festlegen. Diese Eigenschaften werden hauptsächlich verwendet, um Schnittstellen über `ICommandProperties::SetProperties`anzufordern.

   - `DBPROP_IRowsetChange`: durch das Festlegen von wird `DBPROP_IRowsetChange`automatisch festgelegt.

   - `DBPROP_UPDATABILITY`: eine Bitmaske, die die unterstützten Methoden für `IRowsetChange`angibt: `SetData`, `DeleteRows`oder `InsertRow`.

   - `DBPROP_CHANGEINSERTEDROWS`: der Consumer kann `IRowsetChange::DeleteRows` oder `SetData` für neu eingefügte Zeilen aufzurufen.

   - `DBPROP_IMMOBILEROWS`: das Rowset kann keine eingefügten oder aktualisierten Zeilen neu anordnen.

   **Wenn Sie IRowsetUpdateImpl implementieren**

   Wenn Sie `IRowsetUpdateImpl`implementieren, müssen Sie die folgenden Eigenschaften für den Anbieter festlegen, und Sie müssen zusätzlich alle Eigenschaften für `IRowsetChangeImpl` zuvor aufgeführten Eigenschaften festlegen:

   - [https://login.microsoftonline.com/consumers/](`DBPROP_IRowsetUpdate`).

   - `DBPROP_OWNINSERT`: muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OWNUPDATEDELETE`: muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OTHERINSERT`: muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_OTHERUPDATEDELETE`: muss READ_ONLY und VARIANT_TRUE sein.

   - `DBPROP_REMOVEDELETED`: muss READ_ONLY und VARIANT_TRUE sein.

   - [https://login.microsoftonline.com/consumers/](`DBPROP_MAXPENDINGROWS`).

   > [!NOTE]
   > Wenn Sie Benachrichtigungen unterstützen, können auch andere Eigenschaften vorhanden sein. Weitere Informationen finden Sie im Abschnitt `IRowsetNotifyCP` für diese Liste.

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Schreiben in die Datenquelle

Um aus der Datenquelle zu lesen, nennen Sie die `Execute`-Funktion. Um in die Datenquelle zu schreiben, nennen Sie die `FlushData`-Funktion. (Im Allgemeinen bedeutet das leeren, dass Sie Änderungen an einer Tabelle oder einem Index auf einem Datenträger speichern.)

```cpp
FlushData(HROW, HACCESSOR);
```

Die Argumente für Zeilen Handles (HROW) und Accessorhandle (HACCESSOR) ermöglichen es Ihnen, den zu schreibende Bereich anzugeben. In der Regel schreiben Sie jeweils ein einzelnes Datenfeld.

Die `FlushData`-Methode schreibt Daten in dem Format, in dem Sie ursprünglich gespeichert wurden. Wenn Sie diese Funktion nicht außer Kraft setzen, funktioniert der Anbieter ordnungsgemäß, die Änderungen werden jedoch nicht in den Datenspeicher geleert.

### <a name="when-to-flush"></a>Zeitpunkt der Leerung

Die Anbieter Vorlagen aufrufen FlushData, wenn Daten in den Datenspeicher geschrieben werden müssen. Dies geschieht in der Regel (aber nicht immer) aufgrund von Aufrufen der folgenden Funktionen:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (wenn neue Daten in die Zeile eingefügt werden müssen)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Funktionsweise

Der Consumer führt einen-Befehl aus, der eine Leerung (z. b. Update) erfordert, und dieser-Befehl wird an den Anbieter übermittelt, der immer folgende Aktionen ausführt:

- Ruft `SetDBStatus` immer dann auf, wenn ein Statuswert gebunden ist.

- Prüft Spalten-Flags.

- Aufruf von `IsUpdateAllowed`.

Diese drei Schritte helfen Ihnen, die Sicherheit zu gewährleisten. Dann ruft der Anbieter `FlushData`auf.

### <a name="how-to-implement-flushdata"></a>Vorgehensweise beim Implementieren von FlushData

Zum Implementieren von `FlushData`müssen Sie mehrere Probleme berücksichtigen:

Stellen Sie sicher, dass der Datenspeicher Änderungen verarbeiten kann.

Behandeln von NULL-Werten.

### <a name="handling-default-values"></a>Verarbeiten von Standardwerten.

Zum Implementieren ihrer eigenen `FlushData`-Methode müssen Sie folgende Schritte ausführen:

- Wechseln Sie zu ihrer Rowsetklasse.

- Fügen Sie in der Rowset-Klasse die Deklaration von:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Stellen Sie eine Implementierung von `FlushData`bereit.

Eine gute Implementierung von `FlushData` speichert nur die Zeilen und Spalten, die tatsächlich aktualisiert werden. Mit den Parametern HROW und HACCESSOR können Sie die aktuelle Zeile und Spalte ermitteln, die zur Optimierung gespeichert werden.

In der Regel besteht die größte Herausforderung darin, mit Ihrem eigenen systemeigenen Datenspeicher zu arbeiten. Versuchen Sie nach Möglichkeit Folgendes:

- Halten Sie die Methode zum Schreiben in Ihren Datenspeicher so einfach wie möglich.

- Behandeln von NULL-Werten (optional, aber empfohlen).

- Verarbeiten der Standardwerte (optional, aber empfohlen).

Das beste daran ist, dass tatsächlich angegebene Werte im Datenspeicher für NULL-Werte und Standardwerte vorliegen. Es ist am besten, wenn Sie diese Daten extrapolieren können. Andernfalls wird empfohlen, keine NULL-Werte und Standardwerte zuzulassen.

Im folgenden Beispiel wird gezeigt, wie `FlushData` in der `RUpdateRowset`-Klasse im `UpdatePV` Sample implementiert wird (siehe "Rowset. h" im Beispielcode):

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

### <a name="handling-changes"></a>Behandeln von Änderungen

Damit der Anbieter Änderungen verarbeiten kann, müssen Sie zunächst sicherstellen, dass der Datenspeicher (z. b. eine Textdatei oder eine Videodatei) über Funktionen verfügt, mit denen Sie Änderungen vornehmen können. Wenn dies nicht der Fall ist, sollten Sie den Code separat vom Anbieter Projekt erstellen.

### <a name="handling-null-data"></a>Behandeln von NULL-Daten

Es ist möglich, dass ein Endbenutzer NULL-Daten sendet. Wenn Sie NULL-Werte in Felder in der Datenquelle schreiben, treten möglicherweise Probleme auf. Stellen Sie sich eine Anwendung für die Anwendung vor, die Werte für Stadt und Postleitzahl akzeptiert. Sie kann entweder einen oder beide Werte akzeptieren, aber keinen von beiden, da in diesem Fall die Übermittlung nicht möglich wäre. Daher müssen Sie bestimmte Kombinationen von NULL-Werten in Feldern einschränken, die für Ihre Anwendung sinnvoll sind.

Als Anbieter Entwickler müssen Sie in Erwägung gezogen werden, wie diese Daten gespeichert werden, wie Sie diese Daten aus dem Datenspeicher lesen und wie Sie Sie für den Benutzer angeben. Insbesondere müssen Sie in Erwägung gezogen werden, wie der Daten Status von Rowsetdaten in der Datenquelle geändert werden soll (z. b. DataStatus = NULL). Sie entscheiden, welcher Wert zurückgegeben werden soll, wenn ein Consumer auf ein Feld mit einem NULL-Wert zugreift.

Sehen Sie sich den Code im Beispiel UpdatePV an; Es veranschaulicht, wie ein Anbieter NULL-Daten verarbeiten kann. In Update Panel speichert der Anbieter NULL-Daten, indem die Zeichenfolge "Null" im Datenspeicher geschrieben wird. Beim Lesen von NULL-Daten aus dem Datenspeicher wird diese Zeichenfolge angezeigt, und anschließend wird der Puffer geleert, wodurch eine NULL-Zeichenfolge erstellt wird. Außerdem verfügt sie über eine außer Kraft Setzung von `IRowsetImpl::GetDBStatus`, in der Sie DBSTATUS_S_ISNULL zurückgibt, wenn dieser Datenwert leer ist.

### <a name="marking-nullable-columns"></a>Markieren von Spalten mit NULL-Werten

Wenn Sie auch Schemarowsets implementieren (siehe `IDBSchemaRowsetImpl`), sollte Ihre Implementierung im DBSCHEMA_COLUMNS Rowset angeben (in der Regel durch CXxxSchemaColSchemaRowset in Ihrem Anbieter gekennzeichnet), dass die Spalte NULL-Werte zulässt.

Außerdem müssen Sie angeben, dass alle Spalten, die NULL-Werte zulassen, den DBCOLUMNFLAGS_ISNULLABLE Wert in Ihrer Version des `GetColumnInfo`enthalten.

Wenn Sie in der OLE DB Templates-Implementierung Spalten nicht als NULL-Werte zulassen, geht der Anbieter davon aus, dass Sie einen Wert enthalten müssen, und lässt den Consumer keine NULL-Werte senden.

Im folgenden Beispiel wird gezeigt, wie die `CommonGetColInfo`-Funktion in ' CUpdateCommand ' (siehe UpProvRS. cpp) in ' UpdatePV ' implementiert wird. Beachten Sie, dass die Spalten diese DBCOLUMNFLAGS_ISNULLABLE für Spalten enthalten, die NULL-Werte zulassen.

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

Wie bei NULL-Daten sind Sie dafür verantwortlich, die Standardwerte zu ändern.

Der Standardwert von `FlushData` und `Execute` ist die Rückgabe von S_OK. Wenn Sie diese Funktion nicht außer Kraft setzen, erscheinen die Änderungen daher als erfolgreich (S_OK wird zurückgegeben), aber Sie werden nicht an den Datenspeicher übertragen.

Im `UpdatePV` Beispiel (in Rowset. h) verarbeitet die `SetDBStatus`-Methode Standardwerte wie folgt:

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

Wenn Sie Standardwerte für ihre Spalten unterstützen, müssen Sie diese mithilfe von Metadaten in der \<-Anbieter Klasse\>Schemarowset-Klasse festlegen. Legen Sie `m_bColumnHasDefault = VARIANT_TRUE` fest.

Außerdem müssen Sie die Spaltenflags festlegen, die mit dem enumerierten Typ "DBCOLUMNFLAGS" angegeben werden. Die Spaltenflags beschreiben Spalten Eigenschaften.

Beispielsweise wird in der `CUpdateSessionColSchemaRowset`-Klasse in `UpdatePV` (in "Session. h") die erste Spalte wie folgt eingerichtet:

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

Dieser Code gibt unter anderem an, dass die Spalte den Standardwert 0 unterstützt, dass Sie beschreibbar ist und alle Daten in der Spalte dieselbe Länge aufweisen. Wenn Sie möchten, dass die Daten in einer Spalte eine Variable Länge aufweisen, legen Sie dieses Flag nicht fest.

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines OLE DB-Anbieters](creating-an-ole-db-provider.md)
