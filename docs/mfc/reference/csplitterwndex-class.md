---
title: CSplitterWndEx-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363921"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx-Klasse

Stellt ein benutzerdefiniertes unterteiltes Fenster dar.

## <a name="syntax"></a>Syntax

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Der Standardkonstruktor.|
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Wird vom Framework aufgerufen, um ein Splitterfenster zu zeichnen. (Überschreibt [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Bemerkungen

Überschreiben `OnDrawSplitter` Sie die Methode, um die Darstellung der grafischen Komponenten eines Splitterfensters anzupassen.

Die `CSplitterWndEx` Klasse wird zusammen mit den Methoden [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)und [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) verwendet, die von einem visuellen Manager implementiert werden. Um zu bewirken, dass ein visueller Manager ein `CSplitterWnd` Splitterfenster `CSplitterWndEx` in der Anwendung zeichnet, ersetzen Sie Deklarationen der Klasse durch die Klasse. Bei Framefensteranwendungen wird die Splitterfensterklasse in der CMainFrame-Klasse in mainfrm.h deklariert. Ein Beispiel finden `OutlookDemo` Sie im Beispiel im Verzeichnis Samples.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter

Wird vom Framework aufgerufen, um ein Splitterfenster zu zeichnen.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf den Gerätekontext. Wenn dieser Parameter NULL ist, zeichnet das Framework das aktive Fenster neu.

*nType*<br/>
[in] Einer der `CSplitterWnd::ESplitType` Enumerationswerte, der das zu zeichnende Splitterfensterelement angibt. Gültige Werte sind `splitBox`, `splitBar`, `splitIntersection` und `splitBorder`.

*Rect*<br/>
[in] Ein umgrenzendes Rechteck, das die Bemaßungen und die Position zum Zeichnen des angegebenen Splitterfensterelements angibt.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../hierarchy-chart.md)<br/>
[Klassen](mfc-classes.md)<br/>
[CSplitterWnd-Klasse](csplitterwnd-class.md)<br/>
[CMFCVisualManager-Klasse](cmfcvisualmanager-class.md)
