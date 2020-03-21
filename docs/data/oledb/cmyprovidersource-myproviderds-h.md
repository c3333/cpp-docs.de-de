---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 60324ae914c9490144a715e06323ee6d184ce201
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079733"
---
# <a name="ccustomsource-customdsh"></a>Ccustomsource (customds. h)

Die Anbieter Klassen verwenden die mehrfache Vererbung. Der folgende Code zeigt die Vererbungs Kette für das Datenquellen Objekt:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Alle COM-Komponenten werden von `CComObjectRootEx` und `CComCoClass`abgeleitet. `CComObjectRootEx` stellt die gesamte Implementierung für die `IUnknown`-Schnittstelle bereit. Er kann jedes Threading Modell verarbeiten. `CComCoClass` behandelt alle erforderlichen Fehler Unterstützung. Wenn Sie umfangreichere Fehlerinformationen an den Client senden möchten, können Sie einige der Fehler-APIs in `CComCoClass`verwenden.

Das Datenquellen Objekt erbt auch von mehreren "Impl"-Klassen. Jede Klasse stellt die Implementierung für eine Schnittstelle bereit. Das Datenquellen Objekt implementiert die Schnittstellen `IPersist`, `IDBProperties`, `IDBInitialize`und `IDBCreateSession`. Jede Schnittstelle ist erforderlich, um OLE DB, um das Datenquellen Objekt zu implementieren. Sie können sich entscheiden, bestimmte Funktionen zu unterstützen oder nicht zu unterstützen, indem Sie von einer dieser impl-Klassen erben oder nicht. Wenn Sie die `IDBDataSourceAdmin`-Schnittstelle unterstützen möchten, erben Sie von der `IDBDataSourceAdminImpl`-Klasse, um die erforderliche Funktionalität zu erhalten.

## <a name="com-map"></a>COM-Zuordnung

Wenn der Client `QueryInterface` für eine Schnittstelle in der Datenquelle aufruft, durchläuft er die folgende COM-Zuordnung:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Alle COM-Komponenten werden von `CComObjectRootEx` und `CComCoClass`abgeleitet. `CComObjectRootEx` stellt die gesamte Implementierung für die `IUnknown`-Schnittstelle bereit. Er kann jedes Threading Modell verarbeiten. `CComCoClass` behandelt alle erforderlichen Fehler Unterstützung. Wenn Sie umfangreichere Fehlerinformationen an den Client senden möchten, können Sie einige der Fehler-APIs in `CComCoClass`verwenden.

Das Datenquellen Objekt erbt auch von mehreren "Impl"-Klassen. Jede Klasse stellt die Implementierung für eine Schnittstelle bereit. Das Datenquellen Objekt implementiert die Schnittstellen `IPersist`, `IDBProperties`, `IDBInitialize`und `IDBCreateSession`. Jede Schnittstelle ist erforderlich, um OLE DB, um das Datenquellen Objekt zu implementieren. Sie können sich entscheiden, bestimmte Funktionen zu unterstützen oder nicht zu unterstützen, indem Sie von einer dieser impl-Klassen erben oder nicht. Wenn Sie die `IDBDataSourceAdmin`-Schnittstelle unterstützen möchten, erben Sie von der `IDBDataSourceAdminImpl`-Klasse, um die erforderliche Funktionalität zu erhalten.

## <a name="com-map"></a>COM-Zuordnung

Wenn der Client `QueryInterface` für eine Schnittstelle in der Datenquelle aufruft, durchläuft er die folgende COM-Zuordnung:

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

Die COM_INTERFACE_ENTRY-Makros stammen aus ATL und geben die Implementierung von `QueryInterface` in `CComObjectRootEx` an, um die entsprechenden Schnittstellen zurückzugeben.

## <a name="property-map"></a>Eigenschaften Zuordnung

Die Eigenschaften Zuordnung gibt alle vom Anbieter zugewiesenen Eigenschaften an:

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

Eigenschaften in OLE DB werden gruppiert. Das Datenquellen Objekt verfügt über zwei Gruppen von Eigenschaften: eine für den DBPROPSET_DATASOURCEINFO Satz und eine für den DBPROPSET_DBINIT Satz. Der DBPROPSET_DATASOURCEINFO Satz entspricht Eigenschaften des Anbieters und seiner Datenquelle. Der DBPROPSET_DBINIT Satz entspricht den bei der Initialisierung verwendeten Eigenschaften. Die OLE DB-Anbieter Vorlagen verarbeiten diese Sätze mit den PROPERTY_SET-Makros. Die Makros erstellen einen-Block, der ein Array von Eigenschaften enthält. Wenn der Client die `IDBProperties`-Schnittstelle aufruft, verwendet der Anbieter die Eigenschaften Zuordnung.

Sie müssen nicht jede Eigenschaft in der Spezifikation implementieren. Sie müssen jedoch die erforderlichen Eigenschaften unterstützen. Weitere Informationen finden Sie in der Konformitäts Spezifikation der Ebene 0. Wenn Sie eine Eigenschaft nicht unterstützen möchten, können Sie Sie aus der Zuordnung entfernen. Wenn Sie eine Eigenschaft unterstützen möchten, fügen Sie Sie mit einem PROPERTY_INFO_ENTRY-Makro in die Zuordnung ein. Das Makro entspricht der `UPROPINFO` Struktur, wie im folgenden Code gezeigt:

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

Jedes-Element in der-Struktur stellt Informationen zur Behandlung der-Eigenschaft dar. Sie enthält eine `DBPROPID`, um die GUID und die ID für die Eigenschaft zu bestimmen. Sie enthält auch Einträge, um den Typ und den Wert der Eigenschaft zu bestimmen.

Wenn Sie den Standardwert einer Eigenschaft ändern möchten (Beachten Sie, dass ein Consumer jederzeit den Wert einer beschreibbaren Eigenschaft ändern kann), können Sie entweder das PROPERTY_INFO_ENTRY_VALUE-oder PROPERTY_INFO_ENTRY_EX-Makro verwenden. Mit diesen Makros können Sie einen Wert für eine entsprechende Eigenschaft angeben. Das PROPERTY_INFO_ENTRY_VALUE-Makro ist eine Kurznotiz, die es Ihnen ermöglicht, den Wert zu ändern. Das PROPERTY_INFO_ENTRY_VALUE-Makro ruft das PROPERTY_INFO_ENTRY_EX-Makro auf. Mit diesem Makro können Sie alle Attribute in der `UPROPINFO` Struktur hinzufügen oder ändern.

Wenn Sie einen eigenen Eigenschaften Satz definieren möchten, können Sie diesen hinzufügen, indem Sie eine zusätzliche Kombination aus BEGIN_PROPSET_MAP/END_PROPSET_MAP erstellen. Definieren Sie eine GUID für den Eigenschaften Satz, und definieren Sie dann Ihre eigenen Eigenschaften. Wenn Sie über anbieterspezifische Eigenschaften verfügen, fügen Sie Sie einem neuen Eigenschaften Satz hinzu, anstatt einen vorhandenen zu verwenden. Dadurch werden Probleme in späteren Versionen von OLE DB vermieden.

## <a name="user-defined-property-sets"></a>Benutzerdefinierte Eigenschaften Sätze

Visual C++ unterstützt benutzerdefinierte Eigenschaften Sätze. Sie müssen `GetProperties` oder `GetPropertyInfo`nicht außer Kraft setzen. Stattdessen erkennen die Vorlagen jeden benutzerdefinierten Eigenschaften Satz und fügen ihn dem entsprechenden-Objekt hinzu.

Wenn Sie einen benutzerdefinierten Eigenschaften Satz haben, der zur Initialisierungs Zeit verfügbar sein muss (d. h. bevor der Consumer `IDBInitialize::Initialize`aufruft), können Sie diesen mit dem UPROPSET_USERINIT-Flag zusammen mit dem BEGIN_PROPERTY_SET_EX-Makro angeben. Der Eigenschaften Satz muss sich im Datenquellen Objekt befinden, damit dies funktioniert (wie die OLE DB Spezifikation erfordert). Beispiel:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>Weitere Informationen

[Vom Anbieter-Assistenten generierte Dateien](../../data/oledb/provider-wizard-generated-files.md)<br/>
