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
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426252"
---
# <a name="iview-interface"></a>IView-Schnittstelle

Implementiert mehrere Methoden, die [CWinFormsView](../../mfc/reference/cwinformsview-class.md) verwendet, um Ansichts Benachrichtigungen an ein verwaltetes Steuerelement zu senden.

## <a name="syntax"></a>Syntax

```
interface class IView
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.|
|[IView:: OnInitialUpdate](#oninitialupdate)|Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.|
|[IView:: OnUpdate](#onupdate)|Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde. Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.|

## <a name="remarks"></a>Hinweise

`IView` implementiert mehrere Methoden, die `CWinFormsView` verwendet, um allgemeine Ansichts Benachrichtigungen an ein gehosteter verwaltetes Steuerelement weiterzuleiten Dabei handelt es sich um [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) und [OnActivateView](#onactivateview).

`IView` ähnelt [CView](../../mfc/reference/cview-class.md), wird jedoch nur mit verwalteten Sichten und Steuerelementen verwendet.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Voraussetzungen

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

## <a name="remarks"></a>Hinweise

Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.

## <a name="see-also"></a>Siehe auch

[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)
