---
title: IOpenRowsetImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545906"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl-Klasse

Stellt eine Implementierung für die `IOpenRowset`-Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parameter

*Sessionclass*<br/>
Die von `IOpenRowsetImpl`abgeleitete Klasse.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CreateRowset](#createrowset)|Erstellt ein Rowsetobjekt. Wird nicht direkt vom Benutzer aufgerufen.|
|[OPENROWSET](#openrowset)|Öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält, und gibt es zurück. (Nicht in Atldb. Micha|

## <a name="remarks"></a>Hinweise

Die [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) -Schnittstelle ist für ein Sitzungs Objekt obligatorisch. Er wird geöffnet und gibt ein Rowset zurück, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält.

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a>Iopenrowsetimpl:: kreaterowset

Erstellt ein Rowsetobjekt. Wird nicht direkt vom Benutzer aufgerufen. Weitere Informationen finden Sie unter [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) in der *OLE DB Programmierer-Referenz.*

### <a name="syntax"></a>Syntax

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parameter

*RowsetClass*<br/>
Ein Vorlagen Klassenmember, der die Rowsetklasse des Benutzers darstellt. Wird normalerweise vom Assistenten generiert.

*prowsetobj*<br/>
vorgenommen Ein Zeiger auf ein Rowsetobjekt. In der Regel wird dieser Parameter nicht verwendet, kann jedoch verwendet werden, wenn Sie vor der Übergabe an ein COM-Objekt mehr Arbeit an dem Rowset ausführen müssen. Die Lebensdauer von *prowsetobj* wird durch *ppRowset*gebunden.

Informationen zu anderen Parametern finden Sie unter [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) in der *OLE DB Programmierer-Referenz.*

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a>Iopenrowsetimpl:: OPENROWSET

Öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle oder einem einzelnen Index enthält, und gibt es zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Hinweise

Diese Methode wurde in Atldb nicht gefunden. Micha. Sie wird vom ATL-Objekt-Assistenten erstellt, wenn Sie einen Anbieter erstellen.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)