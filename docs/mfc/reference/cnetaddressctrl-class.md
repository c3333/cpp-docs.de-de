---
title: CNetAddressCtrl-Klasse
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: c6f391966ef6657363e8f23e5666a57a935b08e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752777"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl-Klasse

Die Klasse `CNetAddressCtrl` stellt das Netzwerkadressen-Steuerelement dar, das verwendet werden kann, um IPv4-, IPv6- und benannte DNS-Adressen einzugeben und ihr Format zu überprüfen.

## <a name="syntax"></a>Syntax

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Erstellt ein `CNetAddressCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CNetAddressCtrl::Erstellen](#create)|Erstellt ein Netzwerkadresssteuerelement mit angegebenen Stilen `CNetAddressCtrl` und fügt es an das aktuelle Objekt an.|
|[CNetAddressCtrl::CreateEx](#createex)|Erstellt ein Netzwerkadresssteuerelement mit angegebenen erweiterten Stilen `CNetAddressCtrl` und fügt es an das aktuelle Objekt an.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Zeigt eine Fehlersprechblase an, wenn der Benutzer eine nicht unterstützte Netzwerkadresse in das aktuelle Netzwerkadresssteuerelement eingibt.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Ruft eine validierte und analysierte Darstellung der Netzwerkadresse ab, die dem aktuellen Netzwerkadresssteuerelement zugeordnet ist.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Ruft den Typ der Netzwerkadresse ab, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden kann.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Legt den Typ der Netzwerkadresse fest, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden kann.|

## <a name="remarks"></a>Bemerkungen

Das Netzwerkadresssteuerelement überprüft, ob das Format der vom Benutzer eingegebenen Adresse korrekt ist. Das Steuerelement stellt keine Verbindung mit der Netzwerkadresse her. Die [CNetAddressCtrl::SetAllowType-Methode](#setallowtype) gibt einen oder mehrere Adresstypen an, die die [CNetAddressCtrl::GetAddress-Methode](#getaddress) analysieren und überprüfen kann. Eine Adresse kann in Form eines IPv4, IPv6 oder benannten Adressen für einen Server, ein Netzwerk, einen Host oder ein Broadcastnachrichtenziel verwendet werden. Wenn das Format der Adresse falsch ist, können Sie die [CNetAddressCtrl::DisplayErrorTip-Methode](#displayerrortip) verwenden, um ein Infotip-Meldungsfeld anzuzeigen, das grafisch auf das Textfeld des Netzwerkadresssteuerelements zeigt und eine vordefinierte Fehlermeldung anzeigt.

Die `CNetAddressCtrl` Klasse wird von der [CEdit-Klasse](../../mfc/reference/cedit-class.md) abgeleitet. Daher bietet das Netzwerkadresssteuerelement Zugriff auf alle Windows-Bearbeitungssteuerungsmeldungen.

Die folgende Abbildung zeigt ein Dialogfeld, das ein Netzwerkadresssteuerelement enthält. Das Textfeld (1) für das Netzwerkadresssteuerelement enthält eine ungültige Netzwerkadresse. Die Infotip-Meldung (2) wird angezeigt, wenn die Netzwerkadresse ungültig ist.

![Dialogfeld mit einem Netzwerkadressen-Steuerelement und InfoTipps.](../../mfc/reference/media/cnetaddctrl.png "Dialogfeld mit einem Netzwerkadressen-Steuerelement und InfoTipps.")

## <a name="example"></a>Beispiel

Das folgende Codebeispiel ist ein Teil eines Dialogfelds, der eine Netzwerkadresse überprüft. Die Ereignishandler für drei Optionsfelder geben an, dass die Netzwerkadresse einer von drei Adresstypen sein kann. Der Benutzer gibt eine Adresse in das Textfeld des Netzwerksteuerelements ein und drückt dann eine Schaltfläche, um die Adresse zu überprüfen. Wenn die Adresse gültig ist, wird eine Erfolgsmeldung angezeigt. Andernfalls wird die vordefinierte Infotip-Fehlermeldung angezeigt.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Beispiel

Das folgende Codebeispiel aus der Dialogheaderdatei definiert die [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) und [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) Variablen, die für die [CNetAddressCtrl::GetAddress-Methode](#getaddress) erforderlich sind.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

Diese Klasse wird in Windows Vista und höher unterstützt.

Weitere Anforderungen für diese Klasse werden unter [Buildanforderungen für allgemeine Windows Vista-Steuerelemente](../../mfc/build-requirements-for-windows-vista-common-controls.md)beschrieben.

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl

Erstellt ein `CNetAddressCtrl`-Objekt.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CNetAddressCtrl::Create-](#create) oder [CNetAddressCtrl::CreateEx-Methode,](#createex) `CNetAddressCtrl` um ein Netzwerksteuerelement zu erstellen und es an das Objekt anzufügen.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl::Erstellen

Erstellt ein Netzwerkadresssteuerelement mit angegebenen Stilen `CNetAddressCtrl` und fügt es an das aktuelle Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwStyle*|[in] Eine bitweise Kombination von Stilen, die auf das Steuerelement angewendet werden sollen. Weitere Informationen finden Sie unter Bearbeiten von [Stilen](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[in] Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Position und Größe des Steuerelements enthält.|
|*pParentWnd*|[in] Ein Nicht-NULL-Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Steuerelements ist.|
|*nID*|[in] Die ID des Steuerelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl::CreateEx

Erstellt ein Netzwerkadresssteuerelement mit angegebenen erweiterten Stilen `CNetAddressCtrl` und fügt es an das aktuelle Objekt an.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwExStyle*|[in] Eine bitweise Kombination (OR) erweiterter Stile, die auf das Steuerelement angewendet werden sollen. Weitere Informationen finden Sie im *dwExStyle-Parameter* der [CreateWindowEx-Funktion.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyle*|[in] Eine bitweise Kombination (OR) von Stilen, die auf das Steuerelement angewendet werden sollen. Weitere Informationen finden Sie unter Bearbeiten von [Stilen](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[in] Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Position und Größe des Steuerelements enthält.|
|*pParentWnd*|[in] Ein Nicht-NULL-Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Steuerelements ist.|
|*nID*|[in] Die ID des Steuerelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip

Zeigt eine Fehlermeldung in der Sprechblasenspitze an, die dem aktuellen Netzwerkadresssteuerelement zugeordnet ist.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Rückgabewert

Der `S_OK` Wert, wenn diese Methode erfolgreich ist; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CNetAddressCtrl::SetAllowType-Methode,](#setallowtype) um die Adresstypen anzugeben, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden können. Verwenden Sie die [CNetAddressCtrl::GetAddress-Methode,](#getaddress) um die Netzwerkadresse, die der Benutzer eingibt, zu überprüfen und zu analysieren. Verwenden Sie die [CNetAddressCtrl::DisplayErrorTip-Methode,](#displayerrortip) um ein Fehlermeldungs-Infotip anzuzeigen, wenn die [CNetAddressCtrl::GetAddress-Methode](#getaddress) nicht erfolgreich ist.

Diese Meldung ruft das [NetAddr_DisplayErrorTip-Makro](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) auf, das im Windows SDK beschrieben wird. Dieses Makro `NCM_DISPLAYERRORTIP` sendet die Nachricht.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl::GetAddress

Ruft eine validierte und analysierte Darstellung der Netzwerkadresse ab, die dem aktuellen Netzwerkadresssteuerelement zugeordnet ist.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parameter

*pAddress*<br/>
[in, out] Zeiger auf eine [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) Struktur.  Legen Sie den *pAddrInfo-Member* dieser Struktur auf die Adresse einer [NET_ADDRESS_INFO-Struktur](/windows/win32/shell/hkey-type) fest, bevor Sie die GetAddress-Methode aufrufen.

### <a name="return-value"></a>Rückgabewert

Der Wert S_OK, wenn diese Methode erfolgreich ist. andernfalls ein COM-Fehlercode. Weitere Informationen zu den möglichen Fehlercodes finden Sie im Abschnitt Rückgabewert des [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) Makros.

### <a name="remarks"></a>Bemerkungen

Wenn diese Methode erfolgreich ist, enthält die [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) Struktur zusätzliche Informationen zur Netzwerkadresse.

Verwenden Sie die [CNetAddressCtrl::SetAllowType-Methode,](#setallowtype) um die Adresstypen anzugeben, die das aktuelle Netzwerkadresssteuerelement unterstützen kann. Verwenden Sie die [CNetAddressCtrl::GetAddress-Methode,](#getaddress) um die Netzwerkadresse, die der Benutzer eingibt, zu überprüfen und zu analysieren. Verwenden Sie die [CNetAddressCtrl::DisplayErrorTip-Methode,](#displayerrortip) um ein Fehlermeldungs-Infotip anzuzeigen, wenn die [CNetAddressCtrl::GetAddress-Methode](#getaddress) nicht erfolgreich ist.

Diese Methode ruft das [NetAddr_GetAddress-Makro](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) auf, das im Windows SDK beschrieben wird. Dieses Makro sendet die NCM_GETADDRESS Nachricht.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl::GetAllowType

Ruft den Typ der Netzwerkadresse ab, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden kann.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Rückgabewert

Eine bitweise Kombination (OR) von Flags, die die Adresstypen angibt, die das Netzwerkadresssteuerelement unterstützen kann. Weitere Informationen finden Sie [unter NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Bemerkungen

Diese Meldung ruft das [NetAddr_GetAllowType-Makro](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) auf, das im Windows SDK beschrieben wird. Dieses Makro sendet die NCM_GETALLOWTYPE Nachricht.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl::SetAllowType

Legt den Typ der Netzwerkadresse fest, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden kann.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*dwAddrMask*|[in] Eine bitweise Kombination (OR) von Flags, die die Adresstypen angibt, die das Netzwerkadresssteuerelement unterstützen kann. Weitere Informationen finden Sie [unter NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Rückgabewert

S_OK, wenn diese Methode erfolgreich ist. andernfalls ein COM-Fehlercode.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CNetAddressCtrl::SetAllowType-Methode,](#setallowtype) um die Adresstypen anzugeben, die vom aktuellen Netzwerkadresssteuerelement unterstützt werden können. Verwenden Sie die [CNetAddressCtrl::GetAddress-Methode,](#getaddress) um die Netzwerkadresse, die der Benutzer eingibt, zu überprüfen und zu analysieren. Verwenden Sie die [CNetAddressCtrl::DisplayErrorTip-Methode,](#displayerrortip) um ein Fehlermeldungs-Infotip anzuzeigen, wenn die [CNetAddressCtrl::GetAddress-Methode](#getaddress) nicht erfolgreich ist.

Diese Meldung ruft das [NetAddr_SetAllowType-Makro](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) auf, das im Windows SDK beschrieben wird. Dieses Makro sendet die NCM_SETALLOWTYPE Nachricht.

## <a name="see-also"></a>Weitere Informationen

[CNetAddressCtrl-Klasse](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
