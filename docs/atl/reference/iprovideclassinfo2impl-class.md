---
title: IProvideClassInfo2Impl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329570"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl-Klasse

Diese Klasse stellt eine Standardimplementierung der [IProvideClassInfo-](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) und [IProvideClassInfo2-Methoden](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) bereit.

## <a name="syntax"></a>Syntax

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>Parameter

*pcoclsid*<br/>
Ein Zeiger auf den Bezeichner der Coclass.

*psrcid*<br/>
Ein Zeiger auf den Bezeichner für die standardmäßige ausgehende Dispinterface der Co-Klasse.

*plibid*<br/>
Ein Zeiger auf die LIBID der Typbibliothek, die Informationen über die Schnittstelle enthält. Standardmäßig wird die Typbibliothek auf Serverebene übergeben.

*wMajor*<br/>
Die Hauptversion der Typbibliothek Der Standardwert ist 1.

*wMinor*<br/>
Die Nebenversion der Typbibliothek Der Standardwert ist 0.

*tihclass*<br/>
Die Klasse, die zum Verwalten der Typinformationen der Coclass verwendet wird. Der Standardwert ist `CComTypeInfoHolder`.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Ruft einen `ITypeInfo` Zeiger auf die Typinformationen der Coclass ab.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Ruft die GUID für die ausgehende Dispinterface des Objekts ab.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Verwaltet die Typinformationen für die Coclass.|

## <a name="remarks"></a>Bemerkungen

Die [IProvideClassInfo2-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) erweitert [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) durch Hinzufügen der `GetGUID` Methode. Mit dieser Methode kann ein Client die ausgehende Schnittstellen-IID eines Objekts für den Standardereignissatz abrufen. Die `IProvideClassInfo2Impl` Klasse stellt eine `IProvideClassInfo` `IProvideClassInfo2` Standardimplementierung der und -methoden bereit.

`IProvideClassInfo2Impl`enthält einen statischen `CComTypeInfoHolder` Member des Typs, der die Typinformationen für die Coclass verwaltet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo

Ruft einen `ITypeInfo` Zeiger auf die Typinformationen der Coclass ab.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IProvideClassInfo::GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) im Windows SDK.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID

Ruft die GUID für die ausgehende Dispinterface des Objekts ab.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IProvideClassInfo2::GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) im Windows SDK.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

Der Konstruktor.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Bemerkungen

Ruft `AddRef` das [_tih](#_tih) Mitglied an. Der Destruktor ruft `Release` auf.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih

Dieser statische Datenmember ist eine Instanz des Klassenvorlagenparameters *tihclass*, der standardmäßig `CComTypeInfoHolder`ist.

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Bemerkungen

`_tih`verwaltet die Typinformationen für die Coclass.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
