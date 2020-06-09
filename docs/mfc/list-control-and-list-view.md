---
title: Listensteuerelement und Listenansichtsteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621427"
---
# <a name="list-control-and-list-view"></a>Listensteuerelement und Listenansichtsteuerelement

Der Vorteil ist, dass MFC das Listen Steuerelement auf zwei Arten kapselt. Sie können Listen Steuerelemente verwenden:

- Direkt durch Einbetten eines [CListCtrl](reference/clistctrl-class.md) -Objekts in eine Dialogfeld Klasse.

- Indirekt, mithilfe der Klasse [CListView](reference/clistview-class.md).

`CListView`vereinfacht das Integrieren eines Listen Steuer Elements mit der MFC-Dokument-/Ansichtarchitektur und kapselt das Steuerelement so, wie [CEditView](reference/ceditview-class.md) ein Bearbeitungs Steuerelement kapselt: das-Steuerelement füllt den gesamten Oberflächen Bereich einer MFC-Ansicht. (Die Ansicht *ist* das Steuerelement, umgewandelt in `CListView` .)

Ein `CListView` -Objekt erbt von [cctrlview](reference/cctrlview-class.md) und seinen Basisklassen und fügt eine Member-Funktion hinzu, um das zugrunde liegende Listen Steuerelement abzurufen. Verwenden Sie Member anzeigen, um mit der Ansicht als Ansicht zu arbeiten. Verwenden Sie die Member-Funktion von [GetListCtrl](reference/clistview-class.md#getlistctrl) , um Zugriff auf die Member-Funktionen des Listen Steuer Elements zu erhalten. Verwenden Sie diese Member für Folgendes:

- Elemente in der Liste hinzufügen, löschen oder bearbeiten.

- Festlegen oder erhalten von Listen Steuerelement-Attributen.

Um einen Verweis auf den `CListCtrl` zugrunde liegenden a zu erhalten `CListView` , rufen `GetListCtrl` Sie von der Listen Ansichts Klasse auf:

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

In diesem Thema werden beide Möglichkeiten zur Verwendung des Listen Steuer Elements beschrieben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
