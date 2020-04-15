---
title: Makros und Funktionen zum Verwalten von DLLs
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 6945dcc02423516e8d1cee5d8c828c4ed5069bef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365701"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makros und Funktionen zum Verwalten von DLLs

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportiert Klassen.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Schützen Sie eine exportierte Funktion in einer DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Bietet OLE-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[AfxNetInitModule](#afxnetinitmodule)|Bietet MFC-Sockets-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Ruft den aktuellen Status des Statusflags pro Modul ab.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Legt den Modulstatus vor der Initialisierung fest und/oder stellt den vorherigen Modulstatus nach dem Bereinigen wieder her.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Initialisiert die DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|legen Sie das Statusflag pro Modul fest, das sich auf das WinSxS-Verhalten von MFC auswirkt.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Ermöglicht MFC das Bereinigen der MFC-Erweiterungs-DLL, wenn sich jeder Prozess von der DLL löst.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>Afx_ext_class

[MFC-Erweiterungs-DLLs](../../build/extension-dlls.md) verwenden die Makro-AFX_EXT_CLASS zum Exportieren von Klassen. Die ausführbaren Dateien, die mit der MFC-Erweiterungs-DLL verknüpft sind, verwenden das Makro zum Importieren von Klassen.

### <a name="remarks"></a>Bemerkungen

Mit dem AFX_EXT_CLASS-Makro können dieselben Headerdateien, die zum Erstellen der MFC-Erweiterungs-DLL verwendet werden, mit den ausführbaren Dateien verwendet werden, die mit der DLL verknüpft sind.

Fügen Sie in der Headerdatei für Ihre DLL das Schlüsselwort AFX_EXT_CLASS der Deklaration Ihrer Klasse wie folgt hinzu:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Weitere Informationen finden Sie unter [Exportieren und Importieren mit AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>Afx_manage_state

Rufen Sie dieses Makro auf, um eine exportierte Funktion in einer DLL zu schützen.

### <a name="syntax"></a>Syntax

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parameter

*pModuleState*<br/>
Ein Zeiger auf `AFX_MODULE_STATE` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Wenn dieses Makro aufgerufen wird, ist *pModuleState* der effektive Modulstatus für den Rest des unmittelbaren, enthaltenden Bereichs. Nach verlassen dem Bereich wird der vorherige effektive Modulstatus automatisch wiederhergestellt.
Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modulstatus, der verschoben oder geknallt wird.

Standardmäßig verwendet MFC das Ressourcenhandle der Hauptanwendung, um die Ressourcenvorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. B. eine, die ein Dialogfeld in der DLL startet, wird diese Vorlage tatsächlich im DLL-Modul gespeichert. Sie müssen den Modulstatus wechseln, damit das richtige Handle verwendet werden kann. Sie können dies tun, indem Sie den folgenden Code am Anfang der Funktion hinzufügen:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modulstatus mit dem von [AfxGetStaticModuleState](#afxgetstaticmodulestate) zurückgegebenen Status bis zum Ende des aktuellen Bereichs ausgetauscht.

Weitere Informationen zu Modulzuständen und MFC finden Sie unter "Verwalten der Zustandsdaten von MFC-Modulen" unter [Erstellen neuer Dokumente, Windows und Ansichten](../creating-new-documents-windows-and-views.md) sowie in der technischen Anmerkung [58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Wenn MFC einen Aktivierungskontext für eine Assembly erstellt, verwendet `AFX_MANAGE_STATE` es [AfxWinInit,](application-information-and-management.md#afxwininit) um den Kontext zu erstellen und zu aktivieren und zu deaktivieren. Beachten Sie `AFX_MANAGE_STATE` auch, dass für statische MFC-Bibliotheken sowie MFC-DLLs aktiviert ist, damit MFC-Code in dem richtigen Aktivierungskontext ausgeführt werden kann, der von der Benutzer-DLL ausgewählt wurde. Weitere Informationen finden Sie unter [Unterstützung für Aktivierungskontexte im MFC-Modulstatus](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule

Für DIE OLE-Unterstützung durch eine reguläre MFC-DLL, die dynamisch mit MFC `CWinApp::InitInstance` verknüpft ist, rufen Sie diese Funktion in der Funktion Ihrer regulären MFC-DLL auf, um die MFC-OLE-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Die MFC OLE DLL ist eine MFC-Erweiterungs-DLL; Damit eine MFC-Erweiterungs-DLL in `CDynLinkLibrary` eine Kette verdrahtet werden kann, muss sie ein `CDynLinkLibrary` Objekt im Kontext jedes Moduls erstellen, das sie verwendet. `AfxOleInitModule`erstellt `CDynLinkLibrary` das Objekt im Kontext Ihrer regulären MFC-DLL, `CDynLinkLibrary` sodass es in die Objektkette der regulären MFC-DLL verdrahtet wird.

Wenn Sie ein OLE-Steuerelement `COleControlModule`erstellen und verwenden, `InitInstance` sollten Sie `COleControlModule` `AfxOleInitModule`nicht aufrufen, `AfxOleInitModule` da die Memberfunktion für Aufrufe .

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: \<afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInitModule

Für MFC-Sockets-Unterstützung von einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, fügen Sie dieser Funktion in der `CWinApp::InitInstance` Funktion Ihrer regulären MFC-DLL einen Aufruf hinzu, um die MFC-Sockets-DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Bemerkungen

Die MFC Sockets DLL ist eine MFC-Erweiterungs-DLL; Damit eine MFC-Erweiterungs-DLL in `CDynLinkLibrary` eine Kette verdrahtet werden kann, muss sie ein `CDynLinkLibrary` Objekt im Kontext jedes Moduls erstellen, das sie verwendet. `AfxNetInitModule`erstellt `CDynLinkLibrary` das Objekt im Kontext Ihrer regulären MFC-DLL, `CDynLinkLibrary` sodass es in die Objektkette der regulären MFC-DLL verdrahtet wird.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Verwenden Sie diese Funktion, um den aktuellen Status des Statusflags pro Modul abzubekommen, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Rückgabewert

Modulstatus-Flag-Aktueller Wert.

### <a name="remarks"></a>Bemerkungen

Wenn das Flag gesetzt ist (was der Standard ist) und ein Thread in ein MFC-Modul eintritt (siehe [AFX_MANAGE_STATE](#afx_manage_state)), wird der Kontext des Moduls aktiviert.

Wenn das Flag nicht gesetzt ist, wird der Kontext des Moduls beim Eintrag nicht aktiviert.

Der Kontext eines Moduls wird aus seinem Manifest bestimmt, das in der Regel in Modulressourcen eingebettet ist.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

Rufen Sie diese Funktion auf, um den Modulstatus vor der Initialisierung festzulegen und/oder den vorherigen Modulstatus nach dem Bereinigen wiederherzustellen.

### <a name="syntax"></a>Syntax

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `AFX_MODULE_STATE` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Die `AFX_MODULE_STATE` Struktur enthält globale Daten für das Modul, d. h. den Teil des Modulstatus, der verschoben oder geknallt wird.

Standardmäßig verwendet MFC das Ressourcenhandle der Hauptanwendung, um die Ressourcenvorlage zu laden. Wenn Sie eine exportierte Funktion in einer DLL haben, z. B. eine, die ein Dialogfeld in der DLL startet, wird diese Vorlage tatsächlich im DLL-Modul gespeichert. Sie müssen den Modulstatus wechseln, damit das richtige Handle verwendet werden kann. Sie können dies tun, indem Sie den folgenden Code am Anfang der Funktion hinzufügen:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Dadurch wird der aktuelle Modulstatus mit `AfxGetStaticModuleState` dem Zustand ausgetauscht, der bis zum Ende des aktuellen Bereichs zurückgegeben wird.

Weitere Informationen zu Modulzuständen und MFC finden Sie unter "Verwalten der Zustandsdaten von MFC-Modulen" unter [Erstellen neuer Dokumente, Windows und Ansichten](../creating-new-documents-windows-and-views.md) sowie in der technischen Anmerkung [58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Rufen Sie diese Funktion in einer `DllMain` MFC-Erweiterungs-DLL auf, um die DLL zu initialisieren.

### <a name="syntax"></a>Syntax

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parameter

*Staat*<br/>
Ein Verweis auf die [strukturstrukturAFX_EXTENSION_MODULE](afx-extension-module-structure.md) die den Status des MFC-Erweiterungs-DLL-Moduls nach der Initialisierung enthält. Der Status enthält eine Kopie der Laufzeitklassenobjekte, die von der MFC-Erweiterungs-DLL als `DllMain` Teil der normalen statischen Objektkonstruktion initialisiert wurden, die vor der Eingabe ausgeführt wurde.

*hModule*<br/>
Ein Handle des MFC-Erweiterungs-DLL-Moduls.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die MFC-Erweiterungs-DLL erfolgreich initialisiert wurde; andernfalls FALSE.

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

`AfxInitExtensionModule`erstellt eine Kopie des HMODULE der DLL und erfasst die Laufzeitklassen`CRuntimeClass` (Strukturen) der DLL`COleObjectFactory` sowie deren Objektfabriken (Objekte) für die spätere Verwendung, wenn das `CDynLinkLibrary` Objekt erstellt wird.
MFC-Erweiterungs-DLLs müssen in `DllMain` ihrer Funktion zwei Dinge tun:

- Rufen Sie [AfxInitExtensionModule](#afxinitextensionmodule) auf, und überprüfen Sie den Rückgabewert.

- Erstellen `CDynLinkLibrary` Sie ein Objekt, wenn die DLL [CRuntimeClass Structure-Objekte](cruntimeclass-structure.md) exportiert oder über eigene benutzerdefinierte Ressourcen verfügt.

Sie können `AfxTermExtensionModule` aufrufen, um die MFC-Erweiterungs-DLL zu bereinigen, wenn sich jeder Prozess von der MFC-Erweiterungs-DLL `AfxFreeLibrary` löst (was geschieht, wenn der Prozess beendet wird oder wenn die DLL als Ergebnis eines Aufrufs entladen wird).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Verwenden Sie diese Funktion, um das Statusflag pro Modul festzulegen, das sich auf das WinSxS-Verhalten von MFC auswirkt.

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parameter

*bSet*<br/>
Neuer Wert der Modulstatusflagge.

### <a name="remarks"></a>Bemerkungen

Wenn das Flag gesetzt ist (was der Standard ist) und ein Thread in ein MFC-Modul eintritt (siehe [AFX_MANAGE_STATE](#afx_manage_state)), wird der Kontext des Moduls aktiviert.
Wenn das Flag nicht gesetzt ist, wird der Kontext des Moduls beim Eintrag nicht aktiviert.
Der Kontext eines Moduls wird aus seinem Manifest bestimmt, das in der Regel in Modulressourcen eingebettet ist.

### <a name="example"></a>Beispiel

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Anforderungen

**Kopf:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Rufen Sie diese Funktion auf, damit MFC die MFC-Erweiterungs-DLL bereinigen kann, wenn sich jeder Prozess von der DLL `AfxFreeLibrary` löst (was geschieht, wenn der Prozess beendet wird oder wenn die DLL als Ergebnis eines Aufrufs entladen wird).

### <a name="syntax"></a>Syntax

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parameter

*Staat*<br/>
Ein Verweis auf die [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) Struktur, die den Status des MFC-Erweiterungs-DLL-Moduls enthält.

*Ball*<br/>
Wenn TRUE, bereinigen Sie alle MFC-Erweiterungs-DLL-Module. Bereinigen Sie andernfalls nur das aktuelle DLL-Modul.

### <a name="remarks"></a>Bemerkungen

`AfxTermExtensionModule`löscht alle lokalen Speicher, die an das Modul angefügt sind, und entfernt alle Einträge aus dem Nachrichtenzuordnungscache. Beispiel:

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

Wenn Ihre Anwendung MFC-Erweiterungs-DLLs dynamisch lädt `AfxTermExtensionModule`und freigibt, rufen Sie sicher, dass Sie . Da die meisten MFC-Erweiterungs-DLLs nicht dynamisch geladen werden (in `AfxTermExtensionModule` der Regel sind sie über ihre Importbibliotheken verknüpft), ist der Aufruf von in der Regel nicht erforderlich.

MFC-Erweiterungs-DLLs müssen [AfxInitExtensionModule](#afxinitextensionmodule) in ihrer `DllMain`aufrufen. Wenn die DLL [CRuntimeClass-Objekte](cruntimeclass-structure.md) exportiert oder über eigene benutzerdefinierte `CDynLinkLibrary` Ressourcen `DllMain`verfügt, müssen Sie auch ein Objekt in erstellen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdll_.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Verwalten der Statusdaten von MFC-Modulen](../managing-the-state-data-of-mfc-modules.md)<br/>
