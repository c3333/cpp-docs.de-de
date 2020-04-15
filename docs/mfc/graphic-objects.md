---
title: Grafikobjekte
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 0201e53114b71c02877762f89cc65fc46d17700c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370530"
---
# <a name="graphic-objects"></a>Grafikobjekte

Windows bietet eine Reihe von Zeichentools an, die in Gerätekontexten verwendet werden können. Es bietet Stifte zum Zeichnen von Linien, Pinsel zum Auffüllen von Innenbereichen und Schriftarten zum Zeichnen von Text. MFC stellt Grafikobjektklassen bereit, die den Zeichentools in Windows ähneln. In der folgenden Tabelle werden die verfügbaren Klassen und die entsprechenden Windows-GDI-Handletypen (Graphics Device Interface) gezeigt.

> [!NOTE]
> Weitere Informationen finden Sie in der [GDI+ SDK-Dokumentation](/windows/win32/gdiplus/-gdiplus-gdi-start).

Dieser Artikel beschreibt die Verwendung von diesen Grafikobjektklassen:

### <a name="classes-for-windows-gdi-objects"></a>Klassen für Windows-GDI-Objekte

|Klasse|Windows-Handletypen|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> Die Klasse [CImage](../atl-mfc-shared/reference/cimage-class.md) bietet erweiterte Bitmap-Unterstützung.

Jede Grafikobjektklasse in der Klassenbibliothek verfügt über einen Konstruktor, mit dem Sie grafische Objekte dieser Klasse erstellen können. Diese müssen Sie anschließend mit der entsprechenden „create“-Funktion wie `CreatePen` initialisieren.

Jede Grafikobjektklasse in der Klassenbibliothek verfügt über einen „cast“-Operator, der ein MFC-Objekt zum zugehörigen Windows-Handle umwandelt. Das resultierende Handle ist gültig, bis das zugeordnete Objekt es trennt. Verwenden Sie die `Detach` Memberfunktion des Objekts, um das Handle zu trennen.

Im folgenden Code wird ein `CPen`-Objekt zu einem Windows-Handle umgewandelt:

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>So erstellen Sie ein Grafikobjekt in einem Gerätekontext

1. Definieren Sie ein Grafikobjekt im Stapelrahmen. Initialisieren Sie das Objekt mit der „type“-spezifischen „create“-Funktion wie `CreatePen`. Initialisieren Sie alternativ das Objekt im Konstruktor. Sehen Sie sich die Diskussion über [die ein- und zweistufige Erstellung an,](../mfc/one-stage-and-two-stage-construction-of-objects.md)die Beispielcode enthält.

1. [Wählen Sie das Objekt im aktuellen Gerätekontext](../mfc/selecting-a-graphic-object-into-a-device-context.md)aus, und speichern Sie das alte Grafikobjekt, das zuvor ausgewählt wurde.

1. Wenn Sie mit dem aktuellen Grafikobjekt fertig sind, wählen Sie das alte Grafikobjekt zurück im Gerätekontext aus, um dessen Status wiederherzustellen.

1. Ermöglichen Sie dem „frame“-zugewiesenen Grafikobjekt, automatisch gelöscht zu werden, wenn der Bereich verlassen wird.

> [!NOTE]
> Wenn Sie ein Grafikobjekt wiederholt verwenden, können Sie es einmal zuordnen und es im Gerätekontext auswählen, sobald es benötigt wird. Stellen Sie sicher, ein derartiges Objekt zu löschen, wenn Sie es nicht mehr benötigen.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Ein- und zweistufige Konstruktion von Grafikobjekten](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Beispiel für das Erstellen eines Stifts in einer oder zwei Phasen](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Auswählen eines Grafikobjekts für einen Gerätekontext](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Gerätekontexte](../mfc/device-contexts.md)

## <a name="see-also"></a>Siehe auch

[Fensterobjekte](../mfc/window-objects.md)
