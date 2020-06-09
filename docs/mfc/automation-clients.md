---
title: Automatisierungsclients
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 9c34f6fccd06635dfb686e6eb1f2cf895bb86989
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626082"
---
# <a name="automation-clients"></a>Automatisierungsclients

Automation ermöglicht es Ihrer Anwendung, in einer anderen Anwendung implementierte Objekte zu bearbeiten oder Objekte verfügbar zu machen, damit Sie bearbeitet werden können. Ein Automatisierungs Client ist eine Anwendung, die verfügbar gemachte Objekte, die zu einer anderen Anwendung gehören, bearbeiten kann. Die Anwendung, die die Objekte verfügbar macht, wird als Automatisierungsserver bezeichnet. Der Client bearbeitet die Objekte der Serveranwendung, indem er auf die Eigenschaften und Funktionen der Objekte zugreift.

### <a name="types-of-automation-clients"></a>Typen von Automatisierungs Clients

Es gibt zwei Arten von Automatisierungs Clients:

- Clients, die dynamisch (zur Laufzeit) Informationen zu den Eigenschaften und Vorgängen des Servers erhalten.

- Clients, die über statische Informationen verfügen (zur Kompilierzeit bereitgestellt), die die Eigenschaften und Vorgänge des Servers angeben.

Clients der ersten Art erhalten Informationen zu den Methoden und Eigenschaften des Servers, indem Sie den Mechanismus des OLE-Systems Abfragen `IDispatch` . Obwohl es für dynamische Clients geeignet ist, `IDispatch` ist für statische Clients schwierig zu verwenden, wenn die zu über mittelenden Objekte zum Zeitpunkt der Kompilierung bekannt sein müssen. Für statische gebundene Clients stellen die Microsoft Foundation Classes die [COleDispatchDriver](reference/coledispatchdriver-class.md) -Klasse bereit.

Statische gebundene Clients verwenden eine Proxy Klasse, die statisch mit der Client Anwendung verknüpft ist. Diese Klasse stellt eine typsichere C++-Kapselung der Eigenschaften und Vorgänge der Serveranwendung bereit.

Die-Klasse `COleDispatchDriver` stellt die Prinzipal Unterstützung für die Clientseite der Automatisierung bereit. Mit dem Dialogfeld **Neues Element hinzufügen** erstellen Sie eine von abgeleitete Klasse `COleDispatchDriver` .

Anschließend geben Sie die Typbibliotheks Datei an, in der die Eigenschaften und Funktionen des-Objekts der Serveranwendung beschrieben werden. Das Dialogfeld Element hinzufügen liest diese Datei und erstellt die `COleDispatchDriver` von abgeleitete Klasse mit Element Funktionen, die von der Anwendung aufgerufen werden können, um auf typsichere Weise auf die Objekte der Serveranwendung in C++ zuzugreifen. Durch die zusätzlichen Funktionen, die von geerbt werden, wird `COleDispatchDriver` der Aufruf des richtigen Automatisierungs Servers vereinfacht.

### <a name="handling-events-in-automation-clients"></a>Behandeln von Ereignissen in Automatisierungs Clients

Wenn Sie Ereignisse in Ihrem Automatisierungs Client behandeln möchten, müssen Sie eine Sink-Schnittstelle hinzufügen. MFC bietet Assistenten Unterstützung zum Hinzufügen von Sink-Schnittstellen für ActiveX-Steuerelemente, aber keine Unterstützung anderer com-Server.

## <a name="see-also"></a>Siehe auch

[Automatisierungsclients: Verwenden von Typbibliotheken](automation-clients-using-type-libraries.md)<br/>
[Automation](automation.md)<br/>
[MFC-Anwendungs-Assistent](reference/mfc-application-wizard.md)
