---
title: Vom Consumer-Assistenten generierte Methoden
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 15d41aabee174a409ad11e4422292bcea5f10bbf
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919123"
---
# <a name="consumer-wizard-generated-methods"></a>Vom Consumer-Assistenten generierte Methoden

::: moniker range="msvc-160"

Der ATL-OLE DB-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können diese Funktionalität weiterhin manuell hinzufügen.

::: moniker-end

::: moniker range="<=msvc-150"

Der **ATL-OLE DB-Consumer-Assistent** und der **MFC-Anwendungs-Assistent** generieren bestimmte Funktionen, die Sie kennen sollten. Einige Methoden werden in attributierten Projekten anders implementiert, daher gelten einige Einschränkungen. Im Folgenden finden Sie Informationen zu jedem Fall. Informationen zum Anzeigen von injiziertem Code finden Sie unter [Debuggen von injiziertem Code](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` öffnet die Datenquelle sowie Rowsets und aktiviert Textmarken, sofern verfügbar.

- `CloseAll` schließt alle offenen Rowsets und gibt alle Befehlsausführungen frei.

- `OpenRowset` wird von `OpenAll` aufgerufen, um das Rowset bzw. die Rowsets des Consumers zu öffnen.

- `GetRowsetProperties` ruft einen Zeiger auf den Eigenschaftensatz des Rowsets ab, mit dem Eigenschaften festgelegt werden können.

- `OpenDataSource` öffnet die Datenquelle mithilfe der Initialisierungszeichenfolge, die Sie im Dialogfeld **Datenverknüpfungseigenschaften** angegeben haben.

- `CloseDataSource` schließt die Datenquelle auf geeignete Weise.

## <a name="openall-and-closeall"></a>OpenAll und CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

Das folgende Beispiel zeigt, wie Sie `OpenAll` und `CloseAll` aufrufen, wenn Sie wiederholt den gleichen Befehl ausführen. Vergleichen Sie dazu das Codebeispiel in [CCommand::Close](./ccommand-class.md#close) – dieses zeigt eine Variation, die `Close` und `ReleaseCommand` anstelle von `CloseAll` aufruft.

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>Hinweise

Wenn Sie eine `HasBookmark`-Methode definieren, legt der `OpenAll`-Code die `DBPROP_IRowsetLocate`-Eigenschaft fest. Stellen Sie sicher, dass Sie nur dann so vorgehen, wenn Ihr Anbieter diese Eigenschaft unterstützt.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` ruft diese Methode auf, um das Rowset bzw. die Rowsets im Consumer zu öffnen. In der Regel müssen Sie `OpenRowset` nicht aufrufen, es sei denn, Sie möchten mit mehreren Datenquellen/Sitzungen/Rowsets arbeiten. `OpenRowset` wird in der Headerdatei der Befehls- oder Tabellenklasse deklariert:

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

Die Attribute implementieren diese Methode anders. Diese Version akzeptiert ein Sitzungsobjekt und eine Befehlszeichenfolge, die standardmäßig auf die in „db_command“ angegebene Befehlszeichenfolge festgelegt ist. Sie können auch eine andere Zeichenfolge übergeben. Wenn Sie eine `HasBookmark`-Methode definieren, legt der `OpenRowset`-Code die `DBPROP_IRowsetLocate`-Eigenschaft fest. Stellen Sie sicher, dass Sie nur dann so vorgehen, wenn Ihr Anbieter diese Eigenschaft unterstützt.

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

Diese Methode ruft einen Zeiger auf den Eigenschaftensatz des Rowsets ab. Sie können diesen Zeiger verwenden, um Eigenschaften wie `DBPROP_IRowsetChange` festzulegen. `GetRowsetProperties` wird in der Benutzerdatensatzklasse wie folgt verwendet. Sie können diesen Code ändern, um zusätzliche Rowseteigenschaften festzulegen:

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Hinweise

Sie sollten keine globale `GetRowsetProperties`-Methode definieren, weil Konflikte mit der vom Assistenten definierten Methode auftreten können. Dies ist eine vom Assistenten generierte Methode, die Sie mit Projekten mit Vorlagen und Attributen erhalten. Die Attribute fügen diesen Code nicht ein.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource und CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Hinweise

Der Assistent definiert die Methoden `OpenDataSource` und `CloseDataSource`; `OpenDataSource` ruft [CDataSource::OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring) auf.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB Consumers mithilfe eines Assistenten](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
