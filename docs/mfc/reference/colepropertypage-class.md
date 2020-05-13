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
ms.openlocfilehash: 872ade08438e54098da730012f98cdd906483887
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753791"
---
# <a name="colepropertypage-class"></a>COlePropertyPage-Klasse

Wird verwendet, um die Eigenschaften eines benutzerdefinierten Steuerelements in einer grafischen Oberfläche anzuzeigen, ähnlich wie in einem Dialogfeld.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Erstellt ein `COlePropertyPage`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Gibt an, ob der Benutzer den Wert im Steuerelement geändert hat.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Gibt das Array von Objekten zurück, die von der Eigenschaftenseite bearbeitet werden.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Gibt einen Zeiger auf die `IPropertyPageSite` Benutzeroberfläche der Eigenschaftenseite zurück.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Legt fest, welche Steuerelemente die Schaltfläche Anwenden nicht aktivieren.|
|[COlePropertyPage::IsModified](#ismodified)|Gibt an, ob der Benutzer die Eigenschaftenseite geändert hat.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Wird vom Framework aufgerufen, wenn der Benutzer eine Eigenschaft edt.|
|[COlePropertyPage::OnHelp](#onhelp)|Wird vom Framework aufgerufen, wenn der Benutzer Hilfe aufruft.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Wird vom Framework aufgerufen, wenn die Eigenschaftenseite initialisiert wird.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Wird vom Framework aufgerufen, wenn ein anderes OLE-Steuerelement mit neuen Eigenschaften ausgewählt wird.|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Wird vom Framework aufgerufen, wenn der Eigenschaftenrahmen die Website der Seite bereitstellt.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Legt ein Flag fest, das angibt, ob der Benutzer den Wert im Steuerelement geändert hat.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Legt die Dialogressource der Eigenschaftenseite fest.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Legt den kurzen Hilfetext der Eigenschaftenseite, den Namen der Hilfedatei und den Hilfekontext fest.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Legt ein Flag fest, das angibt, ob der Benutzer die Eigenschaftenseite geändert hat.|
|[COlePropertyPage::SetPageName](#setpagename)|Legt den Namen der Eigenschaftenseite (Beschriftung) fest.|

## <a name="remarks"></a>Bemerkungen

Eine Eigenschaftenseite kann z. B. ein Bearbeitungssteuerelement enthalten, mit dem der Benutzer die Beschriftungseigenschaft des Steuerelements anzeigen und ändern kann.

Jede benutzerdefinierte Eigenschaft oder Bestandssteuerungseigenschaft kann über ein Dialogfeldsteuerelement verfügen, das es dem Benutzer des Steuerelements ermöglicht, den aktuellen Eigenschaftswert anzuzeigen und diesen Wert bei Bedarf zu ändern.

Weitere Informationen zur `COlePropertyPage`Verwendung finden Sie im Artikel [ActiveX-Steuerelemente: Eigenschaftenseiten](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage

Erstellt ein `COlePropertyPage`-Objekt.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parameter

*idDlg*<br/>
Ressourcen-ID der Dialogfeldvorlage.

*idCaption*<br/>
Ressourcen-ID der Beschriftung der Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Wenn Sie eine Unterklasse von `COlePropertyPage`implementieren, sollte der `COlePropertyPage` Konstruktor der Unterklasse den Konstruktor verwenden, um die Dialogvorlagenressource zu identifizieren, auf der die Eigenschaftenseite basiert, und die Zeichenfolgenressource, die ihre Beschriftung enthält.

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus

Bestimmt, ob der Benutzer den Wert des Eigenschaftenseitensteuerelements mit der angegebenen Ressourcen-ID geändert hat.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Ressourcen-ID eines Eigenschaftenseitensteuerelements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Steuerelementwert geändert wurde; andernfalls FALSE.

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COlePropertyPage::GetObjectArray

Gibt das Array von Objekten zurück, die von der Eigenschaftenseite bearbeitet werden.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parameter

*pnObjekte*<br/>
Zeigen Sie auf eine nicht signierte lange ganze Zahl, die die Anzahl der Objekte empfängt, die von der Seite bearbeitet werden.

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein `IDispatch` Array von Zeigern, die verwendet werden, um auf die Eigenschaften jedes Steuerelements auf der Eigenschaftenseite zuzugreifen. Der Aufrufer darf diese Schnittstellenzeiger nicht freigeben.

### <a name="remarks"></a>Bemerkungen

Jedes Eigenschaftenseitenobjekt verwaltet ein Array von `IDispatch` Zeigern auf die Schnittstellen der Objekte, die von der Seite bearbeitet werden. Diese Funktion legt das *PnObjects-Argument* auf die Anzahl der Elemente in diesem Array fest und gibt einen Zeiger auf das erste Element des Arrays zurück.

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COlePropertyPage::GetPageSite

Ruft einen Zeiger auf die `IPropertyPageSite` Benutzeroberfläche der Eigenschaftenseite ab.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die `IPropertyPageSite` Benutzeroberfläche der Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

Steuerelemente und Container arbeiten zusammen, sodass Benutzer Steuerelementeigenschaften durchsuchen und bearbeiten können. Das Steuerelement stellt Eigenschaftenseiten bereit, von denen jede ein OLE-Objekt ist, mit dem der Benutzer einen verknüpften Satz von Eigenschaften bearbeiten kann. Der Container stellt einen Eigenschaftenrahmen bereit, der die Eigenschaftenseiten anzeigt. Für jede Seite stellt der Eigenschaftenrahmen eine `IPropertyPageSite` Seitenwebsite bereit, die die Schnittstelle unterstützt.

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COlePropertyPage::IgnoreApply

Legt fest, welche Steuerelemente die Schaltfläche Anwenden nicht aktivieren.

```cpp
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
ID des zu ignorierenden Steuerelements.

### <a name="remarks"></a>Bemerkungen

Die Schaltfläche Anwenden der Eigenschaftenseite ist nur aktiviert, wenn die Werte der Eigenschaftenseitensteuerelemente geändert wurden. Verwenden Sie diese Funktion, um Steuerelemente anzugeben, die nicht dazu führen, dass die Schaltfläche Anwenden aktiviert wird, wenn sich ihre Werte ändern.

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COlePropertyPage::IsModified

Bestimmt, ob der Benutzer Werte auf der Eigenschaftenseite geändert hat.

```
BOOL IsModified();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Eigenschaftenseite geändert wurde.

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty

Das Framework ruft diese Funktion auf, wenn eine bestimmte Eigenschaft bearbeitet werden soll.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Dispatch-ID der zu bearbeitenden Eigenschaft.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt FALSE zurück. Überschreibungen dieser Funktion sollten TRUE zurückgeben.

### <a name="remarks"></a>Bemerkungen

Sie können sie überschreiben, um den Fokus auf das entsprechende Steuerelement auf der Seite festzulegen. Die Standardimplementierung bewirkt nichts und gibt FALSE zurück.

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COlePropertyPage::OnHelp

Das Framework ruft diese Funktion auf, wenn der Benutzer Onlinehilfe anfordert.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parameter

*lpszHelpDir*<br/>
Verzeichnis, das die Hilfedatei der Eigenschaftenseite enthält.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie es, wenn Ihre Eigenschaftenseite eine spezielle Aktion ausführen muss, wenn der Benutzer auf die Hilfe zugreift. Die Standardimplementierung führt nichts aus und gibt FALSE zurück, das das Framework anweist, WinHelp aufzurufen.

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COlePropertyPage::OnInitDialog

Das Framework ruft diese Funktion auf, wenn das Dialogfeld der Eigenschaftenseite initialisiert wird.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt FALSE zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie es, wenn eine spezielle Aktion erforderlich ist, wenn das Dialogfeld initialisiert wird. Die Standardimplementierung `CDialog::OnInitDialog` ruft FALSE auf und gibt sie zurück.

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged

Wird vom Framework aufgerufen, wenn ein anderes OLE-Steuerelement mit neuen Eigenschaften ausgewählt wird.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Bemerkungen

Beim Anzeigen der Eigenschaften eines OLE-Steuerelements in der Entwicklerumgebung wird ein modusloses Dialogfeld verwendet, um seine Eigenschaftenseiten anzuzeigen. Wenn ein anderes Steuerelement ausgewählt ist, muss für den neuen Satz von Eigenschaften ein anderer Satz von Eigenschaftenseiten angezeigt werden. Das Framework ruft diese Funktion auf, um die Eigenschaftenseite der Änderung zu benachrichtigen.

Überschreiben Sie diese Funktion, um eine Benachrichtigung über diese Aktion zu erhalten und spezielle Aktionen auszuführen.

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COlePropertyPage::OnSetPageSite

Das Framework ruft diese Funktion auf, wenn der Eigenschaftenframe die Seitenwebsite der Eigenschaftenseite bereitstellt.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung lädt die Beschriftung der Seite und versucht, die Größe der Seite aus der Dialogressource zu bestimmen. Überschreiben Sie diese Funktion, wenn Ihre Eigenschaftenseite weitere Aktionen erfordert. Ihre Außerkraftsetzung sollte die Basisklassenimplementierung aufrufen.

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus

Ändert den Status eines Eigenschaftenseitensteuerelements.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Enthält die ID eines Eigenschaftenseitensteuerelements.

*bDirty*<br/>
Gibt an, ob ein Feld der Eigenschaftenseite geändert wurde. Wird auf TRUE gesetzt, wenn das Feld geändert wurde, FALSE, wenn es nicht geändert wurde.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das angegebene Steuerelement festgelegt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn der Status eines Eigenschaftenseitensteuerelements verschmutzt ist, wenn die Eigenschaftenseite geschlossen wird oder die Schaltfläche Anwenden ausgewählt wird, wird die Eigenschaft des Steuerelements mit dem entsprechenden Wert aktualisiert.

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COlePropertyPage::SetDialogResource

Legt die Dialogressource der Eigenschaftenseite fest.

```cpp
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parameter

*hDialog*<br/>
Behandeln Sie die Dialogressource der Eigenschaftenseite.

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo

Gibt Tooltip-Informationen, den Hilfedateinamen und den Hilfekontext für Ihre Eigenschaftenseite an.

```cpp
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parameter

*lpszDocString*<br/>
Eine Zeichenfolge, die kurze Hilfeinformationen für die Anzeige in einer Statusleiste oder an einem anderen Speicherort enthält.

*lpszHelpFile*<br/>
Name der Hilfedatei der Eigenschaftenseite.

*dwHelpContext*<br/>
Hilfekontext für die Eigenschaftenseite.

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag

Gibt an, ob der Benutzer die Eigenschaftenseite geändert hat.

```cpp
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parameter

*bModified*<br/>
Gibt den neuen Wert für das geänderte Flag der Eigenschaftenseite an.

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COlePropertyPage::SetPageName

Legt den Namen der Eigenschaftenseite fest, der normalerweise auf der Registerkarte der Seite angezeigt wird.

```cpp
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parameter

*lpszPageName*<br/>
Zeiger auf eine Zeichenfolge, die den Namen der Eigenschaftenseite enthält.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
