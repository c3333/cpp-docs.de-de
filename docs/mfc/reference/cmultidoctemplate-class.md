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
ms.openlocfilehash: af950d188c4e02a38a39ed3c672f0f8c4161bee8
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737485"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate-Klasse

Definiert eine Dokumentvorlage, welche die Multiple Document Interface (MDI) implementiert.

## <a name="syntax"></a>Syntax

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Member

Die Member-Funktionen für diese Klasse sind virtuell. Dokumentation finden Sie unter [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) und [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) .

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CMultiDocTemplate:: CMultiDocTemplate](#cmultidoctemplate)|Erstellt ein `CMultiDocTemplate`-Objekt.|

## <a name="remarks"></a>Hinweise

Eine MDI-Anwendung verwendet das Hauptrahmen Fenster als Arbeitsbereich, in dem der Benutzer NULL oder mehr Dokument Rahmen Fenster öffnen kann, von denen jedes ein Dokument anzeigt. Eine ausführlichere Beschreibung des MDI finden Sie unter *Richtlinien für die Windows-Benutzeroberfläche für den Software Entwurf*.

Eine Dokument Vorlage definiert die Beziehungen zwischen drei Typen von Klassen:

- Eine Dokument Klasse, die Sie von [CDocument](../../mfc/reference/cdocument-class.md)ableiten.

- Eine Ansichts Klasse, die Daten aus der oben aufgeführten Dokument Klasse anzeigt. Sie können diese Klasse von [CView](../../mfc/reference/cview-class.md), `CScrollView` , `CFormView` oder ableiten `CEditView` . (Sie können auch `CEditView` direkt verwenden.)

- Eine Frame Fenster Klasse, die die Ansicht enthält. Bei einer MDI-Dokument Vorlage können Sie diese Klasse von ableiten `CMDIChildWnd` , oder Sie können [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) direkt verwenden, ohne dass Sie eine eigene Klasse ableiten müssen, wenn Sie das Verhalten der Dokument Rahmen Fenster nicht anpassen müssen.

Eine MDI-Anwendung kann mehr als einen Dokumenttyp unterstützen, und Dokumente unterschiedlicher Typen können gleichzeitig geöffnet werden. Die Anwendung verfügt über eine Dokument Vorlage für jeden Dokumenttyp, der von ihr unterstützt wird. Wenn die MDI-Anwendung z. b. sowohl Tabellen-als auch Textdokumente unterstützt, verfügt die Anwendung über zwei- `CMultiDocTemplate` Objekte.

Die Anwendung verwendet die Dokument Vorlage (en), wenn der Benutzer ein neues Dokument erstellt. Wenn die Anwendung mehr als einen Dokumenttyp unterstützt, ruft das Framework die Namen der unterstützten Dokumenttypen aus den Dokumentvorlagen ab und zeigt Sie in einer Liste im Dialogfeld Datei neu an. Nachdem der Benutzer einen Dokumenttyp ausgewählt hat, erstellt die Anwendung ein Dokument Klassenobjekt, ein Rahmen Fenster Objekt und ein Ansichts Objekt und fügt sie einander an.

Sie müssen keine Member-Funktionen von `CMultiDocTemplate` außer dem-Konstruktor aufzurufen. Das Framework verarbeitet- `CMultiDocTemplate` Objekte intern.

Weitere Informationen zu `CMultiDocTemplate` finden Sie unter [Dokumentvorlagen und der Erstellungs Vorgang für Dokumente und Ansichten](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate:: CMultiDocTemplate

Erstellt ein `CMultiDocTemplate`-Objekt.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parameter

*nidresource*<br/>
Gibt die ID der Ressourcen an, die mit dem Dokumenttyp verwendet werden. Dies kann Menü, Symbol, Zugriffstasten Tabelle und Zeichen folgen Ressourcen umfassen.

Die Zeichen folgen Ressource besteht aus bis zu sieben Teil Zeichenfolgen, die durch das Zeichen ' \n ' getrennt sind (das Zeichen ' \n ' wird als Platzhalter benötigt, wenn keine Teil Zeichenfolge eingeschlossen wird. nachfolgende ' \n '-Zeichen sind jedoch nicht erforderlich); Diese Teil Zeichenfolgen beschreiben den Dokumenttyp. Weitere Informationen zu den Teil Zeichenfolgen finden Sie unter [CDocTemplate:: getdocstring](../../mfc/reference/cdoctemplate-class.md#getdocstring). Diese Zeichen folgen Ressource befindet sich in der Ressourcen Datei der Anwendung. Beispiel:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Die Zeichenfolge beginnt mit dem Zeichen "\n", da die erste Teil Zeichenfolge nicht für MDI-Anwendungen verwendet wird und daher nicht eingeschlossen ist. Sie können diese Zeichenfolge mit dem Zeichen folgen-Editor bearbeiten. die gesamte Zeichenfolge wird als einzelner Eintrag im Zeichen folgen-Editor angezeigt, nicht als sieben separate Einträge.

Weitere Informationen zu diesen Ressourcentypen finden Sie unter [Ressourcen-Editoren](../../windows/resource-editors.md).

*pdocclass*<br/>
Verweist auf das- `CRuntimeClass` Objekt der Document-Klasse. Diese Klasse ist eine `CDocument` von abgeleitete Klasse, die Sie zur Darstellung Ihrer Dokumente definieren.

*pframeclass*<br/>
Verweist auf das- `CRuntimeClass` Objekt der Frame-Window-Klasse. Diese Klasse kann eine von `CMDIChildWnd` abgeleitete Klasse sein, oder Sie kann `CMDIChildWnd` selbst sein, wenn Sie das Standardverhalten für die Dokument Rahmen Fenster benötigen.

*pviewclass*<br/>
Verweist auf das- `CRuntimeClass` Objekt der Ansichts Klasse. Diese Klasse ist eine `CView` von abgeleitete Klasse, die Sie definieren, um Ihre Dokumente anzuzeigen.

### <a name="remarks"></a>Hinweise

Weisen `CMultiDocTemplate` Sie für jeden Dokumenttyp, der von der Anwendung unterstützt wird, dynamisch ein Objekt zu, und übergeben Sie jedes `CWinApp::AddDocTemplate` von der `InitInstance` Member-Funktion Ihrer Anwendungsklasse an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Im folgenden finden Sie ein zweites Beispiel.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate-Klasse](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate-Klasse](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)
