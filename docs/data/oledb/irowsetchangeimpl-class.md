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
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376946"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl-Klasse

Die OLE DB Templates-Implementierung der [IRowsetChange-Schnittstelle](/previous-versions/windows/desktop/ms715790(v=vs.85)) in der OLE DB-Spezifikation.

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
Eine Klasse, `IRowsetChangeImpl`die von abgeleitet ist.

*Storage*<br/>
Der Benutzerdatensatz.

*BaseInterface*<br/>
Die Basisklasse für die `IRowsetChange`Schnittstelle, z. B. .

*RowClass*<br/>
Die Speichereinheit für das Zeilenhandle.

*MapClass*<br/>
Die Speichereinheit für alle Zeilenhandles, die sich im Besitz des Anbieters befinden.

## <a name="requirements"></a>Anforderungen

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="interface-methods-used-with-irowsetchange"></a>Schnittstellenmethoden (verwendet mit IRowsetChange)

|||
|-|-|
|[Deleterows](#deleterows)|Löscht Zeilen aus dem Rowset.|
|[InsertRow](#insertrow)|Fügt eine Zeile in das Rowset ein.|
|[Setdata](#setdata)|Legt Datenwerte in einer oder mehreren Spalten fest.|

### <a name="implementation-method-callback"></a>Implementierungsmethode (Callback)

|||
|-|-|
|[Flushdata](#flushdata)|Vom Anbieter überschrieben, um Daten in seinen Speicher zu übertragen.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle ist für sofortige Schreibvorgänge in einen Datenspeicher verantwortlich. "Sofort" bedeutet, dass, wenn der Endbenutzer (die Person, die den Verbraucher verwendet) Änderungen vornimmt, diese Änderungen sofort an den Datenspeicher übertragen werden (und nicht rückgängig gemacht werden können).

`IRowsetChangeImpl`implementiert die OLE `IRowsetChange` DB-Schnittstelle, die das Aktualisieren von Werten von Spalten in vorhandenen Zeilen, das Löschen von Zeilen und das Einfügen neuer Zeilen ermöglicht.

Die OLE DB Templates-Implementierung unterstützt`SetData` `InsertRow`alle `DeleteRows`Basismethoden ( , , und ).

> [!IMPORTANT]
> Es wird dringend empfohlen, die folgende Dokumentation zu lesen, bevor Sie versuchen, Ihren Anbieter zu implementieren:

- [Erstellen eines updatable-Anbieters](../../data/oledb/creating-an-updatable-provider.md)

- Kapitel 6 der Referenz des *OLE DB-Programmierers*

- Sehen Sie `RUpdateRowset` auch, wie die Klasse im [UpdatePV-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) verwendet wird.

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::DeleteRows

Löscht Zeilen aus dem Rowset.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parameter

Siehe [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl::InsertRow

Erstellt und initialisiert eine neue Zeile im Rowset.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parameter

Siehe [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl::SetData

Legt Datenwerte in einer oder mehreren Spalten fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parameter

Siehe [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl::FlushData

Vom Anbieter überschrieben, um Daten in seinen Speicher zu übertragen.

### <a name="syntax"></a>Syntax

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parameter

*hRowToFlush*<br/>
[in] Behandeln Sie die Zeilen für die Daten. Der Typ dieser Zeile wird aus dem *RowClass-Vorlagenargument* der `IRowsetImpl` Klasse bestimmt (standardmäßig).`CSimpleRow`

*hAccessorToFlush*<br/>
[in] Handle an den Accessor, der Bindungsinformationen `PROVIDER_MAP` und Typinformationen in seinem enthält (siehe [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
