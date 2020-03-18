---
title: COlePropertyPage-Klasse
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426486"
---
# <a name="colepropertypage-class"></a>COlePropertyPage-Klasse

Wird verwendet, um die Eigenschaften eines benutzerdefinierten Steuerelements in einer grafischen Oberfläche anzuzeigen, ähnlich wie in einem Dialogfeld.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[COlePropertyPage:: COlePropertyPage](#colepropertypage)|Erstellt ein `COlePropertyPage`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[COlePropertyPage:: getcontrolstatus](#getcontrolstatus)|Gibt an, ob der Benutzer den Wert im-Steuerelement geändert hat.|
|[COlePropertyPage:: getobjectarray](#getobjectarray)|Gibt das Array von-Objekten zurück, die von der Eigenschaften Seite bearbeitet werden.|
|[COlePropertyPage:: getpagesite](#getpagesite)|Gibt einen Zeiger auf die `IPropertyPageSite`-Schnittstelle der Eigenschaften Seite zurück.|
|[COlePropertyPage:: ignoreapply](#ignoreapply)|Bestimmt, welche Steuerelemente die Schaltfläche anwenden nicht aktivieren.|
|[COlePropertyPage:: IsModified](#ismodified)|Gibt an, ob der Benutzer die Eigenschaften Seite geändert hat.|
|[COlePropertyPage:: oneditproperty](#oneditproperty)|Wird von Framework aufgerufen, wenn der Benutzer eine Eigenschaft bearbeitet.|
|[COlePropertyPage:: onhelp](#onhelp)|Wird von Framework aufgerufen, wenn der Benutzer die Hilfe aufruft.|
|[COlePropertyPage:: OnInitDialog](#oninitdialog)|Wird von Framework aufgerufen, wenn die Eigenschaften Seite initialisiert wird.|
|[COlePropertyPage:: onobjectschge](#onobjectschanged)|Wird von Framework aufgerufen, wenn ein anderes OLE-Steuerelement mit neuen Eigenschaften ausgewählt wird.|
|[COlePropertyPage:: onsetpagesite](#onsetpagesite)|Wird von Framework aufgerufen, wenn der Eigenschaften Rahmen die Site der Seite bereitstellt.|
|[COlePropertyPage:: setcontrolstatus](#setcontrolstatus)|Legt ein Flag fest, das angibt, ob der Benutzer den Wert im-Steuerelement geändert hat.|
|[COlePropertyPage:: setdialogresource](#setdialogresource)|Legt die Dialog Ressource der Eigenschaften Seite fest.|
|[COlePropertyPage:: Setup Info](#sethelpinfo)|Legt den kurzen Hilfetext der Eigenschaften Seite, den Namen der Hilfedatei und den zugehörigen Hilfe Kontext fest.|
|[COlePropertyPage:: SetModifiedFlag](#setmodifiedflag)|Legt ein Flag fest, das angibt, ob der Benutzer die Eigenschaften Seite geändert hat.|
|[COlePropertyPage:: setpagename](#setpagename)|Legt den Namen der Eigenschaften Seite (Beschriftung) fest.|

## <a name="remarks"></a>Hinweise

Beispielsweise kann eine Eigenschaften Seite ein Bearbeitungs Steuerelement enthalten, das es dem Benutzer ermöglicht, die Caption-Eigenschaft des Steuer Elements anzuzeigen und zu ändern.

Jede benutzerdefinierte Eigenschaft oder Bestands Steuerungs Eigenschaft kann über ein Dialogfeld Steuerelement verfügen, das es dem Benutzer des Steuer Elements ermöglicht, den aktuellen Eigenschafts Wert anzuzeigen und diesen Wert bei Bedarf zu ändern.

Weitere Informationen zur Verwendung von `COlePropertyPage`finden Sie im Artikel [ActiveX-Steuerelemente: Eigenschaften Seiten](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxctl. h

##  <a name="colepropertypage"></a>COlePropertyPage:: COlePropertyPage

Erstellt ein `COlePropertyPage`-Objekt.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parameter

*iddlg*<br/>
Ressourcen-ID der Dialogfeld Vorlage.

*idcaption*<br/>
Die Ressourcen-ID der Beschriftung der Eigenschaften Seite.

### <a name="remarks"></a>Hinweise

Wenn Sie eine Unterklasse von `COlePropertyPage`implementieren, sollte der Konstruktor der Unterklasse den `COlePropertyPage`-Konstruktor verwenden, um die Dialogfeld Vorlagen Ressource zu identifizieren, auf der die Eigenschaften Seite basiert, und die Zeichen folgen Ressource, die die Beschriftung enthält.

##  <a name="getcontrolstatus"></a>COlePropertyPage:: getcontrolstatus

Bestimmt, ob der Benutzer den Wert des Eigenschaften Seiten-Steuer Elements mit der angegebenen Ressourcen-ID geändert hat.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parameter

*NID*<br/>
Ressourcen-ID eines Eigenschaften Seiten-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Steuerelement Wert geändert wurde. andernfalls false.

##  <a name="getobjectarray"></a>COlePropertyPage:: getobjectarray

Gibt das Array von-Objekten zurück, die von der Eigenschaften Seite bearbeitet werden.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parameter

*pnobjects*<br/>
Zeiger auf eine lange ganze Zahl ohne Vorzeichen, die die Anzahl der Objekte empfängt, die von der Seite bearbeitet werden.

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein Array von `IDispatch` Zeigern, die verwendet werden, um auf die Eigenschaften der einzelnen Steuerelemente auf der Eigenschaften Seite zuzugreifen. Der Aufrufer darf diese Schnittstellen Zeiger nicht freigeben.

### <a name="remarks"></a>Hinweise

Jedes Eigenschaften Seiten Objekt verwaltet ein Array von Zeigern auf die `IDispatch` Schnittstellen der Objekte, die von der Seite bearbeitet werden. Diese Funktion legt das *pnobjects* -Argument auf die Anzahl der Elemente in diesem Array fest und gibt einen Zeiger auf das erste Element des Arrays zurück.

##  <a name="getpagesite"></a>COlePropertyPage:: getpagesite

Ruft einen Zeiger auf die `IPropertyPageSite`-Schnittstelle der Eigenschaften Seite ab.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die `IPropertyPageSite`-Schnittstelle der Eigenschaften Seite.

### <a name="remarks"></a>Hinweise

Steuerelemente und Container arbeiten zusammen, sodass Benutzer Steuerelement Eigenschaften durchsuchen und bearbeiten können. Das-Steuerelement stellt Eigenschaften Seiten bereit, von denen jedes ein OLE-Objekt ist, das es dem Benutzer ermöglicht, einen zugehörigen Satz von Eigenschaften zu bearbeiten. Der Container stellt einen Eigenschaften Rahmen bereit, der die Eigenschaften Seiten anzeigt. Der Eigenschaften Frame für jede Seite stellt eine Seiten Website bereit, die die `IPropertyPageSite`-Schnittstelle unterstützt.

##  <a name="ignoreapply"></a>COlePropertyPage:: ignoreapply

Bestimmt, welche Steuerelemente die Schaltfläche anwenden nicht aktivieren.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parameter

*NID*<br/>
ID des Steuer Elements, das ignoriert werden soll.

### <a name="remarks"></a>Hinweise

Die Schaltfläche Apply (anwenden) der Eigenschaften Seite ist nur aktiviert, wenn die Werte von Eigenschaften Seiten-Steuerelementen geändert wurden. Verwenden Sie diese Funktion, um Steuerelemente anzugeben, die nicht bewirken, dass die Schaltfläche anwenden aktiviert wird, wenn sich die Werte ändern.

##  <a name="ismodified"></a>COlePropertyPage:: IsModified

Bestimmt, ob der Benutzer Werte auf der Eigenschaften Seite geändert hat.

```
BOOL IsModified();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Eigenschaften Seite geändert wurde.

##  <a name="oneditproperty"></a>COlePropertyPage:: oneditproperty

Das Framework ruft diese Funktion auf, wenn eine bestimmte Eigenschaft bearbeitet werden soll.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Dispatch-ID der Eigenschaft, die bearbeitet wird.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt false zurück. Über schreibungen dieser Funktion sollten true zurückgeben.

### <a name="remarks"></a>Hinweise

Sie können es überschreiben, um den Fokus auf das entsprechende Steuerelement auf der Seite festzulegen. Die Standard Implementierung führt keine Aktion aus und gibt false zurück.

##  <a name="onhelp"></a>COlePropertyPage:: onhelp

Das Framework ruft diese Funktion auf, wenn der Benutzer die Online Hilfe anfordert.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parameter

*lpszhelpdir*<br/>
Verzeichnis, das die Hilfedatei der Eigenschaften Seite enthält.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt false zurück.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese, wenn die Eigenschaften Seite eine spezielle Aktion ausführen muss, wenn der Benutzer auf die Hilfe zugreift. Die Standard Implementierung führt keine Aktion aus und gibt false zurück, wodurch das Framework angewiesen wird, WinHelp aufzurufen.

##  <a name="oninitdialog"></a>COlePropertyPage:: OnInitDialog

Das Framework ruft diese Funktion auf, wenn das Dialogfeld der Eigenschaften Seite initialisiert wird.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt false zurück.

### <a name="remarks"></a>Hinweise

Überschreiben Sie diese, wenn beim Initialisieren des Dialog Felds eine spezielle Aktion erforderlich ist. Die Standard Implementierung ruft `CDialog::OnInitDialog` auf und gibt false zurück.

##  <a name="onobjectschanged"></a>COlePropertyPage:: onobjectschge

Wird von Framework aufgerufen, wenn ein anderes OLE-Steuerelement mit neuen Eigenschaften ausgewählt wird.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Hinweise

Wenn Sie die Eigenschaften eines OLE-Steuer Elements in der Entwicklerumgebung anzeigen, wird ein nicht modalem Dialogfeld verwendet, um seine Eigenschaften Seiten anzuzeigen. Wenn ein anderes Steuerelement ausgewählt ist, muss für den neuen Eigenschaften Satz ein anderer Satz von Eigenschaften Seiten angezeigt werden. Das Framework ruft diese Funktion auf, um die Eigenschaften Seite der Änderung zu benachrichtigen.

Überschreiben Sie diese Funktion, um eine Benachrichtigung über diese Aktion zu erhalten und spezielle Aktionen auszuführen.

##  <a name="onsetpagesite"></a>COlePropertyPage:: onsetpagesite

Das Framework ruft diese Funktion auf, wenn der Eigenschaften Rahmen die Seiten Website der Eigenschaften Seite bereitstellt.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Hinweise

Die Standard Implementierung lädt die Beschriftung der Seite und versucht, die Seitengröße aus der Dialogfeld Ressource zu bestimmen. Überschreiben Sie diese Funktion, wenn für ihre Eigenschaften Seite Weitere Aktionen erforderlich sind. Ihre außer Kraft Setzung sollte die Basisklassen Implementierung aufzurufen.

##  <a name="setcontrolstatus"></a>COlePropertyPage:: setcontrolstatus

Ändert den Status eines Eigenschaften Seiten-Steuer Elements.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parameter

*NID*<br/>
Enthält die ID eines Eigenschaften Seiten-Steuer Elements.

*bdirty*<br/>
Gibt an, ob ein Feld der Eigenschaften Seite geändert wurde. Auf true festgelegt, wenn das Feld geändert wurde, false, wenn es nicht geändert wurde.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das angegebene Steuerelement festgelegt wurde. andernfalls false.

### <a name="remarks"></a>Hinweise

Wenn der Status eines Eigenschaften Seiten-Steuer Elements geändert wird, wenn die Eigenschaften Seite geschlossen wird oder die Schaltfläche anwenden ausgewählt wird, wird die-Eigenschaft des Steuer Elements mit dem entsprechenden Wert aktualisiert.

##  <a name="setdialogresource"></a>COlePropertyPage:: setdialogresource

Legt die Dialog Ressource der Eigenschaften Seite fest.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parameter

*hdialog*<br/>
Handle für die Dialog Ressource der Eigenschaften Seite.

##  <a name="sethelpinfo"></a>COlePropertyPage:: Setup Info

Gibt QuickInfo-Informationen, den Hilfe Dateinamen und den Hilfe Kontext für ihre Eigenschaften Seite an.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parameter

*lpszdocstring*<br/>
Eine Zeichenfolge, die kurze Hilfe Informationen für die Anzeige in einer Statusleiste oder an einem anderen Speicherort enthält.

*lpszhelpfile*<br/>
Der Name der Hilfedatei der Eigenschaften Seite.

*dwHelpContext*<br/>
Hilfe Kontext für die Eigenschaften Seite.

##  <a name="setmodifiedflag"></a>COlePropertyPage:: SetModifiedFlag

Gibt an, ob der Benutzer die Eigenschaften Seite geändert hat.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bmodified*<br/>
Gibt den neuen Wert für das geänderte Flag der Eigenschaften Seite an.

##  <a name="setpagename"></a>COlePropertyPage:: setpagename

Legt den Namen der Eigenschaften Seite fest, der in der Regel auf der Registerkarte der Seite angezeigt wird.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parameter

*lpszpagename*<br/>
Zeiger auf eine Zeichenfolge, die den Namen der Eigenschaften Seite enthält.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel für "TESTHELP"](../../overview/visual-cpp-samples.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
