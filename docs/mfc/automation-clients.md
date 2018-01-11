---
title: Automatisierungsclients | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cfb6aae5c947d1f36019e548c72b22a3304aa12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2017
---
# <a name="automation-clients"></a>Automatisierungsclients
Automatisierung ermöglicht es, für die Anwendung in einer anderen Anwendung implementierten Objekte zu bearbeiten oder Objekte verfügbar zu machen, damit sie bearbeitet werden können. Ein Automatisierungsclient ist eine Anwendung, die verfügbar gemachten Objekten gehören zu einer anderen Anwendung bearbeitet werden kann. Die Anwendung, die die Objekte verfügbar macht, wird den Automation-Server aufgerufen. Der Client bearbeitet die Serveranwendung Objekte durch den Zugriff auf diese Objekte Eigenschaften und Funktionen.  
  
### <a name="types-of-automation-clients"></a>Typen von Automatisierungsclients  
 Es gibt zwei Arten von Benutzeroberflächenautomatisierungs-Clients:  
  
-   Clients, die dynamisch (zur Laufzeit) Informationen über die Eigenschaften und Vorgänge des Servers zu erhalten.  
  
-   Clients, die statischen Informationen (zum Zeitpunkt der Kompilierung) besitzen, die die Eigenschaften und Vorgänge des Servers angibt.  
  
 Clients die erste Art Abrufen von Informationen über Methoden und Eigenschaften des Servers durch Abfragen der OLE-System `IDispatch` Mechanismus. Obwohl es ausreichend, um verwenden Sie für dynamische Clients ist `IDispatch` ist schwierig zu verwenden für statische Clients, auf dem Zeitpunkt kompilieren Objekte gesteuert wird zum bekannt sein muss. Geben Sie die Microsoft Foundation Classes für statisch gebundene Clients gilt, die [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) Klasse.  
  
 Statisch gebundene Clients verwenden eine Proxyklasse, die statisch ist, mit der Clientanwendung. Diese Klasse bietet eine typsichere C++ Kapselung von Eigenschaften und Vorgänge der Server-Anwendungsverzeichnis.  
  
 Die Klasse `COleDispatchDriver` bietet Unterstützung für die Clientseite der Automatisierung Prinzipale. Mithilfe der `Add New Item` (Dialogfeld), erstellen Sie eine Klasse, die von abgeleiteten `COleDispatchDriver`.  
  
 Geben Sie dann die Typbibliothek-Datei, die die Eigenschaften und Funktionen des Objekts die Serveranwendung beschrieben. Das Element hinzufügen-Dialogfeld liest diese Datei und erstellt die `COleDispatchDriver`-abgeleitete Klasse, mit Memberfunktionen, die Ihre Anwendung aufrufen kann, um die Serveranwendung-Objekten in C++ in einer typsicheren Weise zugreifen. Zusätzliche Funktionen von geerbten `COleDispatchDriver` vereinfacht den Prozess den richtigen Automatisierungsserver aufrufen.  
  
### <a name="handling-events-in-automation-clients"></a>Behandlung von Ereignissen in Benutzeroberflächenautomatisierungs-Clients  
 Wenn Sie Ereignisse in Ihren Automatisierungsclient behandeln möchten, müssen Sie eine Senkenschnittstelle hinzufügen. MFC bietet assistentenunterstützung senkenschnittstellen für ActiveX-Steuerelemente hinzufügen, jedoch für andere COM_Server nicht unterstützt. Informationen zum Hinzufügen einer Senkenschnittstelle in einem MFC-Client für die Schnittstellen beschrieben, die von COM-Servern finden Sie unter So wird's gemacht: Erstellen Sie eine Senke-Schnittstelle in MFC-basierte COM-Client (KB 181845) am [Http://support.microsoft.com/default.aspxscid=kb;en-us; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845).  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisierungsclients: Verwenden von Typbibliotheken](../mfc/automation-clients-using-type-libraries.md)   
 [Benutzeroberflächenautomatisierung](../mfc/automation.md)   
 [MFC-Anwendungs-Assistent](../mfc/reference/mfc-application-wizard.md)
