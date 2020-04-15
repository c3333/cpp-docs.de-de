---
title: CWindowDC-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371978"
---
# <a name="cwindowdc-class"></a>CWindowDC-Klasse

Abgeleitet von `CDC`.

## <a name="syntax"></a>Syntax

```
class CWindowDC : public CDC
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Erstellt ein `CWindowDC`-Objekt.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|Die HWND, `CWindowDC` an die dies angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Ruft die Windows-Funktion [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)zur Konstruktionszeit und [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) zur Zerstörungszeit auf. Dies bedeutet, dass ein `CWindowDC` Objekt auf den gesamten Bildschirmbereich eines [CWnd](../../mfc/reference/cwnd-class.md) (sowohl Client- als auch Nichtclientbereiche) zugreift.

Weitere Informationen zur `CWindowDC`Verwendung finden Sie unter [Gerätekontexte](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Anforderungen

Header: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC::CWindowDC

Erstellt ein `CWindowDC` Objekt, das auf den gesamten Bildschirmbereich (sowohl `CWnd` Client als auch Nichtclient) des Objekts zugreift, auf das *pWnd*zeigt.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Das Fenster, auf dessen Clientbereich das Device-Context-Objekt zugreift.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor ruft die Windows-Funktion [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)auf.

Eine Ausnahme (vom Typ `CResourceException`) `GetWindowDC` wird ausgelöst, wenn der Windows-Aufruf fehlschlägt. Ein Gerätekontext ist möglicherweise nicht verfügbar, wenn Windows bereits alle verfügbaren Gerätekontexte zugewiesen hat. Ihre Anwendung konkurriert mit den fünf gemeinsamen Anzeigekontexten, die zu einem bestimmten Zeitpunkt unter Windows verfügbar sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC::m_hWnd

Der HWND `CWnd` des Zeigers wird `CWindowDC` verwendet, um das Objekt zu erstellen.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Bemerkungen

`m_hWnd`ist eine geschützte Variable vom Typ HWND.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Siehe auch

[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)
