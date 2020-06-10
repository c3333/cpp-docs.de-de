---
title: Hinzufügen von Elementen zum Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 5cc1c7a921cf6d6ba2c0f968012b48bfcaef0658
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623362"
---
# <a name="adding-items-to-the-control"></a>Hinzufügen von Elementen zum Steuerelement

Um dem Listen Steuerelement ([CListCtrl](reference/clistctrl-class.md)) Elemente hinzuzufügen, müssen Sie eine von mehreren Versionen der [InsertItem](reference/clistctrl-class.md#insertitem) -Member-Funktion aufzurufen, je nachdem, welche Informationen Sie besitzen. Eine Version übernimmt eine [lvitem](/windows/win32/api/commctrl/ns-commctrl-lvitemw) -Struktur, die Sie vorbereiten. Da die `LVITEM` Struktur zahlreiche Member enthält, haben Sie eine bessere Kontrolle über die Attribute des Listen Steuerelement Elements.

Zwei wichtige Member (hinsichtlich der Berichtsansicht) der `LVITEM` -Struktur sind die `iItem` -und-Member `iSubItem` . Der `iItem` -Member ist der null basierte Index des Elements, auf das die-Struktur verweist, und der `iSubItem` -Member ist der einsbasierte Index eines unter Elements, oder 0 (null), wenn die Strukturinformationen zu einem Element enthält. Mit diesen beiden Membern legen Sie den Typ und den Wert der Unterelement Informationen fest, die angezeigt werden, wenn sich das Listen Steuerelement in der Berichtsansicht befindet. Weitere Informationen finden Sie unter [CListCtrl:: System](reference/clistctrl-class.md#setitem)Item.

Zusätzliche Member geben Text-, Symbol-, Zustands-und Elementdaten des Elements an. "Elementdaten" ist ein Anwendungs definierter Wert, der einem Listen Ansichts Element zugeordnet ist. Weitere Informationen zur- `LVITEM` Struktur finden Sie unter [CListCtrl:: GetItem](reference/clistctrl-class.md#getitem).

Andere Versionen von `InsertItem` nehmen einen oder mehrere separate Werte auf, die den Elementen in der `LVITEM` Struktur entsprechen, sodass Sie nur die Member initialisieren können, die Sie unterstützen möchten. Im Allgemeinen verwaltet das Listen Steuerelement den Speicher für Listenelemente, Sie können jedoch einige der Informationen in der Anwendung speichern, indem Sie "Rückruf Elemente" verwenden. Weitere Informationen finden Sie unter [Rückruf Elemente und Rückruf Maske](callback-items-and-the-callback-mask.md) in diesem Thema und [Rückruf Elemente und die Rückruf Maske](/windows/win32/Controls/using-list-view-controls) in der Windows SDK.

Weitere Informationen finden Sie unter [Hinzufügen von Listen Ansichts Elementen und unter Elementen](/windows/win32/Controls/using-list-view-controls).

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
