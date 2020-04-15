---
title: CPaintDC-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374773"
---
# <a name="cpaintdc-class"></a>CPaintDC-Klasse

Eine Gerätekontextklasse, die von [CDC](../../mfc/reference/cdc-class.md)abgeleitet wurde.

## <a name="syntax"></a>Syntax

```
class CPaintDC : public CDC
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Erstellt eine `CPaintDC` Verbindung mit dem angegebenen [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Enthält die [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct) die zum Zeichnen des Clientbereichs verwendet wird.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|Die HWND, `CPaintDC` der dieses Objekt zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Es führt eine [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) zur Bauzeit und [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) bei Zerstörungszeit.

Ein `CPaintDC` Objekt kann nur verwendet werden, wenn auf `OnPaint` eine [WM_PAINT](/windows/win32/gdi/wm-paint) Nachricht reagiert wird, in der Regel in der Nachrichtenhandlermemberfunktion.

Weitere Informationen zur `CPaintDC`Verwendung finden Sie unter [Gerätekontexte](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC::CPaintDC

Erstellt ein `CPaintDC` Objekt, bereitet das Anwendungsfenster für das Malen vor und speichert die [PAINTSTRUCT-Struktur](/windows/win32/api/winuser/ns-winuser-paintstruct) in der [M_ps](#m_ps) Membervariable.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigt auf `CWnd` das Objekt, zu dem das `CPaintDC` Objekt gehört.

### <a name="remarks"></a>Bemerkungen

Eine Ausnahme (vom Typ `CResourceException`) wird ausgelöst, wenn der Windows [GetDC-Aufruf](/windows/win32/api/winuser/nf-winuser-getdc) fehlschlägt. Ein Gerätekontext ist möglicherweise nicht verfügbar, wenn Windows bereits alle verfügbaren Gerätekontexte zugewiesen hat. Ihre Anwendung konkurriert mit den fünf gemeinsamen Anzeigekontexten, die zu einem bestimmten Zeitpunkt unter Windows verfügbar sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC::m_hWnd

Die, `HWND` an `CPaintDC` die dieses Objekt angefügt ist.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Bemerkungen

*m_hWnd* ist eine geschützte Variable vom Typ HWND.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC::m_ps

`m_ps`ist eine öffentliche Membervariable vom Typ [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Bemerkungen

Es ist `PAINTSTRUCT` die, die von CWnd übergeben und ausgefüllt [wird::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Der `PAINTSTRUCT` enthält Informationen, die die Anwendung verwendet, um `CPaintDC` den Clientbereich des Fensters zu zeichnen, das einem Objekt zugeordnet ist.

Beachten Sie, dass Sie über das `PAINTSTRUCT`auf das Gerätekontexthandle zugreifen können. Sie können jedoch direkter über die `m_hDC` Membervariable, `CPaintDC` die von CDC erbt, auf das Handle zugreifen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
