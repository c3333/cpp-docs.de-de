---
title: Zuordnen von GDI-Ressourcen
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370850"
---
# <a name="allocating-gdi-resources"></a>Zuordnen von GDI-Ressourcen

In diesem Artikel wird beschrieben, wie Sie die für das Drucken benötigten Objekte der Windows-GDI (Graphics Device Interface) zuweisen und ihre Zuweisung aufheben.

> [!NOTE]
> Weitere Informationen finden Sie in der [GDI+ SDK-Dokumentation](/windows/win32/gdiplus/-gdiplus-gdi-start).

Angenommen, Sie müssen bestimmte Schriften, Stifte oder andere GDI-Objekte für das Drucken, aber nicht für die Bildschirmanzeige verwenden. Aufgrund des erforderlichen Arbeitsspeichers ist es ineffizient, diese Objekte beim Start der Anwendung zuzuordnen. Wenn die Anwendung gerade kein Dokument druckt, wird dieser Speicher möglicherweise für andere Zwecke benötigt. Es ist besser, sie bei Beginn des Druckens zuzuordnen und nach dem Druckvorgang zu löschen.

Um diese GDI-Objekte zuzuweisen, überschreiben Sie die [OnBeginPrinting-Memberfunktion.](../mfc/reference/cview-class.md#onbeginprinting) Diese Funktion eignet sich aus zwei Gründen gut für diesen Zweck: Das Framework ruft diese Funktion einmal zu Beginn jedes Druckauftrags auf, und im Gegensatz zu [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)hat diese Funktion Zugriff auf das [CDC-Objekt,](../mfc/reference/cdc-class.md) das den Druckergerätetreiber darstellt. Sie können diese Objekte für die Verwendung während des Druckauftrags speichern, indem Sie Membervariablen in Ihrer Ansichtsklasse definieren, die auf GDI-Objekte verweisen (z. `CFont *` B. Member usw.).

Um die von Ihnen erstellten GDI-Objekte zu verwenden, wählen Sie sie in der [OnPrint-Memberfunktion](../mfc/reference/cview-class.md#onprint) im Druckergerätekontext aus. Wenn Sie verschiedene GDI-Objekte für verschiedene Seiten des `m_nCurPage` Dokuments benötigen, können Sie das Element der [CPrintInfo-Struktur](../mfc/reference/cprintinfo-structure.md) untersuchen und das GDI-Objekt entsprechend auswählen. Wenn Sie ein GDI-Objekt für mehrere aufeinanderfolgende Seiten benötigen, müssen Sie es bei jedem Aufrufen von `OnPrint` in den Gerätekontext wählen.

Um diese GDI-Objekte zuzuweisen, überschreiben Sie die [OnEndPrinting-Memberfunktion.](../mfc/reference/cview-class.md#onendprinting) Das Framework ruft diese Funktion am Ende jedes Druckauftrags auf, wodurch Sie die Zuweisung druckspezifischer GDI-Objekte aufheben können, bevor die Anwendung zu anderen Aufgaben zurückkehrt.

## <a name="see-also"></a>Siehe auch

[Drucken](../mfc/printing.md)<br/>
[Funktionsweise des Standarddrucks](../mfc/how-default-printing-is-done.md)
