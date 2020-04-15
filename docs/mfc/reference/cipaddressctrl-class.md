---
title: CIPAddressCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: 28aa0e7137647bc49406dab1e82b9c2b05ca3538
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372345"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Steuerelements für IP-Adressen bereit.

## <a name="syntax"></a>Syntax

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Erstellt ein `CIPAddressCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Löscht den Inhalt des IP-Adresssteuerelements.|
|[CIPAddressCtrl::Erstellen](#create)|Erstellt ein IP-Adresssteuerelement und `CIPAddressCtrl` fügt es an ein Objekt an.|
|[CIPAddressCtrl::CreateEx](#createex)|Erstellt ein IP-Adresssteuerelement mit den angegebenen erweiterten `CIPAddressCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Ruft die Adresswerte für alle vier Felder im IP-Adresssteuerelement ab.|
|[CIPAddressCtrl::IsBlank](#isblank)|Legt fest, ob alle Felder im IP-Adresssteuerelement leer sind.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Legt die Adresswerte für alle vier Felder im IP-Adresssteuerelement fest.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Legt den Tastaturfokus auf das angegebene Feld im IP-Adresssteuerelement fest.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Legt den Bereich im angegebenen Feld im IP-Adresssteuerelement fest.|

## <a name="remarks"></a>Bemerkungen

Mit einem IP-Adresssteuerelement, einem Steuerelement, das einem Bearbeitungssteuerelement ähnelt, können Sie eine numerische Adresse im IP-Format eingeben und bearbeiten.

Dieses Steuerelement (und `CIPAddressCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Microsoft Internet Explorer 4.0 und höher ausgeführt werden. Sie werden auch unter zukünftigen Versionen von Windows und Windows NT verfügbar sein.

Allgemeinere Informationen zum IP-Adresssteuerelement finden Sie unter [IP-Adresssteuerelemente](/windows/win32/Controls/ip-address-controls) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

Erstellt ein `CIPAddressCtrl` -Objekt.

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::ClearAddress

Löscht den Inhalt des IP-Adresssteuerelements.

```
void ClearAddress();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)Win32-IPM_CLEARADDRESS , wie im Windows SDK beschrieben.

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Erstellen

Erstellt ein IP-Adresssteuerelement und `CIPAddressCtrl` fügt es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Der Stil des IP-Adresssteuerelements. Wenden Sie eine Kombination von Fensterstilen an. Sie müssen den WS_CHILD-Stil einschließen, da das Steuerelement ein untergeordnetes Fenster sein muss. Eine Liste der Windows-Stile finden Sie unter [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK.

*Rect*<br/>
Ein Verweis auf die Größe und Position des IP-Adresssteuerelements. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/previous-versions/dd162897\(v=vs.85\)) handelt.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster des IP-Adresssteuerelements. Es darf nicht NULL sein.

*nID*<br/>
Die ID des IP-Adresssteuerelements.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CIPAddressCtrl` ein Objekt in zwei Schritten.

1. Rufen Sie den Konstruktor `CIPAddressCtrl` auf, der das Objekt erstellt.

1. Aufruf `Create`, der das IP-Adresssteuerelement erstellt.

Wenn Sie erweiterte Fensterstile mit Ihrem Steuerelement verwenden `Create`möchten, rufen Sie [CreateEx](#createex) anstelle von auf.

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx

Rufen Sie diese Funktion auf, um ein Steuerelement `CIPAddressCtrl` (ein untergeordnetes Fenster) zu erstellen und es dem Objekt zuzuordnen.

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
Der Stil des IP-Adresssteuerelements. Wenden Sie eine Kombination von Fensterstilen an. Sie müssen den WS_CHILD-Stil einschließen, da das Steuerelement ein untergeordnetes Fenster sein muss. Eine Liste der Windows-Stile finden Sie unter [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) im Windows SDK.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress

Ruft die Adresswerte für alle vier Felder im IP-Adresssteuerelement ab.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parameter

*nField0*<br/>
Ein Verweis auf den Feldwert 0 aus einer gepackten IP-Adresse.

*nFeld1*<br/>
Ein Verweis auf den Feldwert 1 aus einer gepackten IP-Adresse.

*nField2*<br/>
Ein Verweis auf den Feld 2-Wert aus einer gepackten IP-Adresse.

*nField3*<br/>
Ein Verweis auf den Feld-3-Wert aus einer gepackten IP-Adresse.

*dwAddress*<br/>
Ein Verweis auf die Adresse eines DWORD-Werts, der die IP-Adresse empfängt. Siehe **Hinweise** für eine Tabelle, die zeigt, wie *dwAddress* gefüllt wird.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der nicht leeren Felder im IP-Adresssteuerelement.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)Win32-IPM_GETADDRESS , wie im Windows SDK beschrieben. Im ersten Prototyp oben füllen die Zahlen in den Feldern 0 bis 3 des Steuerelements, gelesen von links nach rechts, die vier Parameter. Im zweiten Prototyp oben wird *dwAddress* wie folgt aufgefüllt.

|Feld|Bits, die den Feldwert enthalten|
|-----------|-------------------------------------|
|0|24 bis 31|
|1|16 bis 23|
|2|8 bis 15|
|3|0 bis 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::IsBlank

Legt fest, ob alle Felder im IP-Adresssteuerelement leer sind.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn alle IP-Adresssteuerungsfelder leer sind; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)Win32-IPM_ISBLANK , wie im Windows SDK beschrieben.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress

Legt die Adresswerte für alle vier Felder im IP-Adresssteuerelement fest.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parameter

*nField0*<br/>
Der Feldwert 0 aus einer gepackten IP-Adresse.

*nFeld1*<br/>
Der Feldwert 1 aus einer gepackten IP-Adresse.

*nField2*<br/>
Der Feld-2-Wert aus einer gepackten IP-Adresse.

*nField3*<br/>
Der Feld-3-Wert aus einer gepackten IP-Adresse.

*dwAddress*<br/>
Ein DWORD-Wert, der die neue IP-Adresse enthält. Weitere Informationen finden **Sie unter Hinweise** für eine Tabelle, die zeigt, wie der DWORD-Wert gefüllt wird.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)Win32-IPM_SETADDRESS , wie im Windows SDK beschrieben. Im ersten Prototyp oben füllen die Zahlen in den Feldern 0 bis 3 des Steuerelements, gelesen von links nach rechts, die vier Parameter. Im zweiten Prototyp oben wird *dwAddress* wie folgt aufgefüllt.

|Feld|Bits, die den Feldwert enthalten|
|-----------|-------------------------------------|
|0|24 bis 31|
|1|16 bis 23|
|2|8 bis 15|
|3|0 bis 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Legt den Tastaturfokus auf das angegebene Feld im IP-Adresssteuerelement fest.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parameter

*nField*<br/>
Nullbasierter Feldindex, auf den der Fokus gesetzt werden soll. Wenn dieser Wert größer als die Anzahl der Felder ist, wird der Fokus auf das erste leere Feld gesetzt. Wenn alle Felder nicht leer sind, wird der Fokus auf das erste Feld gesetzt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)Win32-IPM_SETFOCUS , wie im Windows SDK beschrieben.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Legt den Bereich im angegebenen Feld im IP-Adresssteuerelement fest.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parameter

*nField*<br/>
Nullbasierter Feldindex, auf den der Bereich angewendet wird.

*nNieder*<br/>
Ein Verweis auf eine ganze Zahl, die die untere Grenze des angegebenen Felds in diesem IP-Adresssteuerelement empfängt.

*nUpper*<br/>
Ein Verweis auf eine ganze Zahl, die die Obergrenze des angegebenen Felds in diesem IP-Adresssteuerelement empfängt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)Win32-IPM_SETRANGE , wie im Windows SDK beschrieben. Verwenden Sie die beiden Parameter *nLower* und *nUpper*, um die unteren und oberen Grenzwerte des Felds anstelle des mit der Win32-Meldung verwendeten *wRange-Parameters* anzugeben.

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
