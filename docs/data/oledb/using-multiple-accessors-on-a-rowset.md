---
title: Verwenden mehrerer Zugriffsmethoden für ein Rowset
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 48772539b4dda9262a244506a36932d1e752949e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509397"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Verwenden mehrerer Zugriffsmethoden für ein Rowset

Es gibt drei grundlegende Szenarien, in denen Sie mehrere Accessoren verwenden müssen:

- **Mehrere Lese-/Schreib-Rowsets.** In diesem Szenario verfügen Sie über eine Tabelle mit einem Primärschlüssel. Sie möchten alle Spalten in der Zeile lesen können, einschließlich des Primärschlüssels. Sie möchten auch in der Lage sein, Daten in alle Spalten mit Ausnahme des Primärschlüssels zu schreiben (da Sie nicht in die Primärschlüssel Spalte schreiben können). In diesem Fall richten Sie zwei Accessoren ein:

  - Accessor 0 enthält alle Spalten.

  - Accessor 1 enthält alle Spalten außer dem Primärschlüssel.

- **Leistung** In diesem Szenario verfügt eine oder mehrere Spalten über eine große Datenmenge, z. b. Grafik-, Sound-oder Videodateien. Jedes Mal, wenn Sie zu einer Zeile wechseln, möchten Sie die Spalte wahrscheinlich nicht mit der großen Datendatei abrufen, da dadurch die Leistung der Anwendung verlangsamt würde.

  Sie können separate Accessoren einrichten, bei denen der erste Accessor alle Spalten mit Ausnahme derjenigen mit großen Daten enthält und Daten aus diesen Spalten automatisch abruft. der erste Accessor ist die automatische Zugriffsmethode. Der zweite Accessor ruft nur die Spalte ab, die große Daten enthält, ruft jedoch keine Daten aus dieser Spalte automatisch ab. Sie können bei Bedarf andere Methoden aktualisieren oder die großen Daten abrufen.

  - Accessor 0 ist ein automatischer Accessor. alle Spalten mit Ausnahme derjenigen mit großen Daten werden abgerufen.

  - Accessor 1 ist kein automatischer Accessor. die Spalte wird mit umfangreichen Daten abgerufen.

  Verwenden Sie das Auto-Argument, um anzugeben, ob der Accessor eine automatische Zugriffsmethode ist.

- **Mehrere ISequentialStream-Spalten.** In diesem Szenario verfügen Sie über mehr als eine Spalte, die `ISequentialStream` Daten enthält. Allerdings ist jeder Accessor auf einen `ISequentialStream` Datenstream beschränkt. Um dieses Problem zu beheben, richten Sie mehrere Accessoren ein, die jeweils über einen `ISequentialStream` Zeiger verfügen.

In der Regel erstellen Sie Accessoren mithilfe der Makros [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) und [END_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) . Sie können auch das [Db_accessor](../../windows/attributes/db-accessor.md) -Attribut verwenden. (Accessoren werden in [Benutzerdaten Sätzen](../../data/oledb/user-records.md)ausführlicher beschrieben.) Die Makros oder das-Attribut geben an, ob es sich bei einem Accessor um einen automatischen oder einen nicht automatischen Accessor handelt:

- Verschieben Sie in einem automatischen Accessor Methoden wie `MoveFirst` , `MoveLast` , `MoveNext` , und rufen Sie `MovePrev` Daten für alle angegebenen Spalten automatisch ab. Accessor 0 muss der automatische Accessor sein.

- Bei einem nicht automatischen Accessor erfolgt der Abruf nicht, bis Sie explizit eine Methode wie `Update` , `Insert` , `Fetch` oder aufruft `Delete` . In den oben beschriebenen Szenarien möchten Sie möglicherweise nicht alle Spalten bei jedem Verschieben abrufen. Sie können eine oder mehrere Spalten in einem separaten Accessor platzieren und dies als nicht automatischen Accessor festlegen, wie unten gezeigt.

Im folgenden Beispiel werden mehrere Accessoren verwendet, um in die Auftrags Tabelle der SQL Server pubs-Datenbank mithilfe mehrerer Accessoren zu lesen und in diese zu schreiben. Bei diesem Beispiel handelt es sich um die häufigste Verwendung mehrerer Accessoren. Weitere Informationen finden Sie im obigen Szenario "Multiple Read/Write Rowsets".

Die Benutzerdaten Satz-Klasse lautet wie folgt. Er richtet zwei Accessoren ein: Accessor 0 enthält nur die Primärschlüssel Spalte (ID), und Accessor 1 enthält andere Spalten.

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Der Haupt Code lautet wie folgt. `MoveNext`Durch den Aufruf von werden Daten aus der ID der Primärschlüssel Spalte mithilfe von Accessor 0 automatisch abgerufen. Beachten Sie, dass die- `Insert` Methode am Ende-Accessor 1 verwendet, um das Schreiben in die Primärschlüssel Spalte zu vermeiden.

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Accessoren](../../data/oledb/using-accessors.md)<br/>
[Benutzerdaten Sätze](../../data/oledb/user-records.md)
