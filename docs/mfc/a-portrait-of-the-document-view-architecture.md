---
title: Ein Hochformat der Dokument-/Ansichtsarchitektur
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: 8c7bb4add1ebce62147f0bd5403f693cbec87e91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214190"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Ein Portrait der Dokument-/Ansichtarchitektur

Dokumente und Sichten werden in einer typischen MFC-Anwendung gepaart. Die Daten werden im Dokument gespeichert, aber die Sicht hat privilegierten Zugriff auf die Daten. Durch die Trennung eines Dokuments aus der Ansicht werden die Speicherung und Wartung von Daten von der Anzeige getrennt.

## <a name="gaining-access-to-document-data-from-the-view"></a>Zugriff auf Dokument Daten aus der Ansicht

Die Sicht greift entweder mit der [GetDocument](reference/cview-class.md#getdocument) -Funktion auf die Daten des Dokuments zu, die einen Zeiger auf das Dokument zurückgibt, oder durch Festlegen der Ansichts Klasse zu einem C++ **`friend`** der Document-Klasse. Die Sicht verwendet dann den Zugriff auf die Daten, um die Daten abzurufen, wenn Sie zum Zeichnen oder anderweitig bearbeiten bereit sind.

Beispielsweise verwendet die-Sicht in der [OnDraw](reference/cview-class.md#ondraw) -Member-Funktion der Sicht, `GetDocument` um einen Dokument Zeiger zu erhalten. Anschließend wird dieser Zeiger verwendet, um auf einen `CString` Datenmember im Dokument zuzugreifen. Die Ansicht übergibt die Zeichenfolge an die `TextOut` Funktion. Den Code für dieses Beispiel finden Sie unter [Zeichnen in einer Ansicht](drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Benutzereingabe für die Ansicht

In der Ansicht kann auch ein Mausklick in sich selbst als Auswahl oder Bearbeitung von Daten interpretiert werden. Auf ähnliche Weise können Tastatureingaben als Dateneingabe oder-Bearbeitung interpretiert werden. Angenommen, der Benutzer gibt eine Zeichenfolge in einer Ansicht ein, die Text verwaltet. Die Ansicht erhält einen Zeiger auf das Dokument und verwendet den-Zeiger, um die neuen Daten an das Dokument zu übergeben, das in einer Datenstruktur gespeichert wird.

## <a name="updating-multiple-views-of-the-same-document"></a>Aktualisieren mehrerer Ansichten desselben Dokuments

In einer Anwendung mit mehreren Ansichten desselben Dokuments – z. b. ein Splitter Fenster in einem Text-Editor – übergibt die Ansicht zunächst die neuen Daten an das Dokument. Anschließend wird die [UpdateAllViews](reference/cdocument-class.md#updateallviews) -Member-Funktion des Dokuments aufgerufen, die alle Sichten des Dokuments anweist, sich selbst zu aktualisieren und die neuen Daten widerzuspiegeln. Dadurch werden die Ansichten synchronisiert.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Vorteile der Dokument-/Ansichtarchitektur](advantages-of-the-document-view-architecture.md)

- [Alternativen zur Dokument-/Ansichtarchitektur](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Weitere Informationen

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
