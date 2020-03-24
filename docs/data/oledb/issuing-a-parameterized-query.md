---
title: Ausgeben einer parametrisierten Abfrage
ms.date: 10/19/2018
helpviewer_keywords:
- parameter queries, running using CCommand class
ms.assetid: aedb0fce-52a4-4c97-a5c9-b2114be6c3b0
ms.openlocfilehash: bb8b879d08595150b2db61f4840131e3ccc500a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210170"
---
# <a name="issuing-a-parameterized-query"></a>Ausgeben einer parametrisierten Abfrage

Im folgenden Beispiel wird eine einfache parametrisierte Abfrage ausgegeben, die Datensätze mit einem Alters Feld (das größer als 30 ist) aus einer Tabelle in einer Microsoft Access-Datenbank abruft. Um den-Parameter zu unterstützen, muss der Benutzerdaten Satz über eine zusätzliche Karte verfügen. Der folgende Code verwendet in einem ATL-Projekt die `CCommand`-Klasse anstelle der `CTable`-Klasse, die im vorherigen Beispiel verwendet wurde, wobei [ein einfaches Rowset](../../data/oledb/traversing-a-simple-rowset.md)durchlaufen wird.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CCommand<CAccessor<CArtists>> artists;
    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    // Set the parameter for the query
    artists.m_nAge = 30;
    artists.Open(session, "select * from artists where age > ?");

    // Get data from the rowset
    while (artists.MoveNext() == S_OK)
    {
        cout << artists.m_szFirstName;
        cout << artists.m_szLastName;
    }

    return 0;
}
```

Der Benutzerdaten Satz `CArtists`sieht in etwa wie folgt aus:

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Consumervorlagen](../../data/oledb/working-with-ole-db-consumer-templates.md)
