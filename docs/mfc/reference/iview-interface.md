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
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751283"
---
# <a name="iview-interface"></a>IView-Schnittstelle

Implementiert mehrere Methoden, die [CWinFormsView](../../mfc/reference/cwinformsview-class.md) zum Senden von Ansichtsbenachrichtigungen an ein verwaltetes Steuerelement verwendet.

## <a name="syntax"></a>Syntax

```
interface class IView
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert ist.|
|[IView::OnInitialUpdate](#oninitialupdate)|Wird vom Framework aufgerufen, nachdem die Ansicht zuerst an das Dokument angefügt wurde, aber bevor die Ansicht zuerst angezeigt wird.|
|[IView::OnUpdate](#onupdate)|Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde; Diese Funktion ermöglicht es der Ansicht, ihre Anzeige zu aktualisieren, um Änderungen widerzuspiegeln.|

## <a name="remarks"></a>Bemerkungen

`IView`implementiert mehrere Methoden, die `CWinFormsView` zum Weiterleiten von allgemeinen Ansichtsbenachrichtigungen an ein gehostetes verwaltetes Steuerelement verwendet werden. Dies sind [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) und [OnActivateView](#onactivateview).

`IView`ist ähnlich wie [CView](../../mfc/reference/cview-class.md), wird jedoch nur mit verwalteten Ansichten und Steuerelementen verwendet.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requirements (Anforderungen)

Header: afxwinforms.h (definiert in assembly atlmfc-lib-mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView

Wird von MFC aufgerufen, wenn eine Ansicht aktiviert oder deaktiviert ist.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parameter

*aktivieren*<br/>
Gibt an, ob die Ansicht aktiviert oder deaktiviert wird.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate

Wird vom Framework aufgerufen, nachdem die Ansicht zuerst an das Dokument angefügt wurde, aber bevor die Ansicht zuerst angezeigt wird.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate

Wird von MFC aufgerufen, nachdem das Dokument der Ansicht geändert wurde.

```cpp
void OnUpdate();
```

## <a name="remarks"></a>Bemerkungen

Mit dieser Funktion kann die Ansicht ihre Anzeige aktualisieren, um Änderungen widerzuspiegeln.

## <a name="see-also"></a>Weitere Informationen

[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CView-Klasse](../../mfc/reference/cview-class.md)
