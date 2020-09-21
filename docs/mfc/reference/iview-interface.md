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
ms.openlocfilehash: 9233ee5a8330c4b2c79ebc7b79e0616612c00204
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743424"
---
# <a name="iview-interface"></a>IView-Schnittstelle

Implementiert mehrere Methoden, die [CWinFormsView](../../mfc/reference/cwinformsview-class.md) verwendet, um Ansichts Benachrichtigungen an ein verwaltetes Steuerelement zu senden.

## <a name="syntax"></a>Syntax

```
interface class IView
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.|
|[IView:: OnInitialUpdate](#oninitialupdate)|Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.|
|[IView:: OnUpdate](#onupdate)|Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde. Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.|

### <a name="remarks"></a>Bemerkungen

`IView` implementiert verschiedene Methoden, `CWinFormsView` mit denen allgemeine Ansichts Benachrichtigungen an ein gehosteter verwaltetes Steuerelement weitergeleitet werden. Dabei handelt es sich um [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) und [OnActivateView](#onactivateview).

`IView` ähnelt [CView](../../mfc/reference/cview-class.md), wird jedoch nur mit verwalteten Sichten und Steuerelementen verwendet.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Anforderungen

Header: afxwinforms. h (in Assemblyatlmfc\lib\mfcmifc80.dll definiert)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a> IView:: OnActivateView

Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert wird.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parameter

*aktivieren*<br/>
Gibt an, ob die Ansicht aktiviert oder deaktiviert wird.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a> IView:: OnInitialUpdate

Wird von Framework aufgerufen, nachdem die Ansicht zum ersten Mal an das Dokument angefügt wurde, aber bevor die Ansicht anfänglich angezeigt wird.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a> IView:: OnUpdate

Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde.

```cpp
void OnUpdate();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion ermöglicht der Ansicht, Ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.

## <a name="see-also"></a>Weitere Informationen

[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)
