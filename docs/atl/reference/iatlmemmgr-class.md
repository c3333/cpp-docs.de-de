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
ms.openlocfilehash: b23d8f582c53114ea1434e250e8e5e64b642f733
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353011"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr-Klasse

Diese Klasse stellt die Schnittstelle zu einem Speicher-Manager dar.

## <a name="syntax"></a>Syntax

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|-|-|
|[Jugend](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[Free](#free)|Mit dieser Methode können Sie einen Speicherblock freigeben.|
|[GetSize](#getsize)|Rufen Sie diese Methode auf, um die Größe eines zugeordneten Speicherblocks abzurufen.|
|[Erneuten Zuweisen](#reallocate)|Mit dieser Methode können Sie einen Speicherblock neu zuordnen.|

## <a name="remarks"></a>Hinweise

Diese Schnittstelle wird durch [CComHeap](../../atl/reference/ccomheap-class.md), [ccrder AP](../../atl/reference/ccrtheap-class.md), [clocalheap](../../atl/reference/clocalheap-class.md), [cglobalheap](../../atl/reference/cglobalheap-class.md)oder [CWin32Heap](../../atl/reference/cwin32heap-class.md)implementiert.

> [!NOTE]
> Die lokalen und globalen Heap Funktionen sind langsamer als andere Speicherverwaltungsfunktionen und bieten nicht so viele Features. Daher sollten neue Anwendungen die [Heap Funktionen](/windows/win32/Memory/heap-functions)verwenden. Diese sind in der [CWin32Heap](../../atl/reference/cwin32heap-class.md) -Klasse verfügbar.

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlmem. h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a> IAtlMemMgr:: zuordnen

Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Hinweise

Um den von dieser Methode belegten Arbeitsspeicher freizugeben, nennen Sie [IAtlMemMgr:: Free](#free) oder [IAtlMemMgr:: rezuordnen](#reallocate) .

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [Übersicht über IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a> IAtlMemMgr:: Free

Mit dieser Methode können Sie einen Speicherblock freigeben.

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

### <a name="remarks"></a>Hinweise

Verwenden Sie diese Methode, um Arbeitsspeicher freizugeben, der von [IAtlMemMgr:: zuordnen](#allocate) oder [IAtlMemMgr:: Neuzuordnen](#reallocate)abgerufen wurde.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [Übersicht über IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a> IAtlMemMgr:: GetSize

Rufen Sie diese Methode auf, um die Größe eines zugeordneten Speicherblocks abzurufen.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

### <a name="return-value"></a>Rückgabewert

Gibt die Größe des Speicherblocks in Bytes zurück.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [Übersicht über IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a> IAtlMemMgr:: Neuzuordnen

Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*cker*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Hinweise

Um den von dieser Methode belegten Arbeitsspeicher freizugeben, nennen Sie [IAtlMemMgr:: Free](#free) oder [IAtlMemMgr:: rezuordnen](#reallocate) .

Konzeptionell gibt diese Methode den vorhandenen Speicher frei und ordnet einen neuen Speicherblock zu. In der Realität kann der vorhandene Arbeitsspeicher erweitert oder anderweitig wieder verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie in der [Übersicht über IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch:: get_AllowContextMenu

Die- `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement sein eigenes Kontextmenü anzeigen darf.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parameter

*pballowcontextmenu*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch:: get_AllowShowUI

Die- `AllowShowUI` Eigenschaft gibt an, ob für das gehostete Steuerelement eine eigene Benutzeroberfläche angezeigt werden darf.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parameter

*pballowshowui*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch:: get_AllowWindowlessActivation

Die- `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine Fensterlose Aktivierung zulässt.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parameter

*pballowwindowless*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch:: get_BackColor

Die- `BackColor` Eigenschaft gibt die Umgebungs Hintergrundfarbe für den Container an.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parameter

*pclrbackground*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet COLOR_BTNFACE oder COLOR_WINDOW als Standardwert dieser Eigenschaft (abhängig davon, ob das übergeordnete Element des Host Fensters ein Dialogfeld ist oder nicht).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch:: get_DisplayAsDefault

`DisplayAsDefault` eine Ambient-Eigenschaft, die einem Steuerelement ermöglicht, herauszufinden, ob es sich um das Standard Steuerelement handelt.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parameter

*pbdisplayasdefault*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch:: get_DocHostDoubleClickFlags

Die- `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick stattfinden soll.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parameter

*pdwdochostdoubleclickflags*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet DOCHOSTUIDBLCLK_DEFAULT als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch:: get_DocHostFlags

Die- `DocHostFlags` Eigenschaft gibt die Benutzeroberflächen Funktionen des Host Objekts an.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parameter

*pdwdochostflags*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet DOCHOSTUIFLAG_NO3DBORDER als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch:: get_Font

Die- `Font` Eigenschaft gibt die Umgebungs Schriftart des Containers an.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parameter

*pfont*<br/>
vorgenommen Die Adresse eines `IFontDisp` Schnittstellen Zeigers, der zum Empfangen des aktuellen Werts dieser Eigenschaft verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet die standardmäßige GUI-Schriftart oder die System Schriftart als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch:: get_ForeColor

Die- `ForeColor` Eigenschaft gibt die Umgebungs Vordergrundfarbe des Containers an.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parameter

*pclrvordergrund*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet die Textfarbe des System Fensters als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch:: get_LocaleID

Die- `LocaleID` Eigenschaft gibt die Ambient-Gebiets Schema-ID des Containers an.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parameter

*plcidlocaleid*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet das Standard Gebiets Schema des Benutzers als Standardwert dieser Eigenschaft.

Mit dieser Methode können Sie das Ambient-lokzierer ermitteln, d. h. die LocaleID des Programms, in dem Ihr Steuerelement verwendet wird. Sobald Sie die LocaleID kennen, können Sie Code aufrufen, um Gebiets Schema spezifische Beschriftungen, Fehlermeldungs Text usw. aus einer Ressourcen Datei oder Satelliten-DLL zu laden.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch:: get_MessageReflect

Die `MessageReflect` Ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement reflektiert.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parameter

*pbmessagereflect*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch:: get_OptionKeyPath

Die- `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüssel Pfad zu den Benutzereinstellungen an.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parameter

*pbstroptionkeypath*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch:: get_ShowGrabHandles

`ShowGrabHandles`Mit der Ambient-Eigenschaft kann das Steuerelement herausfinden, ob es mit Zieh Handles gezeichnet werden soll.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parameter

*pbshowgrabhandles*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung gibt immer VARIANT_FALSE als Wert dieser Eigenschaft zurück.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch:: get_ShowHatching

`ShowHatching`Mit der Ambient-Eigenschaft kann das Steuerelement herausfinden, ob es sich selbst gezeichnet hat.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parameter

*pbshowhatching*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung gibt immer VARIANT_FALSE als Wert dieser Eigenschaft zurück.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch:: get_UserMode

Die- `UserMode` Eigenschaft gibt den Umgebungs Benutzermodus des Containers an.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parameter

*pbusermode*<br/>
vorgenommen Die Adresse einer Variablen, die den aktuellen Wert dieser Eigenschaft empfangen soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch::p ut_AllowContextMenu

Die- `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement sein eigenes Kontextmenü anzeigen darf.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parameter

*ballowcontextmenu*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch::p ut_AllowShowUI

Die- `AllowShowUI` Eigenschaft gibt an, ob für das gehostete Steuerelement eine eigene Benutzeroberfläche angezeigt werden darf.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parameter

*ballowshowui*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

Die- `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine Fensterlose Aktivierung zulässt.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parameter

*ballowwindowless*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch::p ut_BackColor

Die- `BackColor` Eigenschaft gibt die Umgebungs Hintergrundfarbe für den Container an.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parameter

*clrBackground*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet COLOR_BTNFACE oder COLOR_WINDOW als Standardwert dieser Eigenschaft (abhängig davon, ob das übergeordnete Element des Host Fensters ein Dialogfeld ist oder nicht).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault` eine Ambient-Eigenschaft, die einem Steuerelement ermöglicht, herauszufinden, ob es sich um das Standard Steuerelement handelt.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parameter

*bdisplayasdefault*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_FALSE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

Die- `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick stattfinden soll.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parameter

*dwdochostdoubleclickflags*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet DOCHOSTUIDBLCLK_DEFAULT als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch::p ut_DocHostFlags

Die- `DocHostFlags` Eigenschaft gibt die Benutzeroberflächen Funktionen des Host Objekts an.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parameter

*dwdochostflags*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet DOCHOSTUIFLAG_NO3DBORDER als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch::p ut_Font

Die- `Font` Eigenschaft gibt die Umgebungs Schriftart des Containers an.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parameter

*pfont*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet die standardmäßige GUI-Schriftart oder die System Schriftart als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch::p ut_ForeColor

Die- `ForeColor` Eigenschaft gibt die Umgebungs Vordergrundfarbe des Containers an.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parameter

*clrvorder Grund*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet die Textfarbe des System Fensters als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch::p ut_LocaleID

Die- `LocaleID` Eigenschaft gibt die Ambient-Gebiets Schema-ID des Containers an.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parameter

*lcidlocaleid*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet das Standard Gebiets Schema des Benutzers als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch::p ut_MessageReflect

Die `MessageReflect` Ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement reflektiert.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parameter

*bmessagereflect*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch::p ut_OptionKeyPath

Die- `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüssel Pfad zu den Benutzereinstellungen an.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parameter

*bstroptionkeypath*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch::p ut_UserMode

Die- `UserMode` Eigenschaft gibt den Umgebungs Benutzermodus des Containers an.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parameter

*busermode*<br/>
in Der neue Wert dieser Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Die ATL-Host Objekt Implementierung verwendet VARIANT_TRUE als Standardwert dieser Eigenschaft.

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> Iaxwinambientdispatchex:: setambientdispatch

Diese Methode wird aufgerufen, um die standardmäßige Ambient-Eigenschaften Schnittstelle durch eine benutzerdefinierte Schnittstelle zu ergänzen.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parameter

*pdispatch*<br/>
Ein Zeiger auf die neue-Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Wenn `SetAmbientDispatch` mit einem Zeiger auf eine neue Schnittstelle aufgerufen wird, wird diese neue Schnittstelle verwendet, um alle Eigenschaften oder Methoden aufzurufen, die vom gehosteten Steuerelement angefordert werden – wenn diese Eigenschaften nicht bereits von [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)bereitgestellt werden.

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow:: AttachControl

Fügt ein vorhandenes (und zuvor initialisiertes) Steuerelement mithilfe des durch *HWND*identifizierten Fensters an das Host Objekt an.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parameter

*punkcontrol*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des Steuer Elements, das an das Host Objekt angefügt werden soll.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow:: kreatecontrol

Erstellt ein Steuerelement, initialisiert es und hostet es im durch *HWND*identifizierten Fenster.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parameter

*lpzcsdata*<br/>
in Eine Zeichenfolge zur Identifizierung des zu erstellenden Steuer Elements Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatierte HTML-Datei (mit dem Präfix **MSHTML:**) sein.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

*pStream*<br/>
in Ein Schnittstellen Zeiger für einen Stream, der Initialisierungs Daten für das Steuerelement enthält. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Dieses Fenster wird durch das Host Objekt untergeordnet, das diese Schnittstelle verfügbar macht, sodass Nachrichten für das Steuerelement reflektiert werden können und andere Container Funktionen funktionieren.

Das Aufrufen dieser Methode entspricht dem Aufrufen von [IAxWinHostWindow:: createcontrolex](#createcontrolex).

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [iaxwinhostwindowlisch:: kreatecontrollic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow:: kreatecontrolex

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow:: kreatecontrol](#createcontrol).

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

*lpzcsdata*<br/>
in Eine Zeichenfolge zur Identifizierung des zu erstellenden Steuer Elements Kann eine CLSID (muss die geschweiften Klammern enthalten), ProgID, URL oder unformatierten HTML-Code (mit dem Präfix **MSHTML:**) sein.

*hWnd*<br/>
in Ein Handle für das Fenster, das für das Hosting verwendet werden soll.

*pStream*<br/>
in Ein Schnittstellen Zeiger für einen Stream, der Initialisierungs Daten für das Steuerelement enthält. Kann den Wert NULL haben.

*ppUnk*<br/>
vorgenommen Die Adresse eines Zeigers, der die- `IUnknown` Schnittstelle des erstellten Steuer Elements empfängt. Kann den Wert NULL haben.

*riidrat*<br/>
in Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt. Kann IID_NULL werden.

*punkrat*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt auf dem durch angegebenen enthaltenen Objekt verbunden werden soll `iidSink` .

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Anders als bei der- `CreateControl` Methode `CreateControlEx` können Sie auch einen Schnittstellen Zeiger auf das neu erstellte Steuerelement empfangen und eine Ereignis Senke für den Empfang von Ereignissen einrichten, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [iaxwinhostwindowlischen:: kreatecontrollicex](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow:: querycontrol

Gibt den angegebenen vom gehosteten Steuerelement bereitgestellten Schnittstellen Zeiger zurück.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
in Die ID einer Schnittstelle für das angeforderte Steuerelement.

*ppvObject*<br/>
vorgenommen Die Adresse eines Zeigers, der die angegebene Schnittstelle des erstellten Steuer Elements empfängt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow:: abtexternaldispatch

Legt die externe dispinterface-Methode fest, die mit der [idochostuihandlerdispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) -Methode für enthaltene Steuerelemente verfügbar ist.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine- `IDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow:: abtexternaluihandler

Mit dieser Funktion wird die externe [idochostuihandlerdispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) -Schnittstelle für das Objekt festgelegt `CAxWindow` .

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parameter

*pDisp*<br/>
in Ein Zeiger auf eine- `IDocHostUIHandlerDispatch` Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Diese Funktion wird von Steuerelementen (z. b. dem Webbrowser-Steuerelement) verwendet, die die Website des Hosts für die `IDocHostUIHandlerDispatch` Schnittstelle Abfragen.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> Iaxwinhostwindowlisch:: kreatecontrollic

Erstellt ein lizenziertes Steuerelement, initialisiert es und hostet es im durch identifizierten Fenster `hWnd` .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parameter

*bstrinlisch*<br/>
in Der BSTR-Wert, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [IAxWinHostWindow:: kreatecontrol](#createcontrol) .

Das Aufrufen dieser Methode entspricht dem Aufrufen von [iaxwinhostwindowlischen:: createcontrollicex](#createcontrollicex) .

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `IAxWinHostWindowLic::CreateControlLic` .

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> Iaxwinhostwindowlisch:: kreatecontrollicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster, ähnlich wie [IAxWinHostWindow:: kreatecontrol](#createcontrol).

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

*bstrinlisch*<br/>
in Der BSTR-Wert, der den Lizenzschlüssel für das Steuerelement enthält.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der verbleibenden Parameter und Rückgabewerte finden Sie unter [IAxWinHostWindow:: kreatecontrolex](#createcontrolex) .

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `IAxWinHostWindowLic::CreateControlLicEx` .

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
