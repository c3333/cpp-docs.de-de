---
title: IRowsetChangeImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: b069cd08814855a0528806ac6d19ed8f5beb6f37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210456"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl-Klasse

Die OLE DB Vorlagen Implementierung der [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) -Schnittstelle in der OLE DB-Spezifikation.

## <a name="syntax"></a>Syntax

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von `IRowsetChangeImpl`abgeleitete Klasse.

*Storage*<br/>
Der Benutzerdaten Satz.

*Typeinterface wurde*<br/>
Die Basisklasse für die-Schnittstelle, z. b. `IRowsetChange`.

*RowClass*<br/>
Die Speichereinheit für das Zeilen handle.

*Mapclass*<br/>
Die Speichereinheit für alle Zeilen Handles, die vom Anbieter gehalten werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods-used-with-irowsetchange"></a>Schnittstellen Methoden (mit IRowsetChange verwendet)

|||
|-|-|
|[DeleteRows](#deleterows)|Löscht Zeilen aus dem Rowset.|
|[InsertRow](#insertrow)|Fügt eine Zeile in das Rowset ein.|
|[SetData](#setdata)|Legt Datenwerte in einer oder mehreren Spalten fest.|

### <a name="implementation-method-callback"></a>Implementierungsmethode (Rückruf)

|||
|-|-|
|[FlushData](#flushdata)|Wird vom Anbieter überschrieben, um Daten in seinen Speicher zu übertragen.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle ist für sofortige Schreibvorgänge in einem Datenspeicher verantwortlich. "Immediate" bedeutet, dass diese Änderungen sofort an den Datenspeicher übertragen werden (und nicht rückgängig gemacht werden können), wenn der Endbenutzer (die Person, die den Consumer verwendet) Änderungen vornimmt.

`IRowsetChangeImpl` implementiert die OLE DB `IRowsetChange`-Schnittstelle, die das Aktualisieren von Werten von Spalten in vorhandenen Zeilen, das Löschen von Zeilen und das Einfügen neuer Zeilen ermöglicht.

Die OLE DB-Vorlagen Implementierung unterstützt alle Basis Methoden (`SetData`, `InsertRow`und `DeleteRows`).

> [!IMPORTANT]
>  Es wird dringend empfohlen, dass Sie die folgende Dokumentation lesen, bevor Sie versuchen, Ihren Anbieter zu implementieren:

- [Erstellen eines aktualisierbaren Anbieters](../../data/oledb/creating-an-updatable-provider.md)

- Kapitel 6 der *OLE DB Programmierer-Referenz*

- Sehen Sie sich auch an, wie die `RUpdateRowset`-Klasse im [Update](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) Panel-Beispiel verwendet wird.

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::D eleterows

Löscht Zeilen aus dem Rowset.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetChange::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) in der *OLE DB Programmer es Reference*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl:: InsertRow

Erstellt und Initialisiert eine neue Zeile im Rowset.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetChange:: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl:: SetData

Legt Datenwerte in einer oder mehreren Spalten fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl:: FlushData

Wird vom Anbieter überschrieben, um Daten in seinen Speicher zu übertragen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parameter

*hrowabflush*<br/>
in Handle für die Zeilen für die Daten. Der Typ dieser Zeile wird anhand des *RowClass* -Vorlagen Arguments der `IRowsetImpl`-Klasse bestimmt (standardmäßig`CSimpleRow`).

*haccessorshflush*<br/>
in Handle für den-Accessor, der Bindungs Informationen und Typinformationen im `PROVIDER_MAP` enthält (siehe [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
