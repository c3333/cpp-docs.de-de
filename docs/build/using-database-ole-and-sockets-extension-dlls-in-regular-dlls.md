---
title: Verwenden von MFC-Erweiterungs-DLLs für Datenbanken, OLE und Sockets in regulären MFC-DLLs
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314688"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Verwenden von MFC-Erweiterungs-DLLs für Datenbanken, OLE und Sockets in regulären MFC-DLLs

Wenn Sie eine MFC-Erweiterungs-DLL aus einer regulären MFC-DLL verwenden und die MFC-Erweiterungs-DLL nicht mit der **CDynLinkLibrary**-Objektkette der regulären MFC-DLL verbunden ist, kann es vorkommen, dass ein oder mehrere dadurch begründete Probleme auftreten. Da die Debugversionen der MFC-Unterstützungs-DLLs für Datenbanken, OLE und Sockets als MFC-Erweiterungs-DLLs implementiert werden, treten bei Verwendung dieser MFC-Features möglicherweise selbst dann ähnliche Probleme auf, wenn Sie nicht explizit eine Ihrer eigenen MFC-Erweiterungs-DLLs verwenden. Dies sind einige Anzeichen:

- Beim Deserialisieren eines Objekts eines Klassentyps, der in der MFC-Erweiterungs-DLL definiert ist, wird die Meldung "Warning: Cannot load CYourClass from archive. Class not defined." (Warnung: CYourClass konnte nicht aus dem Archiv geladen werden. Die Klasse ist nicht definiert.) im TRACE-Debugfenster ausgegeben, und das Objekt kann nicht serialisiert werden.

- Es wird eine Ausnahme ausgegeben, die angibt, dass es sich möglicherweise um eine ungültige Klasse handelt.

- In der MFC-Erweiterungs-DLL gespeicherte Ressourcen können nicht geladen werden, da `AfxFindResourceHandle` **NULL** oder ein falsches Ressourcenhandle zurückgibt.

- `DllGetClassObject` und `DllCanUnloadNow` sowie die Memberfunktionen `UpdateRegistry`, `Revoke`, `RevokeAll` und `RegisterAll` von `COleObjectFactory` können keine in der MFC-Erweiterungs-DLL definierte Klassenfactory finden.

- `AfxDoForAllClasses` funktioniert nicht für Klassen in der MFC-Erweiterungs-DLL.

- MFC-Datenbank-, Socket- oder OLE-Standardressourcen können nicht geladen werden. Beispielsweise gibt **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) eine leere Zeichenfolge zurück, auch wenn die reguläre MFC-DLL die MFC-Datenbankklassen ordnungsgemäß verwendet.

Die Lösung für diese Probleme besteht darin, eine Initialisierungsfunktion in der MFC-Erweiterungs-DLL zu erstellen und zu exportieren, die ein **CDynLinkLibrary**-Objekt erstellt. Diese Initialisierungsfunktion wird von jeder regulären MFC-DLL, die die MFC-Erweiterungs-DLL verwendet, genau einmal aufgerufen.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC-Unterstützung für OLE, Datenbanken (oder DAO) oder Sockets

Wenn Sie in Ihrer regulären MFC-DLL die MFC-Unterstützung für OLE, Datenbanken (oder DAO) oder Sockets verwenden, werden die MFC-Erweiterungs-DLLs „MFCOxxD.dll“, „MFCDxxD.dll“ und „MFCNxxD.dll“ automatisch verknüpft (xx steht hier für die Versionsnummer). Sie müssen für jede dieser verwendeten DLLs eine vordefinierte Initialisierungsfunktion abrufen.

Fügen Sie zur Unterstützung von Datenbanken der `CWinApp::InitInstance`-Funktion Ihrer regulären MFC-DLL einen Aufruf von `AfxDbInitModule` hinzu. Stellen Sie sicher, dass dieser Aufruf vor einem Basisklassenaufruf oder einem beliebigen hinzugefügten Code erfolgt, der auf „MFCDxxD.dll“ zugreift. Diese Funktion nimmt keine Parameter an und gibt „void“ zurück.

Fügen Sie zur Unterstützung von OLE der `CWinApp::InitInstance`-Funktion Ihrer regulären MFC-DLL einen Aufruf von `AfxOleInitModule` hinzu. Beachten Sie, dass die **COleControlModule InitInstance**-Funktion bereits `AfxOleInitModule` aufruft. Wenn Sie also ein OLE-Steuerelement entwickeln und `COleControlModule` verwenden, sollten Sie diesen Aufruf von `AfxOleInitModule` nicht hinzufügen.

Fügen Sie zur Unterstützung von Sockets der `CWinApp::InitInstance`-Funktion Ihrer regulären MFC-DLL einen Aufruf von `AfxNetInitModule` hinzu.

Beachten Sie, dass Releasebuilds von MFC-DLLs und -Anwendungen keine separaten DLLs für die Unterstützung von Datenbanken, Sockets oder OLE verwenden. Es ist jedoch sicher, diese Initialisierungsfunktionen im Releasemodus aufzurufen.

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary-Objekte

Bei allen Vorgängen, die am Anfang dieses Artikels erwähnt wurden, muss die MFC nach einem gewünschten Wert oder Objekt suchen. Beispielsweise muss die MFC während der Deserialisierung alle zurzeit verfügbaren Runtimeklassen durchsuchen, um Objekte im Archiv mit der entsprechenden Runtimeklasse abzugleichen.

Im Rahmen dieser Suchvorgänge scannt die MFC mithilfe einer Ketten von **CDynLinkLibrary**-Objekten alle verwendeten MFC-Erweiterungs-DLLs. **CDynLinkLibrary**-Objekte werden während ihrer Erstellung automatisch an eine Kette angefügt und wiederum von jeder MFC-Erweiterungs-DLL während der Initialisierung erstellt. Außerdem verfügt jedes Modul (Anwendung oder reguläre MFC-DLL) über eine eigene Kette von **CDynLinkLibrary**-Objekten.

Damit eine MFC-Erweiterungs-DLL in eine **CDynLinkLibrary**-Kette eingebunden werden kann, muss sie ein **CDynLinkLibrary**-Objekt im Kontext jedes Moduls erstellen, das die MFC-Erweiterungs-DLL verwendet. Wenn eine MFC-Erweiterungs-DLL von regulären MFC-DLLs verwendet werden soll, muss sie daher eine exportierte Initialisierungsfunktion bereitstellen, die ein **CDynLinkLibrary**-Objekt erstellt. Jede reguläre MFC-DLL, die die MFC-Erweiterungs-DLL verwendet, muss die exportierte Initialisierungsfunktion aufrufen.

Wenn eine MFC-Erweiterungs-DLL nur von einer MFC-Anwendung (.exe) und nie von einer regulären MFC-DLL verwendet wird, genügt es, das **CDynLinkLibrary**-Objekt in der `DllMain`-Funktion der MFC-Erweiterungs-DLL zu erstellen. Das ist genau das, was mithilfe des MFC-Erweiterungs-DLL-Codes des MFC-DLL-Assistenten gemacht wird. Beim impliziten Laden einer MFC-Erweiterungs-DLL wird `DllMain` vor dem Starten der Anwendung geladen und ausgeführt. Alle **CDynLinkLibrary**-Erstellungen werden in eine Standardkette eingebunden, die die MFC-DLL für eine MFC-Anwendung reserviert.

Beachten Sie, dass es nicht sinnvoll ist, mehrere **CDynLinkLibrary**-Objekte aus einer MFC-Erweiterungs-DLL in einer Kette zu verwenden, insbesondere, wenn die MFC-Erweiterungs-DLL dynamisch aus dem Arbeitsspeicher entladen wird. Die Initialisierungsfunktion kann nicht mehr als einmal von einem Modul aufgerufen werden.

## <a name="sample-code"></a>Beispielcode

In diesem Beispielcode wird davon ausgegangen, dass die reguläre MFC-DLL implizit mit der MFC-Erweiterungs-DLL verknüpft wird. Dies wird erreicht, indem eine Verknüpfung mit der Importbibliothek (.lib) der MFC-Erweiterungs-DLL erfolgt, wenn die reguläre MFC-DLL erstellt wird.

Die Quelle der MFC-Erweiterungs-DLL sollte die folgenden Zeilen enthalten:

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

Stellen Sie sicher, dass Sie die **InitYourExtDLL**-Funktion exportieren. Dies erreichen Sie mithilfe von **__declspec(dllexport)** oder in der DEF-Datei der DLL wie folgt:

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Fügen Sie mit der MFC-Erweiterungs-DLL in jeder regulären MFC-DLL einen Aufruf für den `InitInstance`-Member des von `CWinApp` abgeleiteten Objekts hinzu:

```
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Initialisieren von MFC-Erweiterungs-DLLs](run-time-library-behavior.md#initializing-extension-dlls)

- [Initialisieren regulärer MFC-DLLs](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [MFC extension DLLs (MFC-Erweiterungs-DLLs)](extension-dlls.md)

- [Regular MFC DLLs Statically Linked to MFC (Reguläre, statisch mit MFC verknüpfte MFC-DLLs)](regular-dlls-statically-linked-to-mfc.md)

- [Regular MFC DLLs Dynamically Linked to MFC (Reguläre, dynamisch mit MFC verknüpfte MFC-DLLs)](regular-dlls-dynamically-linked-to-mfc.md)

- [Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [DLL-Version der MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Siehe auch

[MFC extension DLLs (MFC-Erweiterungs-DLLs)](extension-dlls.md)
