---
title: Identifizieren der Elemente des DHTML-Steuerungsprojekts
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319508"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identifizieren der Elemente des DHTML-Steuerungsprojekts

Der größte Teil des DHTML-Steuercodes ist genau wie der für jedes ATL-Steuerelement erstellte. Für ein grundlegendes Verständnis des generischen Codes, arbeiten Sie sich durch das [ATL-Tutorial](../atl/active-template-library-atl-tutorial.md), und lesen Sie die Abschnitte [Erstellen eines ATL-Projekts](../atl/reference/creating-an-atl-project.md) und [Grundlagen von ATL COM-Objekten](../atl/fundamentals-of-atl-com-objects.md).

Ein DHTML-Steuerelement ähnelt jedem ATL-Steuerelement, außer:

- Zusätzlich zu den regulären Schnittstellen, die ein Steuerelement implementiert, implementiert es eine zusätzliche Schnittstelle, die für die Kommunikation zwischen dem C++-Code und der HTML-Benutzeroberfläche (UI) verwendet wird. Die HTML-Benutzeroberfläche ruft C++-Code mithilfe dieser Schnittstelle auf.

- Es wird eine HTML-Ressource für die Steuerelementbenutzeroberfläche erstellt.

- Es ermöglicht den Zugriff auf das DHTML-Objektmodell über die Membervariable `m_spBrowser`, die ein intelligenter Zeiger vom Typ [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))ist. Verwenden Sie diesen Zeiger, um auf einen beliebigen Teil des DHTML-Objektmodells zuzugreifen.

Die folgende Grafik veranschaulicht die Beziehung zwischen Ihrer DLL, dem DHTML-Steuerelement, dem Webbrowser und der HTML-Ressource.

![Elemente eines DHTML-Steuerelementprojekts](../atl/media/vc52en1.gif "Elemente eines DHTML-Steuerelementprojekts")

> [!NOTE]
> Die Namen in dieser Grafik sind Platzhalter. Die Namen Ihrer HTML-Ressource und die schnittstellen, die auf dem Steuerelement verfügbar gemacht werden, basieren auf den Namen, die Sie ihnen im ATL-Steuerelement-Assistenten zuweisen.

In dieser Grafik sind die Elemente:

- **Meine DLL** Die DLL, die mit dem ATL-Projekt-Assistenten erstellt wurde.

- **DHTML-Steuerelement** (`m_spBrowser`) Das DHTML-Steuerelement, das mit dem ATL-Objekt-Assistenten erstellt wurde. Dieses Steuerelement greift über die Schnittstelle des Webbrowserobjekts auf `IWebBrowser2`das Webbrowserobjekt und seine Methoden zu. Das Steuerelement selbst macht die folgenden beiden Schnittstellen verfügbar, zusätzlich zu den anderen Standardschnittstellen, die für ein Steuerelement erforderlich sind.

  - `IDHCTL1`Die Schnittstelle, die vom Steuerelement für die Verwendung nur durch den Container verfügbar gemacht wird.

  - `IDHCTLUI1`Die Dispatch-Schnittstelle für die Kommunikation zwischen dem C++-Code und der HTML-Benutzeroberfläche. Der Webbrowser verwendet die Dispatch-Schnittstelle des Steuerelements, um das Steuerelement anzuzeigen. Sie können verschiedene Methoden dieser Dispatchschnittstelle über die Benutzeroberfläche `window.external`des Steuerelements aufrufen, indem Sie auf aufrufen, gefolgt vom Methodennamen auf dieser Dispatchschnittstelle, die Sie aufrufen möchten. Sie würden `window.external` von einem SCRIPT-Tag innerhalb des HTML-Codes zugreifen, aus dem die Benutzeroberfläche für dieses Steuerelement besteht. Weitere Informationen zum Aufrufen externer Methoden in der Ressourcendatei finden Sie unter [Aufrufen von C++-Code aus DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** Die Ressourcen-ID der HTML-Ressource. Sein Dateiname ist in diesem Fall DHCTL1UI.htm. Das DHTML-Steuerelement verwendet eine HTML-Ressource, die Standard-HTML-Tags und externe Fensterdispatchbefehle enthält, die Sie mit dem Texteditor bearbeiten können.

- **Webbrowser** Der Webbrowser zeigt die Benutzeroberfläche des Steuerelements basierend auf dem HTML-Code in der HTML-Ressource an. Ein Zeiger auf die Schnittstelle `IWebBrowser2` des Webbrowsers ist im DHTML-Steuerelement verfügbar, um den Zugriff auf das DHTML-Objektmodell zu ermöglichen.

Der ATL-Steuerelement-Assistent generiert ein Steuerelement mit Standardcode sowohl in der HTML-Ressource als auch in der CPP-Datei. Sie können das vom Assistenten generierte Steuerelement kompilieren und ausführen und das Steuerelement dann entweder im Webbrowser oder im ActiveX Control TestContainer anzeigen. Das folgende Bild zeigt das standardmäßige ATL-DHTML-Steuerelement mit drei Schaltflächen, die im Testcontainer angezeigt werden:

![ATL-DHTML-Steuerelement](../atl/media/vc52en2.gif "ATL-DHTML-Steuerelement")

Weitere Informationen finden Sie unter [Erstellen eines ATL-DHTML-Steuerelements,](../atl/creating-an-atl-dhtml-control.md) um mit dem Erstellen eines DHTML-Steuerelements zu beginnen. Informationen zum Zugriff auf testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit Testcontainer.](../mfc/testing-properties-and-events-with-test-container.md)

## <a name="see-also"></a>Siehe auch

[Unterstützung für DHTML-Steuerelemente](../atl/atl-support-for-dhtml-controls.md)
