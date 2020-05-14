---
title: Manifestgenerierung in Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273357"
---
# <a name="manifest-generation-in-visual-studio"></a>Manifestgenerierung in Visual Studio

Die Generierung einer Manifestdatei für ein bestimmtes Projekt kann über das Projektdialogfeld **Eigenschaftenseiten** gesteuert werden. Klicken Sie auf der Registerkarte **Konfigurationseigenschaften** auf **Linker**, **Manifestdatei** und dann **Manifest generieren**. Die Projekteigenschaften eines neuen Projekts sind standardmäßig so festgelegt, dass eine Manifestdatei generiert wird. Es ist jedoch möglich, die Generierung des Manifests für ein Projekt mithilfe der Eigenschaft **Manifest generieren** des Projekts zu deaktivieren. Wenn diese Eigenschaft auf **Ja** festgelegt ist, wird das Manifest für dieses Projekt generiert. Andernfalls ignoriert der Linker beim Auflösen von Abhängigkeiten des Anwendungscodes Assemblyinformationen und generiert kein Manifest.

Das Buildsystem in Visual Studio ermöglicht, dass das Manifest in die endgültige binäre Anwendungsdatei eingebettet oder als externe Datei generiert wird. Dieses Verhalten wird durch die Option **Manifest einbetten** im Dialogfeld **Projekteigenschaften** gesteuert. Öffnen Sie den Knoten **Manifesttool**, und klicken Sie auf **Eingabe und Ausgabe**, um diese Eigenschaft festzulegen. Wenn das Manifest nicht eingebettet ist, wird es als externe Datei generiert und im gleichen Verzeichnis wie die endgültige Binärdatei gespeichert. Wenn das Manifest eingebettet ist, bettet Visual Studio die endgültigen Manifeste mithilfe des folgenden Prozesses ein:

1. Nach der Kompilierung des Quellcodes in Objektdateien sammelt der Linker abhängige Assemblyinformationen. Beim Verknüpfen der endgültigen Binärdatei generiert der Linker ein Übergangsmanifest, das später zum Generieren des endgültigen Manifests verwendet wird.

1. Nachdem das Übergangsmanifest erstellt und die Verknüpfung abgeschlossen ist, wird das Manifesttool ausgeführt, um ein endgültiges Manifest zusammenzuführen und es als externe Datei zu speichern.

1. Das Buildsystem des Projekts erkennt dann, ob das vom Manifesttool generierte Manifest andere Informationen enthält als das bereits in die Binärdatei eingebettete Manifest.

1. Wenn sich das in die Binärdatei eingebettete Manifest von dem durch das Manifesttool generierte Manifest unterscheidet oder die Binärdatei kein eingebettetes Manifest enthält, ruft Visual Studio den Linker ein weiteres Mal auf, um die externe Manifestdatei als Ressource in die Binärdatei einzubetten.

1. Wenn das in die Binärdatei eingebettete Manifest mit dem Manifest übereinstimmt, das durch das Manifesttool generiert wurde, fährt der Build mit den nächsten Buildschritten fort.

Das Manifest ist als Textressource in die endgültige Binärdatei eingebettet und kann angezeigt werden, indem die endgültige Binärdatei als Datei in Visual Studio geöffnet wird. Befolgen Sie die unter [Grundlegendes zu den Abhängigkeiten einer Visual C++-Anwendung](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) beschriebenen Schritte oder die Empfehlungen unter [Problembehandlung bei isolierten Anwendungen und parallelen Assemblys (C/C++)](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md), um sicherzustellen, dass das Manifest auf die richtigen Bibliotheken verweist.

## <a name="see-also"></a>Siehe auch

[Manifestgenerierung für C/C++-Programme](understanding-manifest-generation-for-c-cpp-programs.md)
