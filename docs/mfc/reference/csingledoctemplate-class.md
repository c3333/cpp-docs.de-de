---
title: CSingleDocTemplate-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318347"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate-Klasse

Definiert eine Dokumentvorlage, welche die Single Document Interface (SDI) implementiert.

## <a name="syntax"></a>Syntax

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Erstellt ein `CSingleDocTemplate`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Eine SDI-Anwendung verwendet das Hauptrahmenfenster, um ein Dokument anzuzeigen. es kann jeweils nur ein Dokument geöffnet sein.

Eine Dokumentvorlage definiert die Beziehung zwischen drei Klassentypen:

- Eine Dokumentklasse, von der `CDocument`Sie ableiten.

- Eine Ansichtsklasse, die Daten aus der oben aufgeführten Dokumentklasse anzeigt. Sie können diese Klasse `CView` `CScrollView`von `CFormView`, `CEditView`, oder ableiten. (Sie können `CEditView` es auch direkt verwenden.)

- Eine Rahmenfensterklasse, die die Ansicht enthält. Für eine SDI-Dokumentvorlage können Sie `CFrameWnd`diese Klasse von ableiten. Wenn Sie das Verhalten des Hauptrahmenfensters nicht anpassen `CFrameWnd` müssen, können Sie es direkt verwenden, ohne eine eigene Klasse abzuleiten.

Eine SDI-Anwendung unterstützt in der Regel einen `CSingleDocTemplate` Dokumenttyp, sodass nur ein Objekt enthalten ist. Es kann jeweils nur ein Dokument geöffnet sein.

Sie müssen keine Memberfunktionen außer `CSingleDocTemplate` dem Konstruktor aufrufen. Das Framework `CSingleDocTemplate` verarbeitet Objekte intern.

Weitere Informationen zur `CSingleDocTemplate`Verwendung finden Sie unter [Dokumentvorlagen und den Dokument-/Ansichtserstellungsprozess](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate

Erstellt ein `CSingleDocTemplate`-Objekt.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parameter

*nIDResource*<br/>
Gibt die ID der Ressourcen an, die mit dem Dokumenttyp verwendet werden. Dies kann Menü-, Symbol-, Beschleunigertabelle und Zeichenfolgenressourcen umfassen.

Die Zeichenfolgenressource besteht aus bis zu sieben Teilzeichenfolgen, die durch das Zeichen ''n' getrennt sind (das Zeichen ''n' wird als Platzhalter benötigt, wenn eine Teilzeichenfolge nicht enthalten ist; jedoch sind nachfolgende 'n'-Zeichen nicht erforderlich); Diese Teilzeichenfolgen beschreiben den Dokumenttyp. Informationen zu den Teilzeichenfolgen finden Sie unter [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Diese Zeichenfolgenressource befindet sich in der Ressourcendatei der Anwendung. Beispiel:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Sie können diese Zeichenfolge mit dem Zeichenfolgen-Editor bearbeiten. Die gesamte Zeichenfolge wird als einzelner Eintrag im String-Editor und nicht als sieben separate Einträge angezeigt.

Weitere Informationen zu diesen Ressourcentypen finden Sie im [Zeichenfolgen-Editor](../../windows/string-editor.md).

*pDocClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Dokumentklasse. Diese Klasse `CDocument`ist eine -abgeleitete Klasse, die Sie definieren, um Ihre Dokumente darzustellen.

*pFrameClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Rahmenfensterklasse. Diese Klasse kann `CFrameWnd`eine -derived-Klasse `CFrameWnd` sein, oder sie kann selbst sein, wenn Sie das Standardverhalten für das Hauptframefenster verwenden möchten.

*pViewClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Ansichtsklasse. Diese Klasse `CView`ist eine -abgeleitete Klasse, die Sie zum Anzeigen Ihrer Dokumente definieren.

### <a name="remarks"></a>Bemerkungen

Weisen Sie `CSingleDocTemplate` ein Objekt `CWinApp::AddDocTemplate` dynamisch `InitInstance` zu und übergeben Sie es an die Memberfunktion Ihrer Anwendungsklasse.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument-Klasse](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd-Klasse](../../mfc/reference/cframewnd-class.md)<br/>
[CMultiDocTemplate-Klasse](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)
