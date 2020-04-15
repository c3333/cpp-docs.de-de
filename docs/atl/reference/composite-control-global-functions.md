---
title: Globale Funktionen der Composite Control
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
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331612"
---
# <a name="composite-control-global-functions"></a>Globale Funktionen der Composite Control

Diese Funktionen unterstützen das Erstellen von Dialogfeldern sowie das Erstellen, Hosten und Lizenzieren von ActiveX-Steuerelementen.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Erstellt ein modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage. Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Erstellt ein nicht modales Dialogfeld aus einer vom Benutzer angegebenen Dialogfeldvorlage. Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Erstellt ein ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und ruft einen Schnittstellenzeiger (oder Zeiger) aus dem Steuerelement ab.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und ruft einen Schnittstellenzeiger (oder Zeiger) aus dem Steuerelement ab.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Fügt ein bereits erstelltes Steuerelement an das angegebene Fenster an.|
|[AtlAxGetHost](#atlaxgethost)|Wird verwendet, um einen direkten Schnittstellenzeiger auf den Container für ein angegebenes Fenster (falls vorhanden) zu erhalten, wenn sein Handle angegeben ist.|
|[AtlAxGetControl](#atlaxgetcontrol)|Wird verwendet, um einen direkten Schnittstellenzeiger auf das Steuerelement zu erhalten, das in einem angegebenen Fenster (falls vorhanden) enthalten ist, da sein Handle angegeben ist.|
|[AtlSetChildSite](#atlsetchildsite)|Initialisiert die `IUnknown` untergeordnete Website.|
|[AtlAxWinInit](#atlaxwininit)|Initialisiert den Hostingcode für AxWin-Objekte.|
|[AtlAxWinTerm](#atlaxwinterm)|Der Hostcode für AxWin-Objekte wird nicht initialisiert.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Gibt Informationen über die Standardquellschnittstelle eines Objekts zurück.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>AtlAxDialogBox

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
[in] Identifiziert eine Instanz des Moduls, dessen ausführbare Datei die Dialogfeldvorlage enthält.

*lpTemplateName*<br/>
[in] Identifiziert die Dialogfeldvorlage. Dieser Parameter ist entweder der Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Dialogfeldvorlage angibt, oder ein Ganzzahlwert, der den Ressourcenbezeichner der Dialogfeldvorlage angibt. Wenn der Parameter einen Ressourcenbezeichner angibt, muss sein Wort hoher Ordnung Null sein, und sein Wort niedriger Ordnung muss den Bezeichner enthalten. Sie können das [MakeINTRESOURCE-Makro](/windows/win32/api/winuser/nf-winuser-makeintresourcew) verwenden, um diesen Wert zu erstellen.

*hWndEltern*<br/>
[in] Identifiziert das Fenster, das das Dialogfeld besitzt.

*lpDialogProc*<br/>
[in] Zeigt auf die Dialogfeldprozedur. Weitere Informationen zur Dialogfeldprozedur finden Sie unter [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[in] Gibt den Wert an, der an das Dialogfeld im *LParam-Parameter* der WM_INITDIALOG-Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Um `AtlAxDialogBox` mit einer Dialogfeldvorlage zu verwenden, die ein ActiveX-Steuerelement enthält, geben Sie eine gültige CLSID-, APPID- oder URL-Zeichenfolge als *Textfeld* des **CONTROL-Abschnitts** der Dialogfeldressource sowie "AtlAxWin80" als *Klassennamensfeld* unter demselben Abschnitt an. Im Folgenden wird veranschaulicht, wie ein gültiger **CONTROL-Abschnitt** aussehen könnte:

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Weitere Informationen zum Bearbeiten von Ressourcenskripts finden Sie unter [Gewusst wie: Öffnen einer Ressourcenskriptdatei im Textformat](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Weitere Informationen zu Steuerelementdefinitionsanweisungen finden Sie unter [Allgemeine Steuerelementparameter](/windows/win32/menurc/common-control-parameters) unter Windows SDK: SDK Tools.

Weitere Informationen zu Dialogfeldern im Allgemeinen finden Sie in [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) und [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) im Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAxCreateDialog

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
[in] Identifiziert eine Instanz des Moduls, dessen ausführbare Datei die Dialogfeldvorlage enthält.

*lpTemplateName*<br/>
[in] Identifiziert die Dialogfeldvorlage. Dieser Parameter ist entweder der Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Dialogfeldvorlage angibt, oder ein Ganzzahlwert, der den Ressourcenbezeichner der Dialogfeldvorlage angibt. Wenn der Parameter einen Ressourcenbezeichner angibt, muss sein Wort hoher Ordnung Null sein, und sein Wort niedriger Ordnung muss den Bezeichner enthalten. Sie können das [MakeINTRESOURCE-Makro](/windows/win32/api/winuser/nf-winuser-makeintresourcew) verwenden, um diesen Wert zu erstellen.

*hWndEltern*<br/>
[in] Identifiziert das Fenster, das das Dialogfeld besitzt.

*lpDialogProc*<br/>
[in] Zeigt auf die Dialogfeldprozedur. Weitere Informationen zur Dialogfeldprozedur finden Sie unter [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[in] Gibt den Wert an, der an das Dialogfeld im *LParam-Parameter* der WM_INITDIALOG-Nachricht übergeben werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Das resultierende Dialogfeld kann ActiveX-Steuerelemente enthalten.

Weitere Informationen finden Sie unter [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) und [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) im Windows SDK.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>AtlAxCreateControl

Erstellt ein ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das Steuerelement übergeben werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird.

*hWnd*<br/>
[in] Behandeln Sie das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
[in] Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Diese globale Funktion gibt Ihnen das gleiche Ergebnis wie das Aufrufen von [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, NULL, NULL);.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

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

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das Steuerelement übergeben werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird.

*hWnd*<br/>
[in] Behandeln Sie das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
[in] Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

*ppUnkControl*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der das des erstellten Steuerelements empfängt. Kann den Wert NULL haben.

*iidSink*<br/>
Der Schnittstellenbezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt.

*punkSink*<br/>
Ein Zeiger auf `IUnknown` die Schnittstelle des Senkenobjekts, der mit dem Verbindungspunkt verbunden werden soll, der von *iidSink* für das enthaltene Objekt angegeben wird, nachdem das enthaltene Objekt erfolgreich erstellt wurde.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

`AtlAxCreateControlEx`ist ähnlich wie [AtlAxCreateControl,](#atlaxcreatecontrol) ermöglicht es Ihnen jedoch auch, einen Schnittstellenzeiger auf das neu erstellte Steuerelement zu empfangen und eine Ereignissenke einzurichten, um Ereignisse zu empfangen, die vom Steuerelement ausgelöst werden.

Informationen zum Erstellen eines lizenzierten ActiveX-Steuerelements finden Sie unter [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic

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

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das Steuerelement übergeben werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird.

*hWnd*<br/>
Behandeln Sie das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

*bstrLic*<br/>
Der BSTR, der die Lizenz für das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von ActiveX-Steuerelementen `AtlAxCreateControlLic`mithilfe von ATL AXHost finden Sie unter Hostieren von [ActiveX-Steuerelementen.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

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

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die an das Steuerelement übergeben werden soll. Muss auf eine der folgenden Arten formatiert werden:

- Eine ProgID wie`"MSCAL.Calendar.7"`

- Eine CLSID wie`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Eine URL wie`"<https://www.microsoft.com>"`

- Ein Verweis auf ein aktives Dokument, z. B.`"file://\\\Documents\MyDoc.doc"`

- Ein HTML-Fragment wie`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`muss dem HTML-Fragment vorangestellt werden, damit es als MSHTML-Stream bezeichnet wird.

*hWnd*<br/>
Behandeln Sie das Fenster, an das das Steuerelement angefügt wird.

*pStream*<br/>
Ein Zeiger auf einen Stream, der zum Initialisieren der Eigenschaften des Steuerelements verwendet wird. Kann den Wert NULL haben.

*ppUnkContainer*<br/>
Die Adresse eines Zeigers, `IUnknown` der den Container empfängt. Kann den Wert NULL haben.

*ppUnkControl*<br/>
[out] Die Adresse eines Zeigers, `IUnknown` der das des erstellten Steuerelements empfängt. Kann den Wert NULL haben.

*iidSink*<br/>
Der Schnittstellenbezeichner einer ausgehenden Schnittstelle für das enthaltene Objekt.

*punkSink*<br/>
Ein Zeiger auf `IUnknown` die Schnittstelle des Senkenobjekts, der mit dem Verbindungspunkt verbunden werden soll, der von *iidSink* für das enthaltene Objekt angegeben wird, nachdem das enthaltene Objekt erfolgreich erstellt wurde.

*bstrLic*<br/>
Der BSTR, der die Lizenz für das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

`AtlAxCreateControlLicEx`ist ähnlich wie [AtlAxCreateControlLic,](#atlaxcreatecontrollic) ermöglicht es Ihnen jedoch auch, einen Schnittstellenzeiger auf das neu erstellte Steuerelement zu empfangen und eine Ereignissenke einzurichten, um Ereignisse zu empfangen, die vom Steuerelement ausgelöst werden.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von ActiveX-Steuerelementen `AtlAxCreateControlLicEx`mithilfe von ATL AXHost finden Sie unter Hostieren von [ActiveX-Steuerelementen.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>AtlAxAttachControl

Fügt ein bereits erstelltes Steuerelement an das angegebene Fenster an.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
[in] Ein Zeiger auf `IUnknown` das Steuerelement.

*hWnd*<br/>
[in] Behandeln Sie das Fenster, in dem das Steuerelement hosten wird.

*ppUnkContainer*<br/>
[out] Ein Zeiger auf einen Zeiger `IUnknown` auf das Containerobjekt.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [AtlAxCreateControlEx](#atlaxcreatecontrolex) und [AtlAxCreateControl,](#atlaxcreatecontrol) um gleichzeitig ein Steuerelement zu erstellen und anzufügen.

> [!NOTE]
> Das angehängte Steuerelementobjekt muss vor `AtlAxAttachControl`dem Aufruf korrekt initialisiert werden.

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

Ruft anhand eines bestimmten Fensters einen direkten Schnittstellenzeiger zu dem Container für das Fenster (sofern vorhanden) ab.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parameter

*H*<br/>
[in] Ein Handle für das Fenster, in dem das Steuerelement gehostet wird.

*Pp*<br/>
[out] Der `IUnknown` Container des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

Ruft anhand des Handles eines angegebenen Fensters einen direkten Schnittstellenzeiger zu dem Steuerelement ab, das in dem Fenster enthalten ist.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Parameter

*H*<br/>
[in] Ein Handle für das Fenster, in dem das Steuerelement gehostet wird.

*Pp*<br/>
[out] Die `IUnknown` des zu gehosteten Steuerelements.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSetChildSite

Rufen Sie diese Funktion auf, um `IUnknown` die Site des untergeordneten Objekts auf das des übergeordneten Objekts festzulegen.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Parameter

*punkChild*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des untergeordneten Kindes.

*punkParent*<br/>
[in] Ein Zeiger auf `IUnknown` die Schnittstelle des übergeordneten Elements.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>AtlAxWinInit

Diese Funktion initialisiert den ATL-Steuerhostingcode, indem die Fensterklassen **"AtlAxWin80"** und **"AtlAxWinLic80"** sowie einige benutzerdefinierte Fensternachrichten registriert werden.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung des Steuerelementhostingcodes erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Funktion muss aufgerufen werden, bevor die ATL-Steuerelementhosting-API verwendet wird. Nach einem Aufruf dieser Funktion kann die Fensterklasse **"AtlAxWin"** in Aufrufen von [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) oder [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)verwendet werden, wie im Windows SDK beschrieben.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinTerm

Diese Funktion entinitialisiert den AtL-Steuerhostingcode, indem die Registrierung der Fensterklassen **"AtlAxWin80"** und **"AtlAxWinLic80"** aufheben wird.

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft einfach [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) auf, wie im Windows SDK beschrieben.

Rufen Sie diese Funktion auf, um zu bereinigen, nachdem alle vorhandenen Hostfenster zerstört wurden, wenn Sie [AtlAxWinInit](#atlaxwininit) aufgerufen haben und Keine Hostfenster mehr erstellen müssen. Wenn Sie diese Funktion nicht aufrufen, wird die Registrierung der Fensterklasse automatisch aufgehoben, wenn der Prozess beendet wird.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

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

*punkObj*<br/>
[in] Ein Zeiger auf das Objekt, für das Informationen zurückgegeben werden sollen.

*plibid*<br/>
[out] Ein Zeiger auf die LIBID der Typbibliothek, die die Definition der Quellschnittstelle enthält.

*piid*<br/>
[out] Ein Zeiger auf die Schnittstellen-ID der Standardquellschnittstelle des Objekts.

*pdwMajor*<br/>
[out] Ein Zeiger auf die Hauptversionsnummer der Typbibliothek, die die Definition der Quellschnittstelle enthält.

*pdwMinor*<br/>
[out] Ein Zeiger auf die Nebenversionsnummer der Typbibliothek, die die Definition der Quellschnittstelle enthält.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

`AtlGetObjectSourceInterface`kann Ihnen die Schnittstellen-ID der Standard-Quellschnittstelle sowie die LIBID- und Haupt- und Nebenversionsnummern der Typbibliothek bereitstellen, die diese Schnittstelle beschreibt.

> [!NOTE]
> Damit diese Funktion die angeforderten Informationen erfolgreich abrufen kann, `IDispatch` muss das von `IDispatch::GetTypeInfo` *punkObj* dargestellte Objekt (und geben Typinformationen durch ) implementiert werden und auch entweder `IProvideClassInfo2` oder `IPersist`implementieren. Die Typinformationen für die Quellschnittstelle müssen sich in derselben `IDispatch`Typbibliothek wie die Typinformationen für befinden.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie `CEasySink`eine Ereignissenkenklasse definieren können, die `IDispEventImpl` die Anzahl der Vorlagenargumente reduziert, an die Sie an die nackten Wesentlichen übergeben können. `EasyAdvise`und `EasyUnadvise` `AtlGetObjectSourceInterface` verwenden Sie, um die [IDispEventImpl-Mitglieder](../../atl/reference/idispeventimpl-class.md) zu initialisieren, bevor Sie [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) oder [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)aufrufen.

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)<br/>
[Zusammengesetzte Steuerungsmakros](../../atl/reference/composite-control-macros.md)
