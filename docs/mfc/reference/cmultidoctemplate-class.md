---
title: CMultiDocTemplate-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319734"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate-Klasse

Definiert eine Dokumentvorlage, welche die Multiple Document Interface (MDI) implementiert.

## <a name="syntax"></a>Syntax

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Erstellt ein `CMultiDocTemplate`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Eine MDI-Anwendung verwendet das Hauptrahmenfenster als Arbeitsbereich, in dem der Benutzer null oder mehr Dokumentrahmenfenster öffnen kann, von denen jedes ein Dokument anzeigt. Eine ausführlichere Beschreibung der MDI finden Sie unter *Windows Interface Guidelines for Software Design*.

Eine Dokumentvorlage definiert die Beziehungen zwischen drei Klassentypen:

- Eine Dokumentklasse, die Sie von [CDocument](../../mfc/reference/cdocument-class.md)ableiten.

- Eine Ansichtsklasse, die Daten aus der oben aufgeführten Dokumentklasse anzeigt. Sie können diese Klasse von `CScrollView` [CView](../../mfc/reference/cview-class.md) `CEditView`, , `CFormView`oder ableiten. (Sie können `CEditView` es auch direkt verwenden.)

- Eine Rahmenfensterklasse, die die Ansicht enthält. Für eine MDI-Dokumentvorlage können Sie `CMDIChildWnd`diese Klasse von ableiten, oder wenn Sie das Verhalten der Dokumentrahmenfenster nicht anpassen müssen, können Sie [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) direkt verwenden, ohne eine eigene Klasse abzuleiten.

Eine MDI-Anwendung kann mehr als einen Dokumenttyp unterstützen, und Dokumente unterschiedlicher Art können gleichzeitig geöffnet sein. Ihre Anwendung verfügt über eine Dokumentvorlage für jeden unterstützten Dokumenttyp. Wenn Ihre MDI-Anwendung beispielsweise sowohl Tabellenkalkulationen als auch `CMultiDocTemplate` Textdokumente unterstützt, verfügt die Anwendung über zwei Objekte.

Die Anwendung verwendet die Dokumentvorlage(n), wenn der Benutzer ein neues Dokument erstellt. Wenn die Anwendung mehr als einen Dokumenttyp unterstützt, ruft das Framework die Namen der unterstützten Dokumenttypen aus den Dokumentvorlagen ab und zeigt sie in einer Liste im Dialogfeld Datei neu an. Nachdem der Benutzer einen Dokumenttyp ausgewählt hat, erstellt die Anwendung ein Dokumentklassenobjekt, ein Rahmenfensterobjekt und ein Ansichtsobjekt und fügt sie aneinander an.

Sie müssen keine Memberfunktionen außer `CMultiDocTemplate` dem Konstruktor aufrufen. Das Framework `CMultiDocTemplate` verarbeitet Objekte intern.

Weitere Informationen `CMultiDocTemplate`finden Sie unter [Dokumentvorlagen und den Dokument-/Ansichtserstellungsprozess](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

Erstellt ein `CMultiDocTemplate`-Objekt.

```
CMultiDocTemplate(
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
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Beachten Sie, dass die Zeichenfolge mit einem Zeichen ''n' beginnt. Dies liegt daran, dass die erste Teilzeichenfolge nicht für MDI-Anwendungen verwendet wird und daher nicht enthalten ist. Sie können diese Zeichenfolge mit dem Zeichenfolgen-Editor bearbeiten. Die gesamte Zeichenfolge wird als einzelner Eintrag im String-Editor und nicht als sieben separate Einträge angezeigt.

Weitere Informationen zu diesen Ressourcentypen finden Sie unter [Ressourcen-Editoren](../../windows/resource-editors.md).

*pDocClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Dokumentklasse. Diese Klasse `CDocument`ist eine -abgeleitete Klasse, die Sie definieren, um Ihre Dokumente darzustellen.

*pFrameClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Frame-Window-Klasse. Diese Klasse kann `CMDIChildWnd`eine -derived-Klasse `CMDIChildWnd` sein, oder sie kann selbst sein, wenn Sie das Standardverhalten für Die Dokumentrahmenfenster verwenden möchten.

*pViewClass*<br/>
Zeigt auf `CRuntimeClass` das Objekt der Ansichtsklasse. Diese Klasse `CView`ist eine -abgeleitete Klasse, die Sie zum Anzeigen Ihrer Dokumente definieren.

### <a name="remarks"></a>Bemerkungen

Weisen Sie `CMultiDocTemplate` dynamisch ein Objekt für jeden Dokumenttyp `CWinApp::AddDocTemplate` zu, `InitInstance` den Ihre Anwendung unterstützt, und übergeben Sie jedes Objekt von der Memberfunktion Ihrer Anwendungsklasse.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Hier ist ein zweites Beispiel.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate-Klasse](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)
