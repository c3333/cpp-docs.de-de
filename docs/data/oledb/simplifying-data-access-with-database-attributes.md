---
title: Vereinfachen des Datenzugriffs mit Datenbankattributen
ms.date: 10/19/2018
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
ms.openlocfilehash: d22f8a25bc7bb58f72346a15edb51f062c44e1b4
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79546176"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Vereinfachen des Datenzugriffs mit Datenbankattributen

In diesem Thema wird die Verwendung von Datenbankattributen zum Vereinfachen von Daten Bank Vorgängen veranschaulicht.

Der grundlegende Zugriff auf Informationen aus einer Datenbank besteht darin, eine Befehls Klasse (oder Tabellen Klasse) und eine Benutzerdaten Satz-Klasse für eine bestimmte Tabelle in der Datenbank zu erstellen. Die Daten Bank Attribute vereinfachen einige Vorlagen Deklarationen, die Sie zuvor durchführen mussten.

Um die Verwendung von Datenbankattributen zu veranschaulichen, zeigen die folgenden Abschnitte zwei äquivalente Tabellen-und Benutzerdaten Satz-Klassen Deklarationen an: der erste verwendet Attribute und der zweite verwendet OLE DB Vorlagen. Dieser Deklarations Code wird in der Regel in eine Header Datei mit dem Namen für die Tabelle oder das Befehls Objekt eingefügt, z. b. "Authors. h".

Wenn Sie die beiden Dateien vergleichen, können Sie sehen, wie viel einfacher Sie sind, Attribute zu verwenden. Zu den Unterschieden zählen folgende:

- Mithilfe von Attributen müssen Sie nur eine Klasse deklarieren: `CAuthors`, während Sie mit Vorlagen zwei deklarieren müssen: `CAuthorsNoAttrAccessor` und `CAuthorsNoAttr`.

- Der `db_source`-Aufrufe in der attributierten Version entspricht dem `OpenDataSource()`-Befehl in der Vorlagen Deklaration.

- Der `db_table`-Aufrufe in der attributierten Version entspricht der folgenden Vorlagen Deklaration:

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- Die `db_column` Aufrufe in der attributierten Version entsprechen der Spalten Zuordnung (siehe `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) in der Vorlagen Deklaration.

Die Attribute fügen eine Deklaration der Benutzerdaten Satz-Klasse für Sie ein. Die Benutzerdaten Satz-Klasse ist gleich `CAuthorsNoAttrAccessor` in der Vorlagen Deklaration. Wenn die Tabellen Klasse `CAuthors`ist, wird die eingefügte Benutzerdaten Satz Klasse `CAuthorsAccessor`benannt, und Sie können die Deklaration nur in injiziertem Code anzeigen. Weitere Informationen finden Sie unter "Attribut-injizierte Benutzerdaten Satz Klassen" in [Benutzerdaten Sätzen](../../data/oledb/user-records.md).

Sowohl im attributierten als auch im Vorlagen Code müssen Sie die Rowseteigenschaften mithilfe von `CDBPropSet::AddProperty`festlegen.

Informationen zu den in diesem Thema erläuterten Attributen finden Sie unter [OLE DB Consumer-Attribute](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Die folgenden `include`-Anweisungen sind erforderlich, um die folgenden Beispiele zu kompilieren:

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Tabellen-und Accessor-Deklaration mithilfe von Attributen

Der folgende Code ruft `db_source` auf und `db_table` für die Table-Klasse. `db_source` gibt die zu verwendende Datenquelle und die zu verwendende Verbindung an. `db_table` fügt den entsprechenden Vorlagen Code ein, um eine Tabellen Klasse zu deklarieren. `db_column` die Spalten Zuordnung angeben und die Accessor-Deklaration einfügen. Sie können OLE DB Consumer-Attribute in jedem Projekt verwenden, das ATL unterstützt.

Im folgenden finden Sie die Tabellen-und Accessordeklaration mit Attributen:

```cpp
//////////////////////////////////////////////////////////////////////
// Table and accessor declaration using attributes
// authors.h
//////////////////////////////////////////////////////////////////////

// Table class declaration
// (Note that you must provide your own connection string for db_source.)
[
   db_source(L"your connection string"),
   db_table("Authors")
]
class CAuthors
{
public:
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>Tabellen-und Accessor-Deklaration mithilfe von Vorlagen

Im folgenden finden Sie die Tabellen-und Accessordeklaration mithilfe von Vorlagen.

```cpp
//////////////////////////////////////////////////////////////////////
// Table and user record class declaration using templates
// authors.h
//////////////////////////////////////////////////////////////////////

// User record class declaration
class CAuthorsNoAttrAccessor
{
public:
   DWORD m_dwAuIDStatus;
   DWORD m_dwAuthorStatus;
   DWORD m_dwYearBornStatus;
   DWORD m_dwAuIDLength;
   DWORD m_dwAuthorLength;
   DWORD m_dwYearBornLength;
   LONG m_AuID;
   TCHAR m_Author[51];
   SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
   HRESULT OpenDataSource()
   {
      CDataSource _db;

HRESULT hr;
      hr = _db.OpenFromInitializationString(L"your connection string");
      if (FAILED(hr))
      {
#ifdef _DEBUG
         AtlTraceErrorRecords(hr);
#endif
         return hr;
      }
      return m_session.Open(_db);
   }
   void CloseDataSource()
   {
      m_session.Close();
   }
   operator const CSession&()
   {
      return m_session;
   }
   CSession m_session;
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)
   END_COLUMN_MAP()
};
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
{
public:
   HRESULT OpenAll()
   {
HRESULT hr;
      hr = OpenDataSource();
      if (FAILED(hr))
         return hr;
      __if_exists(GetRowsetProperties)
      {
         CDBPropSet propset(DBPROPSET_ROWSET);
         __if_exists(HasBookmark)
         {
            propset.AddProperty(DBPROP_IRowsetLocate, true);
         }
         GetRowsetProperties(&propset);
         return OpenRowset(&propset);
      }
      __if_not_exists(GetRowsetProperties)
      {
         __if_exists(HasBookmark)
         {
            CDBPropSet propset(DBPROPSET_ROWSET);
            propset.AddProperty(DBPROP_IRowsetLocate, true);
            return OpenRowset(&propset);
         }
      }
      return OpenRowset();
   }
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
   {
HRESULT hr = Open(m_session, "Authors", pPropSet);
#ifdef _DEBUG
      if(FAILED(hr))
         AtlTraceErrorRecords(hr);
#endif
      return hr;
   }
   void CloseAll()
   {
      Close();
      CloseDataSource();
   }
};
```

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumerattribute](../../windows/ole-db-consumer-attributes.md)
