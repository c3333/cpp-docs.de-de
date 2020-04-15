---
title: IDataObjectImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329844"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl-Klasse

Diese Klasse stellt Methoden zum Unterstützen der einheitlichen Datenübertragung und zum Verwalten von Verbindungen bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IDataObjectImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IDataObjectImpl::DAdvise](#dadvise)|Stellt eine Verbindung zwischen dem Datenobjekt und einer Beratungssenke her. Auf diese Weise kann die Beratungssenke Benachrichtigungen über Änderungen am Objekt erhalten.|
|[IDataObjectImpl::DUnadvise](#dunadvise)|Beendet eine zuvor über `DAdvise`hergestellte Verbindung .|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Erstellt einen Enumerator, um die aktuellen Advise-Verbindungen zu durchlaufen.|
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Erstellt einen Enumerator, um die `FORMATETC`-Strukturen zu durchlaufen, die vom Datenobjekt unterstützt werden. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::FireDataChange](#firedatachange)|Sendet eine Änderungsbenachrichtigung an jede Beratungssenke zurück.|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Ruft eine logisch `FORMATETC` äquivalente Struktur zu einer komplexeren Struktur ab. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::GetData](#getdata)|Überträgt Daten vom Datenobjekt zum Client. Die Daten werden `FORMATETC` in einer Struktur `STGMEDIUM` beschrieben und durch eine Struktur übertragen.|
|[IDataObjectImpl::GetDataHere](#getdatahere)|Ähnlich `GetData`wie , außer der `STGMEDIUM` Client muss die Struktur zuweisen. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::QueryGetData](#querygetdata)|Bestimmt, ob das Datenobjekt eine bestimmte `FORMATETC`-Struktur für die Übertragung von Daten unterstützt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IDataObjectImpl::SetData](#setdata)|Überträgt Daten vom Client zum Datenobjekt. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Die [IDataObject-Schnittstelle](/windows/win32/api/objidl/nn-objidl-idataobject) stellt Methoden zur Unterstützung der einheitlichen Datenübertragung bereit. `IDataObject`verwendet die Standardformatstrukturen [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) und [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) zum Abrufen und Speichern von Daten.

`IDataObject`verwaltet auch Verbindungen, um Senken zur Behandlung von Datenänderungsbenachrichtigungen zu beraten. Damit der Client Datenänderungsbenachrichtigungen vom Datenobjekt erhält, muss der Client die [IAdviseSink-Schnittstelle](/windows/win32/api/objidl/nn-objidl-iadvisesink) für ein Objekt implementieren, das als Beratungssenke bezeichnet wird. Wenn der Client `IDataObject::DAdvise`dann aufruft, wird eine Verbindung zwischen dem Datenobjekt und der Beratungssenke hergestellt.

Die `IDataObjectImpl` Klasse stellt `IDataObject` eine Standardimplementierung von und implementiert, `IUnknown` indem Informationen an das Dump-Gerät in Debugbuilds gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl::DAdvise

Stellt eine Verbindung zwischen dem Datenobjekt und einer Beratungssenke her.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Bemerkungen

Auf diese Weise kann die Beratungssenke Benachrichtigungen über Änderungen am Objekt erhalten.

Um die Verbindung zu beenden, rufen Sie [DUnadvise](#dunadvise)auf.

Siehe [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) im Windows SDK.

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl::DUnadvise

Beendet eine zuvor über [DAdvise](#dadvise)hergestellte Verbindung .

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) im Windows SDK.

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

Erstellt einen Enumerator, um die aktuellen Advise-Verbindungen zu durchlaufen.

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) im Windows SDK.

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc

Erstellt einen Enumerator, um die `FORMATETC`-Strukturen zu durchlaufen, die vom Datenobjekt unterstützt werden.

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

Sendet eine Änderungsbenachrichtigung an jede Beratungssenke zurück, die derzeit verwaltet wird.

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

Ruft eine logisch `FORMATETC` äquivalente Struktur zu einer komplexeren Struktur ab.

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) im Windows SDK.

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl::GetData

Überträgt Daten vom Datenobjekt zum Client.

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>Bemerkungen

Der Parameter *pformatetcIn* muss einen Speichermediumtyp von TYMED_MFPICT angeben.

Siehe [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) im Windows SDK.

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl::GetDataHere

Ähnlich `GetData`wie , außer der `STGMEDIUM` Client muss die Struktur zuweisen.

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) im Windows SDK.

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

Bestimmt, ob das Datenobjekt eine bestimmte `FORMATETC`-Struktur für die Übertragung von Daten unterstützt.

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) im Windows SDK.

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl::SetData

Überträgt Daten vom Client zum Datenobjekt.

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IDataObject::SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
