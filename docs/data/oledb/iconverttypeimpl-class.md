---
title: IConvertTypeImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210690"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl-Klasse

Stellt eine Implementierung der [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IConvertTypeImpl`abgeleitete Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[CanConvert](#canconvert)|Enthält Informationen zur Verfügbarkeit von Typkonvertierungen in einem Befehl oder einem Rowset.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle ist für Befehle, Rowsets und Indexrowsets obligatorisch. `IConvertTypeImpl` implementiert die-Schnittstelle durch Delegieren an das von OLE DB bereitgestellte Konvertierungs Objekt.

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>Iconverttypeimpl:: CanConvert

Enthält Informationen zur Verfügbarkeit von Typkonvertierungen in einem Befehl oder einem Rowset.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IConvertType:: CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Verwendet OLE DB Datenkonvertierung in `MSADC.DLL`.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
