---
title: CCommandLineInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369462"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo-Klasse

Unterstützt die Analyse der Befehlszeile beim Anwendungsstart.

## <a name="syntax"></a>Syntax

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Erstellt ein `CCommandLineInfo` Standardobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Überschreiben Sie diesen Rückruf, um einzelne Parameter zu analysieren.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Gibt an, `/Automation` dass die Befehlszeilenoption gefunden wurde.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Gibt an, `/Embedding` dass die Befehlszeilenoption gefunden wurde.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Gibt an, ob ein Begrüßungsbildschirm angezeigt werden soll.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Gibt den zu verarbeitenden Shellbefehl an.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Gibt den Treibernamen an, wenn der Shellbefehl Drucken an ist. ansonsten leer.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Gibt den Dateinamen an, der geöffnet oder gedruckt werden soll. leer, wenn der Shell-Befehl New oder DDE ist.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Gibt den Portnamen an, wenn der Shellbefehl Drucken an ist. ansonsten leer.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Gibt den Druckernamen an, wenn der Shell-Befehl Drucken an lautet. ansonsten leer.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Gibt den eindeutigen Neustartbezeichner für den Neustart-Manager an, wenn der Neustart-Manager die Anwendung neu gestartet hat.|

## <a name="remarks"></a>Bemerkungen

Eine MFC-Anwendung erstellt in der Regel eine lokale Instanz dieser Klasse in der [InitInstance-Funktion](../../mfc/reference/cwinapp-class.md#initinstance) ihres Anwendungsobjekts. Dieses Objekt wird dann an [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)übergeben, das [ParseParam](#parseparam) wiederholt aufruft, um das `CCommandLineInfo` Objekt zu füllen. Das `CCommandLineInfo` Objekt wird dann an [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) übergeben, um die Befehlszeilenargumente und Flags zu behandeln.

Mit diesem Objekt können Sie die folgenden Befehlszeilenoptionen und -parameter kapseln:

|Befehlszeilenargument|Befehl ausgeführt|
|----------------------------|----------------------|
|*app*|Neue Datei.|
|*App-Dateiname*|Öffnen Sie die Datei.|
|*App-Dateiname* `/p`|Drucken Sie die Datei auf den Standarddrucker.|
|*app* App-Dateinamen-Druckertreiber-Port `/pt`|Drucken der Datei auf den angegebenen Drucker.|
|*app* `/dde`|Starten Sie den Befehl DDE, und warten Sie auf den Befehl DDE.|
|*app* `/Automation`|Starten Sie als OLE-Automatisierungsserver.|
|*app* `/Embedding`|Starten Sie, um ein eingebettetes OLE-Element zu bearbeiten.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informiert die Anwendung, um Registrierungsaufgaben auszuführen.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informiert die Anwendung, um alle Nichtregistrierungsaufgaben auszuführen.|

Leiten Sie eine `CCommandLineInfo` neue Klasse ab, um andere Flags und Parameterwerte zu behandeln. Überschreiben Sie [ParseParam,](#parseparam) um die neuen Flags zu verarbeiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo

Dieser Konstruktor `CCommandLineInfo` erstellt ein Objekt mit Standardwerten.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig wird der Begrüßungsbildschirm `m_bShowSplash=TRUE`( ) angezeigt und der Befehl `m_nShellCommand`Neu im Menü Datei ( **=NewFile**) ausgeführt.

Das Anwendungsframework ruft [ParseParam](#parseparam) auf, um Datenmember dieses Objekts zu füllen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated

Gibt an, dass das `/Automation` Flag in der Befehlszeile gefunden wurde.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, bedeutet dies, dass sie als OLE-Automatisierungsserver gestartet werden.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded

Gibt an, dass das `/Embedding` Flag in der Befehlszeile gefunden wurde.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, bedeutet dies, dass ein eingebettetes OLE-Element bearbeitet werden kann.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash

Gibt an, dass der Begrüßungsbildschirm angezeigt werden soll.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, bedeutet dies, dass der Begrüßungsbildschirm für diese Anwendung während des Startvorgangs angezeigt werden sollte. Die Standardimplementierung von [ParseParam](#parseparam) legt diesen [m_nShellCommand](#m_nshellcommand) Datenmember `CCommandLineInfo::FileNew`auf TRUE fest, wenn m_nShellCommand gleich ist.

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand

Gibt den Shellbefehl für diese Instanz der Anwendung an.

```
m_nShellCommand;
```

### <a name="remarks"></a>Bemerkungen

Der Typ für diesen Datenmember ist der folgende aufgezählte `CCommandLineInfo` Typ, der in der Klasse definiert ist.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

Eine kurze Beschreibung dieser Werte finden Sie in der folgenden Liste.

- `CCommandLineInfo::FileNew`Gibt an, dass in der Befehlszeile kein Dateiname gefunden wurde.

- `CCommandLineInfo::FileOpen`Gibt an, dass ein Dateiname in der Befehlszeile gefunden wurde und `/p` `/pt`dass `/dde`keines der folgenden Flags in der Befehlszeile gefunden wurde: , , .

- `CCommandLineInfo::FilePrint`Gibt an, dass das `/p` Flag in der Befehlszeile gefunden wurde.

- `CCommandLineInfo::FilePrintTo`Gibt an, dass das `/pt` Flag in der Befehlszeile gefunden wurde.

- `CCommandLineInfo::FileDDE`Gibt an, dass das `/dde` Flag in der Befehlszeile gefunden wurde.

- `CCommandLineInfo::AppRegister`Gibt an, dass das `/Register` oder `/Regserver` Flag in der Befehlszeile gefunden wurde und die Anwendung aufgefordert wurde, sich zu registrieren.

- `CCommandLineInfo::AppUnregister`Gibt an, dass die `/Unregister` oder `/Unregserver` die Anwendung aufgefordert wurde, die Registrierung zu unterheben.

- `CCommandLineInfo::RestartByRestartManager`Gibt an, dass die Anwendung vom Neustart-Manager neu gestartet wurde.

- `CCommandLineInfo::FileNothing`Deaktiviert beim Start die Anzeige eines neuen untergeordneten MDI-Fensters. Vom Anwendungs-Assistenten generierte MDI-Anwendungen zeigen beim Start ein neues untergeordnetes Fenster an. Um diese Funktion zu deaktivieren, `CCommandLineInfo::FileNothing` kann eine Anwendung beim Aufrufen von [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)als Shell-Befehl verwendet werden. `ProcessShellCommand`wird von `InitInstance( )` der `CWinApp` aller abgeleiteten Klassen aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName

Speichert den Wert des dritten Nicht-Flag-Parameters in der Befehlszeile.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Bemerkungen

Dieser Parameter ist in der Regel der Name des Druckertreibers für einen Befehl "An drucken". Die Standardimplementierung von [ParseParam](#parseparam) legt diesen `/pt` Datenmember nur fest, wenn das Flag in der Befehlszeile gefunden wurde.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLineInfo::m_strFileName

Speichert den Wert des ersten Nicht-Flag-Parameters in der Befehlszeile.

```
CString m_strFileName;
```

### <a name="remarks"></a>Bemerkungen

Dieser Parameter ist in der Regel der Name der zu öffnenden Datei.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLineInfo::m_strPortName

Speichert den Wert des vierten Nicht-Flag-Parameters in der Befehlszeile.

```
CString m_strPortName;
```

### <a name="remarks"></a>Bemerkungen

Dieser Parameter ist in der Regel der Name des Druckeranschlusses für einen Befehl "An drucken". Die Standardimplementierung von [ParseParam](#parseparam) legt diesen `/pt` Datenmember nur fest, wenn das Flag in der Befehlszeile gefunden wurde.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName

Speichert den Wert des zweiten Nicht-Flag-Parameters in der Befehlszeile.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Bemerkungen

Dieser Parameter ist in der Regel der Name des Druckers für einen Befehl "An drucken". Die Standardimplementierung von [ParseParam](#parseparam) legt diesen `/pt` Datenmember nur fest, wenn das Flag in der Befehlszeile gefunden wurde.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier

Der eindeutige Neustartbezeichner in der Befehlszeile.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Bemerkungen

Der Neustartbezeichner ist für jede Instanz der Anwendung eindeutig.

Wenn der Neustart-Manager die Anwendung verlässt und für den Neustart konfiguriert ist, führt der Neustart-Manager die Anwendung über die Befehlszeile mit dem Neustartbezeichner als optionalen Parameter aus. Wenn der Neustart-Manager den Neustartbezeichner verwendet, kann die Anwendung die zuvor geöffneten Dokumente erneut öffnen und automatisch gespeicherte Dateien wiederherstellen.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam

Das Framework ruft diese Funktion auf, um einzelne Parameter aus der Befehlszeile zu analysieren/interpretieren. Die zweite Version unterscheidet sich von der ersten nur in Unicode-Projekten.

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>Parameter

*pszParam*<br/>
Der Parameter oder das Flag.

*bFlag*<br/>
Gibt an, ob *pszParam* ein Parameter oder ein Flag ist.

*Explosion*<br/>
Gibt an, ob dies der letzte Parameter oder das letzte Flag in der Befehlszeile ist.

### <a name="remarks"></a>Bemerkungen

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) `ParseParam` ruft einmal für jeden Parameter oder jedes Flag in der Befehlszeile auf und übergibt das Argument an *pszParam*. Wenn das erste Zeichen des **-** Parameters ein **/**' ' oder ein ' ' ' ist, wird es entfernt und *bFlag* wird auf TRUE gesetzt. Beim Analysieren des letzten Parameters wird *bLast* auf TRUE gesetzt.

Die Standardimplementierung dieser Funktion erkennt die `/p` `/pt`folgenden `/dde` `/Automation`Flags: `/Embedding`, , , und , wie in der folgenden Tabelle dargestellt:

|Befehlszeilenargument|Befehl ausgeführt|
|----------------------------|----------------------|
|*app*|Neue Datei.|
|*App-Dateiname*|Öffnen Sie die Datei.|
|*App-Dateiname* `/p`|Drucken Sie die Datei auf den Standarddrucker.|
|*app* App-Dateinamen-Druckertreiber-Port `/pt`|Drucken der Datei auf den angegebenen Drucker.|
|*app* `/dde`|Starten Sie den Befehl DDE, und warten Sie auf den Befehl DDE.|
|*app* `/Automation`|Starten Sie als OLE-Automatisierungsserver.|
|*app* `/Embedding`|Starten Sie, um ein eingebettetes OLE-Element zu bearbeiten.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informiert die Anwendung, um Registrierungsaufgaben auszuführen.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informiert die Anwendung, um alle Nichtregistrierungsaufgaben auszuführen.|

Diese Informationen werden in [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded)und [m_nShellCommand](#m_nshellcommand)gespeichert. Flags werden entweder durch einen Schrägstrich ' **/**' **-** oder binich ' ' gekennzeichnet.

Die Standardimplementierung setzt den ersten Nicht-Flag-Parameter in [m_strFileName](#m_strfilename). Im Fall des `/pt` Flags setzt die Standardimplementierung die zweiten, dritten und vierten Nicht-Flag-Parameter in [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)und [m_strPortName](#m_strportname).

Die Standardimplementierung legt [auch m_bShowSplash](#m_bshowsplash) nur bei einer neuen Datei auf TRUE fest. Im Falle einer neuen Datei hat der Benutzer Maßnahmen ergriffen, die die Anwendung selbst betreffen. In jedem anderen Fall, einschließlich des Öffnens vorhandener Dateien mithilfe der Shell, bezieht die Benutzeraktion die Datei direkt ein. In dokumentzentrierter Sicht muss der Begrüßungsbildschirm die Inbetriebnahme der Anwendung nicht ankündigen.

Überschreiben Sie diese Funktion in der abgeleiteten Klasse, um andere Flag- und Parameterwerte zu verarbeiten.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
