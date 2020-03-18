---
title: IView-Schnittstelle
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: e8afa7a5f5a7692f88ace4da08209b80f902b603
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445667"
---
# <a name="iview-interface"></a>IView-Schnittstelle

Implementiert mehrere Methoden, die [CWinFormsView](../../mfc/reference/cwinformsview-class.md) verwendet, um Ansichts Benachrichtigungen an ein verwaltetes Steuerelement zu senden.

## <a name="syntax"></a>Syntax

```
interface class IView
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.|
|[IView:: OnInitialUpdate](#oninitialupdate)|Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.|
|[IView:: OnUpdate](#onupdate)|Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde. Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.|

## <a name="remarks"></a>Bemerkungen

`IView` implementiert mehrere Methoden, die `CWinFormsView` verwendet, um allgemeine Ansichts Benachrichtigungen an ein gehosteter verwaltetes Steuerelement weiterzuleiten Dabei handelt es sich um [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) und [OnActivateView](#onactivateview).

`IView` ähnelt [CView](../../mfc/reference/cview-class.md), wird jedoch nur mit verwalteten Sichten und Steuerelementen verwendet.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requirements (Anforderungen)

Header: afxwinforms. h (definiert in Assembly atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>IView:: OnActivateView

Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.

```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parameter

*Aktivieren*<br/>
Gibt an, ob die Ansicht aktiviert oder deaktiviert wird.

## <a name="oninitialupdate"></a>IView:: OnInitialUpdate

Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.

```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView:: OnUpdate

Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde.

```
void OnUpdate();
```

## <a name="remarks"></a>Bemerkungen

Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.

## <a name="see-also"></a>Weitere Informationen

[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)
