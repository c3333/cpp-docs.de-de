---
title: Aktualisieren von C++-Projekten aus früheren Versionen von Visual Studio
description: Hier erfahren Sie, wie ein Upgrade auf Microsoft Visual C++-Projekte aus älteren Visual Studio-Versionen ausgeführt wird.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 7a4ab98c196d601bc458fe33bb1e2cb45ac30088
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505898"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Aktualisieren von C++-Projekten aus früheren Versionen von Visual Studio

Um ein Projekt zu aktualisieren, das in einer früheren Version von Visual Studio erstellt wurde, öffnen Sie einfach das Projekt in der aktuellen Version von Visual Studio. Visual Studio bietet die Option, um das Projekt auf das aktuelle Schema zu aktualisieren.

Wenn Sie **Nein**auswählen, wird das Projekt nicht aktualisiert. Für Projekte, die in Visual Studio 2010 und höher erstellt wurden, können Sie das Projekt weiterhin in der neueren Version von Visual Studio verwenden. Legen Sie die Projekteigenschaften so fest, dass Sie weiterhin auf das ältere Toolset abzielen. Wenn Sie die ältere Version von Visual Studio auf Ihrem Computer belassen, ist das zugehörige Toolset in späteren Versionen verfügbar. Wenn Ihr Projekt beispielsweise weiterhin unter Windows XP ausgeführt werden muss, können Sie ein Upgrade auf Visual Studio 2019 durchführen. Anschließend geben Sie das Toolset als v141_xp oder früher in den Projekteigenschaften an. Weitere Informationen finden Sie unter [Use native multi-targeting in Visual Studio to build old projects (Verwenden der nativen Festlegung von Zielversionen in Visual Studio, um alte Projekte zu erstellen)](use-native-multi-targeting.md).

Wenn Sie **Ja**auswählen, wird das Projekt direkt aktualisiert. Sie kann nicht wieder in die frühere Version konvertiert werden. In den Upgradeszenarien empfiehlt es sich, eine Sicherungskopie der vorhandenen Projekt-und Projektmappendateien zu erstellen.

## <a name="upgrade-reports"></a>Aktualisieren von Berichten

Wenn Sie ein Upgrade für ein Projekt durchführen, erhalten Sie einen Upgradebericht. Der Bericht wird auch als UpgradeLog.htm im Projektordner gespeichert. Der Upgradebericht enthält eine Zusammenfassung der Probleme, die während der Konvertierung gefunden wurden. Darin sind einige Informationen zu vorgenommenen Änderungen aufgeführt. dazu gehören:

- Projekteigenschaften.

- Includedateien.

- Code, der aufgrund von Verbesserungen der Compilerkonformität oder Änderungen am Standard nicht mehr ordnungsgemäß kompiliert wird.

- Code, der auf Visual Studio-oder Windows-Features basiert, die nicht mehr verfügbar sind. Oder, Header Dateien, die entweder nicht in einer Standardinstallation von Visual Studio enthalten sind oder aus dem Produkt entfernt wurden.

- Code, der aufgrund von Änderungen an APIs nicht mehr kompiliert wird, wie z. b. umbenannte APIs, geänderte Funktions Signaturen oder veraltete Funktionen.

- Code, der aufgrund von Änderungen bei der Diagnose nicht mehr kompiliert wird, wie z. b. eine Warnung, die zu einem Fehler wird

- Linker-Fehler aufgrund von geänderten Bibliotheken, insbesondere dann, wenn/NODEFAULTLIB verwendet wird.

- Laufzeitfehler oder unerwartete Ergebnisse aufgrund von Verhaltensänderungen.

- Fehler, die in den Tools eingeführt wurden. Wenn Sie ein Problem feststellen, melden Sie es dem Visual C++-Team über die normalen Support Kanäle oder über die Seite [Visual Studio C++ Developer Community](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Einige aktualisierte Projekte und Projektmappen können ohne Änderung erfolgreich erstellt werden. Die meisten Projekte erfordern jedoch wahrscheinlich Änderungen an den Projekteinstellungen und dem Quellcode. Es gibt keine einzige korrekte Methode, um diese Probleme zu beheben, aber wir empfehlen die Verwendung eines stufenweisen Ansatzes. Bevor Sie beginnen, lesen Sie den [Überblick über mögliche Upgradeprobleme](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , um weitere Informationen zu vielen häufigen Fehlern zu erhalten.

1. Legen Sie das Platt Form Toolset, den C++-sprach Standard und Windows SDK Version (falls zutreffend) auf die bevorzugten Versionen fest. (**Projekt**  >  **Eigenschaften**  >  **Konfigurations Eigenschaften**  >  **Allgemein**)

1. Wenn viele Fehler auftreten, können Sie einige Optionen temporär deaktivieren, während Sie Sie beheben. Um die [/permissive-](../build/reference/permissive-standards-conformance.md) -Option zu deaktivieren, verwenden Sie die **Projekt**  >  **Eigenschaften**  >  **Konfigurations Eigenschaften**  >  **C/C++**-  >  **Sprache**. Um die [Code Analyse](../code-quality/code-analysis-for-c-cpp-overview.md) Option zu deaktivieren, verwenden Sie **Projekt**  >  **Eigenschaften**  >  **Konfigurations Eigenschaften**  >  **Code Analyse**.

1. Stellen Sie sicher, dass alle Abhängigkeiten vorhanden sind und dass die Includepfade oder Bibliotheks Speicherorte korrekt sind. (**Projekt**  >  **Eigenschaften**  >  **Konfigurations Eigenschaften**  >  **VC + +-Verzeichnisse**)

1. Identifizieren und beheben Sie Fehler, die durch Verweise auf APIs verursacht werden, die nicht mehr vorhanden sind.

1. Beheben Sie alle restlichen Fehler, die die Kompilierung verhindern. Weitere Informationen finden Sie unter [Übersicht über mögliche Upgradeprobleme](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) für Fehlerbehebungen für häufige Fehler.

1. Aktivieren Sie **/permissive-** wieder, und beheben Sie alle neuen Fehler, die durch nicht konformen Code verursacht wurden, der zuvor in MSVC kompiliert wurde.

1. Aktivieren Sie die Code Analyse, um potenzielle Probleme oder veraltete Codierungs Muster zu identifizieren, die nicht mehr als akzeptabel erachtet werden. Wenn bei der Code Analyse viele Fehler ausgegeben werden, können Sie einige der Warnungen deaktivieren, damit Sie sich zunächst auf die wichtigsten Warnungen konzentrieren können. Die IDE kann für einige Arten von Problemen bei schnellen Korrekturen helfen.

1. Sehen Sie sich andere Möglichkeiten zur Modernisierung des Codes an. Ersetzen Sie z. b. benutzerdefinierte Datenstrukturen und Algorithmen durch die C++-Standardbibliothek oder die Boost Open Source-Bibliothek. Durch die Verwendung von Standard Features vereinfachen Sie die Verwaltung des Codes durch andere Benutzer. Sie können sicher sein, dass dieser Code von vielen Experten im Standards Committee und der breiteren C++-Community gut getestet und überprüft wurde.

Um Fehlerbehebung zu beheben, versuchen Sie, eine Frage zu Stack Overflow-oder C++- [Entwickler Community](https://developercommunity.visualstudio.com/spaces/62/index.html)zu suchen oder zu veröffentlichen.

## <a name="in-this-section"></a>In diesem Abschnitt

[Übersicht über mögliche Upgradeprobleme](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Aktualisieren Ihres Codes auf die universelle CRT](upgrade-your-code-to-the-universal-crt.md)\
[Aktualisieren von WINVER und _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Beheben der Abhängigkeiten von Bibliotheks internen Elementen](fix-your-dependencies-on-library-internals.md)\
[Probleme mit der Gleit Komma Migration](floating-point-migration-issues.md)\
[C++ Features, die in Visual Studio 2019 veraltet sind](features-deprecated-in-visual-studio.md)\
[VCBuild im Vergleich zu MSBuild](build-system-changes.md)\
[Portieren von Drittanbieterbibliotheken](porting-third-party-libraries.md)

## <a name="see-also"></a>Weitere Informationen

[Neuerungen bei Visual C++ in Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ Änderungs Verlauf 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Nicht dem Standard entsprechende Verhalten](../cpp/nonstandard-behavior.md)\
[Portieren von Datenanwendungen](../data/data-access-programming-mfc-atl.md)
