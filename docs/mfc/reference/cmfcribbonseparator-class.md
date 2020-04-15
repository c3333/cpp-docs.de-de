---
title: CMFCRibbonSeparator-Klasse
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
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368851"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator-Klasse

Implementiert das Bandtrennzeichen.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Erstellt ein `CMFCRibbonSeparator`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Fügt der **Befehlsliste** im Dialogfeld **Anpassen** ein Trennzeichen hinzu. (Überschreibt [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonSeparator::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|

### <a name="protected-methods"></a>Geschützte Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Eine Kopiermethode, die die Membervariablen eines Trennzeichens von einem anderen Objekt festlegt.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Gibt die Größe eines Trennzeichens zurück.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Gibt an, ob es sich um ein Trennzeichen handelt.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Gibt an, ob es sich um einen Tabstopp handelt.|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Wird vom System aufgerufen, um das Trennzeichen entweder auf der Multifunktionsleiste oder der Quick Access Toolbar zu zeichnen.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Wird vom System aufgerufen, um das Trennzeichen in der **Befehlsliste** zu zeichnen.|

## <a name="remarks"></a>Bemerkungen

Ein Multifunktionsleistentrennzeichen ist eine vertikale oder horizontale Linie, die Bandelemente logisch trennt. Ein Trennzeichen kann auf dem Menübandsteuerelement, dem Hauptanwendungsmenü, der Menüleistenstatusleiste und der Schnellzugriffssymbolleiste gezeichnet werden.

Um ein Trennzeichen in Ihrer Anwendung zu verwenden, erstellen Sie das neue Objekt, und fügen Sie es dem Hauptanwendungsmenü hinzu, wie hier gezeigt:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Rufen Sie [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) auf, um Trennzeichen zu Multifunktionsleistenbedienfeldern hinzuzufügen. Die Trennzeichen werden intern von `AddSeparator` der Methode zugewiesen und hinzugefügt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Fügt der **Befehlsliste** im Dialogfeld **Anpassen** ein Trennzeichen hinzu.

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parameter

*pWndListBox*<br/>
[in] Ein Zeiger auf die **Befehlsliste,** in der das Trennzeichen hinzugefügt wird.

*bDeep*<br/>
[in] Ignoriert.

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index für die Zeichenfolge im Listenfeld, das von *pWndListBox*angegeben wird.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

Erstellt ein `CMFCRibbonSeparator`-Objekt.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parameter

*bIsHoriz*<br/>
[in] Wenn TRUE, ist das Trennzeichen horizontal. wenn FALSE, ist das Trennzeichen vertikal.

### <a name="remarks"></a>Bemerkungen

Horizontale Trennzeichen werden in Anwendungsmenüs verwendet. Vertikale Trennzeichen werden in Symbolleisten verwendet.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCRibbonSeparator` wie ein Objekt der Klasse erstellt wird.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom

Eine Kopiermethode, die die Membervariablen eines Trennzeichens von einem anderen Objekt festlegt.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parameter

*Src*<br/>
[in] Das Quell-Menübandelement, aus dem kopiert werden soll.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize

Gibt die Größe eines Trennzeichens zurück.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Geräteinhalt.

### <a name="return-value"></a>Rückgabewert

Die Größe des Trennzeichens im angegebenen Gerätekontext.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

Gibt an, ob es sich um ein Trennzeichen handelt.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Rückgabewert

Immer TRUE für diese Klasse.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Gibt an, ob es sich um einen Tabstopp handelt.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Rückgabewert

Immer FALSE für diese Klasse.

### <a name="remarks"></a>Bemerkungen

Ein Multifunktionsleistentrennzeichen ist kein Tabstopp.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFCRibbonSeparator::OnDraw

Wird vom System aufgerufen, um das Trennzeichen entweder auf der Multifunktionsleiste oder der Quick Access Toolbar zu zeichnen.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Wird vom System aufgerufen, um das Trennzeichen in der **Befehlsliste** zu zeichnen.

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

|||
|-|-|
|Parameter|Beschreibung|
|*pDC*|[in] Ein Zeiger auf einen Gerätekontext.|
|*strText*|[in] Text, der in der Liste angezeigt wird.|
|*nTextOffset*|[in] Abstand zwischen dem Text und der linken Seite des umgrenzenden Rechtecks.|
|*Rect*|[in] Gibt das umgrenzende Rechteck an.|
|*bIsSelected*|[in] Ignoriert.|
|*bHervorgehoben*|[in] Ignoriert.|

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
