---
title: 'Zwischenablage: Daten kopieren und einfügen'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: ed3056ec4fb3d3098870a03522d3bf17f41fbe34
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620702"
---
# <a name="clipboard-copying-and-pasting-data"></a>Zwischenablage: Daten kopieren und einfügen

In diesem Thema werden die Mindestanforderungen beschrieben, die zum Implementieren von Kopieren in und Einfügen aus der Zwischenablage in der OLE-Anwendung erforderlich sind. Es wird empfohlen, dass Sie die Themen [zu Datenobjekten und Datenquellen (OLE)](data-objects-and-data-sources-ole.md) lesen, bevor Sie fortfahren.

Bevor Sie das Kopieren oder Einfügen implementieren können, müssen Sie zunächst Funktionen zum Verarbeiten der Optionen kopieren, Ausschneiden und Einfügen im Menü Bearbeiten bereitstellen.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Kopieren oder Ausschnitten von Daten

#### <a name="to-copy-data-to-the-clipboard"></a>So kopieren Sie Daten in die Zwischenablage

1. Bestimmen Sie, ob die zu kopierenden Datensystem eigene Daten sind oder ein eingebettetes oder verknüpftes Element ist.

   - Wenn die Daten eingebettet oder verknüpft sind, rufen Sie einen Zeiger auf das Objekt ab, `COleClientItem` das ausgewählt wurde.

   - Wenn die Daten nativ sind und es sich bei der Anwendung um einen Server handelt, erstellen Sie ein neues Objekt, `COleServerItem` das aus den ausgewählten Daten abgeleitet ist. Erstellen Sie andernfalls ein- `COleDataSource` Objekt für die Daten.

1. Ruft die Member-Funktion des ausgewählten Elements auf `CopyToClipboard` .

1. Wenn der Benutzer anstelle eines Kopiervorgangs einen Ausschneide Vorgang ausgewählt hat, löschen Sie die ausgewählten Daten aus Ihrer Anwendung.

Ein Beispiel für diese Sequenz finden Sie unter den `OnEditCut` Funktionen und `OnEditCopy` in den MFC-OLE-Beispielprogrammen [OCLIENT](../overview/visual-cpp-samples.md) und [Hierarchien](../overview/visual-cpp-samples.md). Beachten Sie, dass diese Beispiele einen Zeiger auf die aktuell ausgewählten Daten erhalten, sodass Schritt 1 bereits beendet ist.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Einfügen von Daten

Das Einfügen von Daten ist komplizierter als das Kopieren, da Sie das Format auswählen müssen, das beim Einfügen der Daten in die Anwendung verwendet werden soll.

#### <a name="to-paste-data-from-the-clipboard"></a>So fügen Sie Daten aus der Zwischenablage ein

1. Implementieren Sie in ihrer View-Klasse, `OnEditPaste` um Benutzer zu behandeln, indem Sie die Option Einfügen im Menü Bearbeiten auswählen.

1. `OnEditPaste`Erstellen Sie in der-Funktion ein `COleDataObject` -Objekt, und rufen `AttachClipboard` Sie seine Member-Funktion auf, um dieses Objekt mit den Daten in der Zwischenablage zu verknüpfen.

1. Ruft `COleDataObject::IsDataAvailable` auf, um zu überprüfen, ob ein bestimmtes Format verfügbar ist.

   Alternativ können Sie verwenden, `COleDataObject::BeginEnumFormats` um nach anderen Formaten zu suchen, bis Sie einen finden, der für Ihre Anwendung am besten geeignet ist.

1. Führen Sie das Einfügen des Formats aus.

Ein Beispiel dafür, wie dies funktioniert, finden Sie in der Implementierung der Element `OnEditPaste` Funktionen in den Ansichts Klassen, die in den MFC-OLE-Beispielprogrammen [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md)definiert sind.

> [!TIP]
> Der Hauptvorteil der Trennung des Einfügevorgangs in eine eigene Funktion besteht darin, dass derselbe einfügecode verwendet werden kann, wenn Daten während eines Drag & Drop-Vorgangs in der Anwendung abgelegt werden. Wie bei OCLIENT und HIERSVR `OnDrop` kann die Funktion auch aufgerufen `DoPasteItem` werden, um den Code wieder zu verwenden, der zum Implementieren von Einfügevorgängen geschrieben wurde.

Informationen zum Behandeln der Option zum Einfügen von Sonderzeichen im Menü Bearbeiten finden Sie in den Themen [Dialog Feldern in OLE](dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Hinzufügen anderer Formate](clipboard-adding-other-formats.md)

- [OLE-Datenobjekte und Datenquellen und einheitliche Datenübertragung](data-objects-and-data-sources-ole.md)

- [Drag &amp; Drop (OLE)](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus](clipboard-using-the-ole-clipboard-mechanism.md)
