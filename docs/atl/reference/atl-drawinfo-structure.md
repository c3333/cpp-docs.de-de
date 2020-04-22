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
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748808"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO Struktur

Enthält Informationen, die zum Rendern auf verschiedenen Zielen verwendet werden, z. B. einem Drucker, einer Metadatei oder einem ActiveX-Steuerelement.

## <a name="syntax"></a>Syntax

```
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
Die Größe der Struktur in Bytes.

`dwDrawAspect`<br/>
Gibt an, wie das Ziel dargestellt werden soll. Darstellungen können Inhalt, ein Symbol, eine Miniaturansicht oder ein gedrucktes Dokument enthalten. Eine Liste möglicher Werte finden Sie unter [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) und [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Teil des Ziels, der für den Ziehungsvorgang von Interesse ist. Seine Interpretation hängt vom Wert `dwDrawAspect` des Elements ab.

`ptd`<br/>
Zeiger auf eine [DVTARGETDEVICE-Struktur,](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) die Zeichnungsoptimierungen je nach angegebenem Aspekt ermöglicht. Beachten Sie, dass neuere Objekte und Container, die optimierte Zeichnungsschnittstellen unterstützen, auch dieses Member unterstützen. Ältere Objekte und Container, die optimierte Zeichnungsschnittstellen nicht unterstützen, geben immer NULL für diesen Member an.

`hicTargetDev`<br/>
Informationskontext für das Zielgerät, auf `ptd` das das Objekt Gerätemetriken extrahieren und die Gerätefunktionen testen kann. Wenn `ptd` NULL ist, sollte das Objekt `hicTargetDev` den Wert im Member ignorieren.

`hdcDraw`<br/>
Der Gerätekontext, auf den gezeichnet werden soll. Bei einem fensterlosen `hdcDraw` Objekt befindet `MM_TEXT` sich das Element im Zuordnungsmodus mit seinen logischen Koordinaten, die den Clientkoordinaten des enthaltenden Fensters entsprechen. Darüber hinaus sollte sich der Gerätekontext im gleichen Zustand `WM_PAINT` befinden wie der, der normalerweise von einer Nachricht übergeben wird.

`prcBounds`<br/>
Zeiger auf eine [RECTL-Struktur,](/windows/win32/api/windef/ns-windef-rectl) `hdcDraw` die das Rechteck angibt und in dem das Objekt gezeichnet werden soll. Dieses Element steuert die Positionierung und Dehnung des Objekts. Dieser Member sollte NULL sein, um ein fensterloses aktives Objekt zu zeichnen. In jeder anderen Situation ist NULL kein rechtlicher `E_INVALIDARG` Wert und sollte zu einem Fehlercode führen. Wenn der Container einen Nicht-NULL-Wert an ein fensterloses Objekt übergibt, sollte das Objekt den angeforderten Aspekt in den angegebenen Gerätekontext und das angegebene Rechteck rendern. Ein Container kann dies von einem fensterlosen Objekt anfordern, um eine zweite, nicht aktive Ansicht des Objekts zu rendern oder das Objekt zu drucken.

`prcWBounds`<br/>
Wenn `hdcDraw` es sich um einen Metadateigerätekontext handelt (siehe [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) im `RECTL` Windows SDK), ist dies ein Zeiger auf eine Struktur, die das umgrenzende Rechteck in der zugrunde liegenden Metadatei angibt. Die Rechteckstruktur enthält die Fensterausdehnung und den Fensterursprung. Diese Werte sind nützlich zum Zeichnen von Metadateien. Das durch `prcBounds` angezeigte Rechteck `prcWBounds` ist in diesem Rechteck verschachtelt. sie befinden sich im gleichen Koordinatenraum.

`bOptimize`<br/>
Ein Wert ungleich Null, wenn die Zeichnung des Steuerelements optimiert werden soll, andernfalls 0. Wenn die Zeichnung optimiert ist, wird der Status des Gerätekontexts automatisch wiederhergestellt, wenn Sie das Rendern abgeschlossen haben.

`bZoomed`<br/>
Ein Wert ungleich Null, wenn das Ziel einen Zoomfaktor hat, andernfalls 0. Der Zoomfaktor wird `ZoomNum`in gespeichert.

`bRectInHimetric`<br/>
Ein Wert ungleich `prcBounds` Null, wenn die Dimensionen von in HIMETRIC, andernfalls 0 sind.

`ZoomNum`<br/>
Die Breite und Höhe des Rechtecks, in das das Objekt gerendert wird. Der Zoomfaktor entlang der x-Achse (der Anteil der natürlichen Größe des Objekts an `ZoomNum.cx` seiner aktuellen `ZoomDen.cx`Ausdehnung) des Ziels ist der Wert von dividiert durch den Wert von . Der Zoomfaktor entlang der y-Achse wird auf ähnliche Weise erreicht.

`ZoomDen`<br/>
Die tatsächliche Breite und Höhe des Ziels.

## <a name="remarks"></a>Bemerkungen

Typische Verwendung dieser Struktur wäre das Abrufen von Informationen während des Renderns des Zielobjekts. Sie können z. B. Werte aus ATL_DRAWINFO innerhalb Ihrer Überladung von [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)abrufen.

In dieser Struktur werden relevante Informationen gespeichert, die zum Rendern der Darstellung eines Objekts für das Zielgerät verwendet werden. Die bereitgestellten Informationen können beim Zeichnen auf dem Bildschirm, einem Drucker oder sogar einer Metadatei verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlctl.h

## <a name="see-also"></a>Weitere Informationen

[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
