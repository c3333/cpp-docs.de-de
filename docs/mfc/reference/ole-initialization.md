---
title: OLE-Initialisierung
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373033"
---
# <a name="ole-initialization"></a>OLE-Initialisierung

Bevor eine Anwendung OLE-Systemdienste verwenden kann, muss sie die OLE-System-DLLs initialisieren und überprüfen, ob die DLLs die richtige Version sind. Die `AfxOleInit` Funktion initialisiert die OLE-System-DLLs.

### <a name="ole-initialization"></a>OLE-Initialisierung

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Initialisiert die OLE-Bibliotheken.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Rufen Sie diese Funktion in `InitInstance` der Funktion des Anwendungsobjekts auf, um die Unterstützung für die Eindämmung von OLE-Steuerelementen zu aktivieren.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

Rufen Sie diese Funktion in `InitInstance` der Funktion des Anwendungsobjekts auf, um die Unterstützung für die Eindämmung von OLE-Steuerelementen zu aktivieren.

### <a name="syntax"></a>Syntax

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu OLE-Steuerelementen (jetzt als ActiveX-Steuerelemente bezeichnet) finden Sie unter [ActiveX Control Topics](../mfc-activex-controls.md).

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit

Initialisiert die OLE-Unterstützung für die Anwendung.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Rückgabewert

Ist nicht 0 (Null), wenn erfolgreich, und 0, wenn die Initialisierung fehlschlägt, weil möglicherweise falsche Versionen der OLE-Systeme-DLLs installiert sind.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die OLE-Unterstützung für eine MFC-Anwendung zu initialisieren. Wenn diese Funktion aufgerufen wird, werden folgende Aktionen ausgeführt:

- Initialisiert die COM-Bibliothek für das aktuelle Apartment des aufrufenden Anwendung. Weitere Informationen finden Sie unter [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Erstellt ein Nachrichtenfilterobjekt, das die [IMessageFilter-Schnittstelle](/windows/win32/api/objidl/nn-objidl-imessagefilter) implementiert. Auf diesen Nachrichtenfilter kann mit einem Aufruf von [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)zugegriffen werden.

> [!NOTE]
> Wenn **AfxOleInit** von einer MFC-DLL aufgerufen wird, schlägt der Aufruf fehl. Der Fehler tritt auf, weil die Funktion davon ausgeht, dass das OLE-System zuvor von der aufrufenden Anwendung initialisiert wurde, wenn sie von einer DLL aufgerufen wird.

> [!NOTE]
> MFC-Anwendungen müssen als Singlethread-Apartment (STA) initialisiert werden. Wenn Sie [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) `InitInstance` in Ihrer Außerkraftsetzung aufrufen, geben Sie COINIT_APARTMENTTHREADED (anstelle COINIT_MULTITHREADED) an.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
