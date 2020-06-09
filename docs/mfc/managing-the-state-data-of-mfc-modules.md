---
title: Verwalten der Statusdaten von MFC-Modulen
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: 64888b8ab53ebd80f328e1efe79df6256f30f9b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622571"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Verwalten der Statusdaten von MFC-Modulen

In diesem Artikel werden die Statusdaten von MFC-Modulen erläutert und erläutert, wie dieser Status aktualisiert wird, wenn der Ausführungs Fluss (der pfadcode, der beim Ausführen einer Anwendung durchläuft) ein Modul eingibt und verlässt. Das Wechseln von Modul Zuständen mit den AFX_MANAGE_STATE-und METHOD_PROLOGUE-Makros wird ebenfalls erläutert.

> [!NOTE]
> Der Begriff "Module" bezieht sich hier auf ein ausführbares Programm oder eine DLL (oder eine Gruppe von DLLs), die unabhängig vom Rest der Anwendung ausgeführt wird, aber eine freigegebene Kopie der MFC-DLL verwendet. Ein ActiveX-Steuerelement ist ein typisches Beispiel für ein Modul.

Wie in der folgenden Abbildung gezeigt, weist MFC Zustandsdaten für jedes in einer Anwendung verwendete Modul auf. Zu den Beispielen für diese Daten zählen Windows-Instanzhandles (für das Laden von Ressourcen), Zeiger auf das aktuelle `CWinApp` -Objekt und das-Objekt einer `CWinThread` Anwendung, die OLE-Modul Verweis Zähler und eine Vielzahl von Zuordnungen, die die Verbindungen zwischen Windows-Objekt Handles und entsprechenden Instanzen von MFC-Objekten verwalten. Wenn eine Anwendung jedoch mehrere Module verwendet, sind die Zustandsdaten der einzelnen Module nicht Anwendungs weit. Stattdessen verfügt jedes Modul über eine eigene private Kopie der Zustandsdaten des MFC.

![Zustandsdaten eines einzelnen Moduls &#40;Anwendung&#41;](../mfc/media/vc387n1.gif "Zustandsdaten eines einzelnen Moduls &#40;Anwendung&#41;") <br/>
Zustandsdaten eines Einzelmoduls (Anwendung)

Die Zustandsdaten eines Moduls sind in einer Struktur enthalten und sind immer über einen Zeiger auf diese Struktur verfügbar. Wenn der Ausführungs Fluss in ein bestimmtes Modul eintritt, wie in der folgenden Abbildung gezeigt, muss der Zustand des Moduls der Status "Current" oder "Effective" sein. Daher verfügt jedes Thread Objekt über einen Zeiger auf die effektive Zustands Struktur der Anwendung. Wenn Sie diesen Zeiger jederzeit aktualisieren lassen, ist es wichtig, den globalen Zustand der Anwendung zu verwalten und die Integrität der einzelnen Modul Zustände aufrechtzuerhalten. Eine falsche Verwaltung des globalen Zustands kann zu unvorhersehbarem Anwendungsverhalten führen.

![Zustandsdaten mehrerer Module](../mfc/media/vc387n2.gif "Zustandsdaten mehrerer Module") <br/>
Zustandsdaten mehrerer Module

Mit anderen Worten, jedes Modul ist für das ordnungsgemäße wechseln zwischen den Modul Zuständen an allen Einstiegspunkten verantwortlich. Ein Einstiegspunkt ist eine beliebige Stelle, an der der Ausführungs Fluss den Modul Code eingeben kann. Zu den Einstiegspunkten zählen:

- [Exportierte Funktionen in einer dll](exported-dll-function-entry-points.md)

- [Member-Funktionen von COM-Schnittstellen](com-interface-entry-points.md)

- [Fenster Prozeduren](window-procedure-entry-points.md)

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](general-mfc-topics.md)
