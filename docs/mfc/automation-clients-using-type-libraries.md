---
title: 'Automatisierungsclients: Verwenden von Typbibliotheken'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: e5f9ffcebc3725851c599e7b21369f45d0029d81
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626087"
---
# <a name="automation-clients-using-type-libraries"></a>Automatisierungsclients: Verwenden von Typbibliotheken

Automatisierungs Clients müssen Informationen zu den Eigenschaften und Methoden von Server Objekten aufweisen, wenn die Clients die Objekte der Server bearbeiten. Eigenschaften weisen Datentypen auf. Methoden geben häufig Werte zurück und akzeptieren Parameter. Der Client benötigt Informationen zu den Datentypen aller diese, um statisch an den Server Objekttyp gebunden zu werden.

Diese Typinformationen können auf verschiedene Weise bekannt gemacht werden. Die empfohlene Vorgehensweise ist das Erstellen einer Typbibliothek.

Weitere Informationen zu [MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib)finden Sie in der Windows SDK.

Visual C++ können eine Typbibliotheks Datei lesen und eine Dispatch-Klasse erstellen, die von [COleDispatchDriver](reference/coledispatchdriver-class.md)abgeleitet ist. Ein Objekt dieser Klasse verfügt über Eigenschaften und Vorgänge, die die des Server Objekts duplizieren. Die Anwendung ruft die Eigenschaften und Vorgänge dieses Objekts auf, und die von geerbte Funktionalität `COleDispatchDriver` leitet diese Aufrufe an das OLE-System weiter, das Sie wiederum an das Server Objekt weiterleitet.

Visual C++ diese Typbibliotheks Datei automatisch für Sie verwaltet, wenn Sie die Automatisierung beim Erstellen des Projekts ausgewählt haben. Als Teil jedes Builds wird die TLB-Datei mit MkTypLib erstellt.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>So erstellen Sie eine Dispatch-Klasse aus einer Typbibliotheks Datei (. tlb)

1. Klicken Sie entweder in Klassenansicht oder Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Hinzufügen** und dann im Kontextmenü auf **Klasse hinzufügen** .

1. Wählen Sie im Dialogfeld **Klasse hinzufügen** im linken Bereich den Ordner **Visual C++/MFC** aus. Wählen Sie im rechten Bereich die **MFC-Klasse vom TypeLib** -Symbol aus, und klicken Sie auf **Öffnen**.

1. Wählen Sie im Dialogfeld **Klasse aus TypeLib hinzufügen** eine Typbibliothek aus der Dropdown Liste **Verfügbare Typbibliotheken** aus. Im Feld **Schnittstellen** werden die Schnittstellen angezeigt, die für die ausgewählte Typbibliothek verfügbar sind.

    > [!NOTE]
    >  Sie können Schnittstellen aus mehr als einer Typbibliothek auswählen.

   Um Schnittstellen auszuwählen, doppelklicken Sie darauf, oder klicken Sie auf die Schaltfläche **Hinzufügen** . Wenn Sie dies tun, werden die Namen für die Dispatch-Klassen im Feld **generierte Klassen** angezeigt. Sie können die Klassennamen im Feld bearbeiten `Class` .

   Im Feld **Datei** wird die Datei angezeigt, in der die Klasse deklariert wird. (Sie können diesen Dateinamen auch bearbeiten.) Sie können auch die Schaltfläche Durchsuchen verwenden, um andere Dateien auszuwählen, wenn Sie möchten, dass die Header-und Implementierungs Informationen in vorhandenen Dateien oder in einem anderen Verzeichnis als dem Projektverzeichnis geschrieben werden.

    > [!NOTE]
    >  Alle Dispatchklassen für die ausgewählten Schnittstellen werden in die hier angegebene Datei eingefügt. Wenn Sie möchten, dass die Schnittstellen in separaten Headern deklariert werden, müssen Sie diesen Assistenten für jede Header Datei ausführen, die Sie erstellen möchten.

    > [!NOTE]
    >  Einige Typbibliotheks Informationen können in Dateien mit gespeichert werden. DLL,. OCX oder. OLB-Dateierweiterungen.

1. Klicken Sie auf **Fertig stellen**.

   Der Assistent schreibt dann den Code für die Dispatch-Klassen mithilfe der angegebenen Klassen-und Dateinamen.

## <a name="see-also"></a>Siehe auch

[Automatisierungsclients](automation-clients.md)
