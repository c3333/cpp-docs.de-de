---
title: CMFCImageEditorDialog-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367468"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog-Klasse

Die `CMFCImageEditorDialog` Klasse unterstützt ein Bildeditor-Dialogfeld.

## <a name="syntax"></a>Syntax

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Erstellt ein `CMFCImageEditorDialog`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCImageEditorDialog` Klasse stellt ein Dialogfeld bereit, das Folgendes enthält:

- Ein Bildbereich, den Sie zum Ändern einzelner Pixel in einem Bild verwenden.

- Zeichenwerkzeuge, um die Pixel im Bildbereich zu ändern.

- Eine Farbpalette, um die Farbe anzugeben, die von den Zeichenwerkzeugen verwendet wird.

- Ein Vorschaubereich, der den Effekt Ihrer Bearbeitung anzeigt.

Die folgende Abbildung zeigt ein Dialogfeld für den Bildeditor.

![CMFCImageEditorDialog-Dialogfeld](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog-Dialogfeld")

Eine Möglichkeit, `CMFCImageEditorDialog` ein Objekt zu `CBitmap` verwenden, besteht darin, ein zu bearbeitendes Bild zu übergeben. Erstellen Sie kein großes Bild, da der Bildbearbeitungsbereich eine begrenzte Größe aufweist und die logische Pixelgröße an den Bereich angepasst wird. Rufen `DoModal` Sie die Methode auf, um ein modales Dialogfeld zu starten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afximageeditordialog.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog

Erstellt ein `CMFCImageEditorDialog`-Objekt.

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>Parameter

*pBitmap*<br/>
Zeiger auf ein Bild.

*pParent*<br/>
Zeigen Sie mit dem Zeiger auf das übergeordnete Fenster des aktuellen Bildeditor-Dialogfelds.

*nBitsPixel*<br/>
Die Anzahl der Bits, die verwendet werden, um die Farbe eines einzelnen Pixels darzustellen, was auch als Farbtiefe bezeichnet wird.  Wenn der *nBitsPixel-Parameter* -1 ist, wird die Farbtiefe aus dem Bild abgeleitet, das durch den Parameter *pBitmap* angegeben wird. Der Standardwert ist -1.

### <a name="return-value"></a>Rückgabewert

Um ein Bild zu ändern, übergeben `CMFCImageEditorDialog` Sie einen Bildzeiger an den Konstruktor. Rufen Sie `DoModal` dann die Methode auf, um ein modales Dialogfeld zu öffnen. Wenn `DoModal` die Methode zurückgegeben wird, enthält die Bitmap das neue Bild.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCImageEditorDialog` wie ein Objekt der Klasse erstellt wird. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)
