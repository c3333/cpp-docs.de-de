---
title: Makros und Funktionen für die Verwaltung von DLLs
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426696"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makros und Funktionen für die Verwaltung von DLLs

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportiert Klassen.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Schützen einer exportierten Funktion in einer DLL.|
|[Afxolinitmodule](#afxoleinitmodule)|Bietet OLE-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[AfxNetInitModule](#afxnetinitmodule)|Bietet Unterstützung für MFC-Sockets aus einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[Afxgetambientactctx](#afxgetambientactctx)|Ruft den aktuellen Zustand des pro-Modul-Statusflags ab.|
|[Afxgetstaticmodulestate](#afxgetstaticmodulestate)|Legt den Modulstatus vor der Initialisierung fest und/oder, um den vorherigen Modul Zustand nach dem Cleanup wiederherzustellen.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Initialisiert die dll.|
|[Afxsetambientactctx](#afxsetambientactctx)|Legen Sie das Statusflag pro Modul fest, das sich auf das WinSxS-Verhalten von MFC auswirkt.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Ermöglicht MFC das Bereinigen der MFC-Erweiterungs-DLL, wenn jeder Prozess von der DLL getrennt wird.|

## <a name="afx_ext_class"></a>AFX_EXT_CLASS

[MFC-Erweiterungs-DLLs](../../build/extension-dlls.md) verwenden das Makro AFX_EXT_CLASS, um Klassen zu exportieren. die ausführbaren Dateien, die mit der MFC-Erweiterungs-DLL verknüpft sind, verwenden das-Makro, um Klassen zu importieren.

### <a name="remarks"></a>Hinweise

Mit dem AFX_EXT_CLASS-Makro können die gleichen Header Dateien, die zum Erstellen der MFC-Erweiterungs-DLL verwendet wurden, mit den ausführbaren Dateien verwendet werden, die mit der DLL verknüpft sind.

Fügen Sie in der Header Datei für die dll das AFX_EXT_CLASS-Schlüsselwort zur Deklaration ihrer Klasse wie folgt hinzu:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Weitere Informationen finden Sie unter [exportieren und importieren mit AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Voraussetzungen

**Header:** afxv_dll. h

## <a name="afx_manage_state"></a>AFX_MANAGE_STATE

Mit diesem Makro wird eine exportierte Funktion in einer DLL geschützt.

### <a name="syntax"></a>Syntax

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parameter

*pmodulestate*<br/>
Ein Zeiger auf eine `AFX_MODULE_STATE`-Struktur.

### <a name="remarks"></a>Hinweise

Wenn dieses Makro aufgerufen wird, ist *pmodulestate* der effektive Modul Zustand für den Rest des unmittelbaren enthaltenden Bereichs. Wenn Sie den Bereich verlassen, wird der vorherige effektive Modul Zustand automatisch wieder hergestellt.
Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modul Zustands, der per pushübertragung oder Pop-Wert verschoben wird.

Standardmäßig verwendet MFC das Ressourcen Handle der Hauptanwendung, um die Ressourcen Vorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. b. eine, die ein Dialogfeld in der dll öffnet, wird diese Vorlage tatsächlich im dll-Modul gespeichert. Sie müssen den Modul Zustand für das richtige handle ändern, das verwendet werden soll. Hierzu fügen Sie den folgenden Code am Anfang der-Funktion hinzu:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modul Zustand mit dem von [afxgetstaticmodulestate](#afxgetstaticmodulestate) zurückgegebenen Zustand bis zum Ende des aktuellen Bereichs vertauscht.

Weitere Informationen zu Modul Zuständen und MFC finden Sie unter "Verwalten der Statusdaten von MFC-Modulen" in [Erstellen neuer Dokumente, Fenster und Ansichten](../creating-new-documents-windows-and-views.md) und [Technische Notiz 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
>  Wenn MFC einen Aktivierungs Kontext für eine Assembly erstellt, verwendet er [afxwininit](application-information-and-management.md#afxwininit) , um den Kontext zu erstellen, und `AFX_MANAGE_STATE`, um ihn zu aktivieren und zu deaktivieren. Beachten Sie außerdem, dass `AFX_MANAGE_STATE` sowohl für statische MFC-Bibliotheken als auch für MFC-DLLs aktiviert ist, damit MFC-Code im richtigen Aktivierungs Kontext ausgeführt werden kann, der von der Benutzer-DLL ausgewählt wird. Weitere Informationen finden Sie [unter Unterstützung für Aktivierungs Kontexte im MFC-Modulstatus](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Voraussetzungen

**Header:** afxstat_. h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> afxolinitmodule

Für OLE-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, müssen Sie diese Funktion in der `CWinApp::InitInstance` Funktion Ihrer regulären MFC-DLL zum Initialisieren der MFC-OLE-dll-Datei abrufen.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Hinweise

Die MFC-OLE-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine `CDynLinkLibrary` Kette eingebunden werden kann, muss Sie ein `CDynLinkLibrary`-Objekt im Kontext jedes Moduls erstellen, das Sie verwenden wird. `AfxOleInitModule` erstellt das `CDynLinkLibrary`-Objekt im regulären Kontext der MFC-DLL, sodass es in die `CDynLinkLibrary`-Objekt Kette der regulären MFC-DLL eingebunden wird.

Wenn Sie ein OLE-Steuerelement entwickeln und `COleControlModule`verwenden, sollten Sie `AfxOleInitModule` nicht aufrufen, da die `InitInstance` Member-Funktion für `COleControlModule` `AfxOleInitModule`aufruft.

### <a name="requirements"></a>Voraussetzungen

**Header**: \<afxdll_. h >

## <a name="afxnetinitmodule"></a>AfxNetInitModule

Für MFC-Sockets-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, fügen Sie in der `CWinApp::InitInstance`-Funktion Ihrer regulären MFC-DLL einen aufrufsbefehl hinzu, um die MFC-Sockets-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Hinweise

Die MFC-Sockets-dll ist eine MFC-Erweiterungs-DLL. damit eine MFC-Erweiterungs-DLL in eine `CDynLinkLibrary` Kette eingebunden werden kann, muss Sie ein `CDynLinkLibrary`-Objekt im Kontext jedes Moduls erstellen, das Sie verwenden wird. `AfxNetInitModule` erstellt das `CDynLinkLibrary`-Objekt im regulären Kontext der MFC-DLL, sodass es in die `CDynLinkLibrary`-Objekt Kette der regulären MFC-DLL eingebunden wird.

### <a name="requirements"></a>Voraussetzungen

**Header:** \<afxdll_. h >

## <a name="afxgetambientactctx"></a>Afxgetambientactctx

Verwenden Sie diese Funktion, um den aktuellen Zustand des pro-Modul-Statusflags zu erhalten, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Rückgabewert

Der aktuelle Wert des modulstatusflags.

### <a name="remarks"></a>Hinweise

Wenn das-Flag festgelegt ist (Dies ist die Standardeinstellung) und ein Thread in ein MFC-Modul Eintritt (siehe [AFX_MANAGE_STATE](#afx_manage_state)), wird der Kontext des Moduls aktiviert.

Wenn das Flag nicht festgelegt ist, wird der Kontext des Moduls beim Eintrag nicht aktiviert.

Der Kontext eines Moduls wird anhand seines Manifests bestimmt, das normalerweise in Modul Ressourcen eingebettet ist.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxcomctl32. h

## <a name="afxgetstaticmodulestate"></a>Afxgetstaticmodulestate

Mit dieser Funktion können Sie den Modul Zustand vor der Initialisierung festlegen und/oder den vorherigen Modul Zustand nach dem Cleanup wiederherstellen.

### <a name="syntax"></a>Syntax

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine `AFX_MODULE_STATE`-Struktur.

### <a name="remarks"></a>Hinweise

Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modul Zustands, der per pushübertragung oder Pop-Wert verschoben wird.

Standardmäßig verwendet MFC das Ressourcen Handle der Hauptanwendung, um die Ressourcen Vorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. b. eine, die ein Dialogfeld in der dll öffnet, wird diese Vorlage tatsächlich im dll-Modul gespeichert. Sie müssen den Modul Zustand für das richtige handle ändern, das verwendet werden soll. Hierzu fügen Sie den folgenden Code am Anfang der-Funktion hinzu:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modul Zustand mit dem Zustand ausgetauscht, der von `AfxGetStaticModuleState` bis zum Ende des aktuellen Bereichs zurückgegeben wurde.

Weitere Informationen zu Modul Zuständen und MFC finden Sie unter "Verwalten der Statusdaten von MFC-Modulen" in [Erstellen neuer Dokumente, Fenster und Ansichten](../creating-new-documents-windows-and-views.md) und [Technische Notiz 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Voraussetzungen

**Header:** afxstat_. h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Diese Funktion wird in der `DllMain` einer MFC-Erweiterungs-DLL aufgerufen, um die dll zu initialisieren.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parameter

*state*<br/>
Ein Verweis auf die [AFX_EXTENSION_MODULE Struktur](afx-extension-module-structure.md) Struktur, die den Status des MFC-Erweiterungs-DLL-Moduls nach der Initialisierung enthält. Der Status enthält eine Kopie der Lauf Zeit Klassen Objekte, die von der MFC-Erweiterungs-DLL im Rahmen der normalen statischen Objektkonstruktion initialisiert wurden, bevor `DllMain` eingegeben wird.

*HMODULE*<br/>
Ein Handle des MFC-Erweiterungs-DLL-Moduls.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die MFC-Erweiterungs-DLL erfolgreich initialisiert wurde. andernfalls false.

### <a name="remarks"></a>Hinweise

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

`AfxInitExtensionModule` erstellt eine Kopie des HMODULE der dll und erfasst die Lauf Zeit Klassen der dll (`CRuntimeClass` Strukturen) sowie die zugehörigen objektfactorys (`COleObjectFactory` Objekte), die später beim Erstellen des `CDynLinkLibrary` Objekts verwendet werden.
MFC-Erweiterungs-DLLs müssen in ihrer `DllMain` Funktion zwei Dinge erledigen:

- Aufrufen von [AfxInitExtensionModule](#afxinitextensionmodule) und Überprüfen des Rückgabewerts.

- Erstellen Sie ein `CDynLinkLibrary` Objekt, wenn die DLL [CRuntimeClass-Struktur](cruntimeclass-structure.md) Objekte exportiert oder über eigene benutzerdefinierte Ressourcen verfügt.

Sie können `AfxTermExtensionModule` zum Bereinigen der MFC-Erweiterungs-DLL aufzurufen, wenn jeder Prozess von der MFC-Erweiterungs-DLL trennt (was geschieht, wenn der Prozess beendet wird, oder wenn die dll aufgrund eines `AfxFreeLibrary` Aufrufes entladen wird).

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdll_. h

## <a name="afxsetambientactctx"></a>Afxsetambientactctx

Verwenden Sie diese Funktion, um das Statusflag pro Modul festzulegen, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parameter

*BSET*<br/>
Neuer Wert des modulstatusflags.

### <a name="remarks"></a>Hinweise

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

### <a name="requirements"></a>Voraussetzungen

**Header:** afxcomctl32. h

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Mit dieser Funktion können Sie MFC das Bereinigen der MFC-Erweiterungs-DLL gestatten, wenn jeder Prozess von der dll trennt (was geschieht, wenn der Prozess beendet wird oder wenn die dll aufgrund eines `AfxFreeLibrary`-Aufrufes entladen wird).

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parameter

*state*<br/>
Ein Verweis auf die [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) Struktur, die den Status des MFC-Erweiterungs-DLL-Moduls enthält.

*Kopf*<br/>
Wenn true, werden alle MFC-Erweiterungs-DLL-Module bereinigt. Andernfalls sollten Sie nur das aktuelle dll-Modul bereinigen.

### <a name="remarks"></a>Hinweise

`AfxTermExtensionModule` löscht jeden lokalen Speicher, der mit dem Modul verbunden ist, und entfernt alle Einträge aus dem Nachrichten Zuordnungs Cache. Beispiel:

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

Wenn Ihre Anwendung MFC-Erweiterungs-DLLs dynamisch lädt und freigibt, müssen Sie `AfxTermExtensionModule`abrufen. Da die meisten MFC-Erweiterungs-DLLs nicht dynamisch geladen werden (in der Regel werden Sie über Ihre Import Bibliotheken verknüpft), ist der `AfxTermExtensionModule`-Aufrufe in der Regel nicht erforderlich.

MFC-Erweiterungs-DLLs müssen [AfxInitExtensionModule](#afxinitextensionmodule) in ihren `DllMain`aufrufen. Wenn die DLL [CRuntimeClass](cruntimeclass-structure.md) -Objekte exportiert oder über eigene benutzerdefinierte Ressourcen verfügt, müssen Sie in `DllMain`auch ein `CDynLinkLibrary` Objekt erstellen.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdll_. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Verwalten der Statusdaten von MFC-Modulen](../managing-the-state-data-of-mfc-modules.md)<br/>
