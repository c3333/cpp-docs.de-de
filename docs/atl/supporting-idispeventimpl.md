---
title: Unterstützen von IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329325"
---
# <a name="supporting-idispeventimpl"></a>Unterstützen von IDispEventImpl

Die Vorlagenklasse [IDispEventImpl](../atl/reference/idispeventimpl-class.md) kann verwendet werden, um Unterstützung für Verbindungspunktsenken in Ihrer ATL-Klasse bereitzustellen. Eine Verbindungspunktsenke ermöglicht es Ihrer Klasse, Ereignisse zu verarbeiten, die von externen COM-Objekten ausgelöst werden. Diese Verbindungspunktsenken werden mit einer Ereignissenkenzuordnung zugeordnet, die von Ihrer Klasse bereitgestellt wird.

Um eine Verbindungspunktsenke für Ihre Klasse ordnungsgemäß zu implementieren, müssen die folgenden Schritte ausgeführt werden:

- Importieren der Typbibliotheken für jedes externe Objekt

- Deklarieren der `IDispEventImpl` Schnittstellen

- Deklarieren einer Ereignissenkenzuordnung

- Beratung und Unberatung der Anschlusspunkte

Die Schritte zum Implementieren einer Verbindungspunktsenke werden alle ausgeführt, indem nur die Headerdatei (.h) Ihrer Klasse geändert wird.

## <a name="importing-the-type-libraries"></a>Importieren der Typbibliotheken

Für jedes externe Objekt, dessen Ereignisse Sie verarbeiten möchten, müssen Sie die Typbibliothek importieren. Dieser Schritt definiert die Ereignisse, die behandelt werden können, und stellt Informationen bereit, die beim Deklarieren der Ereignissenkenzuordnung verwendet werden. Die [#import](../preprocessor/hash-import-directive-cpp.md) #import-Direktive kann dazu verwendet werden. Fügen Sie `#import` die erforderlichen Direktivenzeilen für jede Dispatch-Schnittstelle hinzu, die Sie der Headerdatei (.h) Ihrer Klasse unterstützen.

Im folgenden Beispiel wird die Typbibliothek`MSCAL.Calendar.7`eines externen COM-Servers importiert ( ):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Sie müssen über `#import` eine separate Anweisung für jede externe Typbibliothek verfügen, die Sie unterstützen.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarieren der IDispEventImpl-Schnittstellen

Nachdem Sie nun die Typbibliotheken jeder Dispatchschnittstelle importiert `IDispEventImpl` haben, müssen Sie separate Schnittstellen für jede externe Dispatchschnittstelle deklarieren. Ändern Sie die Deklaration `IDispEventImpl` Ihrer Klasse, indem Sie für jedes externe Objekt eine Schnittstellendeklaration hinzufügen. Weitere Informationen zu den Parametern finden Sie unter [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Der folgende Code deklariert zwei Verbindungspunktsenken für die `DCalendarEvents` Schnittstelle für `CMyCompositCtrl2`das von der Klasse implementierte COM-Objekt:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Deklarieren einer Ereignissenkenzuordnung

Damit die Ereignisbenachrichtigungen von der richtigen Funktion verarbeitet werden können, muss die Klasse jedes Ereignis an den richtigen Handler weiterleiten. Dies wird erreicht, indem eine Ereignissenkenzuordnung deklariert wird.

ATL stellt mehrere Makros [bereit, BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)und [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), die diese Zuordnung vereinfachen. Das Standardformat ist wie folgt:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

Im folgenden Beispiel wird eine Ereignissenkenzuordnung mit zwei Ereignishandlern deklariert:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

Die Implementierung ist fast abgeschlossen. Der letzte Schritt betrifft die Beratung und Unberatung der externen Schnittstellen.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Beratung und Unberatung der IDispEventImpl-Schnittstellen

Der letzte Schritt besteht darin, eine Methode zu implementieren, die alle Verbindungspunkte zu den richtigen Zeiten berät (oder nicht rät). Diese Beratung muss erfolgen, bevor die Kommunikation zwischen den externen Clients und Ihrem Objekt stattfinden kann. Bevor das Objekt sichtbar wird, wird jede externe Dispatchschnittstelle, die vom Objekt unterstützt wird, nach ausgehenden Schnittstellen abgefragt. Es wird eine Verbindung hergestellt, und es wird ein Verweis auf die ausgehende Schnittstelle verwendet, um Ereignisse aus dem Objekt zu behandeln. Dieses Verfahren wird als "Beratung" bezeichnet.

Nachdem Das Objekt mit den externen Schnittstellen abgeschlossen wurde, sollten die ausgehenden Schnittstellen benachrichtigt werden, dass sie nicht mehr von Ihrer Klasse verwendet werden. Dieser Prozess wird als "unadvising" bezeichnet.

Aufgrund der Einzigartigkeit von COM-Objekten variiert diese Prozedur zwischen Denimplementierungen im Detail und in der Ausführung. Diese Details gehen über den Rahmen dieses Themas hinaus und werden nicht behandelt.

## <a name="see-also"></a>Siehe auch

[Grundlagen von ATL COM-Objekten](../atl/fundamentals-of-atl-com-objects.md)
