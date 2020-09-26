---
title: Globale Funktionen des zusammengesetzten Steuer Elements
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: fe9d9a3a0538e2e5744987adcd64e67562711ea8
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353115"
---
# <a name="composite-control-global-functions"></a>Globale Funktionen des zusammengesetzten Steuer Elements

Diese Funktionen bieten Unterstützung für das Erstellen von Dialogfeldern und zum Erstellen, hosten und lizenzieren von ActiveX-Steuerelementen.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Funktion|BESCHREIBUNG|
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Erstellt ein modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage. Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Erstellt ein nicht modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage. Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Erstellt ein ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem Steuerelement ab.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem Steuerelement ab.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Fügt ein bereits erstelltes Steuerelement an das angegebene Fenster an.|
|[AtlAxGetHost](#atlaxgethost)|Wird verwendet, um einen direkten Schnittstellen Zeiger auf den Container für ein angegebenes Fenster (sofern vorhanden) zu erhalten, wenn sein handle angegeben ist.|
|[AtlAxGetControl](#atlaxgetcontrol)|Wird verwendet, um einen direkten Schnittstellen Zeiger auf das Steuerelement zu erhalten, das in einem angegebenen Fenster (sofern vorhanden) enthalten ist, wenn sein handle angegeben ist.|
|[AtlSetChildSite](#atlsetchildsite)|Initialisiert den `IUnknown` des untergeordneten Standorts.|
|[AtlAxWinInit](#atlaxwininit)|Initialisiert den Hostcode für axwin-Objekte.|
|[AtlAxWinTerm](#atlaxwinterm)|Hebt die Initialisierung des Hostcodes für axwin-Objekte auf.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Gibt Informationen über die standardmäßige Quell Schnittstelle eines Objekts zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlhost. h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a> AtlAxDialogBox

Erstellt ein modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage.

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
in Identifiziert eine Instanz des Moduls, dessen ausführbare Datei die Dialogfeld Vorlage enthält.

*lptemplatename*<br/>
in Bezeichnet die Dialogfeld Vorlage. Dieser Parameter ist entweder der Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen der Dialogfeld Vorlage oder einen ganzzahligen Wert angibt, der den Ressourcen Bezeichner der Dialogfeld Vorlage angibt. Wenn der-Parameter einen Ressourcen Bezeichner angibt, muss das hochwertige Wort NULL sein, und das nieder wertige Wort muss den Bezeichner enthalten. Sie können das [makeintresource](/windows/win32/api/winuser/nf-winuser-makeintresourcew) -Makro verwenden, um diesen Wert zu erstellen.

*hwndParent*<br/>
in Identifiziert das Fenster, das das Dialogfeld besitzt.

*lpdialogproc*<br/>
in Verweist auf die Dialogfeld Prozedur. Weitere Informationen zur Dialogfeld Prozedur finden Sie unter [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwinitparam*<br/>
in Gibt den Wert an, der dem Dialogfeld im *LPARAM* -Parameter der WM_INITDIALOG Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

Wenn Sie `AtlAxDialogBox` mit einer Dialogfeld Vorlage verwenden möchten, die ein ActiveX-Steuerelement enthält, geben Sie eine gültige CLSID, eine AppID oder eine URL-Zeichenfolge als *Textfeld* des **Steuer** Element Abschnitts der Dialogfeld Ressource an, zusammen mit "AtlAxWin80" als *Klassennamen* Feld unterhalb desselben Abschnitts. Das folgende Beispiel zeigt, wie ein gültiger **Steuer** Element Abschnitt aussehen könnte:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Weitere Informationen zum Bearbeiten von Ressourcen Skripts finden [Sie unter Gewusst wie: Erstellen von Ressourcen](../../windows/how-to-create-a-resource-script-file.md). Weitere Informationen zum Steuern von Ressourcen Definitions Anweisungen finden Sie unter [allgemeine Steuerelement Parameter](/windows/win32/menurc/common-control-parameters) unter Windows SDK: SDK Tools.

Weitere Informationen zu Dialogfeldern im Allgemeinen finden Sie unter [Dialogbox](/windows/win32/api/winuser/nf-winuser-dialogboxw) [und in](/windows/win32/api/winuser/nf-winuser-createdialogparamw) der Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a> Atlaxkreatedialog

Erstellt ein nicht modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage.

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
in Identifiziert eine Instanz des Moduls, dessen ausführbare Datei die Dialogfeld Vorlage enthält.

*lptemplatename*<br/>
in Bezeichnet die Dialogfeld Vorlage. Dieser Parameter ist entweder der Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen der Dialogfeld Vorlage oder einen ganzzahligen Wert angibt, der den Ressourcen Bezeichner der Dialogfeld Vorlage angibt. Wenn der-Parameter einen Ressourcen Bezeichner angibt, muss das hochwertige Wort NULL sein, und das nieder wertige Wort muss den Bezeichner enthalten. Sie können das [makeintresource](/windows/win32/api/winuser/nf-winuser-makeintresourcew) -Makro verwenden, um diesen Wert zu erstellen.

*hwndParent*<br/>
in Identifiziert das Fenster, das das Dialogfeld besitzt.

*lpdialogproc*<br/>
in Verweist auf die Dialogfeld Prozedur. Weitere Informationen zur Dialogfeld Prozedur finden Sie unter [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwinitparam*<br/>
in Gibt den Wert an, der dem Dialogfeld im *LPARAM* -Parameter der WM_INITDIALOG Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.

Weitere Informationen finden Sie unter " [kreatedialog](/windows/win32/api/winuser/nf-winuser-createdialogw) " und " [kreatedialogparam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) " im Windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a> Atlaxkreatecontrol

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das-Steuerelement übermittelt werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist.

*hWnd*<br/>
in Handle für das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

Diese globale Funktion gibt Ihnen dasselbe Ergebnis wie das Aufrufen von [atlaxcreatecontrolex](#atlaxcreatecontrolex)(*lpszname*, *HWND*, *pStream*, NULL, NULL, NULL, null);.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [atlaxkreatecontrollic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a> Atlaxkreatecontrolex

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster. Weiterhin können ein Schnittstellenzeiger und eine Ereignissenke für das neue Steuerelement erstellt werden.

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das-Steuerelement übermittelt werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist.

*hWnd*<br/>
in Handle für das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
in Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

*ppunkcontrol*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des erstellten Steuer Elements empfängt. Kann den Wert NULL haben.

*iidsink*<br/>
Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt.

*punksink*<br/>
Ein Zeiger auf die- `IUnknown` Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt verbunden werden soll, der durch *iidsink* für das enthaltene-Objekt angegeben wird, nachdem das enthaltene-Objekt erfolgreich erstellt wurde.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

`AtlAxCreateControlEx` ähnelt [atlaxkreatecontrol](#atlaxcreatecontrol) , ermöglicht Ihnen aber auch das Empfangen eines Schnittstellen Zeigers auf das neu erstellte Steuerelement und das Einrichten einer Ereignis Senke für den Empfang von Ereignissen, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuer Elements finden Sie unter [atlaxkreatecontrollicex](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a> Atlaxkreatecontrollic

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das-Steuerelement übermittelt werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist.

*hWnd*<br/>
Handle für das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

*bstrinlisch*<br/>
Der BSTR, der die Lizenz für das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLic` .

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a> Atlaxkreatecontrollicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster. Weiterhin können ein Schnittstellenzeiger und eine Ereignissenke für das neue Steuerelement erstellt werden.

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Parameter

*lpszname*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das-Steuerelement übermittelt werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID, z. b. `"MSCAL.Calendar.7"`

- Eine CLSID, z. b. `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie `"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. b. `"file://\\\Documents\MyDoc.doc"`

- Ein Fragment von HTML, z. b. `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` muss dem HTML-Fragment vorangestellt sein, damit es als MSHTML-Stream festgelegt ist.

*hWnd*<br/>
Handle für das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
Ein Zeiger auf einen Stream, der verwendet wird, um die Eigenschaften des Steuer Elements zu initialisieren. Kann den Wert NULL haben.

*ppunkcontainer*<br/>
Die Adresse eines Zeigers, der den `IUnknown` des Containers empfängt. Kann den Wert NULL haben.

*ppunkcontrol*<br/>
vorgenommen Die Adresse eines Zeigers, der den `IUnknown` des erstellten Steuer Elements empfängt. Kann den Wert NULL haben.

*iidsink*<br/>
Der Schnittstellen Bezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt.

*punksink*<br/>
Ein Zeiger auf die- `IUnknown` Schnittstelle des Sink-Objekts, das mit dem Verbindungspunkt verbunden werden soll, der durch *iidsink* für das enthaltene-Objekt angegeben wird, nachdem das enthaltene-Objekt erfolgreich erstellt wurde.

*bstrinlisch*<br/>
Der BSTR, der die Lizenz für das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

`AtlAxCreateControlLicEx` ähnelt [atlaxkreatecontrollic](#atlaxcreatecontrollic) , ermöglicht Ihnen aber auch das Empfangen eines Schnittstellen Zeigers auf das neu erstellte Steuerelement und das Einrichten einer Ereignis Senke für den Empfang von Ereignissen, die vom Steuerelement ausgelöst werden.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLicEx` .

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a> Atlaxattachcontrol

Fügt ein bereits erstelltes Steuerelement an das angegebene Fenster an.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
in Ein Zeiger auf den `IUnknown` des Steuer Elements.

*hWnd*<br/>
in Handle für das Fenster, in dem das-Steuerelement gehostet wird.

*ppunkcontainer*<br/>
vorgenommen Ein Zeiger auf einen Zeiger auf den `IUnknown` des Container Objekts.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Hinweise

Verwenden Sie [atlaxkreatecontrolex](#atlaxcreatecontrolex) und [atlaxkreatecontrol](#atlaxcreatecontrol) , um ein Steuerelement gleichzeitig zu erstellen und anzufügen.

> [!NOTE]
> Das anzufügende Steuerelement Objekt muss vor dem Aufrufen von ordnungsgemäß initialisiert werden `AtlAxAttachControl` .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a> AtlAxGetHost

Ruft anhand eines bestimmten Fensters einen direkten Schnittstellenzeiger zu dem Container für das Fenster (sofern vorhanden) ab.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parameter

*h*<br/>
in Ein Handle für das Fenster, in dem das-Steuerelement gehostet wird.

*Trupp*<br/>
vorgenommen Der `IUnknown` des Containers des-Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a> Atlaxgetcontrol

Ruft anhand des Handles eines angegebenen Fensters einen direkten Schnittstellenzeiger zu dem Steuerelement ab, das in dem Fenster enthalten ist.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parameter

*h*<br/>
in Ein Handle für das Fenster, in dem das-Steuerelement gehostet wird.

*Trupp*<br/>
vorgenommen Der `IUnknown` des gehosteten Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a> Atlsetchildsite

Diese Funktion wird aufgerufen, um die Site des untergeordneten Objekts auf die `IUnknown` des übergeordneten Objekts festzulegen.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parameter

*punkchild*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des untergeordneten-Elements.

*punkparent*<br/>
in Ein Zeiger auf die- `IUnknown` Schnittstelle des übergeordneten Elements.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a> AtlAxWinInit

Diese Funktion initialisiert den ATL-Steuerelement-Hostingcode durch die Registrierung der Fenster Klassen **"AtlAxWin80"** und **"AtlAxWinLic80"** sowie von einigen benutzerdefinierten Fenster Meldungen.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Initialisierung des Steuer Elements, das den Code Hostingcode andernfalls false.

### <a name="remarks"></a>Hinweise

Diese Funktion muss vor der Verwendung der ATL-Steuerelement-Hosting-API aufgerufen werden. Nach einem Aufruf dieser Funktion kann die **"AtlAxWin"** -Fenster Klasse in Aufrufen von " [kreatewindow](/windows/win32/api/winuser/nf-winuser-createwindoww) " oder " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw)" verwendet werden, wie im Windows SDK beschrieben.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a> AtlAxWinInit

Diese Funktion initialisiert den ATL-Steuerelement-Hostingcode, indem die Registrierung der Fenster Klassen **"AtlAxWin80"** und **"AtlAxWinLic80"** aufgehoben wird.

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer true zurück.

### <a name="remarks"></a>Hinweise

Diese Funktion ruft einfach [unregisterclass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) auf, wie im Windows SDK beschrieben.

Rufen Sie diese Funktion auf, um eine Bereinigung durchführen, nachdem alle vorhandenen Host Fenster zerstört wurden, wenn Sie [AtlAxWinInit](#atlaxwininit) aufgerufen haben und Sie keine Host Fenster mehr erstellen müssen. Wenn Sie diese Funktion nicht aufzurufen, wird die Registrierung der Fenster Klasse automatisch aufgehoben, wenn der Prozess beendet wird.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a> Atlgetobjectsourceingeterface

Mit dieser Funktion werden Informationen über die Standardquellschnittstelle eines Objekts abgerufen.

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>Parameter

*punkobj*<br/>
in Ein Zeiger auf das-Objekt, für das Informationen zurückgegeben werden sollen.

*plizierung*<br/>
vorgenommen Ein Zeiger auf die LIBID der Typbibliothek, die die Definition der Quell Schnittstelle enthält.

*piid*<br/>
vorgenommen Ein Zeiger auf die-Schnittstellen-ID der standardmäßigen Quell Schnittstelle des Objekts.

*pdwmajor*<br/>
vorgenommen Ein Zeiger auf die Hauptversionsnummer der Typbibliothek, die die Definition der Quell Schnittstelle enthält.

*pdwminor*<br/>
vorgenommen Ein Zeiger auf die neben Versionsnummer der Typbibliothek, die die Definition der Quell Schnittstelle enthält.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

`AtlGetObjectSourceInterface` kann die Schnittstellen-ID der standardmäßigen Quell Schnittstelle zusammen mit der LIBID-und der Haupt-und neben Versionsnummer der Typbibliothek bereitstellen, die diese Schnittstelle beschreibt.

> [!NOTE]
> Damit diese Funktion die angeforderten Informationen erfolgreich abrufen kann, muss das Objekt, das von *punkobj* dargestellt wird, implementieren `IDispatch` (und Typinformationen über `IDispatch::GetTypeInfo` ). Darüber hinaus muss entweder oder implementiert werden `IProvideClassInfo2` `IPersist` . Die Typinformationen für die Quell Schnittstelle müssen sich in derselben Typbibliothek wie die Typinformationen für befinden `IDispatch` .

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine Ereignis Senke-Klasse definieren können, die `CEasySink` die Anzahl von Vorlagen Argumenten verringert, die Sie an `IDispEventImpl` die Bare Essentials-Datei übergeben können. `EasyAdvise` und `EasyUnadvise` verwenden `AtlGetObjectSourceInterface` Sie, um die [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) -Member vor dem Aufruf von [dispeventempfehlung](idispeventsimpleimpl-class.md#dispeventadvise) oder [dispeventunrat](idispeventsimpleimpl-class.md#dispeventunadvise)zu initialisieren.

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)<br/>
[Zusammengesetzte Steuerelement Makros](../../atl/reference/composite-control-macros.md)
