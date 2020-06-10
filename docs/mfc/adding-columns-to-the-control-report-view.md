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
ms.openlocfilehash: 119f0f9cb92d724058ce97fbf477143739ec111e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617313"
---
# <a name="adding-columns-to-the-control-report-view"></a>Hinzufügen von Spalten zum Steuerelement (Berichtsansicht)

> [!NOTE]
> Das folgende Verfahren gilt für ein [CListView](reference/clistview-class.md) -oder [CListCtrl](reference/clistctrl-class.md) -Objekt.

Wenn sich ein Listen Steuerelement in der Berichtsansicht befindet, werden Spalten angezeigt, die eine Methode zum Organisieren der verschiedenen unter Elemente der einzelnen Listen Steuerelement Elemente bereitstellen. Diese Organisation wird mit einer eins-zu-eins-Entsprechung zwischen einer Spalte im Listen Steuerelement und dem zugehörigen Unterelement des Listen Steuerungs Elements implementiert. Weitere Informationen zu unter [Elementen finden Sie unter Hinzufügen von Elementen zum-Steuer](adding-items-to-the-control.md)Element. Ein Beispiel für ein Listen Steuerelement in der Berichtsansicht wird von der Detailansicht in Windows 95 und Windows 98 Explorer bereitgestellt. In der ersten Spalte werden Ordner, Dateisymbole und Bezeichnungen aufgelistet. Andere Spalten Listen Dateigröße, Dateityp, Datum der letzten Änderung usw.

Obwohl Spalten jederzeit zu einem Listen Steuerelement hinzugefügt werden können, sind die Spalten nur sichtbar, wenn das Format Bit für das Steuerelement `LVS_REPORT` aktiviert ist.

Jede Spalte verfügt über ein zugeordnetes Header Element (siehe [CHeaderCtrl](reference/cheaderctrl-class.md)), das die Spalte bezeichnet und es Benutzern ermöglicht, die Größe der Spalte zu ändern.

Wenn das Listen Steuerelement eine Berichtsansicht unterstützt, müssen Sie eine Spalte für jedes mögliche Unterelement in einem Listen Steuerelement hinzufügen. Fügen Sie eine Spalte hinzu, indem Sie eine [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) -Struktur vorbereiten und dann [InsertColumn](reference/clistctrl-class.md#insertcolumn)aufzurufen. Nachdem Sie die erforderlichen Spalten hinzugefügt haben (manchmal auch als Header Elemente bezeichnet), können Sie Sie mithilfe von Element Funktionen und Stilen, die zum eingebetteten Header-Steuerelement gehören, neu anordnen. Weitere Informationen finden Sie unter [Anordnen von Elementen im Header Steuer](ordering-items-in-the-header-control.md)Element.

> [!NOTE]
> Wenn das Listen Steuerelement mit dem **LVS_NOCOLUMNHEADER** -Stil erstellt wird, werden alle Versuche, Spalten einzufügen, ignoriert.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
