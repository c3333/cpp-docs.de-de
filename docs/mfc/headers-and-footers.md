---
title: Kopf- und Fußzeilen
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620111"
---
# <a name="headers-and-footers"></a>Kopf- und Fußzeilen

In diesem Artikel wird erläutert, wie Sie Kopf-und Fußzeilen zu einem gedruckten Dokument hinzufügen.

Wenn Sie sich ein Dokument auf dem Bildschirm ansehen, werden der Name des Dokuments und der aktuelle Speicherort im Dokument häufig in einer Titelleiste und einer Statusleiste angezeigt. Wenn Sie sich eine gedruckte Kopie eines Dokuments ansehen, ist es hilfreich, den Namen und die Seitenzahl in einer Kopf-oder Fußzeile zu sehen. Dies ist eine gängige Methode, mit der sich sogar WYSIWYG-Programme in der Ausführung von Druck-und Bildschirm Anzeige unterscheiden.

Die Member-Funktion von [OnPrint](reference/cview-class.md#onprint) ist die geeignete Stelle zum Drucken von Kopf-oder Fußzeilen, da Sie für jede Seite aufgerufen wird, und da Sie nur für den Druck aufgerufen wird, nicht für die Bildschirm Anzeige. Sie können eine separate Funktion definieren, um eine Kopf-oder Fußzeile zu drucken, und den Drucker Gerätekontext von übergeben `OnPrint` . Sie müssen möglicherweise den Fenster Ursprung oder den Wertebereich vor dem Aufrufen von [OnDraw](reference/cview-class.md#ondraw) anpassen, um zu vermeiden, dass der Text der Seite die Kopfzeile oder Fußzeile überlappt. Sie müssen möglicherweise auch ändern, `OnDraw` da die Menge des Dokuments, das auf die Seite passt, reduziert werden kann.

Eine Möglichkeit, den von der Kopf-oder der Fußzeile ausgeführten Bereich auszugleichen, ist die Verwendung des **m_rectDraw** -Members von [CPrintInfo](reference/cprintinfo-structure.md). Jedes Mal, wenn eine Seite gedruckt wird, wird dieser Member mit dem verwendbaren Bereich der Seite initialisiert. Wenn Sie vor dem Drucken des Texts der Seite einen Kopf-oder Fußzeilen Druck ausgeben, können Sie die Größe des in **m_rectDraw** gespeicherten Rechtecks verringern, um den Bereich der Kopf-oder Fußzeile zu berücksichtigen. Dann `OnPrint` kann auf **m_rectDraw** verwiesen werden, um herauszufinden, wie viel Bereich zum Drucken des Texts der Seite verbleibt.

Es ist nicht möglich, einen Header oder etwas anderes aus [OnPrepareDC](reference/cview-class.md#onpreparedc)zu drucken, da er aufgerufen wird, bevor die `StartPage` Member-Funktion von [CDC](reference/cdc-class.md) aufgerufen wurde. An diesem Punkt wird der Drucker Gerätekontext als Seitenbegrenzung betrachtet. Der Druckvorgang kann nur über die Member-Funktion durchgeführt werden `OnPrint` .

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Drucken von mehrseitigen Dokumenten](multipage-documents.md)

- [Zuordnen von GDI-Ressourcen zum Drucken](allocating-gdi-resources.md)

## <a name="see-also"></a>Siehe auch

[Drucken](printing.md)
