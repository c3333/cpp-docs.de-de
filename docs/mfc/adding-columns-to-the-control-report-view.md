---
title: Hinzufügen von Spalten zum Steuerelement (Berichtsansicht)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 34d7b62985748b9b9d741c083ec9b34fce06b309
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370877"
---
# <a name="adding-columns-to-the-control-report-view"></a>Hinzufügen von Spalten zum Steuerelement (Berichtsansicht)

> [!NOTE]
> Das folgende Verfahren gilt entweder für ein [CListView-](../mfc/reference/clistview-class.md) oder [CListCtrl-Objekt.](../mfc/reference/clistctrl-class.md)

Wenn sich ein Listensteuerelement in der Berichtsansicht befindet, werden Spalten angezeigt, die eine Methode zum Organisieren der verschiedenen Unterelemente jedes Listensteuerelements bereitstellen. Diese Organisation wird mit einer 1:1-Entsprechung zwischen einer Spalte im Listensteuerelement und dem zugehörigen Unterelement des Listensteuerelements implementiert. Weitere Informationen zu Unterelementen finden Sie unter [Hinzufügen von Elementen zum Steuerelement](../mfc/adding-items-to-the-control.md). Ein Beispiel für ein Listensteuerelement in der Berichtsansicht wird in der Detailansicht in Windows 95 und Windows 98 Explorer bereitgestellt. In der ersten Spalte sind Ordner, Dateisymbole und Beschriftungen aufgeführt. Andere Spalten listen Dateigröße, Dateityp, Datum der letzten Änderung usw. auf.

Obwohl Spalten jederzeit zu einem Listensteuerelement hinzugefügt werden können, sind die `LVS_REPORT` Spalten nur sichtbar, wenn das Stilbit für das Steuerelement aktiviert ist.

Jede Spalte verfügt über ein zugeordnetes Headerelement (siehe [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) -, das die Spalte beschriftet und Benutzern ermöglicht, die Größe der Spalte zu ändern.

Wenn das Listensteuerelement eine Berichtsansicht unterstützt, müssen Sie für jedes mögliche Unterelement in einem Listensteuerelement eine Spalte hinzufügen. Fügen Sie eine Spalte hinzu, indem Sie eine [LVCOLUMN-Struktur](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) vorbereiten und dann [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn)aufrufen. Nachdem Sie die erforderlichen Spalten hinzugefügt haben (manchmal auch als Headerelemente bezeichnet), können Sie sie mithilfe von Memberfunktionen und Stilen, die zum eingebetteten Headersteuerelement gehören, neu anordnen. Weitere Informationen finden Sie [unter Bestellen von Artikeln im Kopfzeilensteuerelement](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
> Wenn das Listensteuerelement mit dem **Stil LVS_NOCOLUMNHEADER** erstellt wird, wird jeder Versuch, Spalten einzufügen, ignoriert.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
