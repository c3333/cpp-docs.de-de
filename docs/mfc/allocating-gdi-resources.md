---
title: Zuordnen von GDI-Ressourcen
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: f0cadac5320a8c6e91eb3b1989d1fb3c0c701eb0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623234"
---
# <a name="allocating-gdi-resources"></a>Zuordnen von GDI-Ressourcen

In diesem Artikel wird beschrieben, wie Sie die für das Drucken benötigten Objekte der Windows-GDI (Graphics Device Interface) zuweisen und ihre Zuweisung aufheben.

> [!NOTE]
> Weitere Informationen finden Sie in der [GDI+-SDK-Dokumentation](/windows/win32/gdiplus/-gdiplus-gdi-start).

Angenommen, Sie müssen bestimmte Schriften, Stifte oder andere GDI-Objekte für das Drucken, aber nicht für die Bildschirmanzeige verwenden. Aufgrund des erforderlichen Arbeitsspeichers ist es ineffizient, diese Objekte beim Start der Anwendung zuzuordnen. Wenn die Anwendung gerade kein Dokument druckt, wird dieser Speicher möglicherweise für andere Zwecke benötigt. Es ist besser, sie bei Beginn des Druckens zuzuordnen und nach dem Druckvorgang zu löschen.

Um diese GDI-Objekte zuzuordnen, überschreiben Sie die [OnBeginPrinting](reference/cview-class.md#onbeginprinting) -Member-Funktion. Diese Funktion eignet sich aus zwei Gründen für diesen Zweck: das Framework ruft diese Funktion einmal am Anfang jedes Druckauftrags auf, und im Gegensatz zu [OnPreparePrinting](reference/cview-class.md#onprepareprinting)hat diese Funktion Zugriff auf das [CDC](reference/cdc-class.md) -Objekt, das den Drucker Gerätetreiber darstellt. Sie können diese Objekte für die Verwendung während des Druckauftrags speichern, indem Sie Element Variablen in der Ansichts Klasse definieren, die auf GDI-Objekte verweisen (z. b. Member `CFont *` usw.).

Wenn Sie die von Ihnen erstellten GDI-Objekte verwenden möchten, wählen Sie Sie in der Element Funktion von [OnPrint](reference/cview-class.md#onprint) in den Drucker Gerätekontext aus. Wenn Sie unterschiedliche GDI-Objekte für verschiedene Seiten des Dokuments benötigen, können Sie den `m_nCurPage` Member der [CPrintInfo](reference/cprintinfo-structure.md) -Struktur untersuchen und das GDI-Objekt entsprechend auswählen. Wenn Sie ein GDI-Objekt für mehrere aufeinanderfolgende Seiten benötigen, müssen Sie es bei jedem Aufrufen von `OnPrint` in den Gerätekontext wählen.

Um die Zuteilung dieser GDI-Objekte zu überschreiben, überschreiben Sie die [OnEndPrinting](reference/cview-class.md#onendprinting) -Element Funktion. Das Framework ruft diese Funktion am Ende jedes Druckauftrags auf, wodurch Sie die Zuweisung druckspezifischer GDI-Objekte aufheben können, bevor die Anwendung zu anderen Aufgaben zurückkehrt.

## <a name="see-also"></a>Siehe auch

[Drucken](printing.md)<br/>
[Funktionsweise des Standarddrucks](how-default-printing-is-done.md)
