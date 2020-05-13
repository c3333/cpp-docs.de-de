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
ms.openlocfilehash: c8e79f54ed586201a7d82327662643a9a241b8f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357268"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Verwalten der Statusdaten von MFC-Modulen

In diesem Artikel werden die Statusdaten von MFC-Modulen erläutert und erläutert, wie dieser Status aktualisiert wird, wenn der Ausführungsfluss (der Pfadcode durch eine Anwendung bei der Ausführung führt) ein Modul ein- und verlässt. Auch Schaltmodulzustände mit den AFX_MANAGE_STATE und METHOD_PROLOGUE Makros werden diskutiert.

> [!NOTE]
> Der Begriff "Modul" bezieht sich hier auf ein ausführbares Programm oder auf eine DLL (oder einen Satz von DLLs), die unabhängig vom Rest der Anwendung arbeiten, aber eine freigegebene Kopie der MFC-DLL verwenden. Ein ActiveX-Steuerelement ist ein typisches Beispiel für ein Modul.

Wie in der folgenden Abbildung dargestellt, verfügt MFC über Zustandsdaten für jedes Modul, das in einer Anwendung verwendet wird. Beispiele für diese Daten sind Windows-Instanzhandles (zum Laden `CWinApp` von `CWinThread` Ressourcen), Zeiger auf den aktuellen Wert und Objekte einer Anwendung, OLE-Modul-Verweisanzahlen und eine Vielzahl von Zuordnungen, die die Verbindungen zwischen Windows-Objekthandles und entsprechenden Instanzen von MFC-Objekten verwalten. Wenn eine Anwendung jedoch mehrere Module verwendet, sind die Zustandsdaten der einzelnen Module nicht anwendungsweit. Stattdessen verfügt jedes Modul über eine eigene private Kopie der Statusdaten der MFC.

![Zustandsdaten eines einzelnen Moduls &#40;Anwendung&#41;](../mfc/media/vc387n1.gif "Zustandsdaten eines einzelnen Moduls &#40;Anwendung&#41;") <br/>
Zustandsdaten eines Einzelmoduls (Anwendung)

Die Zustandsdaten eines Moduls sind in einer Struktur enthalten und stehen immer über einen Zeiger auf diese Struktur zur Verfügung. Wenn der Ausführungsfluss in ein bestimmtes Modul eintritt, wie in der folgenden Abbildung dargestellt, muss der Zustand dieses Moduls der "aktuelle" oder "effektive" Zustand sein. Daher verfügt jedes Threadobjekt über einen Zeiger auf die effektive Zustandsstruktur dieser Anwendung. Die Aktualisierung dieses Zeigers ist für die Verwaltung des globalen Status der Anwendung und die Aufrechterhaltung der Integrität des Status jedes Moduls von entscheidender Bedeutung. Eine falsche Verwaltung des globalen Status kann zu einem unvorhersehbaren Anwendungsverhalten führen.

![Zustandsdaten mehrerer Module](../mfc/media/vc387n2.gif "Zustandsdaten mehrerer Module") <br/>
Zustandsdaten mehrerer Module

Mit anderen Worten, jedes Modul ist für das korrekte Umschalten zwischen Denzuständen an allen Einstiegspunkten verantwortlich. Ein "Einstiegspunkt" ist ein beliebiger Ort, an dem der Ausführungsfluss in den Code des Moduls eingegeben werden kann. Zu den Einstiegspunkten gehören:

- [Exportierte Funktionen in einer DLL](../mfc/exported-dll-function-entry-points.md)

- [Mitgliedsfunktionen von COM-Schnittstellen](../mfc/com-interface-entry-points.md)

- [Fensterprozeduren](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
