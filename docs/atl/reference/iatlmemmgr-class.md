---
title: IAtlMemMgr-Klasse
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: c296c9de79c305d0f7d2f135f250d181d3cd667a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330057"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr-Klasse

Diese Klasse stellt die Schnittstelle zu einem Speicher-Manager dar.

## <a name="syntax"></a>Syntax

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Zuordnen](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[Kostenlos](#free)|Rufen Sie diese Methode auf, um einen Speicherblock freizugeben.|
|[GetSize](#getsize)|Rufen Sie diese Methode auf, um die Größe eines zugewiesenen Speicherblocks abzurufen.|
|[Reservieren](#reallocate)|Rufen Sie diese Methode auf, um einen Speicherblock neu zuzuweisen.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird von [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)oder [CWin32Heap](../../atl/reference/cwin32heap-class.md)implementiert.

> [!NOTE]
> Die lokalen und globalen Heapfunktionen sind langsamer als andere Speicherverwaltungsfunktionen und bieten nicht so viele Funktionen. Daher sollten neue Anwendungen die [Heapfunktionen](/windows/win32/Memory/heap-functions)verwenden. Diese sind in der [CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md) verfügbar.

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr::Zuweisen

Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [IAtlMemMgr::Free](#free) oder [IAtlMemMgr::Reallocate](#reallocate) auf, um den mit dieser Methode zugewiesenen Speicher freizugeben.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [IAtlMemMgr-Übersicht](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Kostenlos

Rufen Sie diese Methode auf, um einen Speicherblock freizugeben.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um Speicher freizugeben, der von [IAtlMemMgr::Allocate](#allocate) oder [IAtlMemMgr::Reallocate](#reallocate)abgerufen wurde.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [IAtlMemMgr-Übersicht](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr::GetSize

Rufen Sie diese Methode auf, um die Größe eines zugewiesenen Speicherblocks abzurufen.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

### <a name="return-value"></a>Rückgabewert

Gibt die Größe des Speicherblocks in Bytes zurück.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [IAtlMemMgr-Übersicht](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Neuzuordnen

Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [IAtlMemMgr::Free](#free) oder [IAtlMemMgr::Reallocate](#reallocate) auf, um den mit dieser Methode zugewiesenen Speicher freizugeben.

Diese Methode gibt den vorhandenen Speicher konzeptionell frei und weist einen neuen Speicherblock zu. In Wirklichkeit kann das vorhandene Gedächtnis erweitert oder anderweitig wiederverwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [IAtlMemMgr-Übersicht](../../atl/reference/iatlmemmgr-class.md).

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu

Die `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement ein eigenes Kontextmenü anzeigen darf.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parameter

*pbAllowContextMenu*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

Die `AllowShowUI` Eigenschaft gibt an, ob das gehostete Steuerelement eine eigene Benutzeroberfläche anzeigen darf.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parameter

*pbAllowShowUI*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

Die `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine fensterlose Aktivierung zulässt.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parameter

*pbAllowWindowless*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

Die `BackColor` Eigenschaft gibt die Umgebungshintergrundfarbe des Containers an.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parameter

*pclrHintergrund*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet COLOR_BTNFACE oder COLOR_WINDOW als Standardwert dieser Eigenschaft (je nachdem, ob das übergeordnete Element des Hostfensters ein Dialogfeld ist oder nicht).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`ist eine ambient-Eigenschaft, mit der ein Steuerelement herausfinden kann, ob es sich um das Standardsteuerelement handelt.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parameter

*pbDisplayAsDefault*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

Die `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick erfolgen soll.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parameter

*pdwDocHostDoubleClickFlags*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet DOCHOSTUIDBLCLK_DEFAULT als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

Die `DocHostFlags` Eigenschaft gibt die Benutzeroberflächenfunktionen des Hostobjekts an.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parameter

*pdwDocHostFlags*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet DOCHOSTUIFLAG_NO3DBORDER als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font

Die `Font` Eigenschaft gibt die Umgebungsschriftart des Containers an.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
[out] Die Adresse `IFontDisp` eines Schnittstellenzeigers, der zum Empfangen des aktuellen Werts dieser Eigenschaft verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet die Standard-GUI-Schriftart oder die Systemschriftart als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

Die `ForeColor` Eigenschaft gibt die Umgebungsvordergrundfarbe des Containers an.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parameter

*pclrForeground*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet die Textfarbe des Systemfensters als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

Die `LocaleID` Eigenschaft gibt die Umgebungsgebietsschema-ID des Containers an.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parameter

*plcidLocaleID*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet das Standardgebietsschema des Benutzers als Standardwert dieser Eigenschaft.

Mit dieser Methode können Sie die Ambient LocalID ermitteln, d. h. die LocaleID des Programms, in dem Ihr Steuerelement verwendet wird. Sobald Sie die LocaleID kennen, können Sie Code aufrufen, um gebietsschemaspezifische Beschriftungen, Fehlermeldungstext usw. aus einer Ressourcendatei oder Satelliten-DLL zu laden.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

Die `MessageReflect` ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement wiedergibt.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parameter

*pbMessageReflect*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

Die `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüsselpfad für Benutzereinstellungen an.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parameter

*pbstrOptionKeyPath*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

Die `ShowGrabHandles` ambient-Eigenschaft ermöglicht es dem Steuerelement herauszufinden, ob es sich mit Greifgriffen ziehen sollte.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parameter

*pbShowGrabHandles*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung gibt immer VARIANT_FALSE als Wert dieser Eigenschaft zurück.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

Die `ShowHatching` ambient-Eigenschaft ermöglicht es dem Steuerelement herauszufinden, ob es sich selbst schlüpfen soll.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parameter

*pbShowHatching*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung gibt immer VARIANT_FALSE als Wert dieser Eigenschaft zurück.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

Die `UserMode` Eigenschaft gibt den Umgebungsbenutzermodus des Containers an.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parameter

*pbUserMode*<br/>
[out] Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu

Die `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement ein eigenes Kontextmenü anzeigen darf.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parameter

*bAllowContextMenu*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI

Die `AllowShowUI` Eigenschaft gibt an, ob das gehostete Steuerelement eine eigene Benutzeroberfläche anzeigen darf.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parameter

*bAllowShowUI*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation

Die `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine fensterlose Aktivierung zulässt.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parameter

*bAllowWindowless*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor

Die `BackColor` Eigenschaft gibt die Umgebungshintergrundfarbe des Containers an.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parameter

*clrBackground*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet COLOR_BTNFACE oder COLOR_WINDOW als Standardwert dieser Eigenschaft (je nachdem, ob das übergeordnete Element des Hostfensters ein Dialogfeld ist oder nicht).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault`ist eine ambient-Eigenschaft, mit der ein Steuerelement herausfinden kann, ob es sich um das Standardsteuerelement handelt.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parameter

*bDisplayAsDefault*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

Die `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick erfolgen soll.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parameter

*dwDocHostDoubleClickFlags*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet DOCHOSTUIDBLCLK_DEFAULT als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags

Die `DocHostFlags` Eigenschaft gibt die Benutzeroberflächenfunktionen des Hostobjekts an.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parameter

*dwDocHostFlags*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet DOCHOSTUIFLAG_NO3DBORDER als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font

Die `Font` Eigenschaft gibt die Umgebungsschriftart des Containers an.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet die Standard-GUI-Schriftart oder die Systemschriftart als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor

Die `ForeColor` Eigenschaft gibt die Umgebungsvordergrundfarbe des Containers an.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parameter

*clrForeground*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet die Textfarbe des Systemfensters als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID

Die `LocaleID` Eigenschaft gibt die Umgebungsgebietsschema-ID des Containers an.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parameter

*lcidLocaleID*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet das Standardgebietsschema des Benutzers als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect

Die `MessageReflect` ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement wiedergibt.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parameter

*bMessageReflect*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath

Die `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüsselpfad für Benutzereinstellungen an.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parameter

*bstrOptionKeyPath*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode

Die `UserMode` Eigenschaft gibt den Umgebungsbenutzermodus des Containers an.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parameter

*bUserMode*<br/>
[in] Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Die ATL-Hostobjektimplementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Diese Methode wird aufgerufen, um die standardmäßige Umgebungseigenschaftsschnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parameter

*pDispatch*<br/>
Zeiger auf die neue Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn `SetAmbientDispatch` mit einem Zeiger auf eine neue Schnittstelle aufgerufen wird, wird diese neue Schnittstelle verwendet, um alle Eigenschaften oder Methoden aufzurufen, die vom gehosteten Steuerelement angefordert werden – wenn diese Eigenschaften nicht bereits von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)bereitgestellt werden.

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Fügt ein vorhandenes (und zuvor initialisiertes) Steuerelement mithilfe des von *hWnd*identifizierten Fensters an das Hostobjekt an.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parameter

*pUnkControl*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Steuerelements, das an das Hostobjekt angefügt werden soll.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Erstellt ein Steuerelement, initialisiert es und hostet es in dem von *hWnd*identifizierten Fenster.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parameter

*lpTricsDaten*<br/>
[in] Eine Zeichenfolge, die das zu erstellende Steuerelement identifiziert. Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatiertes HTML **(voranms:**) sein.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

*pStream*<br/>
[in] Ein Schnittstellenzeiger für einen Stream, der Initialisierungsdaten für das Steuerelement enthält. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Dieses Fenster wird vom Hostobjekt unterklassen, das diese Schnittstelle bereitstellt, sodass Nachrichten an das Steuerelement zurückgesendet werden können und andere Container-Features funktionieren.

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parameter

*lpTricsDaten*<br/>
[in] Eine Zeichenfolge, die das zu erstellende Steuerelement identifiziert. Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatiertes HTML (mit **MSHTML:** vorangestellt) sein.

*hWnd*<br/>
[in] Ein Handle zum Fenster, das zum Hosten verwendet werden soll.

*pStream*<br/>
[in] Ein Schnittstellenzeiger für einen Stream, der Initialisierungsdaten für das Steuerelement enthält. Kann den Wert NULL haben.

*ppUnk*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der die Schnittstelle des erstellten Steuerelements empfängt. Kann den Wert NULL haben.

*riidAdvise*<br/>
[in] Der Schnittstellenbezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punkAdvise*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des Senkenobjekts, der mit dem `iidSink`Verbindungspunkt des enthaltenen Objekts verbunden werden soll, das von angegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Im `CreateControl` Gegensatz `CreateControlEx` zur Methode können Sie auch einen Schnittstellenzeiger auf das neu erstellte Steuerelement empfangen und eine Ereignissenke einrichten, um Ereignisse zu empfangen, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Gibt den angegebenen Schnittstellenzeiger zurück, der vom gehosteten Steuerelement bereitgestellt wird.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
[in] Die ID einer Schnittstelle für das angeforderte Steuerelement.

*ppvObject*<br/>
[out] Die Adresse eines Zeigers, der die angegebene Schnittstelle des erstellten Steuerelements empfängt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Legt die externe Dispinterface fest, die für enthaltene Steuerelemente über die [IDocHostUIHandlerDispatch::GetExternal-Methode](../../atl/reference/idochostuihandlerdispatch-interface.md) verfügbar ist.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
[in] Ein Zeiger auf `IDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Rufen Sie diese Funktion auf, um die externe `CAxWindow` [IDocHostUIHandlerDispatch-Schnittstelle](../../atl/reference/idochostuihandlerdispatch-interface.md) für das Objekt festzulegen.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
[in] Ein Zeiger auf `IDocHostUIHandlerDispatch` eine Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von Steuerelementen (z. B. dem Webbrowsersteuerelement) `IDocHostUIHandlerDispatch` verwendet, die die Hostwebsite nach der Schnittstelle abfragen.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowlic::CreateControllic

Erstellt ein lizenziertes Steuerelement, initialisiert es und hostet es in dem Fenster, das von `hWnd`identifiziert wird.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrLic*<br/>
[in] Der BSTR, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow::CreateControl.](#createcontrol)

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `IAxWinHostWindowLic::CreateControlLic`verwendet.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowlic::CreateControllicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrLic*<br/>
[in] Der BSTR, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow::CreateControlEx.](#createcontrolex)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `IAxWinHostWindowLic::CreateControlLicEx`verwendet.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
