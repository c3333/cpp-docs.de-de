---
title: CSmartDockingInfo-Klasse
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: c0ccb9f728add37230cbfd88cc8f6c9b1696fa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318229"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo-Klasse

Definiert die Darstellung von intelligenten Andockmarkern.

## <a name="syntax"></a>Syntax

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSmartDockingInfo::CopyTo](#copyto)|Kopiert die aktuellen Smart Docking-Infoparameter in das bereitgestellte [CSmartDockingInfo-Objekt.](../../mfc/reference/csmartdockinginfo-class.md)|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Gibt an, ob die aktuelle Designfarbe verwendet werden soll, wenn das Framework intelligente Andockmarkierungen anzeigt.|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Gibt die Grundhintergrundfarbe von intelligenten Docking-Markern an.|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Gibt die Farbe an, die in Smart Docking-Marker-Bitmaps ersetzt wird. `m_clrToneSrc`|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Gibt die Farbe der Smart Docking-Marker-Bitmaps an.|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Gibt die Farbe der Smart Docking-Marker-Bitmaps an, wenn sie transparent sind.|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Gibt den Offset der zentralen Gruppe von intelligenten Andockmarkierungen aus den Grenzen des zentralen Gruppenrechtecks an.|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Gibt die Gesamtgröße aller Intelligentandockmarkierungen in einer Gruppe an.|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Definiert die Ressourcen-IDs der Bitmaps, die das Framework für smarte Andockmarkierungen verwendet, die nicht hervorgehoben sind.|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Definiert die Ressourcen-IDs der Bitmaps, die das Framework für hervorgehobene intelligente Andockmarkierungen verwendet.|

## <a name="remarks"></a>Bemerkungen

Das Framework verarbeitet smart docking-Marker intern. Die folgende Abbildung zeigt die standardmäßigen Smart Docking-Marker:

![Standardmarker für intelligentes Andocken](../../mfc/reference/media/nextsdmarkers.png "Standardmarker für intelligentes Andocken")

In dieser Abbildung zeigt das Bild auf der linken Seite eine intelligente Andockmarkierung für eine zentrale Gruppe, für die kein Andocken an eine Registerkarte aktiviert ist. Das Bild in der Mitte zeigt eine intelligente Andockmarkierung am rechten Rand. Das Bild auf der rechten Seite zeigt eine intelligente Andockmarkierung für eine zentrale Gruppe, die an eine Registerkarte angedockt ist. Die Smart Docking-Markierung der zentralen Gruppe verfügt über eine Hauptbitmap und fünf Smart Docking-Marker-Bitmaps.

Sie können die folgenden Parameter von Smart Docking-Markern anpassen:

- Farbe Sie können z. B. die blaue Farbe der Markierungen in der Abbildung durch eine beliebige benutzerdefinierte Farbe ersetzen.

- Transparenzfarbe.

- Versatz einer intelligenten Andockmarkierung in der zentralen Gruppe vom Rand des umgebenden Rechtecks.

- Die Hauptbitmap, die die zentrale Gruppe darstellt.

- Die Bitmaps, die die regulären und hervorgehobenen Smart Docking-Marker darstellen.

Die folgende Abbildung zeigt ein Beispiel für smarte Docking-Marker, die angepasst wurden:

![Benutzerdefinierte Marker für intelligentes Andocken](../../mfc/reference/media/nextsdmarkerscustom.png "Benutzerdefinierte Marker für intelligentes Andocken")

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDockingInfo::CopyTo

Kopiert die aktuellen Smart Docking-Parameter in das bereitgestellte [CSmartDockingInfo-Objekt.](../../mfc/reference/csmartdockinginfo-class.md)

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parameter

*params*<br/>
[out] Ein Objekt `CSmartDockingInfo` des Typs, das mit den aktuellen Smart Docking-Parametern aufgefüllt wird.

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDockingInfo::m_bUseThemeColorInShading

Gibt an, ob die aktuelle Designfarbe verwendet werden soll, wenn das Framework intelligente Andockmarkierungen anzeigt.

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, werden die Marker mit der aktuellen Designfarbe gezeichnet. Andernfalls werden die Markierungen mit einer hellblauen Farbe gezeichnet.

Der Standardwert ist FALSE.

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDockingInfo::m_clrBaseBackground

Gibt die Grundhintergrundfarbe von intelligenten Docking-Markern an.

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDockingInfo::m_clrToneDest

Gibt die Farbe an, die in Smart Docking-Marker-Bitmaps ersetzt `m_clrToneSrc` wird.

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Wert fest, um die Farbe von Markerbitmaps programmgesteuert zu ändern. Wenn Sie beispielsweise die Farbe der mit dem Framework bereitgestellten Standardmarkierungen ändern möchten, legen Sie diesen Wert auf die gewünschte Farbe fest. Standardmäßig ist [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) auf RGB (61, 123, 241) (eine bläuliche Farbe) eingestellt.

Um die Farbe benutzerdefinierter Marker zu `m_clrToneDest` `m_clrToneSrc`ändern, müssen Sie sowohl als auch angeben.

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDockingInfo::m_clrToneSrc

Gibt die Farbe der Smart Docking-Marker-Bitmaps an.

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Wert nur fest, wenn Sie die Farbe einer benutzerdefinierten Bitmap durch eine andere Farbe ersetzen möchten. Sie müssen diesen Wert nicht festlegen, wenn Sie die Farbe eines Standardmarkers (Framework s) ändern.

Verwenden `(COLORREF)-1` Sie diese Datei, um ein Mitglied der Smart Docking-Gruppe leer zu lassen.

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDockingInfo::m_clrTransparent

Gibt die Farbe der Smart Docking-Marker-Bitmaps an, wenn sie transparent sind.

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Bemerkungen

Sie müssen diesen Wert festlegen, wenn Sie benutzerdefinierte Marker und benutzerdefinierte Bitmaps in der Andockgruppe anzeigen.

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDockingInfo::m_nCentralGroupOffset

Gibt den Offset zwischen der zentralen Gruppe von intelligenten Andockmarkierungen und den Grenzen des zentralen Gruppenrechtecks an.

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Bemerkungen

Geben Sie diesen Wert an, wenn Sie den Standardversatz zwischen benutzerdefinierten Markern und den Grenzen der zentralen Gruppe von Intelligentandockmarkierungen ändern möchten. Der Standardoffset beträgt 5 Pixel.

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDockingInfo::m_sizeTotal

Gibt die Gesamtgröße eines umschließenden Rechtecks an, das alle intelligenten Andockmarkierungen in der zentralen Gruppe umschließt.

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Bemerkungen

Legen `m_sizeTotal` Sie die Größe des umgrenzenden Rechtecks der zentralen Gruppenmarkierung fest. Sie müssen diesen Wert angeben, wenn Sie benutzerdefinierte Bitmaps für Marker verwenden.

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDockingInfo::m_uiMarkerBmpResID

Definiert die Ressourcen-IDs der Bitmaps, die für nicht hervorgehobene benutzerdefinierte intelligente Andockmarkierungen verwendet werden.

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Bemerkungen

Füllen Sie dieses Array mit den Ressourcen-IDs der Bitmaps, die die intelligenten Andockmarkierungen darstellen. AFX_SD_MARKERS_NUM ist derzeit als 5 definiert. Sie füllen das Array wie folgt:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDockingInfo::m_uiMarkerLightBmpResID

Definiert die Ressourcen-IDs der Bitmaps, die für hervorgehobene benutzerdefinierte intelligente Andockmarkierungen verwendet werden.

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Bemerkungen

Füllen Sie dieses Array mit den Ressourcen-IDs der Bitmaps, die die hervorgehobenen Intelligentandockmarkierungen darstellen. AFX_SD_MARKERS_NUM ist derzeit als 5 definiert. Sie füllen das Array wie folgt:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
