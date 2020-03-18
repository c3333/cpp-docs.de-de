---
title: CTreeCtrl im Vergleich mit CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445228"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl im Vergleich mit CTreeView

MFC stellt zwei Klassen bereit, die Struktur Steuerelemente Kapseln: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) und [CTreeView](../mfc/reference/ctreeview-class.md). Jede Klasse ist in unterschiedlichen Situationen nützlich.

Verwenden Sie `CTreeCtrl`, wenn Sie ein einfaches untergeordnetes Fenster Steuerelement benötigen. beispielsweise in einem Dialogfeld. Sie möchten insbesondere `CTreeCtrl` verwenden, wenn im Fenster andere untergeordnete Steuerelemente vorhanden sind, wie in einem typischen Dialogfeld.

Verwenden Sie `CTreeView`, wenn das Struktur Steuerelement wie ein Ansichts Fenster in der Dokument-/Ansichtsarchitektur und in einem Struktur Steuerelement agieren soll. Ein `CTreeView` der den gesamten Client Bereich eines Rahmen Fensters oder eines Splitter Fensters einnimmt. Die Größe wird automatisch geändert, wenn die Größe des übergeordneten Fensters geändert wird, und Sie kann Befehls Meldungen aus Menüs, Zugriffstasten und Symbolleisten verarbeiten. Da ein Struktur Steuerelement die zum Anzeigen der Struktur erforderlichen Daten enthält, muss das zugehörige Dokument Objekt nicht kompliziert sein – Sie können auch [CDocument](../mfc/reference/cdocument-class.md) als Dokumenttyp in der Dokument Vorlage verwenden.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
