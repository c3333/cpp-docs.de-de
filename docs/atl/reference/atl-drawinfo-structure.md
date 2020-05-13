---
title: ATL_DRAWINFO Struktur
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 00d93b3dd8b060a21b6ff4083bb9880d8d836a19
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168617"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO Struktur

Enthält Informationen, die zum Rendern verschiedener Ziele verwendet werden, z. b. Drucker, Metadateien oder ActiveX-Steuerelemente.

## <a name="syntax"></a>Syntax

```cpp
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>Member

`cbSize`<br/>
Die Größe der-Struktur in Bytes.

`dwDrawAspect`<br/>
Gibt an, wie das Ziel dargestellt werden soll. Darstellungen können Inhalt, ein Symbol, eine Miniaturansicht oder ein gedruckte Dokument enthalten. Eine Liste möglicher Werte finden Sie unter [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) und [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Der Teil des Ziels, der für den Zeichnungs Vorgang von Interesse ist. Die Interpretation variiert abhängig vom Wert im `dwDrawAspect` Element.

`ptd`<br/>
Ein Zeiger auf eine [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) -Struktur, die das Zeichnen von Optimierungen abhängig vom angegebenen Aspekt ermöglicht. Beachten Sie, dass neuere Objekte und Container, die optimierte Zeichnungs Schnittstellen unterstützen, diesen Member ebenfalls unterstützen. Ältere Objekte und Container, die keine optimierten Zeichnungs Schnittstellen unterstützen, geben für diesen Member immer NULL an.

`hicTargetDev`<br/>
Informations Kontext für das Zielgerät, auf das `ptd` von verwiesen wird, von dem das-Objekt gerätemetriken extrahieren und die Funktionen des Geräts testen kann. Wenn `ptd` NULL ist, sollte das Objekt den Wert im `hicTargetDev` Member ignorieren.

`hdcDraw`<br/>
Der Gerätekontext, auf dem gezeichnet werden soll. Bei einem fensterlosen Objekt befindet sich der `hdcDraw` Member im `MM_TEXT` Zuordnungs Modus, dessen logische Koordinaten mit den Client Koordinaten des enthaltenden Fensters übereinstimmen. Außerdem sollte sich der Gerätekontext in demselben Zustand befinden, der normalerweise von einer `WM_PAINT` Nachricht übermittelt wird.

`prcBounds`<br/>
Ein Zeiger auf eine [RECTL](/windows/win32/api/windef/ns-windef-rectl) `hdcDraw` -Struktur, die das Rechteck in angibt, und in dem das Objekt gezeichnet werden soll. Dieser Member steuert die Positionierung und Streckung des Objekts. Dieser Member sollte NULL sein, um ein fensterloses direktes aktives Objekt zu zeichnen. In jeder anderen Situation ist NULL kein gültiger Wert und sollte zu einem `E_INVALIDARG` Fehlercode führen. Wenn der Container einen nicht-NULL-Wert an ein fensterloses Objekt übergibt, sollte das Objekt den angeforderten Aspekt in den angegebenen Gerätekontext und das angegebene Rechteck Rendering. Ein Container kann dies von einem fensterlosen Objekt anfordern, um eine zweite, nicht aktive Ansicht des Objekts zu erzeugen oder das Objekt zu drucken.

`prcWBounds`<br/>
Wenn `hdcDraw` ein Metadatei-Gerätekontext ist (siehe [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) in der Windows SDK), ist dies ein Zeiger auf `RECTL` eine-Struktur, die das umschließende Rechteck in der zugrunde liegenden Metadatei angibt. Die Rechteck Struktur enthält den Fensterblock und den Fenster Ursprung. Diese Werte sind für das Zeichnen von Metadateien nützlich. Das durch `prcBounds` gekennzeichnete Rechteck ist innerhalb dieses `prcWBounds` Rechtecks geschachtelt. Sie befinden sich im selben Koordinaten Bereich.

`bOptimize`<br/>
Ein Wert ungleich 0 (null), wenn das Zeichnen des Steuer Elements optimiert werden soll, andernfalls 0. Wenn die Zeichnung optimiert ist, wird der Zustand des Geräte Kontexts automatisch wieder hergestellt, wenn Sie das Rendering abgeschlossen haben.

`bZoomed`<br/>
Ein Wert ungleich 0 (null), wenn das Ziel einen Zoomfaktor hat, andernfalls 0. Der Zoomfaktor wird in `ZoomNum`gespeichert.

`bRectInHimetric`<br/>
Ungleich 0 (null), `prcBounds` wenn sich die Abmessungen von in HIMETRIC befinden, andernfalls 0.

`ZoomNum`<br/>
Die Breite und Höhe des Rechtecks, in das das Objekt gerendert wird. Der Zoomfaktor entlang der x-Achse (der Anteil der natürlichen Größe des Objekts auf seinen aktuellen Wert) des Ziels ist der Wert von `ZoomNum.cx` dividiert durch den Wert von. `ZoomDen.cx` Der Zoomfaktor entlang der y-Achse wird auf ähnliche Weise erreicht.

`ZoomDen`<br/>
Die tatsächliche Breite und Höhe des Ziels.

## <a name="remarks"></a>Bemerkungen

Die typische Verwendung dieser Struktur wäre das Abrufen von Informationen während des Renderings des Zielobjekts. Beispielsweise können Sie Werte aus ATL_DRAWINFO in der Überladung von [CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)abrufen.

Diese Struktur speichert relevante Informationen, die verwendet werden, um die Darstellung eines Objekts für das Zielgerät darzustellen. Die bereitgestellten Informationen können zum Zeichnen auf den Bildschirm, einen Drucker oder sogar eine Metadatei verwendet werden.

## <a name="requirements"></a>Anforderungen

**Header:** atlctl. h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[IViewObject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase:: OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
