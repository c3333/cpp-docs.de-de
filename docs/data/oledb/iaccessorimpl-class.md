---
title: IAccessorImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: f1865089100ac7f60e8c011e72eedb3d0a3f8470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545990"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl-Klasse

Stellt eine Implementierung der [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Rowset oder die Befehls Objektklasse.

*BindType*<br/>
Speichereinheit für Bindungs Informationen. Der Standardwert ist die `ATLBINDINGS` Struktur (siehe Atldb. h).

*Bindingvector*<br/>
Speichereinheit für Spalten Informationen. Der Standardwert ist "", wobei das Schlüsselelement ein HACCESSOR- [Wert ist und](../../atl/reference/catlmap-class.md) das Value-Element ein Zeiger auf eine `BindType`-Struktur ist.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|Der Konstruktor.|

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Fügt einem vorhandenen Accessor einen Verweiszähler hinzu.|
|[CreateAccessor](#createaccessor)|Erstellt einen Accessor aus einem Satz von Bindungen.|
|[GetBindings](#getbindings)|Gibt die Bindungen in einem Accessor zurück.|
|[ReleaseAccessor](#releaseaccessor)|Gibt einen Accessor frei.|

## <a name="remarks"></a>Hinweise

Dies ist für Rowsets und Befehle obligatorisch. OLE DB erfordert, dass Anbieter einen HACCESSOR implementieren, bei dem es sich um ein Tag für ein Array von [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) -Strukturen handelt. Die von `IAccessorImpl` bereitgestellten haccessoren sind Adressen der `BindType` Strukturen. Standardmäßig ist `BindType` als `ATLBINDINGS` in der Vorlagen Definition `IAccessorImpl`definiert. `BindType` stellt einen Mechanismus bereit, der von `IAccessorImpl` verwendet wird, um die Anzahl der Elemente im `DBBINDING` Array sowie einen Verweis Zähler und accessorflags zu verfolgen.

## <a name="iaccessorimpliaccessorimpl"></a><a name="iaccessorimpl"></a>IAccessorImpl:: IAccessorImpl

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
IAccessorImpl();
```

## <a name="iaccessorimpladdrefaccessor"></a><a name="addrefaccessor"></a>IAccessorImpl:: adressariessor

Fügt einem vorhandenen Accessor einen Verweiszähler hinzu.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parameter

Weitere [Informationen](/previous-versions/windows/desktop/ms714978(v=vs.85)) finden Sie in der *OLE DB Programmierer-Referenz*.

## <a name="iaccessorimplcreateaccessor"></a><a name="createaccessor"></a>IAccessorImpl::-accateaccessor

Erstellt einen Accessor aus einem Satz von Bindungen.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IAccessor:: erkreateaccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="iaccessorimplgetbindings"></a><a name="getbindings"></a>IAccessorImpl:: getbindungen

Gibt die grundlegenden Spalten Bindungen vom Consumer in einem Accessor zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IAccessor:: getbindungen](/previous-versions/windows/desktop/ms721253(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="iaccessorimplreleaseaccessor"></a><a name="releaseaccessor"></a>IAccessorImpl:: ReleaseAccessor

Gibt einen Accessor frei.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IAccessor:: ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)