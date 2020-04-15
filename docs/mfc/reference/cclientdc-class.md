---
title: CClientDC-Klasse
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352298"
---
# <a name="cclientdc-class"></a>CClientDC-Klasse

Kümmert sich um den Aufruf der Windows-Funktionen [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) zur Konstruktionszeit und [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) zur Zerstörungszeit.

## <a name="syntax"></a>Syntax

```
class CClientDC : public CDC
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Erstellt ein `CClientDC` Objekt, `CWnd`das mit der verbunden ist.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|Die HWND des Fensters, für das dies `CClientDC` gültig ist.|

## <a name="remarks"></a>Bemerkungen

Dies bedeutet, dass der `CClientDC` Gerätekontext, der einem Objekt zugeordnet ist, der Clientbereich eines Fensters ist.

Weitere Informationen `CClientDC`zu finden Sie unter [Gerätekontexte](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC

Erstellt ein `CClientDC` Objekt, auf das der Clientbereich des [CWnd](../../mfc/reference/cwnd-class.md) von *pWnd*angezeigt wird.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fenster, auf dessen Clientbereich das Gerätekontextobjekt zugreift.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor ruft die Windows-Funktion [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)auf.

Eine Ausnahme (vom Typ `CResourceException`) `GetDC` wird ausgelöst, wenn der Windows-Aufruf fehlschlägt. Ein Gerätekontext ist möglicherweise nicht verfügbar, wenn Windows bereits alle verfügbaren Gerätekontexte zugewiesen hat. Ihre Anwendung konkurriert mit den fünf gemeinsamen Anzeigekontexten, die zu einem bestimmten Zeitpunkt unter Windows verfügbar sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd

Der `HWND` Zeiger, der `CWnd` zum `CClientDC` Erstellen des Objekts verwendet wird.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Bemerkungen

*m_hWnd* ist eine geschützte Variable.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)
