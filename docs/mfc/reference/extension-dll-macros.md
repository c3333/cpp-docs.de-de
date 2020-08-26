---
title: Makros und Funktionen für die Verwaltung von DLLs
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: e4170ba95775fd3380837673a76a8adafc8ad011
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837178"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makros und Funktionen für die Verwaltung von DLLs

|Name|Beschreibung|
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportiert Klassen.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Schützen einer exportierten Funktion in einer DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Bietet OLE-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[AfxNetInitModule](#afxnetinitmodule)|Bietet Unterstützung für MFC-Sockets aus einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Ruft den aktuellen Zustand des pro-Modul-Statusflags ab.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Legt den Modulstatus vor der Initialisierung fest und/oder, um den vorherigen Modul Zustand nach dem Cleanup wiederherzustellen.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Initialisiert die dll.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Legen Sie das Statusflag pro Modul fest, das sich auf das WinSxS-Verhalten von MFC auswirkt.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Ermöglicht MFC das Bereinigen der MFC-Erweiterungs-DLL, wenn jeder Prozess von der DLL getrennt wird.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a> AFX_EXT_CLASS

[MFC-Erweiterungs-DLLs](../../build/extension-dlls.md) (Dynamic Link Library) verwenden das Makro AFX_EXT_CLASS zum Exportieren von Klassen. Die ausführbaren Dateien, die mit der MFC-Erweiterungs-DLL verknüpft sind, verwenden das Makro, um Klassen zu importieren.

### <a name="remarks"></a>Bemerkungen

Mit dem AFX_EXT_CLASS-Makro können die gleichen Header Dateien, die zum Erstellen der MFC-Erweiterungs-DLL verwendet wurden, mit den ausführbaren Dateien verwendet werden, die mit der DLL verknüpft sind.

Fügen Sie in der Headerdatei für die DLL der Deklaration der Klasse das AFX_EXT_CLASS-Schlüsselwort wie folgt hinzu:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Weitere Informationen finden Sie unter [exportieren und importieren mit AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxv_dll. h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a> AFX_MANAGE_STATE

Mit diesem Makro wird eine exportierte Funktion in einer DLL geschützt.

### <a name="syntax"></a>Syntax

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parameter

*pmodulestate*<br/>
Ein Zeiger auf eine- `AFX_MODULE_STATE` Struktur.

### <a name="remarks"></a>Bemerkungen

Wenn dieses Makro aufgerufen wird, ist *pmodulestate* der effektive Modul Zustand für den Rest des unmittelbaren enthaltenden Bereichs. Wenn Sie den Bereich verlassen, wird der vorherige effektive Modul Zustand automatisch wieder hergestellt.
Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modul Zustands, der per pushübertragung oder Pop-Wert verschoben wird.

Standardmäßig verwendet MFC das Ressourcen Handle der Hauptanwendung, um die Ressourcen Vorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. b. eine, die ein Dialogfeld in der dll öffnet, wird diese Vorlage tatsächlich im dll-Modul gespeichert. Sie müssen den Modul Zustand für das richtige handle ändern, das verwendet werden soll. Hierzu fügen Sie den folgenden Code am Anfang der-Funktion hinzu:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modul Zustand mit dem von [afxgetstaticmodulestate](#afxgetstaticmodulestate) zurückgegebenen Zustand bis zum Ende des aktuellen Bereichs vertauscht.

Weitere Informationen zu Modul Zuständen und MFC finden Sie unter "Verwalten der Statusdaten von MFC-Modulen" in [Erstellen neuer Dokumente, Fenster und Ansichten](../creating-new-documents-windows-and-views.md) und [Technische Notiz 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Wenn MFC einen Aktivierungs Kontext für eine Assembly erstellt, verwendet er [afxwininit](application-information-and-management.md#afxwininit) , um den Kontext zu erstellen und `AFX_MANAGE_STATE` ihn zu aktivieren und zu deaktivieren. Beachten Sie auch, dass `AFX_MANAGE_STATE` sowohl für statische MFC-Bibliotheken als auch für MFC-DLLs aktiviert ist, damit MFC-Code im richtigen Aktivierungs Kontext ausgeführt werden kann, der von der Benutzer-DLL ausgewählt wird. Weitere Informationen finden Sie [unter Unterstützung für Aktivierungs Kontexte im MFC-Modulstatus](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxstat_. h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> Afxolinitmodule

Für OLE-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, müssen Sie diese Funktion in ihrer regulären MFC-DLL- `CWinApp::InitInstance` Funktion zum Initialisieren der MFC-OLE-dll-Datei abrufen.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Die MFC-OLE-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine Kette eingebunden werden `CDynLinkLibrary` kann, muss Sie `CDynLinkLibrary` im Kontext jedes Moduls, das Sie verwenden wird, ein-Objekt erstellen. `AfxOleInitModule` erstellt das `CDynLinkLibrary` -Objekt im regulären MFC-DLL-Kontext, sodass es in die `CDynLinkLibrary` Objekt Kette der regulären MFC-DLL eingebunden wird.

Wenn Sie ein OLE-Steuerelement entwickeln und verwenden `COleControlModule` , sollten Sie nicht aufrufen, `AfxOleInitModule` da die `InitInstance` Member-Funktion für- `COleControlModule` Aufrufe aufruft `AfxOleInitModule` .

### <a name="requirements"></a>Requirements (Anforderungen)

**Header**: \<afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a> AfxNetInitModule

Für MFC-Sockets-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, fügen Sie einen-Befehl in ihrer regulären MFC-DLL-Funktion hinzu, `CWinApp::InitInstance` um die MFC-Sockets-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Die MFC-Sockets-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine Kette eingebunden werden `CDynLinkLibrary` kann, muss Sie `CDynLinkLibrary` im Kontext jedes Moduls, das Sie verwenden wird, ein-Objekt erstellen. `AfxNetInitModule` erstellt das `CDynLinkLibrary` -Objekt im regulären MFC-DLL-Kontext, sodass es in die `CDynLinkLibrary` Objekt Kette der regulären MFC-DLL eingebunden wird.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a> Afxgetambientactctx

Verwenden Sie diese Funktion, um den aktuellen Zustand des pro-Modul-Statusflags zu erhalten, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Rückgabewert

Der aktuelle Wert des modulstatusflags.

### <a name="remarks"></a>Bemerkungen

Wenn das-Flag festgelegt ist (Dies ist die Standardeinstellung) und ein Thread in ein MFC-Modul Eintritt (siehe [AFX_MANAGE_STATE](#afx_manage_state)), wird der Kontext des Moduls aktiviert.

Wenn das Flag nicht festgelegt ist, wird der Kontext des Moduls beim Eintrag nicht aktiviert.

Der Kontext eines Moduls wird anhand seines Manifests bestimmt, das normalerweise in Modul Ressourcen eingebettet ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcomctl32. h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a> Afxgetstaticmodulestate

Mit dieser Funktion können Sie den Modul Zustand vor der Initialisierung festlegen und/oder den vorherigen Modul Zustand nach dem Cleanup wiederherstellen.

### <a name="syntax"></a>Syntax

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine- `AFX_MODULE_STATE` Struktur.

### <a name="remarks"></a>Bemerkungen

Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modul Zustands, der per pushübertragung oder Pop-Wert verschoben wird.

Standardmäßig verwendet MFC das Ressourcen Handle der Hauptanwendung, um die Ressourcen Vorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. b. eine, die ein Dialogfeld in der dll öffnet, wird diese Vorlage tatsächlich im dll-Modul gespeichert. Sie müssen den Modul Zustand für das richtige handle ändern, das verwendet werden soll. Hierzu fügen Sie den folgenden Code am Anfang der-Funktion hinzu:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modul Zustand mit dem Zustand, der von `AfxGetStaticModuleState` bis zum Ende des aktuellen Bereichs zurückgegeben wird, vertauscht.

Weitere Informationen zu Modul Zuständen und MFC finden Sie unter "Verwalten der Statusdaten von MFC-Modulen" in [Erstellen neuer Dokumente, Fenster und Ansichten](../creating-new-documents-windows-and-views.md) und [Technische Notiz 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxstat_. h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Diese Funktion wird in einer MFC-Erweiterungs-DLL aufgerufen `DllMain` , um die dll zu initialisieren.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parameter

*state*<br/>
Ein Verweis auf die [AFX_EXTENSION_MODULE Struktur](afx-extension-module-structure.md) Struktur, die den Status des MFC-Erweiterungs-DLL-Moduls nach der Initialisierung enthält. Der Status enthält eine Kopie der Lauf Zeit Klassen Objekte, die von der MFC-Erweiterungs-DLL im Rahmen der normalen statischen Objektkonstruktion initialisiert wurden, die vor der Eingabe von ausgeführt wurde `DllMain` .

*HMODULE*<br/>
Ein Handle des MFC-Erweiterungs-DLL-Moduls.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die MFC-Erweiterungs-DLL erfolgreich initialisiert wurde. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Beispiel:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule` erstellt eine Kopie des HMODULE der dll und erfasst die Lauf Zeit Klassen ( `CRuntimeClass` Strukturen) der dll sowie deren objektfactorys ( `COleObjectFactory` Objekte), die später beim Erstellen des Objekts verwendet werden sollen `CDynLinkLibrary` .
MFC-Erweiterungs-DLLs müssen in ihrer Funktion zwei Dinge erledigen `DllMain` :

- Aufrufen von [AfxInitExtensionModule](#afxinitextensionmodule) und Überprüfen des Rückgabewerts.

- Erstellen Sie ein- `CDynLinkLibrary` Objekt, wenn die DLL [CRuntimeClass-Struktur](cruntimeclass-structure.md) Objekte exportiert oder über eigene benutzerdefinierte Ressourcen verfügt.

Sie können aufzurufen `AfxTermExtensionModule` , um die MFC-Erweiterungs-DLL zu bereinigen, wenn jeder Prozess von der MFC-Erweiterungs-DLL trennt (was geschieht, wenn der Prozess beendet wird, oder wenn die dll als Ergebnis eines- `AfxFreeLibrary` Aufrufes entladen wird).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdll_. h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a> Afxsetambientactctx

Verwenden Sie diese Funktion, um das Statusflag pro Modul festzulegen, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parameter

*BSET*<br/>
Neuer Wert des modulstatusflags.

### <a name="remarks"></a>Bemerkungen

Wenn das-Flag festgelegt ist (Dies ist die Standardeinstellung) und ein Thread in ein MFC-Modul Eintritt (siehe [AFX_MANAGE_STATE](#afx_manage_state)), wird der Kontext des Moduls aktiviert.
Wenn das Flag nicht festgelegt ist, wird der Kontext des Moduls beim Eintrag nicht aktiviert.
Der Kontext eines Moduls wird anhand seines Manifests bestimmt, das normalerweise in Modul Ressourcen eingebettet ist.

### <a name="example"></a>Beispiel

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcomctl32. h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a> AfxTermExtensionModule

Mit dieser Funktion können Sie MFC das Bereinigen der MFC-Erweiterungs-DLL gestatten, wenn jeder Prozess von der dll trennt (was geschieht, wenn der Prozess beendet wird oder wenn die dll als Ergebnis eines- `AfxFreeLibrary` Aufrufes entladen wird).

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parameter

*state*<br/>
Ein Verweis auf die [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) Struktur, die den Status des MFC-Erweiterungs-DLL-Moduls enthält.

*Kopf*<br/>
Wenn true, werden alle MFC-Erweiterungs-DLL-Module bereinigt. Andernfalls sollten Sie nur das aktuelle dll-Modul bereinigen.

### <a name="remarks"></a>Bemerkungen

`AfxTermExtensionModule` Löscht jeden lokalen Speicher, der mit dem Modul verbunden ist, und entfernt alle Einträge aus dem Nachrichten Zuordnungs Cache. Beispiel:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

Wenn Ihre Anwendung MFC-Erweiterungs-DLLs dynamisch lädt und freigibt, müssen Sie darauf achten `AfxTermExtensionModule` . Da die meisten MFC-Erweiterungs-DLLs nicht dynamisch geladen werden (in der Regel werden Sie über Ihre Import Bibliotheken verknüpft), ist der-Befehl in `AfxTermExtensionModule` der Regel nicht erforderlich.

MFC-Erweiterungs-DLLs müssen [AfxInitExtensionModule](#afxinitextensionmodule) in Ihrem aufrufen `DllMain` . Wenn die DLL [CRuntimeClass](cruntimeclass-structure.md) -Objekte exportiert oder über eigene benutzerdefinierte Ressourcen verfügt, müssen Sie auch ein- `CDynLinkLibrary` Objekt in Erstellen `DllMain` .

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdll_. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Verwalten der Statusdaten von MFC-Modulen](../managing-the-state-data-of-mfc-modules.md)<br/>
