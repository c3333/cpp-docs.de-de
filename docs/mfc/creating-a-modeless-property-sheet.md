---
title: Erstellen eines nicht modalen Eigenschaftenblatts
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 7a44d96adf0a25a401fbc2e561bd7d32758a37d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617168"
---
# <a name="creating-a-modeless-property-sheet"></a>Erstellen eines nicht modalen Eigenschaftenblatts

Normalerweise sind die von Ihnen erstellten Eigenschaften Blätter modal. Wenn Sie ein modales Eigenschaften Blatt verwenden, muss der Benutzer das Eigenschaften Blatt schließen, bevor ein anderer Teil der Anwendung verwendet werden kann. In diesem Artikel werden Methoden beschrieben, die Sie zum Erstellen eines nicht modalem Eigenschaften Blatts verwenden können, mit dem der Benutzer das Eigenschaften Blatt während der Verwendung anderer Teile der Anwendung geöffnet lassen kann.

Um ein Eigenschaften Blatt als nicht modales Dialogfeld, sondern als nicht modales Dialogfeld anzuzeigen, rufen Sie [CPropertySheet:: Create](reference/cpropertysheet-class.md#create) anstelle von [DoModal](reference/cpropertysheet-class.md#domodal)auf. Außerdem müssen Sie einige zusätzliche Aufgaben implementieren, um ein nicht modalem Eigenschaften Blatt zu unterstützen.

Zu den zusätzlichen Aufgaben gehört der Austausch von Daten zwischen dem Eigenschaften Blatt und dem externen Objekt, das es ändert, wenn das Eigenschaften Blatt geöffnet ist. Dabei handelt es sich im Allgemeinen um dieselbe Aufgabe wie für standardmäßige, nicht modante Dialogfelder. Ein Teil dieser Aufgabe ist die Implementierung eines Kommunikationskanals zwischen dem nicht modalem Eigenschaften Blatt und dem externen Objekt, auf das die Eigenschaften Einstellungen angewendet werden. Diese Implementierung ist weitaus einfacher, wenn Sie eine Klasse von [CPropertySheet](reference/cpropertysheet-class.md) für Ihr nicht modalem Eigenschaften Blatt ableiten. In diesem Artikel wird davon ausgegangen, dass Sie dies erledigt haben

Eine Methode für die Kommunikation zwischen dem nicht modalem Eigenschaften Blatt und dem externen Objekt (z. b. die aktuelle Auswahl in einer Ansicht) besteht darin, einen Zeiger aus dem Eigenschaften Blatt auf das externe Objekt zu definieren. Definieren `SetMyExternalObject` Sie in der von abgeleiteten Klasse eine Funktion (so genannte) `CPropertySheet` , um den Zeiger zu ändern, wenn sich der Fokus von einem externen Objekt zu einem anderen ändert. Die `SetMyExternalObject` Funktion muss die Einstellungen für jede Eigenschaften Seite zurücksetzen, um das neu ausgewählte externe Objekt widerzuspiegeln. Um dies zu erreichen, `SetMyExternalObject` muss die Funktion auf die [CPropertyPage](reference/cpropertypage-class.md) -Objekte zugreifen können, die zur- `CPropertySheet` Klasse gehören.

Die einfachste Möglichkeit, den Zugriff auf Eigenschaften Seiten innerhalb eines Eigenschaften Blatts zu ermöglichen, besteht darin, die `CPropertyPage` Objekte in das von `CPropertySheet` abgeleitete Objekt einzubetten. Das `CPropertyPage` `CPropertySheet` Einbetten von Objekten in das von abgeleitete Objekt unterscheidet sich vom typischen Entwurf für modale Dialogfelder, in denen der Besitzer des Eigenschaften Blatts die `CPropertyPage` Objekte erstellt und über [CPropertySheet:: addPage](reference/cpropertysheet-class.md#addpage)an das Eigenschaften Blatt übergibt.

Es gibt viele Möglichkeiten für die Benutzeroberfläche, um zu bestimmen, wann die Einstellungen der Eigenschaften Seite "nicht modales" auf ein externes Objekt angewendet werden sollen. Eine Alternative besteht darin, die Einstellungen der aktuellen Eigenschaften Seite immer dann anzuwenden, wenn der Benutzer einen beliebigen Wert ändert. Eine weitere Alternative ist das Bereitstellen einer Schaltfläche "anwenden", die es dem Benutzer ermöglicht, Änderungen an den Eigenschaften Seiten zu sammeln, bevor Sie Sie an das externe Objekt übergeben. Informationen zu den Verwendungsmöglichkeiten der Schaltfläche anwenden finden Sie im Artikel [Behandeln der](handling-the-apply-button.md)Schaltfläche "anwenden".

## <a name="see-also"></a>Siehe auch

[Eigenschaften Blätter](property-sheets-mfc.md)<br/>
[Datenaustausch](exchanging-data.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
