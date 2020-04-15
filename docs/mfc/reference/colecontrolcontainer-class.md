---
title: COleControlContainer-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: b1737b2ac114181a4245fff027b756ca30b64129
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366188"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer-Klasse

Dient als Steuerelementcontainer für ActiveX-Steuerelemente.

## <a name="syntax"></a>Syntax

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Erstellt ein `COleControlContainer`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Erstellt eine Kontrollsite, die vom Container gehostet wird.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informiert alle gehosteten Steuerelemente, dass sich eine Umgebungseigenschaft geändert hat.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Ändert das angegebene Schaltflächensteuerelement.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Wählt das angegebene Optionsfeld einer Gruppe aus.|
|[COleControlContainer::CreateControl](#createcontrol)|Erstellt ein gehostetes ActiveX-Steuerelement.|
|[COleControlContainer::CreateOleFont](#createolefont)|Erstellt eine OLE-Schriftart.|
|[COleControlContainer::FindItem](#finditem)|Gibt die benutzerdefinierte Site des angegebenen Steuerelements zurück.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Bestimmt, ob die Kontrollsite Ereignisse akzeptiert.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Ruft die angegebene Umgebungseigenschaft ab.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Ruft das angegebene Dialogfeldsteuerelement ab.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Ruft den Wert des angegebenen Dialogfeldsteuerelements ab.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Ruft die Beschriftung des angegebenen Dialogfeldsteuerelements ab.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Bestimmt, ob der Container WM_SETFOCUS Nachrichten verarbeitet.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Behandelt Nachrichten, die an ein fensterloses Steuerelement gesendet werden.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Bestimmt den Status der angegebenen Schaltfläche.|
|[COleControlContainer::OnPaint](#onpaint)|Wird aufgerufen, um einen Teil des Containers neu zu streichen.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Wird aufgerufen, wenn ein Steuerelement aktiviert werden soll.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Wird aufgerufen, wenn ein Steuerelement deaktiviert werden soll.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Wird vom Framework aufgerufen, wenn Bildlaufnachrichten von einem untergeordneten Fenster empfangen werden.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Sendet eine Nachricht an das angegebene Steuerelement.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Legt den Wert des angegebenen Steuerelements fest.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Legt den Text des angegebenen Steuerelements fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Die Hintergrundfarbe des Containers.|
|[COleControlContainer::m_crFore](#m_crfore)|Die Vordergrundfarbe des Containers.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Eine Liste der unterstützten Kontrollsites.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Die Anzahl der gehosteten fensterlosen Steuerelemente.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Ein Zeiger auf die OLE-Schriftart der benutzerdefinierten Steuerelementsite.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Zeiger auf die Erfassungskontrollstelle.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Zeiger auf das Steuerelement, das derzeit über den Eingabefokus verfügt.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Zeiger auf das Steuerelement, das derzeit an Ort und Stelle aktiviert ist.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Zeigen Sie auf das Fenster, in dem der Steuerelementcontainer implementiert wird.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Die Sitemap.|

## <a name="remarks"></a>Bemerkungen

Dies geschieht durch Unterstützung für eine oder mehrere `COleControlSite`ActiveX-Kontrollsites (implementiert von ). `COleControlContainer`implementiert die [Schnittstellen IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) und [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) vollständig, sodass die enthaltenen ActiveX-Steuerelemente ihre Qualifikationen als ortsgebundene Elemente erfüllen können.

In der Regel wird diese `COccManager` `COleControlSite` Klasse in Verbindung mit und zum Implementieren eines benutzerdefinierten ActiveX-Steuerelementcontainers mit benutzerdefinierten Sites für ein oder mehrere ActiveX-Steuerelemente verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Wird vom Framework aufgerufen, um eine Kontrollsite zu erstellen und anzufügen.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf ein `CWnd`-Objekt.

*nIDC*<br/>
Die ID des zu beanstandenden Steuerelements.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie diesen Prozess anpassen möchten.

> [!NOTE]
> Verwenden Sie die erste Form dieser Funktion, wenn Sie statisch eine Verknüpfung mit der MFC-Bibliothek herstellen. Verwenden Sie das zweite Formular, wenn Sie dynamisch eine Verknüpfung mit der MFC-Bibliothek herstellen.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informiert alle gehosteten Steuerelemente, dass sich eine Umgebungseigenschaft geändert hat.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die Dispatch-ID der geänderten Umgebungseigenschaft.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom Framework aufgerufen, wenn eine ambient-Eigenschaft den Wert geändert hat. Überschreiben Sie diese Funktion, um dieses Verhalten anzupassen.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Ändert den aktuellen Status der Schaltfläche.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parameter

*nIDButton*<br/>
Die ID der zu ändernden Schaltfläche.

*nCheck*<br/>
Gibt den Status der Schaltfläche an. Dabei kann es sich um eine der folgenden Methoden handeln:

- BST_CHECKED Legt den Schaltflächenstatus auf aktiviert fest.

- BST_INDETERMINATE Legt den Schaltflächenstatus auf grau fest und gibt einen unbestimmten Zustand an. Verwenden Sie diesen Wert nur, wenn die Schaltfläche den BS_3STATE- oder BS_AUTO3STATE-Stil hat.

- BST_UNCHECKED Legt den Schaltflächenstatus auf "Löschen" fest.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Wählt ein angegebenes Optionsfeld in einer Gruppe aus und löscht die verbleibenden Schaltflächen in der Gruppe.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parameter

*nIDFirstButton*<br/>
Gibt den Bezeichner des ersten Optionsfelds in der Gruppe an.

*nIDLastButton*<br/>
Gibt den Bezeichner des letzten Optionsfelds in der Gruppe an.

*nIDCheckButton*<br/>
Gibt den Bezeichner des zu überprüfenden Optionsfelds an.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Erstellt ein `COleControlContainer`-Objekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster des Steuerelementcontainers.

### <a name="remarks"></a>Bemerkungen

Nachdem das Objekt erfolgreich erstellt wurde, fügen Sie `AttachControlSite`eine benutzerdefinierte Steuerelementsite mit einem Aufruf von hinzu.

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl

Erstellt ein ActiveX-Steuerelement, `COleControlSite` das vom angegebenen Objekt gehostet wird.

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>Parameter

*pWndCtrl*<br/>
Ein Zeiger auf das Fensterobjekt, das das Steuerelement darstellt.

*clsid*<br/>
Die eindeutige Klassen-ID des Steuerelements.

*lpszWindowName*<br/>
Ein Zeiger auf den Text, der im Steuerelement angezeigt werden soll. Legt den Wert der Beschriftungs- oder Texteigenschaft des Steuerelements fest (falls vorhanden). Wenn NULL, wird die Beschriftungs- oder Texteigenschaft des Steuerelements nicht geändert.

*dwStyle*<br/>
Windows-Stile. Die verfügbaren Stile sind im Abschnitt **"Bemerkungen"** aufgeführt.

*Rect*<br/>
Gibt die Größe und Position des Steuerelements an. Es kann entweder `CRect` ein `RECT` Objekt oder eine Struktur sein.

*nID*<br/>
Gibt die untergeordnete Fenster-ID des Steuerelements an.

*pPersist*<br/>
Ein Zeiger auf `CFile` einen, der den persistenten Zustand für das Steuerelement enthält. Der Standardwert ist NULL, was darauf hinweist, dass sich das Steuerelement selbst initialisiert, ohne seinen Status aus einem persistenten Speicher wiederherzustellen. Wenn nicht NULL, sollte es ein `CFile`Zeiger auf ein -derived-Objekt sein, das die persistenten Daten des Steuerelements in Form eines Streams oder eines Speichers enthält. Diese Daten hätten bei einer vorherigen Aktivierung des Clients gespeichert werden können. Der `CFile` kann andere Daten enthalten, muss jedoch den Lese-/Schreibzeiger auf das erste Byte `CreateControl`persistenter Daten zum Zeitpunkt des Aufrufs von festlegen.

*bSpeicher*<br/>
Gibt an, ob die Daten `IStorage` in `IStream` *pPersist* als oder als Daten interpretiert werden sollen. Wenn es sich bei den Daten in *pPersist* um einen Speicher handelt, sollte *bStorage* TRUE sein. Wenn es sich bei den Daten in *pPersist* um einen Stream handelt, sollte *bStorage* FALSE sein. Der Standardwert ist FALSE.

*bstrLicKey*<br/>
Optionale Lizenzschlüsseldaten. Diese Daten werden nur zum Erstellen von Steuerelementen benötigt, die einen Laufzeitlizenzschlüssel erfordern. Wenn das Steuerelement die Lizenzierung unterstützt, müssen Sie einen Lizenzschlüssel angeben, damit das Steuerelement erfolgreich ausgeführt werden kann. Der Standardwert ist NULL.

*ppNewSite*<br/>
Ein Zeiger auf die vorhandene Kontrollsite, die das erstellte Steuerelement hosten soll. Der Standardwert ist NULL, was darauf hinweist, dass automatisch eine neue Kontrollsite erstellt und dem neuen Steuerelement zugeordnet wird.

*Ppt*<br/>
Ein Zeiger auf `POINT` eine Struktur, die die obere linke Ecke des Steuerelements enthält. Die Größe des Steuerelements wird durch den Wert von *psize*bestimmt. Die *ppt-* und *psize-Werte* sind eine optionale Methode zum Angeben der Größe und Position des Steuerelements.

*psize*<br/>
Ein Zeiger auf `SIZE` eine Struktur, die die Größe des Steuerelements enthält. Die obere linke Ecke wird durch den Wert von *ppt*bestimmt. Die *ppt-* und *psize-Werte* sind eine optionale Methode zum Angeben der Größe und Position des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Nur eine Teilmenge der Windows *dwStyle-Flags* wird unterstützt von: `CreateControl`

- WS_VISIBLE Erstellt ein Fenster, das zunächst sichtbar ist. Erforderlich, wenn das Steuerelement wie normale Fenster sofort sichtbar sein soll.

- WS_DISABLED Erstellt ein Fenster, das zunächst deaktiviert ist. Ein deaktiviertes Fenster kann keine Eingaben vom Benutzer empfangen. Kann festgelegt werden, wenn das Steuerelement über eine Enabled-Eigenschaft verfügt.

- WS_BORDER Erstellt ein Fenster mit einem dünnen Rahmen. Kann festgelegt werden, wenn das Steuerelement über eine BorderStyle-Eigenschaft verfügt.

- WS_GROUP Gibt das erste Steuerelement einer Gruppe von Steuerelementen an. Der Benutzer kann den Tastaturfokus mithilfe der Richtungstasten von einem Steuerelement in der Gruppe zum nächsten ändern. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP-Stil definiert wurden, gehören zur gleichen Gruppe. Das nächste Steuerelement mit dem Stil WS_GROUP beendet die Gruppe und startet die nächste Gruppe.

- WS_TABSTOP Gibt ein Steuerelement an, das den Tastaturfokus empfangen kann, wenn der Benutzer die TAB-Taste drückt. Durch Drücken der TAB-Taste wird der Tastaturfokus auf das nächste Steuerelement des WS_TABSTOP-Stils geändert.

Verwenden Sie die zweite Überladung, um Steuerelemente in Der Standardgröße zu erstellen.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

Erstellt eine OLE-Schriftart.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pFont*<br/>
Ein Zeiger auf die Schriftart, die vom Steuerelementcontainer verwendet werden soll.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

Sucht die benutzerdefinierte Website, die das angegebene Element hostet.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des zu findenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die benutzerdefinierte Site des angegebenen Elements.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Legt fest, ob der Container Ereignisse von den angefügten Kontrollstandorten ignoriert oder akzeptiert.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parameter

*bEinfrieren*<br/>
Ein Wert ungleich Null, wenn Ereignisse verarbeitet werden; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das Steuerelement ist nicht erforderlich, um das Auslösen von Ereignissen zu beenden, wenn dies vom Steuerelementcontainer angefordert wird. Es kann weiterhin ausgelöst werden, aber alle nachfolgenden Ereignisse werden vom Steuerelementcontainer ignoriert.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Ruft den Wert einer angegebenen Umgebungseigenschaft ab.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parameter

*pSite*<br/>
Ein Zeiger auf einen Kontrollort, von dem die ambient-Eigenschaft abgerufen wird.

*Dispid*<br/>
Die Dispatch-ID der gewünschten Ambient-Eigenschaft.

*pVarResult*<br/>
Ein Zeiger auf den Wert der ambient-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Ruft einen Zeiger auf das angegebene Steuerelement oder untergeordnete Fenster in einem Dialogfeld oder einem anderen Fenster ab.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Bezeichner des abzurufenden Dialogelements.

*phWnd*<br/>
Ein Zeiger auf das Handle des Fensterobjekts des angegebenen Dialogfeldelements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Fenster des Dialogelements.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Ruft den Wert des übersetzten Texts des angegebenen Steuerelements ab.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuerelements.

*lpTrans*<br/>
Zeiger auf eine boolesche Variable, die einen Funktionserfolgs-/Fehlerwert empfängt (TRUE gibt Erfolg, FALSE einen Fehler an).

*bSigned*<br/>
Gibt an, ob die Funktion den Text auf ein Minuszeichen am Anfang untersuchen und einen signierten Ganzzahlwert zurückgeben soll, wenn sie einen wert findet. Wenn der *parameter bSigned* TRUE ist und angibt, dass es sich bei dem abzuholenden Wert um einen signierten Ganzzahlwert handelt, wird der Rückgabewert in einen **int-Typ** umgeworfen. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)an.

### <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, wird die Variable, auf die von *lpTrans* verwiesen wird, auf TRUE gesetzt, und der Rückgabewert ist der übersetzte Wert des Steuertexts.

Wenn die Funktion fehlschlägt, wird die Variable, auf die von *lpTrans* verwiesen wird, auf FALSE gesetzt, und der Rückgabewert ist Null. Da Null ein möglicher übersetzter Wert ist, weist ein Rückgabewert von Null nicht allein auf einen Fehler hin.

Wenn *lpTrans* NULL ist, gibt die Funktion keine Informationen über Erfolg oder Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die Funktion übersetzt den abgerufenen Text, indem alle zusätzlichen Leerzeichen am Anfang des Textes abstreifen und dann die Dezimalstellen konvertiert werden. Die Funktion beendet die Übersetzung, wenn sie das Ende des Textes erreicht oder auf ein nicht numerisches Zeichen trifft.

Diese Funktion gibt Null zurück, wenn der übersetzte Wert größer als INT_MAX (für signierte Zahlen) oder UINT_MAX (für nicht signierte Nummern) ist.

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Ruft den Text des angegebenen Steuerelements ab.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuerelements.

*Lpstr*<br/>
Zeiger auf den Text des Steuerelements.

*nMaxCount*<br/>
Gibt die maximale Länge der Zeichenfolge in Zeichen an, auf die in den Puffer von *lpStr*verwiesen werden soll. Wenn die Länge der Zeichenfolge den Grenzwert überschreitet, wird die Zeichenfolge abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist, gibt der Rückgabewert die Anzahl der in den Puffer kopierten Zeichen an, ohne das beendende Nullzeichen.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)an.

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Bestimmt, ob der Container WM_SETFOCUS Nachrichten verarbeitet.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Container WM_SETFOCUS Nachrichten verarbeitet; andernfalls Null.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Verarbeitet Fenstermeldungen für fensterlose Steuerelemente.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Der Bezeichner für die Fensternachricht, der von Windows bereitgestellt wird.

*wParam*<br/>
Parameter der Nachricht; von Windows bereitgestellt werden. Gibt zusätzliche nachrichtenspezifische Informationen an. Der Inhalt dieses Parameters hängt vom Wert des *Message-Parameters* ab.

*lParam*<br/>
Parameter der Nachricht; von Windows bereitgestellt werden. Gibt zusätzliche nachrichtenspezifische Informationen an. Der Inhalt dieses Parameters hängt vom Wert des *Message-Parameters* ab.

*plResult*<br/>
Windows-Ergebniscode. Gibt das Ergebnis der Nachrichtenverarbeitung an und hängt von der gesendeten Nachricht ab.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Handhabung von fensterlosen Steuermeldungen anzupassen.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

Bestimmt den Status der angegebenen Schaltfläche.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parameter

*nIDButton*<br/>
Der Bezeichner des Schaltflächensteuerelements.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert aus einer Schaltfläche, die mit dem Stil BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON oder BS_3STATE erstellt wurde. Dabei kann es sich um eine der folgenden Methoden handeln:

- BST_CHECKED-Taste ist aktiviert.

- BST_INDETERMINATE Schaltfläche ist grau und gibt einen unbestimmten Zustand an (gilt nur, wenn die Schaltfläche den BS_3STATE oder BS_AUTO3STATE Stil hat).

- BST_UNCHECKED-Taste wird gelöscht.

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei der Schaltfläche um ein Steuerelement mit drei Zusen handelt, bestimmt die Memberfunktion, ob sie abgeblendet, aktiviert oder beides nicht ist.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer::m_crBack

Die Hintergrundfarbe des Containers.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore

Die Vordergrundfarbe des Containers.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Eine Liste der vom Container gehosteten Kontrollsites.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Die Anzahl der fensterlosen Steuerelemente, die vom Steuerelementcontainer gehostet werden.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont

Ein Zeiger auf die OLE-Schriftart der benutzerdefinierten Steuerelementsite.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

Zeiger auf die Erfassungskontrollstelle.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

Ein Zeiger auf die Kontrollsite, die derzeit über den Eingabefokus verfügt.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

Ein Zeiger auf die kontrollierbare Kontrollstelle, die an Ort und Stelle aktiviert ist.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd

Ein Zeiger auf das Fensterobjekt, das dem Container zugeordnet ist.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap

Die Sitemap.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint

Wird vom Framework aufgerufen, um WM_PAINT Anforderungen zu verarbeiten.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger auf den Gerätekontext, der vom Container verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wurde; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um den Malvorgang anzupassen.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Wird vom Framework aufgerufen, wenn die Kontrollsite, auf die von *pSite*verwiesen wird, im Begriff ist, an Ort und Stelle aktiviert zu werden.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parameter

*pSite*<br/>
Ein Zeiger auf die Kontrollstelle, die unmittelbar vor Ort aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Die ortsbezogene Aktivierung bedeutet, dass das Hauptmenü des Containers durch ein in-Place-Composite-Menü ersetzt wird.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Wird vom Framework aufgerufen, wenn die Kontrollsite, auf die von *pSite*verwiesen wird, deaktiviert wird.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parameter

*pSite*<br/>
Ein Zeiger auf die Kontrollstelle, die deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn diese Benachrichtigung empfangen wird, sollte der Container seine Benutzeroberfläche neu installieren und den Fokus darauf richten.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Wird vom Framework aufgerufen, wenn Bildlaufnachrichten von einem untergeordneten Fenster empfangen werden.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parameter

*Dx*<br/>
Der In-Pixel-Betrag des Scrollens entlang der x-Achse.

*Dy*<br/>
Der In-Pixel-Betrag des Scrollens entlang der y-Achse.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

Sendet eine Nachricht an das angegebene Steuerelement.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Gibt den Bezeichner des Steuerelements an, das die Nachricht empfängt.

*Nachricht*<br/>
Gibt die zu sendende Nachricht an.

*wParam*<br/>
Gibt zusätzliche nachrichtenspezifische Informationen an.

*lParam*<br/>
Gibt zusätzliche nachrichtenspezifische Informationen an.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Legt den Text eines Steuerelements in einem Dialogfeld auf die Zeichenfolgendarstellung eines angegebenen Ganzzahlwerts fest.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuerelements.

*nValue*<br/>
Der ganzzahlige Wert, der angezeigt werden soll.

*bSigned*<br/>
Gibt an, ob der *nValue-Parameter* signiert oder nicht signiert ist. Wenn dieser Parameter TRUE ist, wird *nValue* signiert. Wenn dieser Parameter TRUE ist und *nValue* kleiner als Null ist, wird ein Minuszeichen vor der ersten Ziffer in der Zeichenfolge platziert. Wenn dieser Parameter FALSE ist, ist *nValue* nicht signiert.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

Legt den Text des angegebenen Steuerelements mithilfe des in *lpszString*enthaltenen Textes fest.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuerelements.

*lpszString*<br/>
Zeiger auf den Text des Steuerelements.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite-Klasse](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager-Klasse](../../mfc/reference/coccmanager-class.md)
