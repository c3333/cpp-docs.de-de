---
title: 'Vorgehensweise: Konfigurieren von C++-Projekten in Visual Studio für 64-Bit-Zielplattformen (x64)'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492240"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Vorgehensweise: Konfigurieren von C++-Projekten in Visual Studio für 64-Bit-Zielplattformen (x64)

Sie können die Projektkonfigurationen in der Visual Studio-IDE verwenden, um C++-Anwendungen für 64-Bit-Zielplattformen (x64) einzurichten. Außerdem können Sie Win32-Projekteinstellungen zu einer 64-Bit-Projektkonfiguration migrieren.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>So richten Sie C++-Anwendungen für 64-Bit-Zielplattformen ein

1. Öffnen Sie das C++-Projekt, das Sie konfigurieren möchten.

1. Öffnen Sie die Eigenschaftenseiten für das betreffende Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](working-with-project-properties.md).

   > [!NOTE]
   > Achten Sie bei .NET-Projekten darauf, dass im Dialogfeld **\<Projektname> Eigenschaftenseiten** der Knoten **Konfigurationseigenschaften** oder einer seiner Unterknoten ausgewählt ist. Andernfalls ist die Schaltfläche **Konfigurations-Manager** nicht verfügbar.

1. Wählen Sie die Schaltfläche **Konfigurations-Manager** aus, um das Dialogfeld **Konfigurations-Manager** zu öffnen.

1. Wählen Sie in der Dropdownliste **Aktive Projektmappenplattform** die Option **\<Neu…>** aus, um das Dialogfeld **Neue Projektmappenplattform** zu öffnen.

1. Wählen Sie in der Dropdownliste **Neue Plattform eingeben oder auswählen** eine 64-Bit-Zielplattform aus.

   > [!NOTE]
   > Im Dialogfeld **Neue Projektmappenplattform** können Sie die Option **Einstellungen kopieren von** verwenden, um vorhandene Projekteinstellungen in die neue 64-Bit-Projektkonfiguration zu kopieren.

1. Klicken Sie auf die Schaltfläche **OK** . Die Plattform, die Sie im vorherigen Schritt ausgewählt haben, wird unter **Aktive Projektmappenplattform** im Dialogfeld **Konfigurations-Manager** angezeigt.

1. Klicken Sie im Dialogfeld **Konfigurations-Manager** auf **Schließen** und dann im Dialogfeld **\<Projektname> Eigenschaftenseiten** auf **OK**.

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>So kopieren Sie Win32-Projekteinstellungen in eine 64-Bit-Projektkonfiguration

- Wenn das Dialogfeld **Neue Projektmappenplattform** geöffnet ist, während Sie ein Projekt für eine 64-Bit-Zielplattform einrichten, wählen Sie in der Dropdownliste **Einstellungen kopieren von** den Wert **Win32**aus. Diese Projekteinstellungen werden auf der Projektebene automatisch aktualisiert:

  - Die Linkeroption [/MACHINE](reference/machine-specify-target-platform.md) wird auf **/MACHINE:X64**festgelegt.

  - **Ausgabe registrieren** ist deaktiviert. Weitere Informationen finden Sie unter [Linker Property Pages](reference/linker-property-pages.md).

  - **Zielumgebung** wird auf **/env x64**festgelegt. Weitere Informationen finden Sie unter [MIDL-Eigenschaftenseiten](reference/midl-property-pages.md).

  - **Parameter überprüfen** wird deaktiviert und auf den Standardwert zurückgesetzt. Weitere Informationen finden Sie unter [MIDL-Eigenschaftenseiten](reference/midl-property-pages.md).

  - Wenn **Debuginformationsformat** in der Win32-Projektkonfiguration auf **/ZI** festgelegt war, wird der Wert in der 64-Bit-Projektkonfiguration auf **/Zi** festgelegt. Weitere Informationen finden Sie unter [/Z7, /Zi, /ZI (Debuginformationsformat)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Keine dieser Projekteigenschaften wird geändert, wenn sie auf der Dateiebene überschrieben werden.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von C++-Projekten für 64-Bit-x64-Ziele](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Debuggen von 64-Bit-Anwendungen](/visualstudio/debugger/debug-64-bit-applications)
