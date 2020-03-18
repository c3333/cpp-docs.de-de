---
title: Verwenden von nativen Zielversionen in Visual Studio, um alte Projekte zu erstellen
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: aff21121c181131b04ad22d75f03b7cbb222228a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423807"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Verwenden von nativen Zielversionen in Visual Studio, um alte Projekte zu erstellen

Normalerweise wird empfohlen, dass Sie Ihre Projekte aktualisieren, wenn Sie die neueste Version von Visual Studio installieren. Die Kosten der Aktualisierung Ihrer Projekte und des Codes werden in der Regel durch die Vorteile der neuen IDE, des Compilers, der Bibliotheken und Tools ausgeglichen. Wir wissen jedoch, dass Sie einige Projekte möglicherweise nicht aktualisiert können. Sie verfügen möglicherweise über Binärdaten, die mit älteren Bibliotheken oder Plattformen verknüpft sind, die Sie aus Wartungsgründen nicht upgraden können. Ihr Code kann womöglich nicht standardmäßige Sprachkonstrukte verwenden, die Fehler verursachen würden, wenn sie an einen aktuelleren Compiler verschoben werden würden. Ihr Code könnte sich auf Bibliotheken eines Drittanbieters verlassen, die für eine bestimmte Version von Visual C++ kompiliert sind. Alternativ können Sie Bibliotheken für andere erstellen, die auf eine bestimmte ältere Version von Visual C++ abzielen müssen.

Glücklicherweise können Sie zum Erstellen von Projekten, die auf ältere Compiler-Toolsets und Bibliotheken ausgerichtet sind, Visual Studio 2017 und Visual Studio 2015 verwenden. Sie müssen kein Projekt von Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 oder Visual Studio 2015 upgraden, um Vorteile aus den neuen Features der IDE zu ziehen:

  - Neue Umgestaltungsfunktionen für C++ und experimentelle Funktionen für den Editor
  - Neues Debuggerfenster „Diagnosetools“ und neues Fenster „Fehlerliste“
  - Überarbeitete Breakpoints, das Fenster „Ausnahmen“ und neue PerfTips
  - Neue Tools zur Codenavigation und Suche
  - Neue C++-Schnellkorrekturen und Erweiterungen für Productivity Power Tools

Sie können auch auf Visual Studio 2008-Projekte abzielen, doch diese können nicht unverändert verwendet werden. Weitere Informationen finden Sie im Abschnitt **Anweisungen für Visual Studio 2008**.

Die neuesten Versionen von Visual Studio unterstützen die native Festlegung von Zielversionen und Roundtripping für Projekte. Die native Festlegung von Zielversionen ist Möglichkeit der neuesten IDE für die Entwicklung mithilfe von Toolsets, die von vorherigen Versionen von Visual Studio installiert wurden. Die Roundtrip-Funktion ist die Fähigkeit der neuesten IDE, ohne jede Änderung an dem Projekt eine frühere Version der IDE erstellte Projekte zu laden. Wenn Sie die neueste Version von Visual Studio zusammen mit Ihrer aktuellen Version installieren, können Sie die neue Version der IDE mit dem Compiler und den Tools aus der aktuellen Version verwenden, um Ihre Projekte zu erstellen. Andere Mitglieder Ihres Teams können weiterhin die Projekte in der älteren Version von Visual Studio verwenden.

Wenn Sie ein älteres Toolset verwenden, können Sie von vielen der neuesten IDE-Features profitieren, jedoch nicht von den neuesten Fortschritten im C++-Compiler, in den Bibliotheken und Buildtools. Sie können z.B. nicht die neuen verbesserten Sprachübereinstimmungen sowie die neuen Features für das Debuggen und zur Codeanalyse. Ebenso erhalten Sie nicht den schnelleren Builddurchsatz des neuesten Toolsets. Es gibt auch einige IDE-Funktionen, die mit älteren Toolsets nicht kompatibel sind. Es können z.B. Typinformationen im neuen Memory Profiler fehlen, und der Umgestaltungsvorgang **Convert to Raw string literals** (In unformatierte Zeichenfolgenliterale konvertieren) generiert C++11-konformen Code, der nicht kompiliert werden kann, wenn Sie Toolsets aus Visual Studio 2012 oder älter verwenden.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>So verwenden Sie die native Festlegung von Zielversionen in Visual Studio

Nachdem Sie Visual Studio parallel mit Ihrer älteren Version installiert haben, öffnen Sie Ihr vorhandenes Projekt in der neuen Visual Studio-Version. Wenn das Projekt geladen wird, fragt Visual Studio Sie, ob sie die Version für die Verwendung des neuesten C++-Compilers und der C++-Bibliotheken upgraden möchten. Da Sie möchten, dass das Projekt den alten Compiler und die alten Bibliotheken behält, klicken Sie auf die Schaltfläche **Abbrechen**.

Visual Studio upgradet weiterhin Ihr Projekt. Damit das Dialogfeld zum Upgraden nicht jedes Mal erscheint, wenn Sie das Projekt laden, können Sie die folgende Eigenschaft in Ihren Projekten oder in den PROPS- oder TARGET-Dateien, die von ihnen importiert werden, definieren.

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Wenn Sie Ihre Projekte upgraden möchten, müssen Sie diese Eigenschaft entfernen.

Wenn Sie kein Upgrade durchführen möchten, führt Visual Studio keine Änderungen an Ihrer Projektmappe oder den Projektdateien durch. Wenn Sie das Projekt erstellen, werden die generierten Binärdateien vollständig kompatibel mit jenen, die Sie mit der älteren Version von Visual Studio erstellt haben. Der Grund dafür ist, da Visual Studio den gleiche C++-Compiler verwendet und die gleichen Bibliotheken verknüpft, mit der Ihre ältere IDE ausgestattet war. Darum weist das Dialogfeld für das Upgrade Sie auch darauf hin, die ältere Visual Studio-Version zu behalten, wenn Sie auf **Abbrechen** klicken.

## <a name="instructions-for-visual-studio-2008"></a>Anweisungen für Visual Studio 2008

Visual Studio 2008 verfügte über ein eigenes dediziertes Buildsystem für C++ mit dem Namen **VCBuild**. Ab Visual Studio 2010 wurden C++-Projekte in Visual Studio so verändert, dass sie **MSBuild** verwendeten. Dies bedeutet, dass Sie bei einer permanenten oder fest Zuweisungs basierten Aktualisierung einen Aktualisierungs Schritt durchführen müssen, um Ihre Visual Studio 2008-Projekte in der neuesten Version von Visual Studio zu erstellen. Ihr aktualisiertes Projekt erstellt noch immer Binärdateien, die mit den Binärdateien, die mithilfe der IDE von Visual Studio 2008 erstellt wurden, voll kompatibel sind.

Zunächst müssen Sie zusätzlich zur aktuellen Visual Studio-Version Visual Studio 2010 auf demselben Computer erstellen, auf dem sich Visual Studio 2008 befindet. Nur Visual Studio 2010 installiert die **MSBuild**-Skripts, die für Visual Studio 2008-Projekte erforderlich sind.

Als Nächstes müssen Sie Ihre Visual Studio 2008-Projektmappen und -Projekte auf die aktuelle Version von Visual Studio aktualisieren. Es wird empfohlen, eine Sicherung Ihrer Projekt- und Projektmappendateien zu erstellen, bevor Sie das Upgrade durchführen. Damit der Upgradeprozess beginnen kann, öffnen Sie die Projektmappe in der aktuellen Version von Visual Studio. Wenn Sie die Aufforderung zur Aktualisierung erhalten, überprüfen Sie die dargestellte Information, und wählen Sie dann **OK** aus, um mit dem Upgrade zu beginnen. Wenn Sie mehr als ein Projekt in der Projektmappe haben, müssen Sie den Assistenten zum Erstellen neuer VCXPROJ-Projektdateien parallel mit den vorhandenen VCPROJ-Dateien aktualisieren. Solange Sie noch über eine Kopie der ursprünglichen SLN-Datei verfügen, hat das Upgrade keinen anderen Einfluss auf Ihre vorhandenen Visual Studio 2008-Projekte.

> [!NOTE]
> Die folgenden Schritte gelten nur für Szenarien mit mehreren Zielanwendungen. Wenn Sie beabsichtigen, das Projekt dauerhaft auf ein späteres Toolset zu aktualisieren, müssen Sie im nächsten Schritt das Projekt speichern, in Visual Studio 2019 öffnen und die dort angezeigten Buildprobleme beheben.

Wenn das Upgrade abgeschlossen ist und der Protokollbericht Fehler oder Warnungen für Ihre Projekte ausgibt, überprüfen Sie diese sorgfältig. Die Konvertierung von **VCBuild** in **MSBuild** kann Probleme verursachen. Stellen Sie sicher, dass Sie alle Aktionselemente verstehen und implementieren, die im Bericht aufgeführt sind. Weitere Informationen zum Upgradeprotokollbericht und zu Problemen, die womöglich bei der Konvertierung von **VCBuild** in **MSBuild** auftreten, finden Sie im Blogpost: [C++ Native Multi-Targeting (Native Festlegung von Zielversionen für C++)](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/).

Wenn das Projektupgrade abgeschlossen ist, und Sie alle Probleme in der Protokolldatei behoben haben, ist Ihre Lösung tatsächlich auf das neueste Toolset ausgerichtet. Als letzten Schritt ändern Sie die Eigenschaften für jedes Projekt in der Projektmappe, um das Toolset von Visual Studio 2008 zu verwenden. Öffnen Sie mithilfe der Lösung, die in der aktuellen Visual Studio-Version geladen ist, für jedes Projekt das Dialogfeld **Eigenschaftenseiten** des Projekts: Klicken Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer**, und wählen Sie anschließend **Eigenschaften** aus. Ändern Sie im Dialogfeld **Eigenschaftenseiten** den Wert der Dropdownliste **Konfiguration** in **Alle Konfigurationen**. Wählen Sie unter **Konfigurationseigenschaften**die Option **Allgemein** aus, und ändern Sie dann **Plattformtoolset** in **Visual Studio 2008 (v90)** .

Nach dieser Änderung wird der Visual Studio 2008-Compiler und die -Bibliotheken zum Generieren von Projektbinärdateien verwendet, wenn Sie die Projektmappe in der aktuellen Version von Visual Studio erstellen.

## <a name="install-an-older-visual-studio-toolset"></a>Installieren eines älteren Visual Studio-Toolsets

Sie besitzen möglicherweise ein älteres C++-Projekt in Visual Studio, dass Sie nicht upgraden können oder wollen. Sie verfügen jedoch nicht über die für Ihr Projekt geeignete Plattformtoolsetversion. Um das Toolset zu erhalten, können Sie in diesem Fall die kostenlose Visual Studio Community- oder Express-Edition der von Ihnen benötigten Version installieren. Jede Version von Visual Studio ab Visual Studio 2008 kann den Compiler, die Tools und Bibliotheken installieren, die auf diese Version der aktuellen Visual Studio-Version ausgerichtet sein muss. Durchsuchen Sie das Microsoft Download Center, um eine bestimmte Visual Studio-Version zu finden und herunterzuladen. Stellen Sie sicher, dass Sie die C++-Installationsoptionen während des Setups auswählen. Führen Sie nach dem Abschluss des Setups diese Visual Studio-Version aus, um Updates zu installieren. Prüfen Sie auch auf mögliche Windows Update-Änderungen, die erforderlich sein könnten. Dieser Updateüberprüfungsprozess muss möglicherweise mehrmals wiederholt werden, damit Sie jedes Update erhalten.

Die derzeit verfügbaren Downloads, finden Sie unter [Herunterladen älterer Visual Studio-Software](https://visualstudio.microsoft.com/vs/older-downloads/).

Wenn diese Produkte installiert sind, wird die Eigenschaftendropdownliste **Plattformtoolset** im Dialogfeld **Eigenschaftenseiten** automatisch aktualisiert, um die verfügbaren Toolsets anzuzeigen. Sie können jetzt die neueste Version von Visual Studio verwenden, um Projekte für diese älteren Versionen des Toolsets zu erstellen, ohne sie zu konvertieren oder zu aktualisieren.

## <a name="see-also"></a>Siehe auch

[Aktualisieren von Projekten aus früheren Versionen von VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Verbesserungen der C++-Konformität in Visual Studio](../overview/cpp-conformance-improvements.md)
