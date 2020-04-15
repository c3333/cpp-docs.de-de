---
title: CFormView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373801"
---
# <a name="cformview-class"></a>CFormView-Klasse

Die für Formularansichten verwendete Basisklasse.

## <a name="syntax"></a>Syntax

```
class CFormView : public CScrollView
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Erstellt ein `CFormView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Wird für die Synchronisierung während der Initialisierung verwendet.|

## <a name="remarks"></a>Bemerkungen

Eine Formularansicht ist im Wesentlichen eine Ansicht, die Steuerelemente enthält. Diese Steuerelemente werden basierend auf einer Dialogfeldvorlagenressource angeordnet. Verwenden Sie `CFormView`, wenn Sie Formulare in der Anwendung verwenden möchten. Diese Ansichten unterstützen bei Bedarf das Scrollen mithilfe der [CScrollView-Funktionalität.](../../mfc/reference/cscrollview-class.md)

Wenn Sie [eine formularbasierte Anwendung erstellen,](../../mfc/reference/creating-a-forms-based-mfc-application.md)können Sie `CFormView`ihre Ansichtsklasse auf basieren und sie zu einer formularbasierten Anwendung machen.

Sie können auch neue [Formularthemen](../../mfc/form-views-mfc.md) in dokumentansichtsbasierte Anwendungen einfügen. Auch wenn die Anwendung ursprünglich keine Formulare unterstützte, fügt Visual C++ diese Unterstützung hinzu, wenn Sie ein neues Formular einfügen.

Der MFC-Anwendungs-Assistent und der Befehl "Klasse hinzufügen" sind die bevorzugten Methoden zum Erstellen formularbasierter Anwendungen. Wenn Sie eine formularbasierte Anwendung erstellen müssen, ohne diese Methoden zu verwenden, finden Sie weitere Informationen unter [Erstellen einer formularbasierten Anwendung](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView

Erstellt ein `CFormView`-Objekt.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Enthält eine null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Objekt eines `CFormView`von abgeleiteten Typs erstellen, rufen Sie einen der Konstruktoren auf, um das Ansichtsobjekt zu erstellen und die Dialogfeldressource zu identifizieren, auf der die Ansicht basiert. Sie können die Ressource entweder anhand des Namens (übergeben Sie eine Zeichenfolge als Argument an den Konstruktor) oder anhand ihrer ID (übergeben Sie eine ganzzahlige Datei ohne Vorzeichen als Argument) identifizieren.

Das Formularansichtsfenster und die untergeordneten Steuerelemente werden erst erstellt, wenn `CWnd::Create` sie aufgerufen werden. `CWnd::Create`wird vom Framework als Teil des Dokument- und Ansichtserstellungsprozesses aufgerufen, der von der Dokumentvorlage gesteuert wird.

> [!NOTE]
> Die abgeleitete Klasse *muss* einen eigenen Konstruktor bereitstellen. Rufen Sie im Konstruktor den `CFormView::CFormView`Konstruktor , mit dem Ressourcennamen oder der Ressourcen-ID als Argument auf, wie in der vorherigen Klassenübersicht gezeigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgAbgeschlossen

Von MFC verwendet, um sicherzustellen, dass die Initialisierung abgeschlossen ist, bevor andere Vorgänge ausgeführt werden.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierungsfunktion für diesen Dialog abgeschlossen wurde.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView-Klasse](../../mfc/reference/cscrollview-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView-Klasse](../../mfc/reference/cscrollview-class.md)
