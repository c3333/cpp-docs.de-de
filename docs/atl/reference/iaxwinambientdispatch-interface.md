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
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330009"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch-Schnittstelle

Diese Schnittstelle stellt Methoden zum Angeben von Eigenschaften des gehosteten Steuerelements oder Containers bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|Die `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement ein eigenes Kontextmenü anzeigen darf.|
|[get_AllowShowUI](#get_allowshowui)|Die `AllowShowUI` Eigenschaft gibt an, ob das gehostete Steuerelement eine eigene Benutzeroberfläche anzeigen darf.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Die `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine fensterlose Aktivierung zulässt.|
|[get_BackColor](#get_backcolor)|Die `BackColor` Eigenschaft gibt die Umgebungshintergrundfarbe des Containers an.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`ist eine ambient-Eigenschaft, mit der ein Steuerelement herausfinden kann, ob es sich um das Standardsteuerelement handelt.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Die `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick erfolgen soll.|
|[get_DocHostFlags](#get_dochostflags)|Die `DocHostFlags` Eigenschaft gibt die Benutzeroberflächenfunktionen des Hostobjekts an.|
|[get_Font](#get_font)|Die `Font` Eigenschaft gibt die Umgebungsschriftart des Containers an.|
|[get_ForeColor](#get_forecolor)|Die `ForeColor` Eigenschaft gibt die Umgebungsvordergrundfarbe des Containers an.|
|[get_LocaleID](#get_localeid)|Die `LocaleID` Eigenschaft gibt die Umgebungsgebietsschema-ID des Containers an.|
|[get_MessageReflect](#get_messagereflect)|Die `MessageReflect` ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement wiedergibt.|
|[get_OptionKeyPath](#get_optionkeypath)|Die `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüsselpfad für Benutzereinstellungen an.|
|[get_ShowGrabHandles](#get_showgrabhandles)|Die `ShowGrabHandles` ambient-Eigenschaft ermöglicht es dem Steuerelement herauszufinden, ob es sich mit Greifgriffen ziehen sollte.|
|[get_ShowHatching](#get_showhatching)|Die `ShowHatching` ambient-Eigenschaft ermöglicht es dem Steuerelement herauszufinden, ob es sich selbst schlüpfen soll.|
|[get_UserMode](#get_usermode)|Die `UserMode` Eigenschaft gibt den Umgebungsbenutzermodus des Containers an.|
|[put_AllowContextMenu](#put_allowcontextmenu)|Die `AllowContextMenu` Eigenschaft gibt an, ob das gehostete Steuerelement ein eigenes Kontextmenü anzeigen darf.|
|[put_AllowShowUI](#put_allowshowui)|Die `AllowShowUI` Eigenschaft gibt an, ob das gehostete Steuerelement eine eigene Benutzeroberfläche anzeigen darf.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Die `AllowWindowlessActivation` Eigenschaft gibt an, ob der Container eine fensterlose Aktivierung zulässt.|
|[put_BackColor](#put_backcolor)|Die `BackColor` Eigenschaft gibt die Umgebungshintergrundfarbe des Containers an.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`ist eine ambient-Eigenschaft, mit der ein Steuerelement herausfinden kann, ob es sich um das Standardsteuerelement handelt.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Die `DocHostDoubleClickFlags` Eigenschaft gibt den Vorgang an, der als Reaktion auf einen Doppelklick erfolgen soll.|
|[put_DocHostFlags](#put_dochostflags)|Die `DocHostFlags` Eigenschaft gibt die Benutzeroberflächenfunktionen des Hostobjekts an.|
|[put_Font](#put_font)|Die `Font` Eigenschaft gibt die Umgebungsschriftart des Containers an.|
|[put_ForeColor](#put_forecolor)|Die `ForeColor` Eigenschaft gibt die Umgebungsvordergrundfarbe des Containers an.|
|[put_LocaleID](#put_localeid)|Die `LocaleID` Eigenschaft gibt die Umgebungsgebietsschema-ID des Containers an.|
|[put_MessageReflect](#put_messagereflect)|Die `MessageReflect` ambient-Eigenschaft gibt an, ob der Container Nachrichten an das gehostete Steuerelement wiedergibt.|
|[put_OptionKeyPath](#put_optionkeypath)|Die `OptionKeyPath` Eigenschaft gibt den Registrierungsschlüsselpfad für Benutzereinstellungen an.|
|[put_UserMode](#put_usermode)|Die `UserMode` Eigenschaft gibt den Umgebungsbenutzermodus des Containers an.|

## <a name="remarks"></a>Bemerkungen

Diese Schnittstelle wird von ATLs ActiveX-Steuerelementhostingobjekten verfügbar gemacht. Rufen Sie die Methoden auf dieser Schnittstelle auf, um die Umgebungseigenschaften festzulegen, die für das gehostete Steuerelement verfügbar sind, oder um andere Aspekte des Verhaltens des Containers anzugeben. Um die von `IAxWinAmbientDispatch`bereitgestellten Eigenschaften zu ergänzen, verwenden Sie [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost>versucht, Typinformationen über `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` und aus dem typlib zu laden, der den Code enthält.

Wenn Sie eine Verknüpfung mit ATL90.dll herstellen, lädt **AXHost** die Typinformationen aus der Typelib in der DLL.

Weitere Informationen finden Sie unter [Hosting von ActiveX-Steuerelementen unter Verwendung von ATL AXHost.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="requirements"></a>Anforderungen

Die Definition dieser Schnittstelle ist in einer Reihe von Formen verfügbar, wie in der folgenden Tabelle dargestellt.

|Definitionstyp|Datei|
|---------------------|----------|
|Idl|atliface.idl|
|Typbibliothek|ATL.dll|
|C++|atliface.h (auch in ATLBase.h enthalten)|

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

## <a name="see-also"></a>Siehe auch

[IAxWinAmbientDispatchEx-Schnittstelle](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow-Schnittstelle](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
