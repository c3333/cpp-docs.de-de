---
title: Klassen im Zusammenhang mit RichEdit-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
ms.openlocfilehash: 584649a2bb2d9a118e390aebf9f7411c3123b1a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620712"
---
# <a name="classes-related-to-rich-edit-controls"></a>Klassen im Zusammenhang mit RichEdit-Steuerelementen

Die Klassen [CRichEditView](reference/cricheditview-class.md), [CRichEditDoc](reference/cricheditdoc-class.md)und [cricheditcnytem](reference/cricheditcntritem-class.md) stellen die Funktionalität des Rich-Edit-Steuer Elements ([CRichEditCtrl](reference/cricheditctrl-class.md)) im Kontext der MFC-Dokument-/Ansichtsarchitektur bereit. `CRichEditView`behält den Text und das Formatierungs Merkmal von Text bei. `CRichEditDoc`verwaltet die Liste der OLE-Client Elemente in der Ansicht. `CRichEditCntrItem`bietet Container seitigen Zugriff auf das OLE-Client Element. Um den Inhalt eines zu ändern `CRichEditView` , verwenden Sie [CRichEditView:: GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl) für den Zugriff auf das zugrunde liegende Rich Edit-Steuerelement.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
