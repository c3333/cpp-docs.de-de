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
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864982"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl-Klasse

Diese Klasse implementiert `IUnknown` und stellt eine Standard Implementierung der [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) -Schnittstelle bereit.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IPropertyPageImpl`abgeleitete Klasse.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl:: IPropertyPageImpl](#ipropertypageimpl)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl:: Aktivierung](#activate)|Erstellt das Dialogfeld Fenster für die Eigenschaften Seite.|
|[IPropertyPageImpl:: apply](#apply)|Wendet aktuelle Eigenschaften Seiten Werte auf die zugrunde liegenden Objekte an, die durch `SetObjects`angegeben werden. Die ATL-Implementierung gibt S_OK zurück.|
|[IPropertyPageImpl::D eaktivierung](#deactivate)|Zerstört das Fenster, das mit `Activate`erstellt wurde.|
|[IPropertyPageImpl:: getpageingefo](#getpageinfo)|Ruft Informationen zur Eigenschaften Seite ab.|
|[IPropertyPageImpl:: Help](#help)|Ruft die Windows-Hilfe für die Eigenschaften Seite auf.|
|[IPropertyPageImpl:: ispagedirty](#ispagedirty)|Gibt an, ob die Eigenschaften Seite seit der Aktivierung geändert wurde.|
|[IPropertyPageImpl:: Move](#move)|Positioniert und ändert die Größe des Dialog Felds der Eigenschaften Seite.|
|[IPropertyPageImpl:: SetDirty](#setdirty)|Markiert den Zustand der Eigenschaften Seite als geändert oder unverändert.|
|[IPropertyPageImpl:: SetObjects](#setobjects)|Stellt ein Array von `IUnknown` Zeigern für die Objekte bereit, die der Eigenschaften Seite zugeordnet sind. Diese Objekte empfangen die aktuellen Eigenschaften Seiten Werte mithilfe eines Aufrufes `Apply`.|
|[IPropertyPageImpl:: setpagesite](#setpagesite)|Stellt die Eigenschaften Seite mit einem `IPropertyPageSite` Zeiger bereit, über den die Eigenschaften Seite mit dem Eigenschaften Rahmen kommuniziert.|
|[IPropertyPageImpl:: Show](#show)|Ermöglicht, dass das Dialogfeld Eigenschaften Seite sichtbar oder unsichtbar ist.|
|[IPropertyPageImpl:: TranslateAccelerator](#translateaccelerator)|Verarbeitet einen angegebenen Tastatur Strich.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPageImpl:: m_bDirty](#m_bdirty)|Gibt an, ob sich der Zustand der Eigenschaften Seite geändert hat.|
|[IPropertyPageImpl:: m_dwDocString](#m_dwdocstring)|Speichert den Ressourcen Bezeichner, der der Zeichenfolge zugeordnet ist, die die Eigenschaften Seite beschreibt.|
|[IPropertyPageImpl:: m_dwHelpContext](#m_dwhelpcontext)|Speichert den Kontext Bezeichner für das Hilfethema, das der Eigenschaften Seite zugeordnet ist.|
|[IPropertyPageImpl:: m_dwHelpFile](#m_dwhelpfile)|Speichert den Ressourcen Bezeichner, der dem Namen der Hilfedatei zugeordnet ist, die die Eigenschaften Seite beschreibt.|
|[IPropertyPageImpl:: m_dwTitle](#m_dwtitle)|Speichert den Ressourcen Bezeichner, der der Text Zeichenfolge zugeordnet ist, die auf der Registerkarte für die Eigenschaften Seite angezeigt wird.|
|[IPropertyPageImpl:: m_nObjects](#m_nobjects)|Speichert die Anzahl der-Objekte, die der Eigenschaften Seite zugeordnet sind.|
|[IPropertyPageImpl:: m_pPageSite](#m_ppagesite)|Verweist auf die `IPropertyPageSite`-Schnittstelle, über die die Eigenschaften Seite mit dem Eigenschaften Rahmen kommuniziert.|
|[IPropertyPageImpl:: m_ppUnk](#m_ppunk)|Verweist auf ein Array von `IUnknown` Zeigern auf die-Objekte, die der Eigenschaften Seite zugeordnet sind.|
|[IPropertyPageImpl:: m_size](#m_size)|Speichert die Höhe und Breite des Dialog Felds der Eigenschaften Seite in Pixel.|

## <a name="remarks"></a>Bemerkungen

Die [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) -Schnittstelle ermöglicht es einem Objekt, eine bestimmte Eigenschaften Seite innerhalb eines Eigenschaften Blatts zu verwalten. Class `IPropertyPageImpl` stellt eine Standard Implementierung dieser Schnittstelle bereit und implementiert `IUnknown`, indem Informationen in Debugbuilds an das dumpgerät gesendet werden.

**Zugehörige Artikel** [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md), [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlctl. h

##  <a name="activate"></a>IPropertyPageImpl:: Aktivierung

Erstellt das Dialogfeld Fenster für die Eigenschaften Seite.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist das Dialogfeld immer ohne Modus, unabhängig vom Wert des *bmodal* -Parameters.

Weitere Informationen finden Sie unter [IPropertyPage:: Aktivierung](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) in der Windows SDK.

##  <a name="apply"></a>IPropertyPageImpl:: apply

Wendet aktuelle Eigenschaften Seiten Werte auf die zugrunde liegenden Objekte an, die durch `SetObjects`angegeben werden.

```
HRESULT Apply();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage:: apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) in the Windows SDK.

##  <a name="deactivate"></a>IPropertyPageImpl::D eaktivierung

Zerstört das mit [aktivieren](#activate)erstellte Dialogfeld Fenster.

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage::D eaktivierungs](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) in der Windows SDK.

##  <a name="getpageinfo"></a>IPropertyPageImpl:: getpageingefo

Füllt die *ppageinfo* -Struktur mit Informationen aus, die in den Datenmembern enthalten sind.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Bemerkungen

`GetPageInfo` lädt die [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)und [m_dwTitle](#m_dwtitle)zugeordneten Zeichen folgen Ressourcen.

Weitere Informationen finden Sie im Windows SDK unter [IPropertyPage:: getpageingefo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) .

##  <a name="help"></a>IPropertyPageImpl:: Help

Ruft die Windows-Hilfe für die Eigenschaften Seite auf.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage:: Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) im Windows SDK.

##  <a name="ipropertypageimpl"></a>IPropertyPageImpl:: IPropertyPageImpl

Der Konstruktor.

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert alle Datenmember.

##  <a name="ispagedirty"></a>IPropertyPageImpl:: ispagedirty

Gibt an, ob die Eigenschaften Seite seit der Aktivierung geändert wurde.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Bemerkungen

`IsPageDirty` gibt S_OK zurück, wenn die Seite seit der Aktivierung geändert wurde.

##  <a name="m_bdirty"></a>IPropertyPageImpl:: m_bDirty

Gibt an, ob sich der Zustand der Eigenschaften Seite geändert hat.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl:: m_nObjects

Speichert die Anzahl der-Objekte, die der Eigenschaften Seite zugeordnet sind.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl:: m_dwHelpContext

Speichert den Kontext Bezeichner für das Hilfethema, das der Eigenschaften Seite zugeordnet ist.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>IPropertyPageImpl:: m_dwDocString

Speichert den Ressourcen Bezeichner, der der Zeichenfolge zugeordnet ist, die die Eigenschaften Seite beschreibt.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl:: m_dwHelpFile

Speichert den Ressourcen Bezeichner, der dem Namen der Hilfedatei zugeordnet ist, die die Eigenschaften Seite beschreibt.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl:: m_dwTitle

Speichert den Ressourcen Bezeichner, der der Text Zeichenfolge zugeordnet ist, die auf der Registerkarte für die Eigenschaften Seite angezeigt wird.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>IPropertyPageImpl:: m_pPageSite

Verweist auf die [ipropertypagesite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) -Schnittstelle, über die die Eigenschaften Seite mit dem Eigenschaften Rahmen kommuniziert.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl:: m_ppUnk

Verweist auf ein Array von `IUnknown` Zeigern auf die-Objekte, die der Eigenschaften Seite zugeordnet sind.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl:: m_size

Speichert die Höhe und Breite des Dialog Felds der Eigenschaften Seite in Pixel.

```
SIZE m_size;
```

##  <a name="move"></a>IPropertyPageImpl:: Move

Positioniert und ändert die Größe des Dialog Felds der Eigenschaften Seite.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Windows SDK unter [IPropertyPage:: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) .

##  <a name="setdirty"></a>IPropertyPageImpl:: SetDirty

Markiert den Status der Eigenschaften Seite je nach Wert von *bdirty*als geändert oder unverändert.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parameter

*bdirty*<br/>
in TRUE gibt an, dass der Zustand der Eigenschaften Seite als geändert markiert wird. Andernfalls wird Sie als unverändert markiert.

### <a name="remarks"></a>Bemerkungen

Bei Bedarf informiert `SetDirty` den Frame darüber, dass die Eigenschaften Seite geändert wurde.

##  <a name="setobjects"></a>IPropertyPageImpl:: SetObjects

Stellt ein Array von `IUnknown` Zeigern für die Objekte bereit, die der Eigenschaften Seite zugeordnet sind.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage:: abtobjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) in der Windows SDK.

##  <a name="setpagesite"></a>IPropertyPageImpl:: setpagesite

Stellt die Eigenschaften Seite mit einem [ipropertypagesite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) -Zeiger bereit, über den die Eigenschaften Seite mit dem Eigenschaften Rahmen kommuniziert.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IPropertyPage:: setpagesite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) im Windows SDK.

##  <a name="show"></a>IPropertyPageImpl:: Show

Ermöglicht, dass das Dialogfeld Eigenschaften Seite sichtbar oder unsichtbar ist.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage:: Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) in der Windows SDK.

##  <a name="translateaccelerator"></a>IPropertyPageImpl:: TranslateAccelerator

Verarbeitet den in `pMsg`angegebenen Tastatur Strich.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Windows SDK unter [IPropertyPage:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) .

## <a name="see-also"></a>Weitere Informationen

[IPropertyPage2Impl-Klasse](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl-Klasse](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl-Klasse](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
