---
title: Erstellen eines auf MSBuild basierenden C++-Projekts für Linux in Visual Studio
ms.date: 10/15/2020
description: Erstellen Sie ein neues MSBuild-basiertes Linux-Projekt in Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 458a26408bfd29b714150e5259fd23807c9b2908
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921632"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>Erstellen eines auf MSBuild basierenden C++-Projekts für Linux in Visual Studio

::: moniker range="msvc-140"

Linux-Projekte sind in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range="msvc-150"

Stellen Sie zunächst sicher, dass Sie die **Workload „Linux-Entwicklung“** für Visual Studio installiert haben. Weitere Informationen finden Sie unter [Herunterladen, Installieren und Einrichten der Linux-Workload](download-install-and-setup-the-linux-development-workload.md).

Für eine plattformübergreifende Kompilierung wird die Verwendung von CMake empfohlen. CMake wird in Visual Studio 2019 umfassender unterstützt. Wenn CMake nicht verwendet werden kann und Sie über eine vorhandene Visual Studio-Projektmappe für Windows verfügen, die Sie für die Kompilierung unter Linux erweitern möchten, können Sie der Windows-Projektmappe ein Visual Studio-Projekt für Linux sowie ein Projekt für **freigegebene Elemente** hinzufügen. Platzieren Sie den von beiden Plattformen gemeinsam verwendeten Code im Projekt „Freigegebene Elemente“, und fügen Sie für die Windows- und Linux-Projekte einen Verweis auf dieses Projekt hinzu.

## <a name="to-create-a-new-linux-project"></a>So erstellen Sie ein neues Linux-Projekts

Führen Sie folgende Schritte aus, um ein neues Linux-Projekt in Visual Studio 2017 zu erstellen:

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Wählen Sie **Visual C++ > Plattformübergreifend > Linux** und anschließend den Projekttyp aus, den Sie erstellen möchten. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie dann auf **OK**.

   ![Screenshot des Dialogfelds „Neues Projekt“, in dem „Visual C plus plus“ > „Plattformübergreifend“ > „Linux“ ausgewählt ist, alle Projekttypen gekennzeichnet sind und die Textfelder „Name“ und „Speicherort“ gekennzeichnet sind](media/newproject.png)

   | Projekttyp | Beschreibung |
   | ------------ | --- |
   | **Blink (Raspberry)** | Projekt für ein Raspberry Pi-Gerät mit Beispielcode für das Aufblinken einer LED |
   | **Konsolenanwendung (Linux)** | Projekt für alle Linux-Computer mit Beispielcode für die Ausgabe von Text an die Konsole |
   | **Leeres Projekt (Linux)** | Projekt für alle Linux-Computer ohne Beispielcode |
   | **Makefile-Projekt (Linux)** | Projekt für alle Linux-Computer, die mithilfe eines Standard-Makefile-Buildsystems erstellt wurden |

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren eines auf MSBuild basierenden Linux-Projekts](configure-a-linux-project.md)

::: moniker-end

::: moniker range="msvc-160"

Stellen Sie zunächst sicher, dass Sie die **Workload „Linux-Entwicklung“** für Visual Studio installiert haben. Weitere Informationen finden Sie unter [Herunterladen, Installieren und Einrichten der Linux-Workload](download-install-and-setup-the-linux-development-workload.md).

Wenn Sie ein neues C++-Projekt für Linux in Visual Studio erstellen, können Sie zwischen einem Visual Studio- und einem CMake-Projekt wählen. In diesem Artikel wird beschrieben, wie Sie ein Visual Studio-Projekt erstellen können. Im Allgemeinen empfiehlt sich für neue Projekte, die möglicherweise Open-Source-Code enthalten oder für die plattformübergreifende Entwicklung kompiliert werden sollen, die Verwendung von CMake mit Visual Studio. Mithilfe eines CMake-Projekts können Sie dasselbe Projekt sowohl für Windows als auch für Linux erstellen und debuggen. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines Linux-CMake-Projekts](cmake-linux-project.md).

Wenn Sie über eine vorhandene Visual Studio-Projektmappe für Windows verfügen, die Sie für die Kompilierung unter Linux erweitern möchten, und CMake nicht verwendet werden kann, können Sie der Windows-Projektmappe ein Visual Studio-Projekt für Linux sowie ein Projekt für **freigegebene Elemente** hinzufügen. Platzieren Sie den von beiden Plattformen gemeinsam verwendeten Code im Projekt „Freigegebene Elemente“, und fügen Sie für die Windows- und Linux-Projekte einen Verweis auf dieses Projekt hinzu.

## <a name="create-a-new-linux-project"></a>Erstellen eines neuen Linux-Projekts

Führen Sie folgende Schritte aus, um ein neues Linux-Projekt in Visual Studio 2019 zu erstellen:

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**. Das Dialogfeld „Neues Projekt erstellen“ wird angezeigt.
1. Geben Sie im Textfeld **Nach Vorlagen suchen** **Linux** ein, damit die verfügbaren Vorlagen für Linux-Projekte aufgeführt werden.
1. Wählen Sie den Projekttyp aus, der erstellt werden soll, z. B. **Konsolenanwendung** , und klicken Sie dann auf **Weiter**. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie auf **Erstellen**.

   ![Screenshot des Dialogfelds „Neues Projekt“ mit dem Sprachdropdown, in dem C++ ausgewählt ist, und dem Plattformdropdown, in dem Linux ausgewählt ist](media/newproject-vs2019.png)

   | Projekttyp | Beschreibung |
   | ------------ | --- |
   | **Raspberry Pi-Projekt** | Projekt für ein Raspberry Pi-Gerät mit Beispielcode für das Aufblinken einer LED |
   | **Konsolenanwendung** | Projekt für alle Linux-Computer mit Beispielcode für die Ausgabe von Text an die Konsole |
   | **Leeres Projekt** | Projekt für alle Linux-Computer ohne Beispielcode |
   | **Makefile-Projekt** | Projekt für alle Linux-Computer, die mithilfe eines Standard-Makefile-Buildsystems erstellt wurden |
   | **CMake-Projekt** | Projekt für alle Linux-Computer, die mithilfe eines CMake-Buildsystems erstellt wurden |

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren eines MSBuild-Projekts für Linux](configure-a-linux-project.md)

::: moniker-end
