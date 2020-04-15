---
title: CMFCToolBarFontSizeComboBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 09811b14ed805b1965015a32a25c0b67c947ff4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358306"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox-Klasse

Eine Symbolleistenschaltfläche, die ein Kombinationsfeldsteuerelement enthält, mit dem der Benutzer eine Schriftgröße auswählen kann.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Erstellt ein `CMFCToolBarFontSizeComboBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Gibt die ausgewählte Schriftgröße in Twips zurück.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Füllt die Kombinationsfeldliste mit allen unterstützten Schriftgrößen für eine angegebene Schriftart.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Legt die Schriftgröße in Twips fest.|

## <a name="remarks"></a>Bemerkungen

Sie können `CMFCToolBarFontSizeComboBox` ein Objekt zusammen mit einem [CMFCToolBarFontComboBox-Klassenobjekt](../../mfc/reference/cmfctoolbarfontcombobox-class.md) verwenden, um es einem Benutzer zu ermöglichen, eine Schriftart und Schriftgröße auszuwählen.

Sie können einer Symbolleiste eine Kombinationsschaltfläche für Schriftgröße hinzufügen, genau wie Sie eine Schriftkombinationsfeldschaltfläche hinzufügen. Weitere Informationen finden Sie unter [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Wenn der Benutzer eine neue `CMFCToolBarFontComboBox` Schriftart in einem Objekt auswählt, können Sie das Kombinationsfeld Schriftgröße mit den unterstützten Größen für diese Schriftart füllen, indem Sie die [CMFCToolBarFontSizeComboBox::RebuildFontSizes-Methode verwenden.](#rebuildfontsizes)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCToolBarFontSizeComboBox` wie verschiedene `CMFCToolBarFontSizeComboBox` Methoden in der Klasse zum Konfigurieren eines Objekts verwendet werden. Das Beispiel veranschaulicht, wie Sie die Schriftgröße in twips aus dem Textfeld abrufen, das Kombinationsfeld Schriftgröße mit allen gültigen Größen der angegebenen Schriftart füllen und die Schriftgröße in Twips angeben. Dieser Codeausschnitt ist Teil des [WordPad-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Erstellt ein `CMFCToolBarFontSizeComboBox`-Objekt.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize

Ruft die Schriftgröße in Twips aus dem Textfeld eines Kombinationsfelds für die Schriftgröße ab.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert positiv ist, ist es die Schriftgröße in twips. Es ist -1, wenn das Textfeld des Kombinationsfelds leer ist. Es ist -2, wenn ein Fehler auftritt.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes

Füllt ein Kombinationsfeld für schriftgröße mit allen gültigen Größen der angegebenen Schriftart.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parameter

*strFontName*<br/>
[in] Gibt einen Schriftartnamen an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, wenn Sie zwischen der Auswahl in einem Schriftkombinationsfeld und einem Kombinationsfeld für die Schriftgröße synchronisieren möchten, z. B. einer [CMFCToolBarFontComboBox-Klasse](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize

Rundet die angegebene Größe (in Twips) in Punkten auf die nächste Größe und legt dann die ausgewählte Größe im Kombinationsfeld auf diesen Wert fest.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
[in] Gibt die festzulegende Schriftgröße (in Twips) an.

### <a name="remarks"></a>Bemerkungen

Sie können die vorherige gültige Schriftgröße später abrufen, indem Sie die [CMFCToolBarFontSizeComboBox::GetTwipSize-Methode](#gettwipsize) aufrufen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton-Klasse](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton-Klasse](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo-Klasse](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
