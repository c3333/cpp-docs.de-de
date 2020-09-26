---
title: IAxWinAmbientDispatch-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: dbd682451ca5499aef4b16b3b51feba8411bdd12
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352959"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch-Schnittstelle

Diese Schnittstelle stellt Methoden zum Angeben von Merkmalen für das gehostete Steuerelement oder den Container bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|Die- `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement sein eigenes Kontextmenü anzeigen darf.|
|[get_AllowShowUI](#get_allowshowui)|Die- `AllowShowUI` Eigenschaft gibt an, ob für das gehostete Steuerelement eine eigene Benutzeroberfläche angezeigt werden darf.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Die- `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine Fensterlose Aktivierung zulässt.|
|[get_BackColor](#get_backcolor)|Die- `BackColor` Eigenschaft gibt die Umgebungs Hintergrundfarbe für den Container an.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` eine Ambient-Eigenschaft, die einem Steuerelement ermöglicht, herauszufinden, ob es sich um das Standard Steuerelement handelt.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Die- `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick stattfinden soll.|
|[get_DocHostFlags](#get_dochostflags)|Die- `DocHostFlags` Eigenschaft gibt die Benutzeroberflächen Funktionen des Host Objekts an.|
|[get_Font](#get_font)|Die- `Font` Eigenschaft gibt die Umgebungs Schriftart des Containers an.|
|[get_ForeColor](#get_forecolor)|Die- `ForeColor` Eigenschaft gibt die Umgebungs Vordergrundfarbe des Containers an.|
|[get_LocaleID](#get_localeid)|Die- `LocaleID` Eigenschaft gibt die Ambient-Gebiets Schema-ID des Containers an.|
|[get_MessageReflect](#get_messagereflect)|Die `MessageReflect` Ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement reflektiert.|
|[get_OptionKeyPath](#get_optionkeypath)|Die- `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüssel Pfad zu den Benutzereinstellungen an.|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`Mit der Ambient-Eigenschaft kann das Steuerelement herausfinden, ob es mit Zieh Handles gezeichnet werden soll.|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`Mit der Ambient-Eigenschaft kann das Steuerelement herausfinden, ob es sich selbst gezeichnet hat.|
|[get_UserMode](#get_usermode)|Die- `UserMode` Eigenschaft gibt den Umgebungs Benutzermodus des Containers an.|
|[put_AllowContextMenu](#put_allowcontextmenu)|Die- `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement sein eigenes Kontextmenü anzeigen darf.|
|[put_AllowShowUI](#put_allowshowui)|Die- `AllowShowUI` Eigenschaft gibt an, ob für das gehostete Steuerelement eine eigene Benutzeroberfläche angezeigt werden darf.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Die- `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine Fensterlose Aktivierung zulässt.|
|[put_BackColor](#put_backcolor)|Die- `BackColor` Eigenschaft gibt die Umgebungs Hintergrundfarbe für den Container an.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` eine Ambient-Eigenschaft, die einem Steuerelement ermöglicht, herauszufinden, ob es sich um das Standard Steuerelement handelt.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Die- `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick stattfinden soll.|
|[put_DocHostFlags](#put_dochostflags)|Die- `DocHostFlags` Eigenschaft gibt die Benutzeroberflächen Funktionen des Host Objekts an.|
|[put_Font](#put_font)|Die- `Font` Eigenschaft gibt die Umgebungs Schriftart des Containers an.|
|[put_ForeColor](#put_forecolor)|Die- `ForeColor` Eigenschaft gibt die Umgebungs Vordergrundfarbe des Containers an.|
|[put_LocaleID](#put_localeid)|Die- `LocaleID` Eigenschaft gibt die Ambient-Gebiets Schema-ID des Containers an.|
|[put_MessageReflect](#put_messagereflect)|Die `MessageReflect` Ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement reflektiert.|
|[put_OptionKeyPath](#put_optionkeypath)|Die- `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüssel Pfad zu den Benutzereinstellungen an.|
|[put_UserMode](#put_usermode)|Die- `UserMode` Eigenschaft gibt den Umgebungs Benutzermodus des Containers an.|

## <a name="remarks"></a>Hinweise

Diese Schnittstelle wird durch die ActiveX-Steuerelemente des ATL-Steuer Elements verfügbar gemacht. Ruft die-Methoden für diese Schnittstelle auf, um die Umgebungs Eigenschaften festzulegen, die für das gehostete Steuerelement verfügbar sind, oder um andere Aspekte des Container Verhaltens anzugeben. Um die von bereitgestellten Eigenschaften zu ergänzen `IAxWinAmbientDispatch` , verwenden Sie [iaxwinambientdispatchex](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost> versucht, Typinformationen über `IAxWinAmbientDispatch` und `IAxWinAmbientDispatchEx` aus der Typbibliothek, die den Code enthält, zu laden.

Wenn Sie mit ATL90.dll verknüpfen, lädt **AxHost** die Typinformationen aus der Typbibliothek in der dll.

Weitere Informationen finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="requirements"></a>Requirements (Anforderungen)

Die Definition dieser Schnittstelle ist in einer Reihe von Formularen verfügbar, wie in der folgenden Tabelle dargestellt.

|Definitionstyp|Datei|
|---------------------|----------|
|IDL|atliface. idl|
|Typbibliothek|ATL.dll|
|C++|atliface. h (auch in "atlbase. h" enthalten)|

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

## <a name="see-also"></a>Weitere Informationen

[Iaxwinambientdispatchex-Schnittstelle](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow-Schnittstelle](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
