---
title: Konzept der isolierten Anwendungen und der parallelen Assemblys
ms.date: 05/06/2019
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: f75a95ccca214f437152d13e099fbd9d03eaaee2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493305"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Konzept der isolierten Anwendungen und der parallelen Assemblys

Eine Anwendung wird als [isolierte Anwendung](/windows/win32/SbsCs/isolated-applications) angesehen, wenn alle ihre Komponenten [parallele Assemblys](/windows/win32/SbsCs/about-side-by-side-assemblies-)sind. Eine parallele Assembly ist eine Ansammlung von Ressourcen, z. B. eine Gruppe von DLLs, Windows-Klassen, COM-Servern, Typbibliotheken oder Schnittstellen, die zusammen entwickelt wurden und einer Anwendung zur Laufzeit zur Verfügung gestellt werden. Im Normalfall besteht eine parallele Assembly aus einer oder mehreren DLLs.

## <a name="shared-or-private"></a>Freigegeben oder privat

Eine parallele Assembly kann entweder freigegeben oder privat sein. [Freigegebene parallele Assemblys](/windows/win32/sbscs/about-shared-assemblies-) können von mehreren Anwendungen verwendet werden, die in ihren Manifesten eine Abhängigkeit von der Assembly angeben. Verschiedene Anwendungen, die zur selben Zeit ausgeführt werden, können mehrere Versionen paralleler Assemblys verwenden. Eine [private Assembly](/windows/win32/SbsCs/about-private-assemblies-) ist eine Assembly, die zusammen mit einer Anwendung bereitgestellt wird und nur dieser Anwendung für den exklusiven Zugriff zur Verfügung steht. Private Assemblys werden in dem Ordner, der die ausführbare Datei der Anwendung enthält, oder in einem seiner Unterordner installiert.

## <a name="manifests-and-search-order"></a>Manifeste und Suchreihenfolge

Sowohl isolierte Anwendungen als auch parallele Assemblys werden von [Manifesten](/windows/win32/sbscs/manifests)beschrieben. Ein Manifest ist ein XML-Dokument, das entweder als externe Datei vorliegt oder als Ressource in einer Anwendung oder Assembly eingebettet ist. Die Manifestdatei einer isolierten Anwendung wird zur Verwaltung der Namen und Versionen freigegebener paralleler Assemblys verwendet, an die die Anwendung zu Laufzeit gebunden werden muss. Das Manifest einer parallelen Assembly gibt den Namen, die Versionen, die Ressourcen sowie abhängige Assemblys der parallelen Assembly an. Das Manifest einer freigegebenen parallelen Assembly wird im Ordner %WINDIR%\WinSxS\Manifests\ installiert. Bei privaten Assemblys empfiehlt es sich, das Manifest als Ressource mit der ID 1 in die DLL einzubeziehen. Sie können der privaten Assembly und der DLL auch denselben Namen geben. Weitere Informationen finden Sie unter [Informationen zu privaten Assemblys](/windows/win32/SbsCs/about-private-assemblies-).

Zur Ausführungszeit verwendet Windows die Assemblyinformationen aus dem Anwendungsmanifest zur Suche und zum Laden der entsprechenden parallelen Assembly. Wenn eine isolierte Anwendung eine Assemblyabhängigkeit angibt, sucht das Betriebssystem zuerst unter den freigegebenen Assemblys im systemeigenen Assemblycache im Ordner %WINDIR%\WinSxS\ nach der betreffenden Assembly. Wenn die benötigte Assembly nicht gefunden werden kann, sucht das Betriebssystem anschließend in der Ordnerstruktur des Anwendungsverzeichnisses nach einer privaten Assembly. Weitere Informationen finden Sie unter [Assemblysuchsequenz](/windows/win32/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Ändern von Abhängigkeiten

Die Abhängigkeiten von parallelen Assemblys können nach der Bereitstellung einer Anwendung mithilfe von [Herausgeberkonfigurationsdateien](/windows/win32/SbsCs/publisher-configuration-files) und [Anwendungskonfigurationsdateien](/windows/win32/SbsCs/application-configuration-files)geändert werden. Eine Herausgeberkonfigurationsdatei, auch Herausgeberrichtliniendatei genannt, ist eine XML-Datei, mit der Anwendungen und Assemblys global von der Verwendung einer Version einer parallelen Assembly auf die Verwendung einer anderen Version derselben Assembly umgeleitet werden können. Sie können eine Abhängigkeit z. B. bei der Bereitstellung einer Fehlerkorrektur oder eines Sicherheitsupdates für eine parallele Assembly ändern, wenn Sie alle Anwendungen so umleiten möchten, dass sie die korrigierte Version verwenden. Eine Anwendungskonfigurationsdatei ist eine XML-Datei, die eine bestimmte Anwendung von der Verwendung einer Version einer parallelen Assembly auf eine andere zu verwendende Version derselben Assembly umleitet. Verwenden Sie eine Anwendungskonfigurationsdatei, um eine bestimmte Anwendung so umzuleiten, dass sie eine andere Version einer parallelen Assembly verwendet als in der Herausgeberkonfigurationsdatei angegeben wurde. Weitere Informationen finden Sie unter [Konfiguration](/windows/win32/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Visual C++-Bibliotheken

In Visual Studio 2005 und Visual Studio 2008 wurden verteilbare Bibliotheken wie ATL, MRC, CRT, die C++-Standardbibliothek, OpenMP und MSDIA als freigegebene parallele Assemblys im systemeigenen Assemblycache bereitgestellt. In der aktuellen Version werden die verteilbaren Bibliotheken zentral bereitgestellt. Standardmäßig enthalten alle mit Visual Studio erstellten Anwendungen ein in die endgültige Binärdatei eingebettetes Manifest, das die Abhängigkeiten dieser Binärdatei von den Visual C++-Bibliotheken beschreibt. Weitere Informationen zur Manifestgenerierung für Visual C++-Anwendungen finden Sie unter [Manifestgenerierung für C-/C++-Programme](understanding-manifest-generation-for-c-cpp-programs.md). Für Anwendungen, die statisch mit den verwendeten Bibliotheken verknüpft sind, oder für lokal bereitgestellte Anwendungen ist kein Manifest erforderlich. Weitere Informationen zur Bereitstellung finden Sie unter [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Siehe auch

[Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
