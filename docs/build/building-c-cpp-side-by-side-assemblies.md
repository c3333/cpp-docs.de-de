---
title: Erstellen von parallelen C/C++-Assemblys
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493325"
---
# <a name="building-cc-side-by-side-assemblies"></a>Erstellen von parallelen C/C++-Assemblys

Eine [parallele Assembly](/windows/win32/SbsCs/about-side-by-side-assemblies-) ist eine Reihe von Ressourcen, z. B. eine Gruppe von DLLs, Windows-Klassen, COM-Servern, Typbibliotheken oder Schnittstellen, die einer Anwendung zur Laufzeit zur Verfügung stehen. Der Hauptvorteil des Neupackens von DLLs in Assemblys besteht darin, dass mehrere Versionen von Assemblys gleichzeitig von Anwendungen verwendet werden können. Außerdem ermöglicht das Neupacken, alle derzeit installierte Assemblys zu aktualisieren, falls Updates veröffentlicht werden.

Eine C++-Anwendung kann mindestens eine DLL in verschiedenen Teilen der Anwendung verwenden. Zur Laufzeit werden die DLLs in den Hauptprozess geladen, und der erforderliche Code wird ausgeführt. Die Anwendung ist auf das Betriebssystem angewiesen, um die angeforderten DLLs zu finden, zu verstehen, welche anderen abhängigen DLLs geladen werden müssen, und diese dann zusammen mit der angeforderten DLL zu laden. In Versionen des Windows-Betriebssystems, die älter als Windows XP, Windows Server 2003 und Windows Vista sind, sucht das Betriebssystem-Ladeprogramm entweder im lokalen Ordner der Anwendung oder in einem anderen Ordner, der im Systempfad angegeben ist, nach abhängigen DLLs. Unter Windows XP, Windows Server 2003 und Windows Vista kann das Betriebssystem-Ladeprogramm auch mithilfe einer [Manifestdatei](/windows/win32/sbscs/manifests) nach abhängigen DLLs suchen. Das Betriebssystem-Ladeprogramm kann zudem parallele Assemblys suchen, die diese DLLs enthalten.

Wenn eine DLL mit Visual Studio erstellt wird, wird automatisch ein [Anwendungsmanifest](/windows/win32/SbsCs/application-manifests) als eine RT_MANIFEST-Ressource mit einer ID=2 eingebettet. Wie bei einer ausführbaren Datei werden im Manifest Abhängigkeiten dieser DLL zu anderen Assemblys beschrieben. Dabei wird davon ausgegangen, dass die DLL kein Teil einer parallelen Assembly ist und dass Anwendungen, die von dieser DLL abhängen, kein Anwendungsmanifest verwenden, um diese zu laden. Stattdessen wird davon ausgegangen, dass Anwendungen die DLL mithilfe des Betriebssystem-Ladeprogramms im Systempfad finden.

> [!NOTE]
> Bei DLLs, die ein Anwendungsmanifest verwenden, ist es wichtig, dass das Manifest als Ressource mit der ID=2 eingebettet ist. Wenn die DLL zur Laufzeit dynamisch geladen wird (z. B. mithilfe der Funktion [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)), lädt das Betriebssystem-Ladeprogramm abhängige Assemblys, die im Manifest der DLL angegeben sind. Ein externes Anwendungsmanifest für DLLs wird während eines Aufrufs von `LoadLibrary` nicht geprüft. Wenn das Manifest nicht eingebettet ist, versucht das Ladeprogramm unter Umständen, die falschen Versionen der Assemblys zu laden oder die abhängigen Assemblys zu finden, wobei ein Fehler auftritt.

Eine oder mehrere dazugehörige DLLs können neu in eine parallele Assembly mit einem entsprechenden [Assemblymanifest](/windows/win32/SbsCs/assembly-manifests) gepackt werden. Im Manifest wird beschrieben, aus welchen Dateien die Assembly besteht sowie von welchen anderen parallelen Assemblys sie abhängt.

> [!NOTE]
> Wenn eine Assembly eine DLL enthält, empfiehlt es sich, das Assemblymanifest als Ressource mit der ID=1 in diese DLL einzubetten und der privaten Assembly denselben Namen wie die DLL zu geben. Wenn der Name der DLL z. B. mylibrary.dll lautet, kann der Wert des Namensattributs, das im Element \<assemblyIdentity> des Manifests verwendet wird, auch „mylibrary“ lauten. In einigen Fällen kann ein externes Assemblymanifest erstellt werden, wenn eine Bibliothek eine andere Dateiendung als „.dll“ aufweist (für ein MFC-ActiveX-Steuerelementprojekt wird z. B. eine OCX-Bibliothek erstellt). In diesem Fall müssen sich der Name der Assembly und des zugehörigen Manifests von dem Namen der DLL unterscheiden (sie könnten z. B. MyAssembly, MyAssembly.manifest und mylibrary.ocx lauten). Es wird jedoch dennoch empfohlen, solche Bibliotheken mit der Dateiendung „.dll“ umzubenennen und das Manifest als Ressource einzubetten, um die zukünftigen Wartungskosten dieser Assembly zu verringern. Weitere Informationen darüber, wie das Betriebssystem nach privaten Assemblys sucht, finden Sie unter [Assemblysuchsequenz](/windows/win32/SbsCs/assembly-searching-sequence).

Diese Änderung ermöglicht unter Umständen die Bereitstellung entsprechender DLLs als [private Assembly](/windows/win32/Msi/private-assemblies) in einem lokalen Anwendungsordner oder als [freigegebene Assembly](/windows/win32/Msi/shared-assemblies) im WinSxS-Assemblycache. Damit diese neue Assembly ein korrektes Laufzeitverhalten aufweist, müssen mehrere Schritte ausgeführt werden. Diese werden im [Leitfaden für das Erstellen von parallelen Assemblys](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies) beschrieben. Nachdem eine Assembly korrekt erstellt wurde, kann sie entweder als freigegebene oder private Assembly zusammen mit einer Anwendung bereitgestellt werden, die von ihr abhängt. Bei der Installation von parallelen Assemblys als freigegebene Assembly können Sie entweder die Anleitung in [Installieren von Win32-Assemblys für die parallele Freigabe ](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp) befolgen oder [Mergemodule](/windows/win32/msi/merge-modules) verwenden. Bei der Installation paralleler Assemblys als private Assembly können Sie die entsprechende DLL, die entsprechenden Ressourcen und das dazugehörige Assemblymanifest in den lokalen Anwendungsordner auf dem Zielcomputer kopieren. Dadurch wird sichergestellt, dass diese Assembly vom Ladeprogramm zur Laufzeit gefunden wird (s. [Assemblysuchsequenz](/windows/win32/SbsCs/assembly-searching-sequence)). Eine weitere Möglichkeit besteht darin, den [Windows Installer](/windows/win32/Msi/windows-installer-portal) zu verwenden und die unter [Installieren von Win32-Assemblys für die private Verwendung einer Anwendung unter Windows XP](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp) beschriebene Anleitung zu befolgen.

## <a name="see-also"></a>Siehe auch

[Erstellen isolierter C/C++-Anwendungen](building-c-cpp-isolated-applications.md)<br/>
[Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
