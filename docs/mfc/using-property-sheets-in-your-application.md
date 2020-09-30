---
title: Verwenden von Eigenschaftenseiten in einer Anwendung
ms.date: 11/04/2016
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
ms.openlocfilehash: 789764c9af988135219bd710d4f8aec1cda9143a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504651"
---
# <a name="using-property-sheets-in-your-application"></a>Verwenden von Eigenschaftenseiten in einer Anwendung

Führen Sie die folgenden Schritte aus, um ein Eigenschaften Blatt in der Anwendung zu verwenden:

1. Erstellen Sie eine Dialogfeld Vorlagen-Ressource für jede Eigenschaften Seite. Beachten Sie, dass der Benutzer möglicherweise von einer Seite auf eine andere Seite wechselt. Legen Sie daher jede Seite so konsistent wie möglich fest.

   Die Dialog Vorlagen für alle Seiten müssen nicht die gleiche Größe aufweisen. Das Framework verwendet die Größe der größten Seite, um zu bestimmen, wie viel Speicherplatz auf dem Eigenschaften Blatt für die Eigenschaften Seiten belegt werden soll.

   Wenn Sie die Dialogfeld Vorlagen Ressource für eine Eigenschaften Seite erstellen, müssen Sie die folgenden Stile auf dem Eigenschaften Blatt Dialog Eigenschaften angeben:

   - Legen Sie auf der Seite **Allgemein** auf den Text fest **, der auf** der Registerkarte für diese Seite angezeigt werden soll.

   - Legen Sie auf der Seite **Stile** das Listenfeld **Stil** **auf unter**geordnetes Element fest.

   - Legen Sie das Feld **für die Rahmen Liste auf** der Seite **Stile** auf **dünn**fest.

   - Stellen Sie sicher, dass das Kontrollkästchen **TitleBar** auf der Seite **Stile** ausgewählt ist.

   - Stellen Sie sicher, dass das Kontrollkästchen **deaktiviert** auf der Seite **weitere Stile** ausgewählt ist.

1. Erstellen Sie eine von [CPropertyPage](../mfc/reference/cpropertypage-class.md)abgeleitete Klasse, die den einzelnen Eigenschaften Seiten-Dialog Vorlagen entspricht. Siehe [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md). Wählen Sie `CPropertyPage` als Basisklasse aus.

1. Erstellen Sie Element Variablen, um die Werte für diese Eigenschaften Seite zu speichern. Der Prozess zum Hinzufügen von Element Variablen zu einer Eigenschaften Seite entspricht dem Hinzufügen von Element Variablen zu einem Dialogfeld, da eine Eigenschaften Seite ein spezielles Dialogfeld ist. Weitere Informationen finden Sie unter [Definieren von Element Variablen für Dialog](../windows/adding-editing-or-deleting-controls.md)Feld Steuerelemente.

1. Erstellen Sie ein [CPropertySheet](../mfc/reference/cpropertysheet-class.md) -Objekt im Quellcode. In der Regel erstellen Sie das- `CPropertySheet` Objekt im-Handler für den Befehl, der das Eigenschaften Blatt anzeigt. Dieses Objekt stellt das gesamte Eigenschaften Blatt dar. Wenn Sie ein modales Eigenschaften Blatt mit der [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) -Funktion erstellen, liefert das Framework standardmäßig drei Befehls Schaltflächen: OK, Abbrechen und anwenden. Das Framework erstellt keine Befehls Schaltflächen für nicht mit der [Create](../mfc/reference/cpropertysheet-class.md#create) -Funktion erstellte nicht modalem Eigenschaften Blätter. Sie müssen keine Klasse von ableiten, `CPropertySheet` es sei denn, Sie möchten entweder andere Steuerelemente (z. b. ein Vorschaufenster) hinzufügen oder ein nicht modalem Eigenschaften Blatt anzeigen. Dieser Schritt ist für nicht modante Eigenschaften Blätter erforderlich, da Sie keine Standard Steuerelemente enthalten, die zum Schließen des Eigenschaften Blatts verwendet werden könnten.

1. Gehen Sie für jede Seite, die dem Eigenschaften Blatt hinzugefügt werden soll, wie folgt vor:

   - Erstellen Sie ein-Objekt für jede von `CPropertyPage` abgeleitete Klasse, die Sie zuvor in diesem Prozess erstellt haben.

   - Aufrufen von [CPropertySheet:: addPage](../mfc/reference/cpropertysheet-class.md#addpage) für jede Seite.

   In der Regel erstellt das Objekt, das den erstellt, `CPropertySheet` auch die- `CPropertyPage` Objekte in diesem Schritt. Wenn Sie jedoch eine von `CPropertySheet` abgeleitete Klasse implementieren, können Sie die `CPropertyPage` Objekte in das `CPropertySheet` `AddPage` -Objekt einbetten und für jede Seite aus dem von `CPropertySheet` abgeleiteten Klassenkonstruktor aufzurufen. `AddPage` Fügt das `CPropertyPage` -Objekt der Liste der Seiten des Eigenschaften Blatts hinzu, erstellt das Fenster für diese Seite jedoch nicht. Daher ist es nicht erforderlich, zu warten, bis die Erstellung des Eigenschaften Blatt Fensters aufgerufen wird `AddPage` . Sie können `AddPage` vom Konstruktor des Eigenschaften Blatts aus aufzurufen.

   Wenn ein Eigenschaften Blatt mehr Registerkarten enthält, als in eine einzelne Zeile des Eigenschaften Blatts passen, werden die Registerkarten standardmäßig in mehreren Zeilen gestapelt. Um das Stapeln zu deaktivieren, müssen Sie [CPropertySheet:: enablestackedtabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) aufrufen, wobei der-Parameter auf **false**festgelegt ist. Sie müssen `EnableStackedTabs` beim Erstellen des Eigenschaften Blatts aufzurufen.

1. Rufen Sie [CPropertySheet::D omodal](../mfc/reference/cpropertysheet-class.md#domodal) oder [Create](../mfc/reference/cpropertysheet-class.md#create) auf, um das Eigenschaften Blatt anzuzeigen. Rufen `DoModal` Sie auf, um ein Eigenschaften Blatt als modales Dialogfeld zu erstellen. Rufen Sie **Create** auf, um das Eigenschaften Blatt als nicht modalem Dialogfeld zu erstellen.

1. Austauschen von Daten zwischen Eigenschaften Seiten und dem Besitzer des Eigenschaften Blatts. Dies wird im Artikel austauschen von [Daten](../mfc/exchanging-data.md)erläutert.

Ein Beispiel für die Verwendung von Eigenschafts Blättern finden Sie unter MFC allgemeine Beispiel [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Weitere Informationen

[Eigenschaften Blätter](../mfc/property-sheets-mfc.md)
