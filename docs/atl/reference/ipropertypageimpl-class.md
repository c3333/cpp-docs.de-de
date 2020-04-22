---
title: IPropertyPageImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 154bfb5beb258ff26649f44f0bd4c23fb8708977
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745866"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt eine Standardimplementierung der [IPropertyPage-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPropertyPageImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl::Aktivieren](#activate)|Erstellt das Dialogfeldfenster für die Eigenschaftenseite.|
|[IPropertyPageImpl::Bewerben](#apply)|Wendet aktuelle Eigenschaftenseitenwerte auf die `SetObjects`zugrunde liegenden Objekte an, die über angegeben werden. Die ATL-Implementierung gibt S_OK zurück.|
|[IPropertyPageImpl::Deactivate](#deactivate)|Zerstört das Fenster, `Activate`das mit erstellt wurde.|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Ruft Informationen zur Eigenschaftenseite ab.|
|[IPropertyPageImpl::Hilfe](#help)|Ruft die Windows-Hilfe für die Eigenschaftenseite auf.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Gibt an, ob sich die Eigenschaftenseite seit der Aktivierung geändert hat.|
|[IPropertyPageImpl::Verschieben](#move)|Positioniert und ändert die Größe des Dialogfelds eigenschaftenseite.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Kennzeichnet den Status der Eigenschaftenseite als geändert oder unverändert.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Stellt ein `IUnknown` Array von Zeigern für die Objekte bereit, die der Eigenschaftenseite zugeordnet sind. Diese Objekte erhalten die aktuellen Eigenschaftenseitenwerte durch einen Aufruf von `Apply`.|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Stellt der Eigenschaftenseite `IPropertyPageSite` einen Zeiger zur Verfügung, über den die Eigenschaftenseite mit dem Eigenschaftenrahmen kommuniziert.|
|[IPropertyPageImpl::Anzeigen](#show)|Macht das Dialogfeld Eigenschaftenseite sichtbar oder unsichtbar.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Verarbeitet einen angegebenen Tastenanschlag.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Gibt an, ob sich der Status der Eigenschaftenseite geändert hat.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Speichert den Ressourcenbezeichner, der der Textzeichenfolge zugeordnet ist, die die Eigenschaftenseite beschreibt.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Speichert den Kontextbezeichner für das Hilfethema, das der Eigenschaftenseite zugeordnet ist.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Speichert den Ressourcenbezeichner, der dem Namen der Hilfedatei zugeordnet ist, die die Eigenschaftenseite beschreibt.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Speichert den Ressourcenbezeichner, der der Textzeichenfolge zugeordnet ist, die auf der Registerkarte für die Eigenschaftenseite angezeigt wird.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Speichert die Anzahl der Objekte, die der Eigenschaftenseite zugeordnet sind.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Zeigt auf `IPropertyPageSite` die Schnittstelle, über die die Eigenschaftenseite mit dem Eigenschaftenrahmen kommuniziert.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Zeigt auf ein `IUnknown` Array von Zeigern auf die Objekte, die der Eigenschaftenseite zugeordnet sind.|
|[IPropertyPageImpl::m_size](#m_size)|Speichert die Höhe und Breite des Dialogfelds der Eigenschaftenseite in Pixeln.|

## <a name="remarks"></a>Bemerkungen

Die [IPropertyPage-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) ermöglicht es einem Objekt, eine bestimmte Eigenschaftenseite innerhalb eines Eigenschaftenblatts zu verwalten. Die `IPropertyPageImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageImpl::Aktivieren

Erstellt das Dialogfeldfenster für die Eigenschaftenseite.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist das Dialogfeld immer moduslos, unabhängig vom Wert des *Parameters bModal.*

Siehe [IPropertyPage::Aktivieren](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) im Windows SDK.

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertyPageImpl::Bewerben

Wendet aktuelle Eigenschaftenseitenwerte auf die `SetObjects`zugrunde liegenden Objekte an, die über angegeben werden.

```
HRESULT Apply();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::Anwenden](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) im Windows SDK.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Deactivate

Zerstört das mit [Activate](#activate)erstellte Dialogfeldfensterfenster.

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::Deactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) im Windows SDK.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Füllt die *pPageInfo-Struktur* mit Informationen, die in den Datenmembern enthalten sind.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Bemerkungen

`GetPageInfo`lädt die Zeichenfolgenressourcen, [die m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)und [m_dwTitle](#m_dwtitle)zugeordnet sind.

Siehe [IPropertyPage::GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) im Windows SDK.

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Hilfe

Ruft die Windows-Hilfe für die Eigenschaftenseite auf.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage::Hilfe](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) im Windows SDK.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

Der Konstruktor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert alle Datenmember.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Gibt an, ob sich die Eigenschaftenseite seit der Aktivierung geändert hat.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Bemerkungen

`IsPageDirty`gibt S_OK zurück, wenn sich die Seite seit der Aktivierung geändert hat.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty

Gibt an, ob sich der Status der Eigenschaftenseite geändert hat.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

Speichert die Anzahl der Objekte, die der Eigenschaftenseite zugeordnet sind.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

Speichert den Kontextbezeichner für das Hilfethema, das der Eigenschaftenseite zugeordnet ist.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString

Speichert den Ressourcenbezeichner, der der Textzeichenfolge zugeordnet ist, die die Eigenschaftenseite beschreibt.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

Speichert den Ressourcenbezeichner, der dem Namen der Hilfedatei zugeordnet ist, die die Eigenschaftenseite beschreibt.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

Speichert den Ressourcenbezeichner, der der Textzeichenfolge zugeordnet ist, die auf der Registerkarte für die Eigenschaftenseite angezeigt wird.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite

Verweist auf die [IPropertyPageSite-Schnittstelle,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) über die die Eigenschaftenseite mit dem Eigenschaftenframe kommuniziert.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

Zeigt auf ein `IUnknown` Array von Zeigern auf die Objekte, die der Eigenschaftenseite zugeordnet sind.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageImpl::m_size

Speichert die Höhe und Breite des Dialogfelds der Eigenschaftenseite in Pixeln.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>IPropertyPageImpl::Verschieben

Positioniert und ändert die Größe des Dialogfelds eigenschaftenseite.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::Verschieben](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) im Windows SDK.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>IPropertyPageImpl::SetDirty

Flags den Status der Eigenschaftenseite als geändert oder unverändert, abhängig vom Wert von *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parameter

*bDirty*<br/>
[in] Wenn TRUE, wird der Status der Eigenschaftenseite als geändert markiert. Andernfalls wird sie als unverändert markiert.

### <a name="remarks"></a>Bemerkungen

Informiert Sie `SetDirty` den Rahmen ggf. darüber, dass sich die Eigenschaftenseite geändert hat.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertyPageImpl::SetObjects

Stellt ein `IUnknown` Array von Zeigern für die Objekte bereit, die der Eigenschaftenseite zugeordnet sind.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) im Windows SDK.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

Stellt die Eigenschaftenseite mit einem [IPropertyPageSite-Zeiger](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) bereit, über den die Eigenschaftenseite mit dem Eigenschaftenframe kommuniziert.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) im Windows SDK.

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageImpl::Anzeigen

Macht das Dialogfeld Eigenschaftenseite sichtbar oder unsichtbar.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::Im](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) Windows SDK anzeigen.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Verarbeitet den in `pMsg`angegebenen Tastenanschlag.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[IPropertyPage2Impl-Klasse](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl-Klasse](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl-Klasse](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
