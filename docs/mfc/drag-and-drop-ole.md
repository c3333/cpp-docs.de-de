---
title: Drag & Drop (OLE)
description: Übersicht über Microsoft Foundation Classes (MFC) OLE-Drag & Drop, das Implementieren einer Ablage Quelle, ein Ablage Ziel und das Anpassen von Drag & Drop.
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 23680765377d325bdc1f8878daf4d4fc553a1304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623192"
---
# <a name="ole-drag-and-drop"></a>Drag & Drop (OLE)

Die Drag & Drop-Funktion von OLE ist hauptsächlich eine Verknüpfung zum Kopieren und Einfügen von Daten. Wenn Sie die Zwischenablage zum Kopieren oder Einfügen von Daten verwenden, sind mehrere Schritte erforderlich. Wählen Sie die Daten aus, und wählen Sie im Menü **Bearbeiten** die Option **Ausschneiden** oder **Kopieren** aus. Wechseln Sie dann zur Ziel-APP oder zum Zielfenster, und platzieren Sie den Cursor am Ziel Speicherort. Schließlich **Wählen Sie**  >  im Menü die Option "**Einfügen** " aus.

Die Drag & Drop-Funktion von OLE unterscheidet sich vom Drag & Drop-Mechanismus des Datei-Managers. Der Datei-Manager kann nur Dateinamen verarbeiten und dient speziell zum Übergeben von Dateinamen an Anwendungen. Drag & Drop in OLE ist weitaus allgemeiner. Sie ermöglicht das ziehen und Ablegen von Daten, die auch in die Zwischenablage eingefügt werden können.

Wenn Sie OLE Drag & amp; Drop verwenden, entfernen Sie zwei Schritte aus dem Prozess. Wählen Sie die Daten aus dem Quell Code Fenster ("Drop Source") aus, und ziehen Sie Sie dann auf das Ziel ("Drop Target"). Sie löschen Sie, indem Sie die Maustaste loslassen. Durch den-Vorgang entfällt die Notwendigkeit von Menüs, und es ist schneller als die Sequenz zum Kopieren/Einfügen. Es gibt nur eine Anforderung: sowohl die Ablage Quelle als auch das Ablage Ziel müssen geöffnet und zumindest teilweise auf dem Bildschirm sichtbar sein.

Mithilfe von OLE Drag & Drop können Daten problemlos von einem Speicherort an einen anderen übertragen werden: innerhalb eines Dokuments, zwischen verschiedenen Dokumenten oder zwischen Anwendungen. Sie kann entweder in einer Container-oder einer Serveranwendung implementiert werden. Jede Anwendung kann eine Ablage Quelle, ein Ablage Ziel oder beides sein. Wenn eine Anwendung sowohl Drop-Source-als auch Drop-Target-Unterstützung implementiert, können Sie zwischen untergeordneten Fenstern oder innerhalb eines Fensters ziehen und ablegen. Diese Funktion erleichtert die Verwendung Ihrer Anwendung.

In den Artikeln zu [Datenobjekten und Datenquellen (OLE)](data-objects-and-data-sources-ole.md) wird erläutert, wie die Datenübertragung in Ihren Anwendungen implementiert wird. Außerdem ist es hilfreich, die MFC-OLE-Beispiele [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md)zu untersuchen.

## <a name="implement-a-drop-source"></a><a name="implement-a-drop-source"></a>Implementieren einer Ablage Quelle

Damit Ihre Anwendung Daten für einen Drag & Drop-Vorgang bereitstellen kann, implementieren Sie eine Drop-Quelle. Die grundlegende Implementierung einer Drop-Quelle ist relativ einfach. Der erste Schritt besteht darin, zu bestimmen, welche Ereignisse einen Zieh Vorgang beginnen. Empfohlene Richtlinien für die Benutzeroberfläche definieren den Anfang eines Zieh Vorgangs, als wenn ein **WM_LBUTTONDOWN** Ereignis an einem Punkt innerhalb einiger ausgewählter Daten auftritt. Die MFC-OLE-Beispiele [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md) befolgen diese Richtlinien.

Wenn es sich bei der Anwendung um einen Container handelt und die ausgewählten Daten ein verknüpftes oder eingebettetes Objekt vom Typ sind `COleClientItem` , müssen Sie Ihre Member-Funktion aufzurufen `DoDragDrop` . Erstellen Sie andernfalls ein `COleDataSource` -Objekt, initialisieren Sie es mit der Auswahl, und wenden Sie die Member-Funktion des Datenquellen Objekts an `DoDragDrop` . Wenn es sich bei der Anwendung um einen Server handelt, verwenden Sie `COleServerItem::DoDragDrop` . Weitere Informationen zum Anpassen des standardmäßigen Drag & Drop-Verhaltens finden Sie im Abschnitt [Anpassen von Drag & Drop](#customize-drag-and-drop).

Wenn `DoDragDrop` **DROPEFFECT_MOVE**zurückgibt, löschen Sie die Quelldaten sofort aus dem Quelldokument. Kein anderer Rückgabewert aus wirkt `DoDragDrop` sich auf eine Drop-Quelle aus.

Weitere Informationen finden Sie unter [OLE-Datenobjekte und Datenquellen: Erstellen und zerstören](data-objects-and-data-sources-creation-and-destruction.md) und [OLE-Datenobjekte und Datenquellen: Manipulation](data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a><a name="implement-a-drop-target"></a>Implementieren eines Ablage Ziels

Es ist etwas mehr Arbeit, ein Ablage Ziel als eine Drop-Quelle zu implementieren, aber es ist immer noch relativ einfach.

### <a name="to-implement-an-ole-drop-target"></a>So implementieren Sie ein OLE-Ablage Ziel

1. Wenn Sie noch nicht vorhanden ist, fügen Sie `AfxOleInit` in der Member-Funktion Ihrer Anwendung einen-Rückruf hinzu `InitInstance` . Dieser-Befehl ist erforderlich, um die OLE-Bibliotheken zu initialisieren.

1. Fügen Sie jeder Ansicht in der Anwendung, die ein Ablage Ziel sein soll, eine Member-Variable hinzu. Diese Member-Variable muss vom Typ `COleDropTarget` oder einer von ihr abgeleiteten Klasse sein.

1. In der Funktion der Ansichts Klasse, die die **WM_CREATE** Nachricht verarbeitet (in der Regel `OnCreate` ), wird die Member-Funktion der neuen Element Variablen aufgerufen `Register` . `Revoke`wird automatisch für Sie aufgerufen, wenn Ihre Ansicht zerstört wird.

1. Überschreiben Sie die folgenden Funktionen. Wenn Sie das gleiche Verhalten in der gesamten Anwendung wünschen, überschreiben Sie diese Funktionen in der Ansichts Klasse. Wenn Sie das Verhalten in isolierten Fällen ändern oder das Ablegen unter nicht-Windows aktivieren möchten `CView` , überschreiben Sie diese Funktionen in der von `COleDropTarget` abgeleiteten Klasse.

   | Überschreiben | So lassen Sie |
   | -------- | -------- |
   | `OnDragEnter` | Drop-Vorgänge, die im Fenster auftreten. Wird aufgerufen, wenn der Cursor zuerst das Fenster betritt. |
   | `OnDragLeave` | Besonderes Verhalten, wenn der Zieh Vorgang das angegebene Fenster verlässt. |
   | `OnDragOver` | Drop-Vorgänge, die im Fenster auftreten. Wird aufgerufen, wenn der Cursor über das Fenster gezogen wird. |
   | `OnDrop` | Behandlung von Daten, die im angegebenen Fenster abgelegt werden. |
   | `OnScrollBy` | Spezielles Verhalten für den Fall, dass im Zielfenster ein Bildlauf notwendig ist. |

Weitere Informationen finden Sie unter MAINVIEW. Cpp-Datei, die Teil des MFC-OLE- [beispieloclient](../overview/visual-cpp-samples.md) ist, um ein Beispiel dafür zu finden, wie diese Funktionen zusammenarbeiten.

Weitere Informationen finden Sie unter [OLE-Datenobjekte und Datenquellen: Erstellen und zerstören](data-objects-and-data-sources-creation-and-destruction.md) und [OLE-Datenobjekte und Datenquellen: Manipulation](data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a><a name="customize-drag-and-drop"></a>Drag & Drop anpassen

Die Standard Implementierung der Drag & Drop-Funktion ist für die meisten Anwendungen ausreichend. Bei einigen Anwendungen ist es jedoch möglicherweise erforderlich, dieses Standardverhalten zu ändern. In diesem Abschnitt werden die erforderlichen Schritte zum Ändern dieser Standardeinstellungen erläutert. Sie können diese Technik verwenden, um Anwendungen, die Verbund Dokumente nicht unterstützen, in Ablage Quellen zu setzen.

Wenn Sie das standardmäßige OLE-Drag & Drop-Verhalten anpassen oder eine nicht-OLE-Anwendung verwenden, müssen Sie ein-Objekt erstellen, `COleDataSource` das die Daten enthält. Wenn der Benutzer einen Drag & Drop-Vorgang startet, sollte der Code die `DoDragDrop` Funktion aus diesem Objekt anstelle von anderen Klassen, die Drag & Drop-Vorgänge unterstützen, aufruft.

Optional können Sie ein `COleDropSource` -Objekt erstellen, um den Löschvorgang zu steuern und einige seiner Funktionen zu überschreiben, abhängig vom Typ des Verhaltens, das Sie ändern möchten. Dieses Drop-Source-Objekt wird dann an weitergegeben `COleDataSource::DoDragDrop` , um das Standardverhalten dieser Funktionen zu ändern. Diese unterschiedlichen Optionen ermöglichen eine hohe Flexibilität bei der Unterstützung von Drag & Drop-Vorgängen in Ihrer Anwendung. Weitere Informationen zu Datenquellen finden Sie im Artikel [Datenobjekte und Datenquellen (OLE)](data-objects-and-data-sources-ole.md).

Sie können die folgenden Funktionen überschreiben, um Drag & Drop-Vorgänge anzupassen:

| Überschreiben | Anpassen |
| -------- | ------------ |
| `OnBeginDrag` | Gibt an, wie der Zieh Vorgang beginnt, nachdem Sie aufgerufen haben `DoDragDrop` . |
| `GiveFeedback` | Visuelles Feedback, wie z. b. Cursor Darstellung, für verschiedene Ablage Ergebnisse. |
| `QueryContinueDrag` | Die Beendigung eines Drag & Drop-Vorgangs. Diese Funktion ermöglicht das Überprüfen von modifiziererschlüsselzuständen während des Zieh Vorgangs. |

## <a name="see-also"></a>Siehe auch

[Schieren](ole-in-mfc.md)\
[OLE-Datenobjekte und-Datenquellen](data-objects-and-data-sources-ole.md)\
[OLE-Datenobjekte und Datenquellen: Erstellen und zerstören](data-objects-and-data-sources-creation-and-destruction.md)\
[OLE-Datenobjekte und Datenquellen: Bearbeitung](data-objects-and-data-sources-manipulation.md)\
[COleClientItem::D odragdrop](reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource-Klasse](reference/coledatasource-class.md)\
[COleDataSource::D odragdrop](reference/coledatasource-class.md#dodragdrop)\
[COleDropSource-Klasse](reference/coledropsource-class.md)\
[COleDropTarget-Klasse](reference/coledroptarget-class.md)\
[CView:: OnDragLeave](reference/cview-class.md#ondragleave)
