---
title: CTreeCtrl im Vergleich mit CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 83e07c75b9eab6df05dbcd0f52cfbe8b90e1d768
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620482"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl im Vergleich mit CTreeView

MFC stellt zwei Klassen bereit, die Struktur Steuerelemente Kapseln: [CTreeCtrl](reference/ctreectrl-class.md) und [CTreeView](reference/ctreeview-class.md). Jede Klasse ist in unterschiedlichen Situationen nützlich.

Verwenden `CTreeCtrl` Sie, wenn Sie ein Steuerelement mit nur einem untergeordneten Fenster benötigen, z.b. in einem Dialogfeld. Sie möchten insbesondere verwenden `CTreeCtrl` , wenn im Fenster andere untergeordnete Steuerelemente vorhanden sind, wie in einem typischen Dialogfeld.

Verwenden `CTreeView` Sie, wenn das Struktur Steuerelement wie ein Ansichts Fenster in der Dokument-/Ansichtsarchitektur und in einem Struktur Steuerelement agieren soll. Ein `CTreeView` belegt den gesamten Client Bereich eines Rahmen Fensters oder eines Splitter Fensters. Die Größe wird automatisch geändert, wenn die Größe des übergeordneten Fensters geändert wird, und Sie kann Befehls Meldungen aus Menüs, Zugriffstasten und Symbolleisten verarbeiten. Da ein Struktur Steuerelement die zum Anzeigen der Struktur erforderlichen Daten enthält, muss das zugehörige Dokument Objekt nicht kompliziert sein – Sie können auch [CDocument](reference/cdocument-class.md) als Dokumenttyp in der Dokument Vorlage verwenden.

## <a name="see-also"></a>Siehe auch

[Verwenden von CTreeCtrl](using-ctreectrl.md)<br/>
[Steuerelemente](controls-mfc.md)
