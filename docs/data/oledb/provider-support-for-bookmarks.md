---
title: Anbieterunterstützung für Lesezeichen
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 240cb4da03d6c8c1958b7a86e78171aca2dc30e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216452"
---
# <a name="provider-support-for-bookmarks"></a>Anbieterunterstützung für Lesezeichen

Im Beispiel in diesem Thema wird der-Klasse die- `IRowsetLocate` Schnittstelle hinzugefügt `CCustomRowset` . In fast allen Fällen beginnen Sie mit dem Hinzufügen einer Schnittstelle zu einem vorhandenen COM-Objekt. Anschließend können Sie Sie testen, indem Sie weitere Aufrufe aus den Consumer-Vorlagen hinzufügen. Das Beispiel veranschaulicht Folgendes:

- Fügen Sie einem Anbieter eine Schnittstelle hinzu.

- Legen Sie dynamisch fest, welche Spalten an den Consumer zurückgegeben werden sollen.

- Lesezeichen Unterstützung hinzufügen.

Die `IRowsetLocate` -Schnittstelle erbt von der `IRowset` -Schnittstelle. Um die- `IRowsetLocate` Schnittstelle hinzuzufügen, erben Sie `CCustomRowset` von [irowsetlompeimpl](../../data/oledb/irowsetlocateimpl-class.md).

Das Hinzufügen der `IRowsetLocate` Schnittstelle unterscheidet sich etwas von den meisten Schnittstellen. Zum Erstellen der vtables-Zeile verfügen die OLE DB Anbieter Vorlagen über einen Vorlagen Parameter, der die abgeleitete Schnittstelle behandelt. Der folgende Code zeigt die neue Vererbungs Liste:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Alle vierten, fünften und sechsten Parameter werden hinzugefügt. In diesem Beispiel werden die Standardwerte für den vierten und fünften Parameter verwendet, aber `IRowsetLocateImpl` als der sechste Parameter angegeben. `IRowsetLocateImpl`ist eine OLE DB Vorlagen Klasse, die zwei Vorlagen Parameter annimmt: diese verbinden die- `IRowsetLocate` Schnittstelle mit der- `CCustomRowset` Klasse. Um die meisten Schnittstellen hinzuzufügen, können Sie diesen Schritt überspringen und zum nächsten wechseln. Nur die `IRowsetLocate` - `IRowsetScroll` Schnittstellen und die-Schnittstelle müssen auf diese Weise behandelt werden.

Sie müssen dann den angeben `CCustomRowset` , um `QueryInterface` für die- `IRowsetLocate` Schnittstelle aufzurufen. Fügen Sie der Karte die Zeile hinzu `COM_INTERFACE_ENTRY(IRowsetLocate)` . Die Schnittstellen Zuordnung für `CCustomRowset` sollte wie im folgenden Code dargestellt aussehen:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Außerdem müssen Sie Ihre Karte mit der- `CRowsetImpl` Klasse verbinden. Fügen Sie im COM_INTERFACE_ENTRY_CHAIN-Makro in die Zuordnung ein `CRowsetImpl` . Erstellen Sie außerdem eine typedef namens `RowsetBaseClass` , die aus den Vererbungs Informationen besteht. Diese TypeDef ist willkürlich und kann ignoriert werden.

Behandeln Sie schließlich den-Befehl `IColumnsInfo::GetColumnsInfo` . Normalerweise verwenden Sie hierfür die PROVIDER_COLUMN_ENTRY Makros. Allerdings möchte ein Consumer möglicherweise Lesezeichen verwenden. Sie müssen in der Lage sein, die vom Anbieter zurückgegebenen Spalten zu ändern, je nachdem, ob der Consumer ein Lesezeichen verlangt.

Um den-Befehl zu behandeln `IColumnsInfo::GetColumnsInfo` , löschen Sie die PROVIDER_COLUMN Map in der- `CTextData` Klasse. Das PROVIDER_COLUMN_MAP-Makro definiert eine Funktion `GetColumnInfo` . Definieren Sie eine eigene `GetColumnInfo` Funktion. Die Funktionsdeklaration sollte wie folgt aussehen:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

Implementieren Sie dann die- `GetColumnInfo` Funktion in der *benutzerdefinierten*Rs. cpp-Datei wie folgt:

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo`prüft zunächst, ob eine Eigenschaft mit dem Namen `DBPROP_IRowsetLocate` festgelegt ist. OLE DB verfügt über Eigenschaften für jede optionale Schnittstelle aus dem Rowsetobjekt. Wenn der Consumer eine dieser optionalen Schnittstellen verwenden möchte, wird eine Eigenschaft auf true festgelegt. Der Anbieter kann diese Eigenschaft dann überprüfen und spezielle Aktionen basierend darauf durchführen.

In ihrer Implementierung erhalten Sie die-Eigenschaft, indem Sie den Zeiger auf das Command-Objekt verwenden. Der `pThis` Zeiger stellt das Rowset oder die Befehls Klasse dar. Da Sie hier Vorlagen verwenden, müssen Sie diese in als Zeiger übergeben, **`void`** oder der Code wird nicht kompiliert.

Geben Sie ein statisches Array an, das die Spalten Informationen enthalten soll. Wenn der Consumer die Lesezeichen Spalte nicht wünschen, wird ein Eintrag im Array verschwendet. Sie können dieses Array dynamisch zuordnen, aber Sie müssen sicherstellen, dass es ordnungsgemäß zerstört wird. In diesem Beispiel werden die Makros ADD_COLUMN_ENTRY und ADD_COLUMN_ENTRY_EX verwendet, um die Informationen in das Array einzufügen. Sie können dem *benutzerdefinierten*RS die Makros hinzufügen. H-Datei, wie im folgenden Code gezeigt:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = 0; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);

#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = flags; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;
```

Um den Code im Consumer zu testen, müssen Sie einige Änderungen am `OnRun` Handler vornehmen. Die erste Änderung an der-Funktion besteht darin, dass Sie Code hinzufügen, um dem Eigenschaften Satz eine Eigenschaft hinzuzufügen. Im Code wird die-Eigenschaft auf "true" festgelegt `DBPROP_IRowsetLocate` , sodass dem Anbieter mitgeteilt wird, dass Sie die Lesezeichen Spalte benötigen. Der `OnRun` Handlercode sollte wie folgt aussehen:

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

Die- **`while`** Schleife enthält Code zum aufzurufen der- `Compare` Methode in der- `IRowsetLocate` Schnittstelle. Der Code, den Sie verwenden, sollte immer übergeben werden, da Sie genau die gleichen Lesezeichen vergleichen. Speichern Sie außerdem ein Lesezeichen in einer temporären Variablen, sodass Sie es nach Abschluss der Schleife verwenden können, **`while`** um die `MoveToBookmark` Funktion in den Consumervorlagen aufzurufen. Die- `MoveToBookmark` Funktion Ruft die- `GetRowsAt` Methode in auf `IRowsetLocate` .

Außerdem müssen Sie den Benutzerdaten Satz im Consumer aktualisieren. Fügen Sie in der-Klasse einen Eintrag hinzu, um ein Lesezeichen und einen Eintrag in der COLUMN_MAP zu behandeln:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Wenn Sie den Code aktualisiert haben, sollten Sie in der Lage sein, den Anbieter mit der-Schnittstelle zu erstellen und auszuführen `IRowsetLocate` .

## <a name="see-also"></a>Weitere Informationen

[Erweiterte Anbieter Techniken](../../data/oledb/advanced-provider-techniques.md)
