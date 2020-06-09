---
title: MFC MBCS DLL-Add-On
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 522bd5cf573aa3a0b24f14bc50f23b0d0e300d2e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625352"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL-Add-On

Die Unterstützung für MFC und seine Multibytezeichen-Zeichensatz Bibliotheken (MBCS) erfordern bei der Installation von Visual Studio in Visual Studio 2013 und höher einen zusätzlichen Schritt.

**Visual Studio 2013**: Standardmäßig unterstützen die in Visual Studio 2013 installierten MFC-Bibliotheken nur die Unicode-Entwicklung. Sie benötigen die MBCS-DLLs, um in Visual Studio 2013 ein MFC-Projekt zu erstellen, für das die **Zeichensatz** -Eigenschaft auf **Multi-Byte-Zeichensatz verwenden** oder **nicht fest**gelegt festgelegt ist. Laden Sie die dll in der [Multibyte-MFC-Bibliothek für Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770)herunter.

**Visual Studio 2015**: sowohl Unicode-als auch MBCS-MFC-DLLs sind in den Visual C++ Setup-Komponenten enthalten, aber die Unterstützung für MFC ist standardmäßig nicht installiert. Visual C++ und MFC sind optionale Installationskonfigurationen beim Visual Studio-Setup. Um sicherzustellen, dass MFC installiert wird, wählen Sie im Setup **Benutzerdefiniert** aus. Unter **Programmiersprachen**stellen Sie dann sicher, dass die Optionen **Visual C++** und **Microsoft Foundation Classes für C++** ausgewählt sind. Wenn Sie Visual Studio bereits installiert haben, werden Sie aufgefordert, Visual C++ und/oder MFC zu installieren, wenn Sie versuchen, ein MFC-Projekt zu erstellen.

**Visual Studio 2017 und**höher: die MFC-DLLs für Unicode und MBCS werden mit der Arbeitsauslastung " **Desktop Entwicklung mit C++** " installiert, wenn Sie die **MFC-und ATL-Unterstützung** aus dem Bereich " **optionale Komponenten** " des Visual Studio-Installer Programms auswählen. Wenn Ihre Installation diese Komponenten nicht enthält, navigieren Sie zu der **Datei | Dialogfeld Neues Projekt** , und klicken Sie auf den Link **Visual Studio-Installer öffnen** . Weitere Informationen finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="see-also"></a>Siehe auch

[MFC-Bibliotheksversionen](mfc-library-versions.md)
