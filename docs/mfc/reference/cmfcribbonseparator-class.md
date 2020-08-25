---
title: CMF cribbonseparator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: f435dc5ae8821a6d5626af2f93710a1672fd374c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831800"
---
# <a name="cmfcribbonseparator-class"></a>CMF cribbonseparator-Klasse

Implementiert das Menüband Trennzeichen.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|[CMF cribbonseparator:: CMF cribbonseparator](#cmfcribbonseparator)|Erstellt ein `CMFCRibbonSeparator`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfcribbonseparator:: AddTo ListBox](#addtolistbox)|Fügt der Liste **Befehle** im Dialogfeld **Anpassen** ein Trennzeichen hinzu. (Überschreibt [cmfcribbonbaseelement:: addtlistbox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonSeparator::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Objekt abzurufen, das diesem Klassentyp zugeordnet ist.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|-|-|
|[CMF cribbonseparator:: CopyFrom](#copyfrom)|Eine Kopiermethode, mit der die Element Variablen eines Trenn Zeichens von einem anderen Objekt festgelegt werden.|
|[CMF cribbonseparator:: getregularsize](#getregularsize)|Gibt die Größe eines Trenn Zeichens zurück.|
|[CMF cribbonseparator:: IsSeparator](#isseparator)|Gibt an, ob dies ein Trennzeichen ist.|
|[CMF cribbonseparator:: istabstopp](#istabstop)|Gibt an, ob es sich um einen Tabstopp handelt.|
|[CMF cribbonseparator:: OnDraw](#ondraw)|Wird vom System aufgerufen, um das Trennzeichen auf dem Menüband oder der Symbolleiste für den schnell Zugriff zu zeichnen.|
|[CMF cribbonseparator:: ondrawonlist](#ondrawonlist)|Wird vom System aufgerufen, um das Trennzeichen in der Liste der **Befehle** zu zeichnen.|

## <a name="remarks"></a>Bemerkungen

Ein Menüband-Trennzeichen ist eine vertikale oder horizontale Linie, die Menü Band Elemente logisch trennt. Ein Trennzeichen kann auf dem Menüband-Steuerelement, dem Hauptmenü der Anwendung, der Multifunktionsleisten-Statusleiste und der Symbolleiste für den schnell Zugriff gezeichnet werden.

Wenn Sie ein Trennzeichen in Ihrer Anwendung verwenden möchten, erstellen Sie das neue-Objekt, und fügen Sie es wie im folgenden gezeigt zum Hauptmenü der Anwendung hinzu:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Wenden Sie [CMFCRibbonPanel:: addSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) an, um den Menü Band Bereichen Trennzeichen hinzuzufügen. Die Trennzeichen werden zugeordnet und intern von der- `AddSeparator` Methode hinzugefügt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMF cribbonseparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a> Cmfcribbonseparator:: AddTo ListBox

Fügt der Liste **Befehle** im Dialogfeld **Anpassen** ein Trennzeichen hinzu.

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parameter

*pwndlistbox*<br/>
in Ein Zeiger auf die **Befehls** Liste, in der das Trennzeichen hinzugefügt wird.

*bdeep*<br/>
in Erten.

### <a name="return-value"></a>Rückgabewert

NULL basierter Index der Zeichenfolge im Listenfeld, das von *pwndlistbox*angegeben wird.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a> CMF cribbonseparator:: CMF cribbonseparator

Erstellt ein `CMFCRibbonSeparator`-Objekt.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parameter

*bishoriz*<br/>
in TRUE gibt an, dass das Trennzeichen horizontal ist. FALSE gibt an, dass das Trennzeichen vertikal ist.

### <a name="remarks"></a>Bemerkungen

Horizontale Trennzeichen werden in Anwendungs Menüs verwendet. Vertikale Trennzeichen werden in Symbolleisten verwendet.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt der- `CMFCRibbonSeparator` Klasse erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a> CMF cribbonseparator:: CopyFrom

Eine Kopiermethode, mit der die Element Variablen eines Trenn Zeichens von einem anderen Objekt festgelegt werden.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parameter

*Src*<br/>
in Das quellribbon-Element, aus dem kopiert werden soll.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a> CMF cribbonseparator:: getregularsize

Gibt die Größe eines Trenn Zeichens zurück.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Geräte Inhalt.

### <a name="return-value"></a>Rückgabewert

Die Größe des Trenn Zeichens im angegebenen Gerätekontext.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a> CMF cribbonseparator:: IsSeparator

Gibt an, ob dies ein Trennzeichen ist.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Rückgabewert

Immer true für diese Klasse.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a> CMF cribbonseparator:: istabstopp

Gibt an, ob es sich um einen Tabstopp handelt.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Rückgabewert

Immer false für diese Klasse.

### <a name="remarks"></a>Bemerkungen

Ein Menüband-Trennzeichen ist kein Tabstopp.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a> CMF cribbonseparator:: OnDraw

Wird vom System aufgerufen, um das Trennzeichen auf dem Menüband oder der Symbolleiste für den schnell Zugriff zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a> CMF cribbonseparator:: ondrawonlist

Wird vom System aufgerufen, um das Trennzeichen in der Liste der **Befehle** zu zeichnen.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parameter

*PDC*\
in Ein Zeiger auf einen Gerätekontext.

*Text*\
in Der in der Liste angezeigte Text.

*ntexumffset*\
in Abstand zwischen dem Text und der linken Seite des umgebenden Rechtecks.

*Rect*\
in Gibt das umgebende Rechteck an.

*bissgewählt*\
in Erten.

*bhervor gehoben*\
in Erten.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
