---
title: Asynchrone Moniker im Internet
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: 74add1ad894f883c67eefab888898c0abf518b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625036"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Asynchrone Moniker im Internet

Das Internet erfordert aufgrund des langsamen Netzwerk Zugriffs neue Ansätze für den Anwendungs Entwurf. Anwendungen sollten den Netzwerk Zugriff asynchron durchführen, um zu verhindern, dass die Benutzeroberfläche blockiert wird. Die MFC-Klasse [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) bietet asynchrone Unterstützung für das Herunterladen von Dateien.

Mit asynchronen Monikern können Sie die COM-Anwendung so erweitern, dass Sie asynchron über das Internet heruntergeladen wird, und das Progressive Rendering von großen Objekten, wie z. b. Bitmaps und VRML-Objekten, ermöglichen. Asynchrone Moniker ermöglichen das Herunterladen einer ActiveX-Steuerelement Eigenschaft oder einer Datei im Internet, ohne dass die Antwort auf die Benutzeroberfläche blockiert wird.

## <a name="advantages-of-asynchronous-monikers"></a>Vorteile von asynchronen Monikern

Sie können asynchrone Moniker für Folgendes verwenden:

- Herunterladen von Code und Dateien ohne Blockierung.

- Herunterladen von Eigenschaften in ActiveX-Steuerelementen ohne Blockierung

- Empfangen von Benachrichtigungen über den Download Fortschritt.

- Verfolgen Sie den Status und die Statusinformationen.

- Bereitstellen von Statusinformationen für den Benutzer über den Fortschritt.

- Ermöglicht es dem Benutzer, einen Download jederzeit abzubrechen.

## <a name="mfc-classes-for-asynchronous-monikers"></a>MFC-Klassen für asynchrone Moniker

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md) ist von [CMonikerFile](reference/cmonikerfile-class.md)abgeleitet, das wiederum von [colestreamfile](reference/colestreamfile-class.md)abgeleitet ist. Ein `COleStreamFile` -Objekt stellt einen Datenstrom dar `CMonikerFile` . ein-Objekt verwendet, `IMoniker` um die Daten abzurufen, und ein- `CAsyncMonikerFile` Objekt führt dies asynchron aus.

Asynchrone Moniker werden hauptsächlich in Internet fähigen Anwendungen und ActiveX-Steuerelementen verwendet, um während der Übertragung von Dateien eine reaktionsfähige Benutzeroberfläche bereitzustellen. Ein gutes Beispiel hierfür ist die Verwendung von [CDataPathProperty](reference/cdatapathproperty-class.md) , um asynchrone Eigenschaften für ActiveX-Steuerelemente bereitzustellen.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>MFC-Klassen für Daten Pfade in ActiveX-Steuerelementen

Die MFC `CDataPathProperty` -Klassen und [CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md) implementieren ActiveX-Steuerelement Eigenschaften, die asynchron geladen werden können. Asynchrone Eigenschaften werden nach der synchronen Initiierung geladen. Asynchrone ActiveX-Steuerelemente rufen wiederholt einen Rückruf auf, um die Verfügbarkeit neuer Daten während eines langen Eigenschaften Austauschvorgangs anzugeben.

`CDataPathProperty` wird von `CAsyncMonikerFile` abgeleitet. `CCachedDataPathProperty` wird von `CDataPathProperty` abgeleitet. Um asynchrone Eigenschaften in ihren ActiveX-Steuerelementen zu implementieren, leiten Sie eine Klasse von `CDataPathProperty` oder ab `CCachedDataPathProperty` , und überschreiben Sie [ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) und andere Benachrichtigungen, die Sie empfangen möchten.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>So laden Sie eine Datei mithilfe von asynchronen Monikern herunter

1. Deklarieren Sie eine von [CAsyncMonikerFile](reference/casyncmonikerfile-class.md)abgeleitete Klasse.

1. Überschreiben Sie [ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) , um die Daten anzuzeigen.

1. Überschreiben Sie andere Element Funktionen, einschließlich " [OnProgress](reference/casyncmonikerfile-class.md#onprogress)", " [onstartbinding](reference/casyncmonikerfile-class.md#onstartbinding)" und " [onstopbinding](reference/casyncmonikerfile-class.md#onstopbinding)".

1. Deklarieren Sie eine Instanz dieser Klasse, und verwenden Sie Sie zum Öffnen von URLs.

Weitere Informationen zum asynchronen Herunterladen in einem ActiveX-Steuerelement finden Sie unter ActiveX-Steuer [Elemente im Internet](activex-controls-on-the-internet.md).

## <a name="see-also"></a>Siehe auch

[MFC-Internetprogrammierungsaufgaben](mfc-internet-programming-tasks.md)<br/>
[Grundlagen der MFC-Internetprogrammierung](mfc-internet-programming-basics.md)
