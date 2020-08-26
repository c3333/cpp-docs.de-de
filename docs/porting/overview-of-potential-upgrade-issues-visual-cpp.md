---
title: Überblick über potenzielle Aktualisierungsprobleme (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: d62bccfb3e508145773c01b26976f46dbcb6490f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839672"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Überblick über potenzielle Aktualisierungsprobleme (Visual C++)

Im Laufe der Jahre wurde der Microsoft C++-Compiler stetig überarbeitet und es wurden Änderungen an der Programmiersprache C++ selbst, der C++-Standardbibliothek, der C-Runtime (CRT) und anderen Bibliotheken wie MFC (Microsoft Foundation Classes) und ATL (Active Template Library) vorgenommen. Daher können beim Aktualisieren einer Anwendung aus einer früheren Version von Visual Studio Compiler- und Linkerfehler sowie Warnungen im Code auftreten, der zuvor ordnungsgemäß kompiliert wurde. Je älter die ursprünglichen Codebasis, desto größer die Wahrscheinlichkeit derartiger Fehler. Diese Übersicht fasst die am häufigsten auftretenden Problemklassen zusammen, mit denen Sie sich wahrscheinlich konfrontiert sehen werden, und enthält Links zu ausführlicheren Informationen.

> [!NOTE]
> In der Vergangenheit haben wir empfohlen, Upgrades, die verschiedene Versionen von Visual Studio umfassen, inkrementell auszuführen, also immer von einer Version zur nächst höheren Version. Dieser Ansatz ist allerdings nicht mehr empfehlenswert. Wir haben festgestellt, dass es fast immer einfacher ist, unabhängig vom Alter der Codebasis direkt auf die aktuellste Version von Visual Studio zu aktualisieren.

Fragen oder Kommentare zum Upgradevorgang können Sie an vcupgrade@microsoft.com senden.

## <a name="library-and-toolset-dependencies"></a>Abhängigkeiten zwischen Bibliothek und Toolset

> [!NOTE]
> Dieser Abschnitt gilt für Anwendungen und Bibliotheken, die mit Visual Studio 2013 und früheren Versionen erstellt wurden. Die in Visual Studio 2015, Visual Studio 2017 und Visual Studio 2019 verwendeten Toolsets sind binärkompatibel. Weitere Informationen finden Sie unter [C++ Binary Compatibility between Visual Studio 2015 and Visual Studio 2019 (Kompatibilität von C++-Binärdateien zwischen Visual Studio 2015 und Visual Studio 2019)](binary-compat-2015-2017.md).

Beim Aktualisieren einer Anwendung auf eine neue Version von Visual Studio wird empfohlen, auch alle mit der Anwendung verknüpften Bibliotheken und DLLs zu aktualisieren. In vielen Fällen ist dies sogar notwendig. Es ist erforderlich, dass Sie entweder auf den Quellcode zugreifen können oder dass der Hersteller der Bibliothek Ihnen neue Binärdateien zur Verfügung stellen kann, die mit derselben Hauptversion des Compilers kompiliert wurden. Wenn eine der folgenden Bedingungen zutrifft, können Sie diesen Abschnitt überspringen, der sich mit den Details der Binärdateikompatibilität befasst. Wenn dies nicht zutrifft, können die Bibliotheken in Ihrer aktualisierten Anwendung möglicherweise nicht verwendet werden können. Die Informationen in diesem Abschnitt helfen Ihnen zu entscheiden, ob Sie mit der Aktualisierung fortfahren können.

### <a name="toolset"></a>Toolset

Die Dateiformate OBJ und LIB sind klar definiert und ändern sich nur selten. Wenn diese Dateiformate erweitert werden, haben diese Erweiterungen im Allgemeinen keinen Einfluss auf die Fähigkeit neuerer Toolsets, die von älteren Toolsets erzeugten Objektdateien und Bibliotheken zu nutzen. Die große Ausnahme hierbei ist die Verwendung von [/GL (Whole Program Optimization) (/GL (Optimierung des gesamten Programms))](../build/reference/gl-whole-program-optimization.md) bei der Kompilierung. Wenn Sie mit `/GL` kompilieren, kann die resultierende Objektdatei nur unter Verwendung desselben Toolsets verknüpft werden, mit dem sie erzeugt wurde. Wurde eine Objektdatei also mit `/GL` und dem Compiler von Visual Studio 2017 (v141) erzeugt, muss die Verknüpfung mit dem Linker von Visual Studio 2017 (v141) erfolgen. Dies liegt daran, dass die internen Datenstrukturen innerhalb der Objektdateien in den Hauptversionen des Toolsets nicht stabil sind, und die älteren Datenformate in neueren Toolsets nicht verstanden werden.

C++ verfügt über keine stabile Anwendungsbinärdateischnittstelle (Application Binary Interface, ABI). Allerdings verwaltet Visual Studio eine stabile C++-ABI für alle Nebenversionen eines Releases. Visual Studio 2015 (v140), Visual Studio 2017 (v141) und Visual Studio 2019 (v142) unterscheiden sich nur der jeweiligen Nebenversion. Sie haben alle die gleiche Hauptversionsnummer (nämlich 14). Weitere Informationen finden Sie unter [C++ Binary Compatibility between Visual Studio 2015 and Visual Studio 2019 (Kompatibilität von C++-Binärdateien zwischen Visual Studio 2015 und Visual Studio 2019)](binary-compat-2015-2017.md).

Angenommen, Sie verfügen über eine Objektdatei, die externe Symbole mit C++-Verknüpfung enthält. Dann kann diese Objektdatei möglicherweise nicht ordnungsgemäß mit Objektdateien verknüpft werden, die mit einer anderen Hauptversion des Toolsets erzeugt wurden. Die Ergebnisse können unterschiedlich ausfallen: Die Verknüpfung kann vollständig fehlschlagen (z. B. bei geänderter Namensergänzung). Zwar kann die Verknüpfung erfolgreich ausgeführt werden, allerdings funktionieren bestimmte Dinge zur Laufzeit nicht (wenn z. B. das Typlayout geändert wurde). In vielen Fällen funktioniert alles, und nichts geht schief. Beachten Sie außerdem, dass die C++-ABI zwar nicht stabil ist, die C-ABI und die für COM erforderliche Teilmenge der C++-ABI jedoch stabil sind.

Wenn Sie eine Verknüpfung mit einer Importbibliothek herstellen, können jegliche spätere Versionen der verteilbaren Visual Studio-Bibliotheken, die die ABI-Kompatibilität beibehalten, zur Laufzeit verwendet werden. Wenn Ihre App z. B. mit dem Toolset von Visual Studio 2015 Update 3 kompiliert und verknüpft ist, können Sie jede verteilbare Visual Studio 2017- oder Visual Studio 2019-Bibliothek verwenden, da die Bibliotheken von VS 2015, VS 2017 und VS 2019 die binäre Abwärtskompatibilität beibehalten haben. Das Gegenteil trifft nicht zu: Sie können eine verteilbare Komponente nicht für eine frühere Version des Toolsets verwenden, als Sie zum Erstellen des Codes verwendet haben, auch wenn Sie über eine kompatible ABI verfügen.

### <a name="libraries"></a>Bibliotheken

Wenn Sie eine Quelldatei mit einer bestimmten Version der Visual Studio C++-Bibliotheksheaderdateien – durch Einschließen (#including) der Header – kompilieren, muss die resultierende Objektdatei mit der gleichen Bibliotheksversion verknüpft werden. Wenn Ihre Quelldatei beispielsweise mit Visual Studio 2015 Update 3 kompiliert wird \<immintrin.h> , müssen Sie eine Verknüpfung mit der vcruntime-Bibliothek von Visual Studio 2015 Update 3 herstellen. Analog dazu müssen Sie, wenn Ihre Quelldatei mit Visual Studio 2017, Version 15,5, kompiliert wird \<iostream> , eine Verknüpfung mit der Visual Studio 2017 Version 15,5 C++-Standard Bibliothek (Msvcprt) herstellen. Das Kombinieren und Anpassen wird nicht unterstützt.

Für die C++-Standardbibliothek wurde das Kombinieren und Anpassen durch Verwendung von `#pragma detect_mismatch` in den Standardheadern seit Visual Studio 2010 explizit gesperrt. Wenn Sie versuchen, inkompatible Objektdateien zu verknüpfen oder eine Verknüpfung zur falschen Standardbibliothek herzustellen, schlägt die Verknüpfung fehl.

Für die CRT wurde das Kombinieren und Anpassen nie unterstützt, hat aber oft trotzdem funktioniert, zumindest bis zur Visual Studio 2015-Version und Universal CRT, da die API-Oberfläche bis dahin nicht wesentlich geändert wurde. Mit der Universal CRT wurde die Abwärtskompatibilität unterbrochen, sodass eine Abwärtskompatibilität für die Zukunft erreicht werden kann. Mit anderen Worten, es bestehen keine Pläne, in Zukunft neue Universal CRT-Binärdateien mit Versionsangabe einzuführen. Für die vorhandenen Universal CRT erfolgt jetzt stattdessen eine direkte Aktualisierung.

Um eine Teilkompatibilität der Verknüpfungen mit Objektdateien (und Bibliotheken) zu gewährleisten, die mit älteren Versionen der Microsoft C-Laufzeitheader kompiliert wurden, stellen wir ab Visual Studio 2015 die Bibliothek „legacy_stdio_definitions.lib“ bereit. Diese Bibliothek bietet Kompatibilitätssymbole für die meisten Funktionen und Datenexporte, die aus der Universal CRT entfernt wurden. Der Satz der von „legacy_stdio_definitions.lib“ bereitgestellten von Kompatibilitätssymbolen reicht aus, um den meisten Abhängigkeiten gerecht zu werden, einschließlich aller Abhängigkeiten in den im Windows SDK enthaltenen Bibliotheken. Es gibt jedoch einige Symbole, die aus der Universal CRT entfernt wurden und für die keine Kompatibilitätssymbole bereitgestellt werden können. Diese Symbole enthalten einige Funktionen (z. B. \_\_iob\_func) und die Datenexporte (z. B. \_\_imp\_\_\_iob, \_\_imp\_\_\_pctype, \_\_imp\_\_\_mb\_cur\_max).

Wenn Sie über eine statische Bibliothek verfügen, die mit einer älteren Version der C-Runtimeheader erstellt wurde, sollten Sie folgende Schritte in dieser Reihenfolge ausführen:

1. Erstellen Sie die statische Bibliothek mithilfe der neuen Version von Visual Studio und den Universal CRT-Headern neu, um das Verknüpfen mit der Universal CRT zu unterstützen. Dieser Ansatz ist die vollständig unterstützte (und daher beste) Option.

1. Wenn Sie die statische Bibliothek nicht neu erstellen können (oder möchten), können Sie versuchen, eine Verknüpfung mit „legacy\_stdio\_definitions.lib“ herzustellen. Wenn damit die Linkzeitabhängigkeiten Ihrer statischen Bibliothek erfüllt sind, sollten Sie die statische Bibliothek in der Form, in der sie in der Binärdatei verwendet wird, gründlich testen, um sicherzustellen, dass sie von den [an der Universal CRT vorgenommenen Änderungen des Verhaltens](visual-cpp-change-history-2003-2015.md#BK_CRT) nicht beeinträchtigt wird.

1. Wenn die Abhängigkeiten ihrer statischen Bibliothek nicht durch die Legacy-Datei " \_ stdio \_ Definitions. lib" erfüllt werden oder die Bibliothek aufgrund der erwähnten Verhaltensänderungen nicht mit der universellen CRT funktioniert, empfiehlt es sich, die statische Bibliothek in eine DLL zu kapseln, die Sie mit der richtigen Version der Microsoft C-Laufzeit verknüpfen. Wenn die statische Bibliothek beispielsweise mit Visual Studio 2013 erstellt wurde, müssten Sie diese DLL-Datei ebenfalls mit Visual Studio 2013 und den Visual Studio 2013 C++-Bibliotheken erstellen. Durch das Erstellen der Bibliothek in einer DLL-Datei kapseln Sie das Implementierungsdetail, das die Abhängigkeit von einer bestimmten Version der Microsoft C-Laufzeit darstellt. Achten Sie darauf, dass die DLL-Schnittstelle keine Details über die verwendete C-Runtime offenlegt, indem z. B. FILE* über die DLL-Grenze hinweg übergeben wird oder indem ein über „malloc“ zugeordneter Zeiger zurückgegeben und vom Aufrufer die Freigabe erwartet wird.

Die Verwendung mehrerer CRTs in einem einzigen Prozess ist an und für sich nicht problematisch (tatsächlich werden die meisten Prozesse am Ende mehrere CRT-DLLs laden; Windows-Betriebssystemkomponenten sind z. B. von „msvcrt.dll“ abhängig, und die CLR hängt von ihrer eigenen privaten CRT ab). Probleme entstehen dann, wenn Zustände unterschiedlicher CRTs gemischt werden. Beispielsweise sollten Sie Arbeitsspeicher nicht mit „msvcr110.dll!malloc“ zuweisen und versuchen, die Zuweisung dieses Arbeitsspeichers mit „msvcr120.dll!free“ aufzuheben, und Sie sollten nicht versuchen, eine Datei mit „msvcr110!fopen“ zu öffnen und mit „msvcr120!fread“ daraus zu lesen. Solange Sie den Zustand nicht von verschiedenen CRTs überspringen, können Sie sicher mehrere CRTs in einem einzigen Prozess laden.

Weitere Informationen finden Sie unter [Aktualisieren von Code für die Universal CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Fehler aufgrund von Projekteinstellungen

Öffnen Sie ein älteres Projekt, eine ältere Projektmappe oder einen älteren Arbeitsbereich in der neuesten Version von Visual Studio, um das Upgrade zu starten. Visual Studio erstellt ein neues Projekt basierend auf den alten Projekteinstellungen. Wenn das ältere Projekt Bibliothek-oder Includepfade enthält, die für nicht standardmäßige Speicherorte hart codiert sind, ist es möglich, dass die Dateien in diesen Pfaden für den Compiler nicht sichtbar sind, wenn das Projekt die Standardeinstellungen verwendet. Weitere Informationen finden Sie unter [OutputFile-Einstellung des Linkers](porting-guide-spy-increment.md#linker_output_settings).

Grundsätzlich ist jetzt der ideale Zeitpunkt, Ihren Projektcode richtig zu organisieren, um die Projektwartung zu vereinfachen und die Kompilierung des aktualisierten Codes zu erleichtern und zu beschleunigen. Wenn der Quellcode bereits gut organisiert ist und das ältere Projekt mit Visual Studio 2010 oder höher kompiliert wurde, können Sie die neue Projektdatei manuell bearbeiten, damit die Kompilierung im alten und neuen Compiler unterstützt wird. Das folgende Beispiel zeigt, wie Sie die Kompilierung für Visual Studio 2015 und Visual Studio 2017 durchführen:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nicht aufgelöste Externe

Für nicht aufgelöste Symbole müssen Sie die Projekteinstellungen möglicherweise korrigieren.

- Wenn sich die Quelldatei an einem nicht standardmäßigen Speicherort befindet, haben Sie den Pfad zu den Includeverzeichnissen des Projekts hinzugefügt?

- Wenn das externe Symbol in einer LIB-Datei definiert ist: Haben Sie den LIB-Pfad in den Projekteigenschaften angegeben und befindet sich dort die richtige Version der LIB-Datei?

- Versuchen Sie, eine Verknüpfung zu einer LIB-Datei herzustellen, die mit einer anderen Version von Visual Studio kompiliert wurde? Wenn dies der Fall ist, lesen Sie den vorherigen Abschnitt über Abhängigkeiten zwischen Bibliothek und Toolset.

- Stimmen die Typen der Argumente an der Aufrufsite tatsächlich mit einer vorhandenen Funktionsüberladung überein? Überprüfen Sie die zugrunde liegenden Typen für alle Typdefinitionen in der Signatur der Funktion, und in dem Code, der die Funktion aufruft, sehen Sie, was Sie erwarten.

Um nicht aufgelöste Symbolfehler zu beheben, können Sie mit „dumpbin.exe“ versuchen, die in einer Binärdatei definierten Symbole zu überprüfen. Verwenden Sie zum Anzeigen der in einer Bibliothek definierten Symbole die folgende Befehlszeile:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t ist der systemeigene Typ)

(In Microsoft Visual C++ 6,0 und früher **`wchar_t`** wurde nicht als integrierter Typ implementiert, sondern in "WCHAR. h" als typedef für "Ganzzahl ohne Vorzeichen Short" deklariert.) Der C++-Standard erfordert, dass **`wchar_t`** ein integrierter Typ ist. Die Verwendung der „typedef“-Version kann Portabilitätsprobleme verursachen. Wenn Sie ein Upgrade von früheren Versionen von Visual Studio ausführen und Compilerfehler auftreten C2664 da der Code versucht, eine implizit **`wchar_t`** in zu konvertieren **`unsigned short`** , empfiehlt es sich, den Code zu ändern, um den Fehler zu beheben, anstatt festzulegen `/Zc:wchar_t-` . Weitere Informationen finden Sie unter[/Zc:wchar_t (wchar_t ist der systemeigene Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Aktualisieren mit den Optionen /NODEFAULTLIB, /ENTRY und /NOENTRY des Linkers

Die Linkeroption `/NODEFAULTLIB` (oder die Linkereigenschaft „Alle Standardbibliotheken ignorieren“) weist den Linker an, in den Standardbibliotheken wie der CRT keine automatische Verknüpfung vorzunehmen. Das bedeutet, dass jede Bibliothek als einzelne Eingabe aufgelistet werden muss. Diese Liste der Bibliotheken wird in der Eigenschaft **Zusätzliche Abhängigkeiten** im **Linkerabschnitt** des Dialogfelds **Projekteigenschaften** angegeben.

Projekte, die diese Option verwenden, stellen bei der Aktualisierung ein Problem dar, weil der Inhalt einiger Standardbibliotheken geändert wurde. Da jede Bibliothek in der Eigenschaft **Zusätzliche Abhängigkeiten** oder in der Befehlszeile des Linkers aufgelistet werden muss, ist es erforderlich, die Liste der Bibliotheken so zu aktualisieren, dass alle aktuellen Namen verwendet werden.

In der folgenden Tabelle werden die Bibliotheken angezeigt, deren Inhalt seit Visual Studio 2015 geändert wurde. Sie müssen zum Aktualisieren die Bibliotheksnamen in der zweiten Spalte zu den Bibliotheken in der ersten Spalte hinzufügen. Einige dieser Bibliotheken sind Import Bibliotheken, aber das sollte nicht von Bedeutung sein.

|Bisher verwendet:|Sie müssen diese Bibliotheken verwenden:|
|-|-|
|libcmt.lib|libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|msvcrt.lib, ucrt.lib, vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib, ucrtd.lib, vcruntimed.lib|

Dasselbe Problem tritt auch auf, wenn Sie die Option `/ENTRY` oder `/NOENTRY` verwenden, die ebenfalls zur Umgehung der Standardbibliotheken führen.

## <a name="errors-due-to-improved-language-conformance"></a>Fehler aufgrund der verbesserten Sprachübereinstimmung

Die Konformität des Microsoft C++-Compilers mit dem C++-Standard wurde im Lauf der Zeit stetig verbessert. Code, der in früheren Versionen kompiliert wurde, lässt sich in höheren Versionen von Visual Studio möglicherweise nicht kompilieren, weil der Compiler einen Fehler ordnungsgemäß kennzeichnet, der zuvor ignoriert wurde oder explizit erlaubt war.

Der Parameter `/Zc:forScope` wurde beispielsweise früh im Verlauf von MSVC eingeführt. Er lässt nicht konformes Verhalten für Schleifenvariablen zu. Dieser Schalter ist inzwischen veraltet und kann in zukünftigen Versionen entfernt werden. Es wird dringend empfohlen, diesen Schalter nicht zu verwenden, wenn Sie Code aktualisieren. Weitere Informationen finden Sie unter [/Zc:forScope- ist veraltet](porting-guide-spy-increment.md#deprecated_forscope).

Ein Beispiel für einen bei der Aktualisierung häufig auftretenden Compilerfehler ist die Übergabe eines nicht konstanten Arguments an einen konstanten Parameter. Ältere Versionen des Compilers haben dies nicht immer als Fehler gekennzeichnet. Weitere Informationen finden Sie unter [Strikte Compilerkonvertierungen](porting-guide-spy-increment.md#stricter_conversions).

Weitere Informationen zu bestimmten Verbesserungen bei der Übereinstimmung mit Standards finden Sie unter [Änderungsverlauf von Visual C++ von 2003 bis 2015](visual-cpp-change-history-2003-2015.md) und [C++ conformance improvements in Visual Studio (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio)](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Fehler bei ganzzahligen \<stdint.h> Typen

Der \<stdint.h> -Header definiert Typedefs und Makros, die im Gegensatz zu integrierten ganzzahligen Typen garantiert eine angegebene Länge auf allen Plattformen aufweisen. Beispiele sind `uint32_t` und `int64_t`. Der \<stdint.h> Header wurde in Visual Studio 2010 hinzugefügt. Code, der vor 2010 geschrieben wurde, hat möglicherweise private Definitionen für diese Typen bereitgestellt, und diese Definitionen sind möglicherweise nicht immer konsistent mit den \<stdint.h> Definitionen.

Wenn der Fehler C2371 generiert wird, und ein `stdint`-Typ beteiligt ist, bedeutet dies wahrscheinlich, dass der Typ in einem Header entweder im Code oder in der LIB-Datei eines Drittanbieters definiert ist. Wenn Sie ein Upgrade durchführen, sollten Sie alle benutzerdefinierten Definitionen der \<stdint.h> Typen entfernen, aber zunächst die benutzerdefinierten Definitionen mit den aktuellen Standarddefinitionen vergleichen, um sicherzustellen, dass keine neuen Probleme eingeführt werden.

Sie können **F12** (**Gehe zu Definition**) drücken, um zu sehen, wo der betreffende Typ definiert ist.

Die Compileroption [/showIncludes](../build/reference/showincludes-list-include-files.md) kann hier hilfreich sein. Öffnen Sie im Dialogfeld **Eigenschaftenseiten** für Ihr Projekt die Seite **C/C++** > ** Erweitert**, und legen Sie **Includes anzeigen** auf **Ja** fest. Erstellen Sie das Projekt anschließend neu, und sehen Sie sich die Liste der `#include`s im Ausgabefenster an. Jeder Header wird unterhalb des Headers, der ihn enthält, eingerückt.

## <a name="errors-involving-crt-functions"></a>Fehler im Zusammenhang mit CRT-Funktionen

Im Laufe der Jahre wurden viele Änderungen an der C-Laufzeit vorgenommen. Viele sichere Versionen von Funktionen wurden hinzugefügt, und einige Funktionen wurden entfernt. Auch, wie weiter oben in diesem Artikel beschrieben, wurde die Microsoft-Implementierung der CRT in Visual Studio 2015 in neue Binärdateien und zugehörige lib-Dateien umgestaltet.

Wenn ein Fehler eine CRT-Funktion betrifft, finden Sie ggf. in den Artikeln [Visual C++ change history 2003 – 2015 (Änderungsverlauf von Visual C++ von 2003 bis 2015)](visual-cpp-change-history-2003-2015.md) und [C++ conformance improvements in Visual Studio (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio)](../overview/cpp-conformance-improvements.md) zusätzliche Informationen. Wenn der Fehler „LNK2019, Nicht aufgelöste Externe“ auftritt, stellen Sie sicher, dass die Funktion nicht entfernt wurde. Wenn Sie jedoch sicher sind, dass die Funktion noch vorhanden und der aufrufende Code korrekt ist, überprüfen Sie, ob im Projekt `/NODEFAULTLIB` verwendet wird. Ist dies der Fall, müssen Sie die Liste der Bibliotheken aktualisieren, sodass das Projekt die neuen universellen Bibliotheken (UCRT) verwendet. Weitere Informationen finden Sie oben im Abschnitt zu Bibliotheken und Abhängigkeiten.

Wenn der Fehler `printf` oder `scanf` betrifft, stellen Sie sicher, dass Sie die beiden Funktion nicht privat und ohne „stdio.h“ definieren. Falls dies der Fall ist, entfernen Sie entweder die privaten Definitionen, oder stellen Sie eine Verknüpfung mit „legacy\_stdio\_definitions.lib“ her. Sie können diese Bibliothek im Dialogfeld **Eigenschaftenseiten** unter **Konfigurationseigenschaften** > **Linker** > **Eingabe** in der Eigenschaft **Zusätzliche Abhängigkeiten** festlegen. Wenn Sie eine Verknüpfung mit dem Windows SDK 8.1 oder früher herstellen, fügen Sie „legacy\_stdio\_definitions.lib“ hinzu.

Wenn der Fehler Argumente von Formatzeichenfolgen betrifft, liegt dies wahrscheinlich daran, dass der Compiler eine strengere Erzwingung als der Standard einsetzt. Weitere Informationen finden Sie im Änderungsverlauf. Berücksichtigen Sie alle hier aufgeführten Fehler, da sie ein potenzielles Sicherheitsrisiko darstellen können.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Fehler aufgrund von Änderungen im C++-Standard

Der C++-Standard selbst hat sich auf eine Art und Weise entwickelt, die nicht immer abwärts kompatibel ist. Die Einführung von Verschiebesemantik, neuen Schlüsselwörtern sowie anderen Sprach- und Standardbibliothekfeatures in C ++11 kann potenziell Compilerfehler und sogar ein unterschiedliches Laufzeitverhalten verursachen.

Ein altes C++-Programm kann z. B. den „iostream.h“-Header enthalten. Dieser Header ist im Verlauf von C++ schon lange veraltet, und wurde aus Visual Studio schließlich vollständig entfernt. In diesem Fall müssen Sie \<iostream> den Code verwenden und neu schreiben. Weitere Informationen finden Sie unter [Aktualisieren von altem iostreams-Code](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>Warnung „C4838: Einschränkende Konvertierung“

Der C++-Standard legt jetzt fest, dass Konvertierungen von ganzzahligen Werten ohne Vorzeichen in ganzzahlige Werte mit Vorzeichen als einschränkende Konvertierungen angesehen werden. Der Compiler hat diese Warnung vor Visual Studio 2015 nicht ausgelöst. Überprüfen Sie jedes Vorkommen, um sicherzustellen, dass die Richtigkeit Ihres Codes durch diese Einschränkung nicht beeinträchtigt wird.

## <a name="warnings-to-use-secure-crt-functions"></a>Warnungen zur Verwendung von sicheren CRT-Funktionen

Im Laufe der Jahre wurden sichere Versionen der C-Laufzeitfunktionen eingeführt. Zwar sind die alten, nicht sicheren Versionen weiterhin verfügbar, Sie sollten aber dennoch Ihren Code ändern und die sicheren Versionen verwenden. Der Compiler gibt bei Verwendung der nicht sicheren Versionen eine Warnung aus. Sie können diese Warnungen auch deaktivieren oder ignorieren. Um die Warnung für alle Projekte in der Projekt Mappe zu deaktivieren, öffnen Sie **Ansicht**  >  **Eigenschaften-Manager**, wählen Sie alle Projekte aus, für die Sie die Warnung deaktivieren möchten, klicken Sie dann mit der rechten Maustaste auf die ausgewählten Elemente, und wählen Sie **Eigenschaften**aus. Wählen Sie im Dialogfeld **Eigenschaftenseiten** und **Konfigurationseigenschaften** > **C/C++** > **Erweitert****Bestimmte Warnungen deaktivieren** aus. Klicken Sie auf den Dropdown Pfeil, und klicken Sie dann auf **Bearbeiten**. Geben Sie „4996“ in das Textfeld ein (Schließen Sie das Präfix "C" nicht ein.) Weitere Informationen finden Sie unter [portieren, um die sichere CRT zu verwenden](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Fehler aufgrund von Änderungen in Windows-APIs oder veralteten SDKs

Im Laufe der Jahre wurden Windows-APIs und Datentypen hinzugefügt sowie manchmal geändert oder entfernt. Darüber hinaus wurden andere SDKs, die nicht zum Kernbetriebssystem gehörten, hinzugefügt und entfernt. Ältere Programme können daher Aufrufe von APIs enthalten, die nicht mehr vorhanden sind. Sie können auch Aufrufe von APIs in anderen Microsoft-SDKs enthalten, die nicht mehr unterstützt werden. Wenn Ihnen ein Fehler im Zusammenhang mit einer Windows-API oder einer API aus einem älteren Microsoft-SDK angezeigt wird, ist es möglich, dass eine API entfernt bzw. durch eine neuere, sicherere Funktion ersetzt wurde.

Weitere Informationen zum aktuellen API-Satz und den unterstützten unterstützten Betriebssystemen für eine bestimmte Windows-API finden Sie unter [API-Index für Windows-Desktop Anwendungen](/windows/win32/apiindex/api-index-portal) und navigieren zur API.

### <a name="windows-version"></a>Windows-Version

Beim Aktualisieren eines Programms, das die Windows-API direkt oder indirekt verwendet, müssen Sie entscheiden, welche Mindestversion von Windows unterstützt werden soll. In den meisten Fällen ist Windows 7 eine gute Wahl. Weitere Informationen finden Sie unter [Header file problems (Probleme mit Headerdateien)](porting-guide-spy-increment.md#header_file_problems). Das Makro `WINVER` definiert die älteste Version von Windows, unter der das Programm ausgeführt werden kann. Wenn Ihr MFC-Programm WINVER auf 0x0501 (Windows XP) festlegt, wird eine Warnung angezeigt, da XP von MFC nicht mehr unterstützt wird, obwohl der Compiler selbst über einen XP-Modus verfügt.

Weitere Informationen finden Sie unter [Aktualisieren der Windows-Zielversion](porting-guide-spy-increment.md#updating_winver) und [Weitere veraltete Headerdateien](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL/MFC

ATL und MFC sind relativ stabile APIs, allerdings werden auch hier gelegentlich Änderungen vorgenommen. Weitere Informationen finden Sie unter [Visual C++ change history 2003 – 2015 (Änderungsverlauf von Visual C++ von 2003 bis 2015)](visual-cpp-change-history-2003-2015.md), [What's New for Visual C++ in Visual Studio (Neuerungen bei Visual C++ in Visual Studio 2019)](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) und [C++ conformance improvements in Visual Studio (Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio)](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 wurde bereits in „MSVCRTD.lib“ definiert

Dieser Fehler kann in MFC-Anwendungen auftreten. Er weist auf ein Sortierungsproblem zwischen der CRT- und der MFC-Bibliothek hin. Die MFC-Bibliothek muss zuerst so verknüpft werden, dass die Operatoren „new“ und „delete“ bereitgestellt werden. Um den Fehler zu beheben, verwenden Sie den Schalter `/NODEFAULTLIB`, um diese Standardbibliotheken zu ignorieren: „MSVCRTD.lib“ und „mfcs140d.lib“. Fügen Sie diese Bibliotheken dann als zusätzliche Abhängigkeiten hinzu.

## <a name="32-vs-64-bit"></a>32-Bit oder 64-Bit

Wenn Ihr ursprünglicher Code für 32-Bit-Systeme kompiliert wurde, können Sie eine 64-Bit-Version anstelle von oder zusätzlich zu einer neuen 32-Bit-App erstellen. Im Allgemeinen sollten Sie das Programm zuerst im 32-Bit-Modus kompilieren, und anschließend die Kompilierung der 64-Bit-Version vornehmen. Die Kompilierung für 64-Bit ist einfach, aber in einigen Fällen werden Fehler sichtbar, die in 32-Bit-Builds verborgen waren.

Außerdem sollten Sie mögliche Probleme im Zusammenhang mit Zeigergröße, Zeit- und Größenwerten sowie Formatbezeichnern in den Funktionen „printf“ und „scanf“ kennen, die während der Kompilierung und zur Laufzeit auftreten können. Weitere Informationen finden Sie unter [Konfigurieren von Visual C++ für für 64-Bit-x64-Ziele](../build/configuring-programs-for-64-bit-visual-cpp.md) und [Häufig auftretende 64-Bit-Migrationsprobleme bei Visual C++](../build/common-visual-cpp-64-bit-migration-issues.md). Weitere Migrationstipps finden Sie im [Programmierhandbuch für 64-Bit-Windows](/windows/win32/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode oder MBCS/ASCII

Bevor Unicode standardisiert wurde, verwendeten viele Programme den Mehrbyte-Zeichensatz (MBCS) zur Darstellung von Zeichen, die im ASCII-Zeichensatz nicht enthalten sind. In älteren MFC-Projekten war der MBCS die Standardeinstellung, und wenn Sie ein solches Programm aktualisieren, werden Warnungen angezeigt, die Ihnen raten, stattdessen Unicode zu verwenden. Sie können die Warnung deaktivieren oder ignorieren, wenn Sie der Meinung sind, dass die Konvertierung in Unicode die Entwicklungskosten nicht wert ist. Um es für alle Projekte in der Projekt Mappe zu deaktivieren, öffnen Sie **Ansicht**  >  **Eigenschaften-Manager**, wählen Sie alle Projekte aus, für die Sie die Warnung deaktivieren möchten, klicken Sie dann mit der rechten Maustaste auf die ausgewählten Elemente, und wählen Sie **Eigenschaften**aus. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Konfigurationseigenschaften** > **C/C++** > **Erweitert**. Klicken Sie in der Eigenschaft **Bestimmte Warnungen deaktivieren** auf den Pfeil des Dropdownmenüs und dann auf **Bearbeiten**. Geben Sie „4996“ in das Textfeld ein (Schließen Sie das Präfix "C" nicht ein.) Wählen Sie **OK** , um die Eigenschaft zu speichern, und klicken Sie dann auf **OK** , um die Änderungen zu speichern

Weitere Informationen finden Sie unter [Portieren von MBCS zu Unicode](porting-guide-spy-increment.md#porting_to_unicode). Allgemeine Informationen zu MBCS und Unicode finden Sie unter [Text und Zeichen folgen in Visual C++](../text/text-and-strings-in-visual-cpp.md) und [Internationalisierung](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Weitere Informationen

[Aktualisieren von Projekten aus früheren Versionen von Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Verbesserungen der C++-Konformität in Visual Studio](../overview/cpp-conformance-improvements.md)
