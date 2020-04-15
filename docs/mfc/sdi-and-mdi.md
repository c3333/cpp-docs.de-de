---
title: SDI und MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372758"
---
# <a name="sdi-and-mdi"></a>SDI und MDI

MFC erleichtert die Arbeit mit SDI-Anwendungen (Single-Document Interface) und MDI-Anwendungen (Multiple Document Interface).

SDI-Anwendungen erlauben jeweils nur ein geöffnetes Dokumentrahmenfenster. MDI-Anwendungen ermöglichen das Öffnen mehrerer Dokumentrahmenfenster in derselben Instanz einer Anwendung. Eine MDI-Anwendung verfügt über ein Fenster, in dem mehrere untergeordnete MDI-Fenster geöffnet werden können, die selbst Rahmenfenster sind, die jeweils ein separates Dokument enthalten. In einigen Anwendungen können die untergeordneten Fenster unterschiedlicher Art sein, z. B. Diagrammfenster und Tabellenkalkulationsfenster. In diesem Fall kann sich die Menüleiste ändern, wenn untergeordnete MDI-Fenster unterschiedlicher Art aktiviert werden.

> [!NOTE]
> Unter Windows 95 und höher sind Anwendungen häufig SDI, da das Betriebssystem eine "dokumentzentrierte" Ansicht übernommen hat.

Weitere Informationen finden Sie unter [Dokumente, Ansichten und das Framework](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Siehe auch

[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
