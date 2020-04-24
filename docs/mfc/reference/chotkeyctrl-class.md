---
title: CHotKeyCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: a79cc0ab2c01633f96430477aa536a60385461e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750798"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Abkürzungstasten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Erstellt ein `CHotKeyCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHotKeyCtrl::Erstellen](#create)|Erstellt ein Hotkey-Steuerelement und `CHotKeyCtrl` fügt es an ein Objekt an.|
|[CHotKeyCtrl::CreateEx](#createex)|Erstellt ein Hotkey-Steuerelement mit den angegebenen erweiterten `CHotKeyCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Ruft den virtuellen Schlüsselcode und die Modifikatorflags eines Hotkeys von einem Hotkey-Steuerelement ab.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Ruft den Schlüsselnamen im lokalen Zeichensatz ab, der einem Hotkey zugewiesen ist.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Ruft den Schlüsselnamen im lokalen Zeichensatz ab, der dem angegebenen virtuellen Schlüsselcode zugewiesen ist.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Legt die Hot-Key-Kombination für eine Hotkey-Steuerung fest.|
|[CHotKeyCtrl::SetRules](#setrules)|Definiert die ungültigen Kombinationen und die Standardmodifikatorkombination für ein Hotkey-Steuerelement.|

## <a name="remarks"></a>Bemerkungen

Ein "Hotkey-Steuerelement" ist ein Fenster, das es dem Benutzer ermöglicht, einen Hotkey zu erstellen. Eine "Hot-Taste" ist eine Tastenkombination, die der Benutzer drücken kann, um eine Aktion schnell auszuführen. (Ein Benutzer kann z. B. einen Hotkey erstellen, der ein bestimmtes Fenster aktiviert und an den oberen Rand der Z-Reihenfolge bringt.) Das Hotkey-Steuerelement zeigt die Auswahlmöglichkeiten des Benutzers an und stellt sicher, dass der Benutzer eine gültige Tastenkombination auswählt.

Dieses Steuerelement (und `CHotKeyCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Wenn der Benutzer eine Tastenkombination ausgewählt hat, kann die Anwendung die angegebene Tastenkombination aus dem Steuerelement abrufen und die WM_SETHOTKEY Nachricht verwenden, um den Hotkey im System einzurichten. Wenn der Benutzer danach die Hotkey-Taste von einem beliebigen Teil des Systems aus drückt, erhält das in der WM_SETHOTKEY-Nachricht angegebene Fenster eine WM_SYSCOMMAND Meldung, die SC_HOTKEY angibt. Diese Meldung aktiviert das Fenster, das sie empfängt. Der Hotkey bleibt gültig, bis die Anwendung, die WM_SETHOTKEY aufgerufen hat, beendet wird.

Dieser Mechanismus unterscheidet sich von der Hotkey-Unterstützung, die von der WM_HOTKEY Nachricht und den Funktionen Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) und [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) abhängt.

Weitere Informationen zur `CHotKeyCtrl`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl

Erstellt ein `CHotKeyCtrl`-Objekt.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::Erstellen

Erstellt ein Hotkey-Steuerelement und `CHotKeyCtrl` fügt es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Hotkey-Steuerelements an. Wenden Sie eine beliebige Kombination von Steuerelementstilen an. Weitere Informationen finden Sie unter [Allgemeine Steuerelementformatvorlagen](/windows/win32/Controls/common-control-styles) im Windows SDK.

*Rect*<br/>
Gibt die Größe und Position des Hotkey-Steuerelements an. Es kann entweder ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect)sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Hotkey-Steuerelements an, in der Regel ein [CDialog](../../mfc/reference/cdialog-class.md). Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Hotkeys-Steuerelements an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CHotKeyCtrl` ein Objekt in zwei Schritten. Rufen Sie zuerst den Konstruktor auf, und rufen Sie dann `Create` `CHotKeyCtrl` auf, das das Hotkey-Steuerelement erstellt und an das Objekt anfügt.

Wenn Sie erweiterte Fensterstile mit Ihrem Steuerelement verwenden `Create`möchten, rufen Sie [CreateEx](#createex) anstelle von auf.

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyCtrl::CreateEx

Rufen Sie diese Funktion auf, um ein Steuerelement `CHotKeyCtrl` (ein untergeordnetes Fenster) zu erstellen und es dem Objekt zuzuordnen.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Hotkey-Steuerelements an. Wenden Sie eine beliebige Kombination von Steuerelementstilen an. Weitere Informationen finden Sie unter [Allgemeine Steuerelementstile](/windows/win32/Controls/common-control-styles) im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyCtrl::GetHotKey

Ruft den virtuellen Tastencode und die Modifikatorflags einer Tastenkombination von einem Hotkey-Steuerelement ab.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parameter

*wVirtualKeyCode*<br/>
[out] Virtueller Tastencode der Tastenkombination. Eine Liste der standardmäßigen virtuellen Schlüsselcodes finden Sie unter Winuser.h.

*wModifiers*<br/>
[out] Eine bitweise Kombination (OR) von Flags, die die Modifikatortasten in der Tastenkombination anzeigen.

Die Modifikatorflags lauten wie folgt:

|Flag|Entsprechender Schlüssel|
|----------|-----------------------|
|HOTKEYF_ALT|ALT-TASTE|
|HOTKEYF_CONTROL|STRG-Taste|
|HOTKEYF_EXT|Erweiterter Schlüssel|
|HOTKEYF_SHIFT|Umschalttaste|

### <a name="return-value"></a>Rückgabewert

In der ersten überladenen Methode ein DWORD, das den virtuellen Schlüsselcode und modifiziererflags enthält. Das Low-Order-Byte des Wortes niedriger Ordnung enthält den virtuellen Schlüsselcode, das Byte der hohen Ordnung des Low-Order-Worts enthält die Modifikatorflags, und das Wort hoher Ordnung ist Null.

### <a name="remarks"></a>Bemerkungen

Der virtuelle Tastencode und die Modifikatortasten definieren zusammen die Tastenkombination.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName

Rufen Sie diese Memberfunktion auf, um den lokalisierten Namen des Hotkeys abzurufen.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Rückgabewert

Der lokalisierte Name des aktuell ausgewählten Hotkeys. Wenn kein ausgewählter Hotkey vorhanden ist, `GetHotKeyName` wird eine leere Zeichenfolge zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der Name, den diese Memberfunktion zurückgibt, stammt vom Tastaturtreiber. Sie können einen nicht lokalisierten Tastaturtreiber in einer lokalisierten Windows-Version installieren und umgekehrt.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyCtrl::GetKeyName

Rufen Sie diese Memberfunktion auf, um den lokalisierten Namen des Schlüssels abzurufen, der einem angegebenen virtuellen Schlüsselcode zugewiesen ist.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parameter

*vk*<br/>
Der virtuelle Schlüsselcode.

*fExtended*<br/>
Wenn der virtuelle Schlüsselcode ein erweiterter Schlüssel ist, TRUE; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

Der lokalisierte Name des Schlüssels, der durch den *vk-Parameter* angegeben wird. Wenn der Schlüssel keinen zugeordneten Namen hat, `GetKeyName` wird eine leere Zeichenfolge zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der Schlüsselname, den diese Funktion zurückgibt, stammt vom Tastaturtreiber, sodass Sie einen nicht lokalisierten Tastaturtreiber in einer lokalisierten Windows-Version installieren können und umgekehrt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyCtrl::SetHotKey

Legt die Tastenkombination für ein Hotkey-Steuerelement fest.

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parameter

*wVirtualKeyCode*<br/>
[in] Virtueller Tastencode der Tastenkombination. Eine Liste der standardmäßigen virtuellen Schlüsselcodes finden Sie unter Winuser.h.

*wModifiers*<br/>
[in] Eine bitweise Kombination (OR) von Flags, die die Modifikatortasten in der Tastenkombination anzeigen.

Die Modifikatorflags lauten wie folgt:

|Flag|Entsprechender Schlüssel|
|----------|-----------------------|
|HOTKEYF_ALT|ALT-TASTE|
|HOTKEYF_CONTROL|STRG-Taste|
|HOTKEYF_EXT|Erweiterter Schlüssel|
|HOTKEYF_SHIFT|Umschalttaste|

### <a name="remarks"></a>Bemerkungen

Der virtuelle Tastencode und die Modifikatortasten definieren zusammen die Tastenkombination.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyCtrl::SetRules

Rufen Sie diese Funktion auf, um die ungültigen Kombinationen und die Standardmodifikatorkombination für ein Hotkey-Steuerelement zu definieren.

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parameter

*wInvalidComb*<br/>
Array von Flags, das ungültige Tastenkombinationen angibt. Es kann eine Kombination der folgenden Werte sein:

- HKCOMB_A ALT

- HKCOMB_C STRG

- HKCOMB_CA STRG+ALT

- HKCOMB_NONE Unveränderte Schlüssel

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT+CTRL

- HKCOMB_SCA SHIFT+CTRL+ALT

*wModifiers*<br/>
Array von Flags, das die Tastenkombination angibt, die verwendet werden soll, wenn der Benutzer eine ungültige Kombination eingibt. Weitere Informationen zu den Modifikatorflags finden Sie unter [GetHotKey](#gethotkey).

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer eine ungültige Tastenkombination eingibt, wie in *wInvalidComb*angegeben, verwendet das System den OPERATOR ODER, um die vom Benutzer eingegebenen Schlüssel mit den in *wModifiers*angegebenen Flags zu kombinieren. Die resultierende Tastenkombination wird in eine Zeichenfolge konvertiert und dann im Hotkey-Steuerelement angezeigt.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
