---
title: Eigenschaftenblätter und Eigenschaftenseiten in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371168"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Eigenschaftenblätter und Eigenschaftenseiten in MFC

Ein Eigenschaftenblatt, auch als Registerkartendialogfeld bezeichnet, ist ein Dialogfeld, das Eigenschaftenseiten enthält. Jede Eigenschaftenseite basiert auf einer Dialogfeldvorlagenressource und enthält Steuerelemente. Es ist auf einer Seite mit einer Registerkarte oben eingeschlossen. Die Registerkarte benennt die Seite und gibt deren Zweck an. Benutzer klicken auf eine Registerkarte im Eigenschaftenblatt, um eine Reihe von Steuerelementen auszuwählen.

Verwenden Sie Seiten, um die Steuerelemente im Eigenschaftenblatt in sinnvolle Mengen zu gruppieren. Das enthaltene Eigenschaftenblatt verfügt in der Regel über mehrere eigene Steuerelemente. Diese gelten für alle Seiten.

Eigenschaftenblätter basieren auf der Klasse [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Eigenschaftenseiten basieren auf der Klasse [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Ein Eigenschaftenblatt ist eine spezielle Art von Dialogfeld, das im Allgemeinen verwendet wird, um die Attribute eines externen Objekts zu ändern, z. B. die aktuelle Auswahl in einer Ansicht. Das Eigenschaftenblatt besteht aus drei Hauptteilen: dem Dialogfeld, einer oder mehreren Eigenschaftenseiten, die nacheinander angezeigt werden, und einer Registerkarte oben auf jeder Seite, auf die der Benutzer klickt, um diese Seite auszuwählen. Eigenschaftenblätter sind nützlich für Situationen, in denen Sie mehrere ähnliche Gruppen von Einstellungen oder Optionen ändern können. Ein Eigenschaftenblatt gruppiert Informationen auf leicht verständliche Weise.

> [!NOTE]
> Wenn Sie versuchen, ein Eigenschaftenblatt `CPropertySheet::DoModal`mithilfe von anzuzeigen, generiert das System möglicherweise eine Ausnahme der ersten Chance. Diese Ausnahme tritt auf, weil das System versucht, die [Fensterstile](../mfc/reference/styles-used-by-mfc.md#window-styles) des Objekts zu ändern, bevor das Objekt erstellt wurde. Weitere Informationen zu dieser Ausnahme und zum Vermeiden oder Behandeln finden Sie unter [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Siehe auch

[Eigenschaftenblätter](../mfc/property-sheets-mfc.md)
