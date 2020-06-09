---
title: Mithilfe des MFC-Anwendungs-Assistenten erstellte Dokument- und Ansichtsklassen
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 766fe4efb37c199c5babb75ce2cb08ebf676cca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616049"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Mithilfe des MFC-Anwendungs-Assistenten erstellte Dokument- und Ansichtsklassen

Der MFC-Anwendungs-Assistent bietet Ihnen einen Vorsprung in der Programmentwicklung, indem Sie für Sie ein Skelett Dokument und eine Ansichts Klasse erstellen. Anschließend können Sie den [Klassen Befehle und Nachrichten](reference/mapping-messages-to-functions.md) zuordnen und den Visual C++ Quellcode-Editor verwenden, um ihre Member-Funktionen zu schreiben.

Die vom MFC-Anwendungs-Assistenten erstellte Dokument Klasse wird von der [CDocument](reference/cdocument-class.md)-Klasse abgeleitet. Die Ansichts Klasse wird von [CView](reference/cview-class.md)abgeleitet. Die Namen, die der Anwendungs-Assistent für diese Klassen und die darin enthaltenen Dateien enthält, basieren auf dem Projektnamen, den Sie im Dialogfeld des Anwendungs-Assistenten angeben. Im Anwendungs-Assistenten können Sie die Seite generierte Klassen verwenden, um die Standardnamen zu ändern.

Einige Anwendungen benötigen möglicherweise mehr als eine Dokument Klasse, eine Ansichts Klasse oder eine Frame Fenster Klasse. Weitere Informationen finden Sie unter [mehrere Dokumenttypen, Ansichten und Rahmen Fenster](multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
