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
ms.openlocfilehash: 2c2c97090fc8255c06e1678a377fe2dcc968ffd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214112"
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
|[COleControlContainer:: COleControlContainer](#colecontrolcontainer)|Erstellt ein `COleControlContainer`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlContainer:: attachcontrolsite](#attachcontrolsite)|Erstellt eine Steuerelement Site, die vom Container gehostet wird.|
|[COleControlContainer:: BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informiert alle gehosteten Steuerelemente darüber, dass eine Ambient-Eigenschaft geändert wurde.|
|[COleControlContainer:: checkdlgbutton](#checkdlgbutton)|Ändert das angegebene Schaltflächen Steuerelement.|
|[COleControlContainer:: checkradio Button](#checkradiobutton)|Wählt das angegebene Optionsfeld einer Gruppe aus.|
|[COleControlContainer:: kreatecontrol](#createcontrol)|Erstellt ein gehostetes ActiveX-Steuerelement.|
|[COleControlContainer:: kreateolefont](#createolefont)|Erstellt eine OLE-Schriftart.|
|[COleControlContainer:: FindItem](#finditem)|Gibt die benutzerdefinierte Site des angegebenen Steuer Elements zurück.|
|[COleControlContainer:: frezeallevents](#freezeallevents)|Bestimmt, ob die Steuerelement Site Ereignisse annimmt.|
|[COleControlContainer:: getambientprop](#getambientprop)|Ruft die angegebene Ambient-Eigenschaft ab.|
|[COleControlContainer:: GetDlgItem](#getdlgitem)|Ruft das angegebene Dialogfeld Steuerelement ab.|
|[COleControlContainer:: getdlgitemint](#getdlgitemint)|Ruft den Wert des angegebenen Dialogfeld Steuer Elements ab.|
|[COleControlContainer:: getdlgitemtext](#getdlgitemtext)|Ruft die Beschriftung des angegebenen Dialogfeld Steuer Elements ab.|
|[COleControlContainer:: Lenker Fokus](#handlesetfocus)|Bestimmt, ob der Container WM_SETFOCUS Nachrichten verarbeitet.|
|[COleControlContainer:: Lenker Message Message](#handlewindowlessmessage)|Verarbeitet Nachrichten, die an ein fensterloses Steuerelement gesendet werden.|
|[COleControlContainer:: isdlgbuttoncheck](#isdlgbuttonchecked)|Bestimmt den Zustand der angegebenen Schaltfläche.|
|[COleControlContainer:: OnPaint](#onpaint)|Wird aufgerufen, um einen Teil des Containers neu zu zeichnen.|
|[COleControlContainer:: onuiaktivierungs](#onuiactivate)|Wird aufgerufen, wenn ein Steuerelement gerade direkt aktiviert wird.|
|[COleControlContainer:: onuideaktivierungs](#onuideactivate)|Wird aufgerufen, wenn ein Steuerelement im Begriff ist, deaktiviert zu werden.|
|[COleControlContainer:: scrollchildren](#scrollchildren)|Wird von Framework aufgerufen, wenn scrollnachrichten von einem untergeordneten Fenster empfangen werden.|
|[COleControlContainer:: SendDlgItemMess age](#senddlgitemmessage)|Sendet eine Nachricht an das angegebene Steuerelement.|
|[COleControlContainer:: setdlgitemint](#setdlgitemint)|Legt den Wert des angegebenen Steuer Elements fest.|
|[COleControlContainer:: SetDlgItemText](#setdlgitemtext)|Legt den Text des angegebenen Steuer Elements fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleControlContainer:: m_crBack](#m_crback)|Die Hintergrundfarbe des Containers.|
|[COleControlContainer:: m_crFore](#m_crfore)|Die Vordergrundfarbe des Containers.|
|[COleControlContainer:: m_listSitesOrWnds](#m_listsitesorwnds)|Eine Liste der unterstützten Steuerelement Sites.|
|[COleControlContainer:: m_nWindowlessControls](#m_nwindowlesscontrols)|Die Anzahl der gehosteten fensterlosen Steuerelemente.|
|[COleControlContainer:: m_pOleFont](#m_polefont)|Ein Zeiger auf die OLE-Schriftart der benutzerdefinierten Steuerelement Website.|
|[COleControlContainer:: m_pSiteCapture](#m_psitecapture)|Ein Zeiger auf die Erfassungs Steuerungs Website.|
|[COleControlContainer:: m_pSiteFocus](#m_psitefocus)|Zeiger auf das Steuerelement, das derzeit den Eingabefokus besitzt.|
|[COleControlContainer:: m_pSiteUIActive](#m_psiteuiactive)|Zeiger auf das Steuerelement, das gerade direkt aktiviert ist.|
|[COleControlContainer:: m_pWnd](#m_pwnd)|Zeiger auf das Fenster, das den Steuerelement Container implementiert.|
|[COleControlContainer:: m_siteMap](#m_sitemap)|Die Site Übersicht.|

## <a name="remarks"></a>Bemerkungen

Dies erfolgt durch Bereitstellen von Unterstützung für eine oder mehrere ActiveX-Steuerelement Sites (implementiert von `COleControlSite` ). `COleControlContainer`implementiert die [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) -Schnittstelle und die [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) -Schnittstelle vollständig, sodass die enthaltenen ActiveX-Steuerelemente ihre Qualifikationen als direkte Elemente erfüllen können.

Diese Klasse wird häufig in Verbindung mit und verwendet `COccManager` , `COleControlSite` um einen benutzerdefinierten ActiveX-Steuerelement Container mit benutzerdefinierten Websites für ein oder mehrere ActiveX-Steuerelemente zu implementieren.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxocc. h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer:: attachcontrolsite

Wird von Framework aufgerufen, um eine Steuerelement Site zu erstellen und anzufügen.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf ein `CWnd`-Objekt.

*nIDC*<br/>
Die ID des anzufügenden Steuer Elements.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie diesen Prozess anpassen möchten.

> [!NOTE]
> Verwenden Sie die erste Form dieser Funktion, wenn Sie statisch mit der MFC-Bibliothek verknüpfen. Verwenden Sie das zweite Formular, wenn Sie dynamisch mit der MFC-Bibliothek verknüpfen.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer:: BroadcastAmbientPropertyChange

Informiert alle gehosteten Steuerelemente darüber, dass eine Ambient-Eigenschaft geändert wurde.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID der Ambient-Eigenschaft, die geändert wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von Framework aufgerufen, wenn eine Ambient-Eigenschaft den Wert geändert hat. Überschreiben Sie diese Funktion, um dieses Verhalten anzupassen.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer:: checkdlgbutton

Ändert den aktuellen Zustand der Schaltfläche.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parameter

*nidbutton*<br/>
Die ID der Schaltfläche, die geändert werden soll.

*nPrüfen*<br/>
Gibt den Zustand der Schaltfläche an. Dabei kann es sich um eine der folgenden Methoden handeln:

- BST_CHECKED legt den Schaltflächen Zustand auf aktiviert fest.

- BST_INDETERMINATE legt den Zustand der Schaltfläche auf abgeblendet fest und gibt einen unbestimmten Zustand an. Verwenden Sie diesen Wert nur, wenn die Schaltfläche die BS_3STATE oder BS_AUTO3STATE Format hat.

- BST_UNCHECKED legt den Schaltflächen Zustand auf "deaktiviert" fest.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer:: checkradio Button

Wählt eine angegebene Options Schaltfläche in einer Gruppe aus und löscht die verbleibenden Schaltflächen in der Gruppe.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parameter

*nidfirstbutton*<br/>
Gibt den Bezeichner des ersten Options Felds in der Gruppe an.

*nidlastbutton*<br/>
Gibt den Bezeichner des letzten Options Felds in der Gruppe an.

*nidcheckbutton*<br/>
Gibt den Bezeichner des Options Felds an, das geprüft werden soll.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer:: COleControlContainer

Erstellt ein `COleControlContainer`-Objekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Ein Zeiger auf das übergeordnete Fenster des Steuerelement Containers.

### <a name="remarks"></a>Bemerkungen

Nachdem das Objekt erfolgreich erstellt wurde, fügen Sie eine benutzerdefinierte Steuerungs Website mit einem-Befehl hinzu `AttachControlSite` .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer:: kreatecontrol

Erstellt ein ActiveX-Steuerelement, das vom angegebenen-Objekt gehostet wird `COleControlSite` .

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

*pwndctrl*<br/>
Ein Zeiger auf das Fenster Objekt, das das Steuerelement darstellt.

*CLSID*<br/>
Die eindeutige Klassen-ID des Steuer Elements.

*lpszWindowName*<br/>
Ein Zeiger auf den Text, der im-Steuerelement angezeigt werden soll. Legt den Wert der Beschriftung-oder Text-Eigenschaft des Steuer Elements fest (sofern vorhanden). Wenn der Wert NULL ist, wird die Beschriftung oder die Text-Eigenschaft des Steuer Elements nicht geändert.

*dwstyle*<br/>
Windows-Stile. Die verfügbaren Stile sind im Abschnitt " **Hinweise** " aufgeführt.

*Rect*<br/>
Gibt die Größe und Position des Steuer Elements an. Dies kann entweder ein- `CRect` Objekt oder eine- `RECT` Struktur sein.

*nID*<br/>
Gibt die untergeordnete Fenster-ID des Steuer Elements an.

*ppersistent*<br/>
Ein Zeiger auf einen, `CFile` der den persistenten Zustand für das Steuerelement enthält. Der Standardwert ist NULL, was bedeutet, dass das Steuerelement selbst initialisiert wird, ohne seinen Zustand aus einem persistenten Speicher wiederherzustellen. Wenn nicht NULL, sollte es sich um einen Zeiger auf ein von `CFile` abgeleitetes Objekt handeln, das die persistenten Daten des Steuer Elements in Form eines Datenstroms oder eines Speichers enthält. Diese Daten wurden möglicherweise bei einer früheren Aktivierung des Clients gespeichert. Der `CFile` kann andere Daten enthalten, muss jedoch zum Zeitpunkt des Aufrufes auf das erste Byte der persistenten Daten festgelegt sein `CreateControl` .

*bstorage*<br/>
Gibt an, ob die Daten in *ppersistent* als-oder-Daten interpretiert werden sollen `IStorage` `IStream` . Wenn es sich bei den *ppersistent* -Daten um einen Speicher handelt, sollte *bstorage* den Wert true haben. Wenn es sich bei den *ppersistent* -Daten um einen Stream handelt, sollte *bstorage* den Wert false aufweisen. Der Standardwert ist FALSE.

*bstraulickey*<br/>
Optionale Lizenzschlüssel Daten. Diese Daten werden nur zum Erstellen von Steuerelementen benötigt, für die ein Laufzeitlizenz Schlüssel erforderlich ist. Wenn das Steuerelement die Lizenzierung unterstützt, müssen Sie einen Lizenzschlüssel bereitstellen, damit die Erstellung des Steuer Elements erfolgreich ist. Der Standardwert ist NULL.

*ppnewsite*<br/>
Ein Zeiger auf die vorhandene Steuerungs Site, die das zu erstellende Steuerelement hostet. Der Standardwert ist NULL, was bedeutet, dass automatisch eine neue Steuerungs Site erstellt und an das neue Steuerelement angefügt wird.

*PPT*<br/>
Ein Zeiger auf eine- `POINT` Struktur, die die linke obere Ecke des-Steuer Elements enthält. Die Größe des Steuer Elements wird durch den Wert von *Psize*bestimmt. Die *PPT* -und *Psize* -Werte sind eine optionale Methode zum Angeben der Größe und Position des Steuer Elements.

*Psize*<br/>
Ein Zeiger auf eine- `SIZE` Struktur, die die Größe des-Steuer Elements enthält. Die linke obere Ecke wird durch den Wert von *PPT*bestimmt. Die *PPT* -und *Psize* -Werte sind eine optionale Methode zum Angeben der Größe und Position des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Nur eine Teilmenge der Windows *dwstyle* -Flags wird unterstützt von `CreateControl` :

- WS_VISIBLE erstellt ein Fenster, das anfänglich sichtbar ist. Erforderlich, wenn das Steuerelement sofort sichtbar sein soll, wie z. b. gewöhnliche Fenster.

- WS_DISABLED erstellt ein Fenster, das anfänglich deaktiviert ist. Ein deaktiviertes Fenster kann keine Eingaben vom Benutzer empfangen. Kann festgelegt werden, wenn das Steuerelement über eine aktivierte Eigenschaft verfügt.

- WS_BORDER erstellt ein Fenster mit einem dünn zeiligen Rahmen. Kann festgelegt werden, wenn das Steuerelement eine BorderStyle-Eigenschaft aufweist.

- WS_GROUP gibt das erste Steuerelement einer Gruppe von Steuerelementen an. Der Benutzer kann den Tastaturfokus mithilfe der Richtungs Tasten von einem Steuerelement in der Gruppe zur nächsten ändern. Alle Steuerelemente, die nach dem ersten Steuerelement mit dem WS_GROUP Format definiert sind, gehören zur selben Gruppe. Das nächste Steuerelement mit dem WS_GROUP Stil beendet die Gruppe und startet die nächste Gruppe.

- WS_TABSTOP gibt ein Steuerelement an, das den Tastaturfokus erhalten kann, wenn der Benutzer die Tab-Taste drückt. Wenn Sie die Tab-Taste drücken, wird der Tastaturfokus auf das nächste Steuerelement des WS_TABSTOP Stils geändert.

Verwenden Sie die zweite Überladung, um Steuerelemente mit Standardgrößen zu erstellen.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer:: kreateolefont

Erstellt eine OLE-Schriftart.

```cpp
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parameter

*pfont*<br/>
Ein Zeiger auf die Schriftart, die vom Steuerelement Container verwendet werden soll.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer:: FindItem

Sucht die benutzerdefinierte Site, die das angegebene Element hostet.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Elements, das gefunden werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die benutzerdefinierte Site des angegebenen Elements.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer:: frezeallevents

Bestimmt, ob der Container Ereignisse von den angefügten Steuerungs Standorten ignoriert oder akzeptiert.

```cpp
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parameter

*bfreeze*<br/>
Ungleich 0 (null), wenn Ereignisse verarbeitet werden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das-Steuerelement ist nicht erforderlich, um das Auslösen von Ereignissen zu verhindern, wenn es vom Steuerelement Container angefordert Sie kann weiterhin ausgelöst werden, aber alle nachfolgenden Ereignisse werden vom Steuerelement Container ignoriert.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer:: getambientprop

Ruft den Wert einer angegebenen Ambient-Eigenschaft ab.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parameter

*psite*<br/>
Ein Zeiger auf eine Steuerelement Website, von der die Ambient-Eigenschaft abgerufen wird.

*DISPID*<br/>
Die Dispatch-ID der gewünschten Ambient-Eigenschaft.

*pVarResult*<br/>
Ein Zeiger auf den Wert der Ambient-Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer:: GetDlgItem

Ruft einen Zeiger auf das angegebene Steuerelement oder untergeordnete Fenster in einem Dialogfeld oder einem anderen Fenster ab.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des abzurufenden Dialog Felds.

*phwnd*<br/>
Ein Zeiger auf das Handle des Fenster Objekts des angegebenen Dialog Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Fenster des Dialog Elements.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer:: getdlgitemint

Ruft den Wert des übersetzten Texts des angegebenen Steuer Elements ab.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuer Elements.

*lptrans*<br/>
Zeiger auf eine boolesche Variable, die einen Funktions Erfolg/-Fehlerwert empfängt (true gibt Erfolg an, false gibt einen Fehler an).

*bsigniert*<br/>
Gibt an, ob die Funktion den Text für ein Minuszeichen am Anfang untersuchen und einen ganzzahligen Wert mit Vorzeichen zurückgeben soll, wenn ein Wert gefunden wird. Wenn der *bsigned* -Parameter true ist, wird angegeben, dass der abzurufende Wert ein ganzzahliger Wert mit Vorzeichen ist. wandeln Sie den Rückgabewert in einen- **`int`** Typ um. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung ist die Variable, auf die von *lptrans* verwiesen wird, auf true festgelegt, und der Rückgabewert ist der übersetzte Wert des Steuerelement Texts.

Wenn die Funktion fehlschlägt, wird die Variable, auf die von *lptrans* verwiesen wird, auf false festgelegt, und der Rückgabewert ist 0 (null). Beachten Sie, dass der Rückgabewert NULL nicht allein auf einen Fehler hinweist, da NULL ein möglicher über setzter Wert ist.

Wenn *lptrans* NULL ist, gibt die Funktion keine Informationen über Erfolg oder Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die Funktion übersetzt den abgerufenen Text, indem alle zusätzlichen Leerzeichen am Anfang des Texts entfernt werden und anschließend die Dezimalziffern konvertiert werden. Die-Funktion beendet die Übersetzung, wenn Sie das Ende des Texts erreicht oder ein nicht numerisches Zeichen trifft.

Diese Funktion gibt 0 (null) zurück, wenn der übersetzte Wert größer als INT_MAX (für signierte Zahlen) oder UINT_MAX (für nicht signierte Zahlen) ist.

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer:: getdlgitemtext

Ruft den Text des angegebenen Steuer Elements ab.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuer Elements.

*lpStr*<br/>
Zeiger auf den Text des Steuer Elements.

*nMaxCount*<br/>
Gibt die maximale Länge (in Zeichen) der Zeichenfolge an, die in den Puffer kopiert werden soll, auf den von *LPSTR*verwiesen wird. Wenn die Länge der Zeichenfolge den Grenzwert überschreitet, wird die Zeichenfolge abgeschnitten.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ausgeführt wird, gibt der Rückgabewert die Anzahl der in den Puffer kopierten Zeichen an, ohne das abschließende Null Zeichen.

Wenn die Funktion fehlerhaft ist, ist der Rückgabewert null. Um erweiterte Fehlerinformationen abzurufen, nennen Sie [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer:: Lenker Fokus

Bestimmt, ob der Container WM_SETFOCUS Nachrichten verarbeitet.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Container WM_SETFOCUS Nachrichten verarbeitet. andernfalls NULL.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer:: Lenker Message Message

Verarbeitet Fenster Meldungen für fensterlose Steuerelemente.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
Der Bezeichner für die Fenster Meldung, der von Windows bereitgestellt wird.

*wParam*<br/>
Der-Parameter der Nachricht. von Windows bereitgestellt. Gibt zusätzliche Nachrichten spezifische Informationen an. Der Inhalt dieses Parameters hängt vom Wert des *Message* -Parameters ab.

*lParam*<br/>
Der-Parameter der Nachricht. von Windows bereitgestellt. Gibt zusätzliche Nachrichten spezifische Informationen an. Der Inhalt dieses Parameters hängt vom Wert des *Message* -Parameters ab.

*plresult*<br/>
Windows-Ergebniscode. Gibt das Ergebnis der Nachrichtenverarbeitung an und hängt von der gesendeten Nachricht ab.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Handhabung von fensterlosen Steuerelement Meldungen anzupassen.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer:: isdlgbuttoncheck

Bestimmt den Zustand der angegebenen Schaltfläche.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parameter

*nidbutton*<br/>
Der Bezeichner des Schaltflächen-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert aus einer Schaltfläche, die mit dem BS_AUTOCHECKBOX-, BS_AUTORADIOBUTTON-, BS_AUTO3STATE-, BS_CHECKBOX-, BS_RADIOBUTTON-oder BS_3STATE-Format erstellt wurde. Dabei kann es sich um eine der folgenden Methoden handeln:

- BST_CHECKED Schaltfläche aktiviert ist.

- BST_INDETERMINATE Schaltfläche ist abgeblendet und gibt einen unbestimmten Zustand an (gilt nur, wenn die Schaltfläche die BS_3STATE oder BS_AUTO3STATE Stil hat).

- BST_UNCHECKED Schaltfläche ist deaktiviert.

### <a name="remarks"></a>Bemerkungen

Wenn die Schaltfläche ein drei-Status-Steuerelement ist, bestimmt die Member-Funktion, ob Sie abdimmt, überprüft oder keines von beiden ist.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer:: m_crBack

Die Hintergrundfarbe des Containers.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer:: m_crFore

Die Vordergrundfarbe des Containers.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer:: m_listSitesOrWnds

Eine Liste der vom Container gehosteten Steuerelement Sites.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer:: m_nWindowlessControls

Die Anzahl der fensterlosen Steuerelemente, die vom Steuerelement Container gehostet werden.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer:: m_pOleFont

Ein Zeiger auf die OLE-Schriftart der benutzerdefinierten Steuerelement Website.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer:: m_pSiteCapture

Ein Zeiger auf die Erfassungs Steuerungs Website.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer:: m_pSiteFocus

Ein Zeiger auf die Steuerelement Site, die derzeit den Eingabefokus besitzt.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer:: m_pSiteUIActive

Ein Zeiger auf die Steuerungs Site, die direkt aktiviert ist.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer:: m_pWnd

Ein Zeiger auf das Fenster Objekt, das dem Container zugeordnet ist.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer:: m_siteMap

Die Site Übersicht.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer:: OnPaint

Wird von Framework aufgerufen, um WM_PAINT Anforderungen zu verarbeiten.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
Ein Zeiger auf den Gerätekontext, der vom Container verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Meldung behandelt wurde. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um den Zeichnungsprozess anzupassen.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer:: onuiaktivierungs

Wird von Framework aufgerufen, wenn die Steuerungs Website, auf die von *psite*verwiesen wird, direkt aktiviert wird.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parameter

*psite*<br/>
Ein Zeiger auf die Steuerungs Site, die direkt aktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Direkte Aktivierung bedeutet, dass das Haupt Menü des Containers durch ein direktes zusammengesetztes Menü ersetzt wird.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer:: onuideaktivierungs

Wird von Framework aufgerufen, wenn die Steuerungs Website, auf die von *psite*verwiesen wird, gerade deaktiviert wird.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parameter

*psite*<br/>
Ein Zeiger auf die Steuerungs Site, die deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Beim Empfang dieser Benachrichtigung sollte der Container seine Benutzeroberfläche neu installieren und den Fokus übernehmen.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer:: scrollchildren

Wird von Framework aufgerufen, wenn scrollnachrichten von einem untergeordneten Fenster empfangen werden.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parameter

*Market*<br/>
Der Umfang des Bildlaufs auf der x-Achse in Pixel.

*reiche*<br/>
Der Umfang des Bildlaufs auf der y-Achse in Pixel.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer:: SendDlgItemMess age

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
Gibt den Bezeichner des Steuer Elements an, das die Nachricht empfängt.

*Nachricht*<br/>
Gibt die zu sendende Nachricht an.

*wParam*<br/>
Gibt zusätzliche Nachrichten spezifische Informationen an.

*lParam*<br/>
Gibt zusätzliche Nachrichten spezifische Informationen an.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer:: setdlgitemint

Legt den Text eines-Steuer Elements in einem Dialogfeld auf die Zeichen folgen Darstellung eines angegebenen ganzzahligen Werts fest.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuer Elements.

*nWert*<br/>
Der ganzzahlige Wert, der angezeigt werden soll.

*bsigniert*<br/>
Gibt an, ob der *nValue* -Parameter signiert oder nicht signiert ist. Wenn dieser Parameter true ist, wird *nValue* signiert. Wenn dieser Parameter true und *nValue* kleiner als 0 (null) ist, wird vor der ersten Ziffer in der Zeichenfolge ein Minuszeichen eingefügt. Wenn dieser Parameter false ist, wird *nValue* nicht signiert.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer:: SetDlgItemText

Legt den Text des angegebenen Steuer Elements fest, wobei der in *lpszstring*enthaltene Text verwendet wird.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Der Bezeichner des Steuer Elements.

*lpszstring*<br/>
Zeiger auf den Text des Steuer Elements.

## <a name="see-also"></a>Weitere Informationen

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite-Klasse](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager-Klasse](../../mfc/reference/coccmanager-class.md)
