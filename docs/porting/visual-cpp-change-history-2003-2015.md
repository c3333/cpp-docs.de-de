---
title: Änderungsverlauf von Visual C++ von 2003 bis 2015
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 51de46487d85f4b8d7d357a0d1842f3d3192fff7
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404794"
---
# <a name="visual-c-change-history-2003---2015"></a>Änderungsverlauf von Visual C++ von 2003 bis 2015

In diesem Artikel werden alle bedeutenden Änderungen von Visual Studio 2015 zurück bis Visual Studio 2003 beschrieben. Die in diesem Artikel verwendeten Begriffe „neues Verhalten“ und „jetzt“ beziehen sich auf Visual Studio 2015 und höher. Die Begriffe „altes Verhalten“ und „davor“ beziehen sich auf Visual Studio 2013 und frühere Versionen.

Informationen zur neuesten Version von Visual Studio finden Sie unter [What's new for Visual C++ in Visual Studio (Neuerungen bei Visual C++ in Visual Studio)](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) und [Conformance Improvements in Visual C++ in Visual Studio (Verbesserungen bei der Übereinstimmung mit Visual C++-Standards in Visual Studio)](../overview/cpp-conformance-improvements.md).

> [!NOTE]
> Es gibt keine binären Änderungen von Visual Studio 2015 auf Visual Studio 2017.

Wenn Sie auf eine neue Version von Visual Studio upgraden, treten unter Umständen Kompilierungs- und/oder Laufzeitfehler im Code auf, der zuvor ordnungsgemäß kompiliert und ausgeführt wurde. Änderungen in der neuen Version, die solche Probleme verursachen, werden als *bedeutende Änderungen* bezeichnet und werden in der Regel durch Änderungen im C++-Sprachenstandard, in den Funktionssignaturen oder im Layout von Objekten im Arbeitsspeicher erforderlich.

Es wird empfohlen, dass Sie keine statischen Links zu Binärdateien mit einer anderen Version des Compilers erstellen, um Laufzeitfehler zu vermeiden, die schwer zu erkennen und zu diagnostizieren sind. Stellen Sie beim Aktualisieren eines EXE- oder DLL-Projekts außerdem sicher, die Bibliotheken zu aktualisieren, mit denen es verknüpft ist. Übergeben Sie keine CRT- (C-Laufzeit) oder C++-Standardbibliothekstypen zwischen Binärdateien, einschließlich DLL-Dateien, die mit verschiedenen Versionen des Compilers kompiliert wurden. Weitere Informationen finden Sie unter [Potenzielle Fehler bei der Übergabe von CRT-Objekten über DLL-Grenzen](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Sie sollten außerdem nie Code schreiben, der von einem bestimmten Layout für ein Objekt abhängt, das weder eine COM-Schnittstelle noch ein POD-Objekt ist. Wenn Sie diesen Code schreiben, müssen Sie sicherstellen, dass er nach dem Upgrade funktioniert. Weitere Informationen finden Sie unter [Portabilität an ABI-Grenzen](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Darüber hinaus können fortlaufende Verbesserungen der Übereinstimmung des Compilers mit Standards mitunter ändern, wie der Compiler den vorhandenen Quellcode versteht. Beispielsweise können während des Buildvorgangs neue oder andere Fehler oder sogar Verhaltensunterschiede im Code auftreten, für den zuvor Builds erstellt wurden und die Ausführung ordnungsgemäß schien. Obwohl diese Verbesserungen keine Breaking Changes wie die in diesem Artikel genannten Änderungen sind, müssen Sie möglicherweise einige Änderungen an Ihrem Quellcode vornehmen, um diese Probleme zu beheben:

- [C-Laufzeitbibliothek (CRT): Bedeutende Änderungen](#BK_CRT)

- [Standard-C++ und C++-Standardbibliothek: Breaking Changes](#BK_STL)

- [MFC und ATL: Bedeutende Änderungen](#BK_MFC)

- [Concurrency Runtime: Bedeutende Änderungen](#BK_ConcRT)

## <a name="visual-studio-2015-conformance-changes"></a><a name="VC_2015"></a> Visual Studio 2015: Änderungen bei der Konformität mit Standards

### <a name="c-runtime-library-crt"></a><a name="BK_CRT"></a>C-Lauf Zeit Bibliothek (CRT)

#### <a name="general-changes"></a>Allgemeine Änderungen

- **Umgestaltete Binärdateien**

   Die CRT-Bibliothek wurde in zwei verschiedene Binärdateien umgestaltet: eine Universal CRT (ucrtbase), die den Großteil der Standardfunkionen enthält, und eine VC-Laufzeitbibliothek (vcruntime). Die VC-Laufzeitbibliothek enthält die compilergebundenen Funktionen wie die Ausnahmebehandlung und intrinsische Funktionen. Wenn Sie die standardmäßigen Projekteinstellungen verwenden, sind Sie von dieser Änderung nicht betroffen, da der Linker automatisch die neuen Standardbibliotheken verwendet. Wenn Sie die **Linker**-Eigenschaft **Alle Standardbibliotheken ignorieren** des Projekts auf **Ja** festgelegt haben oder die `/NODEFAULTLIB`-Linkeroption in der Befehlszeile verwenden, müssen Sie die Liste der Bibliotheken (bei der Eigenschaft **Zusätzliche Abhängigkeiten**) so aktualisieren, dass sie die neuen umgestalteten Bibliotheken enthält. Ersetzen Sie die alte CRT-Bibliothek (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) mit den entsprechenden umgestalteten Bibliotheken. Für jede der beiden umgestalteten Bibliotheken gibt es eine statische (.lib) und eine dynamische (.dll) Version sowie endgültige (ohne Suffix) und Debugversionen (mit dem Suffix „d“). Die dynamischen Versionen haben eine Importbibliothek, mit der eine Verknüpfung erstellt wird. Die zwei umgestalteten Bibliotheken sind Universal CRT, d. h. „ucrtbase.dll“ oder „ucrtbase.lib“, „ucrtbased.dll“ oder „ucrtbased.lib“, und die VC-Laufzeitbibliothek, „libvcruntime.lib“, die „vcruntime*Version*.dll“, „libvcruntimed.lib“ und „vcruntimed*Version*.dll“. Die *Version* sowohl in Visual Studio 2015 als auch in Visual Studio 2017 ist 140. Siehe [CRT-Bibliotheksfunktionen](../c-runtime-library/crt-library-features.md).

#### \<locale.h>

- **localeconv**

   Die in „locale.h“ deklarierte [localeconv](../c-runtime-library/reference/localeconv.md)-Funktion funktioniert nun ordnungsgemäß, wenn [threadspezifisches Gebietsschema](../parallel/multithreading-and-locales.md) aktiviert ist. In früheren Versionen der Bibliothek hat diese Funktion die `lconv`-Daten für das globale Gebietsschema zurückgegeben statt den für das Gebietsschema des Threads.

   Wenn Sie threadspezifische Gebietsschemas verwenden, sollten Sie Ihre Nutzung von `localeconv` überprüfen. Wenn Ihr Code davon ausgeht, dass die `lconv`-Daten für das globale Gebietsschema zurückgegeben werden, sollten Sie dies korrigieren.

#### \<math.h>

- **C++-Überladungen der math-Bibliotheksfunktionen**

   In früheren Versionen wurden \<math.h> einige, jedoch nicht alle C++-über Ladungen für die Funktionen der mathematischen Bibliothek definiert. Die restlichen über Ladungen waren in der \<cmath> Kopfzeile. Code, der nur enthalten ist, \<math.h> kann Probleme mit der Auflösung von Funktions Überladungen haben. Die C++-über Ladungen wurden nun aus entfernt \<math.h> und werden nur in gefunden \<cmath> .

   Um Fehler zu beheben, schließen Sie ein, \<cmath> um die Deklarationen der Funktionen zu erhalten, die aus entfernt wurden \<math.h> . Die folgenden Funktionen wurden entfernt:

  - `double abs(double)` und `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - Die `float`- und `long double`-Versionen der folgenden Gleitkommafunktionen: `acos`, `acosh`, `asin`, `asinh`, `atan`, `atanh`, `atan2`, `cbrt`, `ceil`, `copysign`, `cos`, `cosh`, `erf`, `erfc`, `exp`, `exp2`, `expm1`, `fabs`, `fdim`, `floor`, `fma`, `fmax`, `fmin`, `fmod`, `frexp`, `hypot`, `ilogb`, `ldexp`, `lgamma`, `llrint`, `llround`, `log`, `log10`, `log1p`, `log2`, `lrint`, `lround`, `modf`, `nearbyint`, `nextafter`, `nexttoward`, `remainder`, `remquo`, `rint`, `round`, `scalbln`, `scalbn`, `sin`, `sinh`, `sqrt`, `tan`, `tanh`, `tgamma` und `trunc`

  Wenn Sie über Code verfügen, der `abs` mit einem Gleit kommatyp verwendet, der nur den- \<math.h> Header enthält, sind die Gleit Komma Versionen nicht mehr verfügbar. Der Aufruf wird nun in `abs(int)` aufgelöst, selbst wenn ein Gleitkommaargument vorhanden ist, wodurch der folgende Fehler ausgelöst wird:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Die Behebung für diese Warnung besteht darin, den-Aufrufvorgang `abs` durch eine Gleit Komma Version von zu ersetzen, z. b. `abs` `fabs` für ein doppeltes Argument oder `fabsf` für ein Float-Argument, oder den \<cmath> -Header einzuschließen und weiterhin zu verwenden `abs` .

- **Gleitkommakonformität**

   Viele an der math-Bibliothek vorgenommenen Änderungen wurden zur Verbesserung der Konformität mit den im Anhang F enthaltenen IEEE-754- und C11-Spezifikationen in Bezug auf Eingaben bei Sonderfällen wie NaN- und unendliche Werte. Stille NaN-Eingaben, die in früheren Bibliotheksversionen häufig als Fehler behandelt wurden, werden z. B. nicht mehr als Fehler behandelt. Weitere Informationen finden Sie unter [IEEE 754-Standard](https://standards.ieee.org/standard/754-2008.html) und Anhang F des [C11-Standards](https://www.iso.org/standard/57853.html).

   Diese Änderungen führen nicht zu Kompilierungsfehlern, können jedoch dazu führen, dass Programme ggf. ein anderes und standardkonformeres Verhalten aufweisen.

- **FLT_ROUNDS**

   Das FLT_ROUNDS-Makro wurde in Visual Studio 2013 auf einen konstanten Ausdruck erweitert, was nicht korrekt war, da der Rundungsmodus, z. B. beim Aufruf von fesetround, zur Laufzeit konfigurierbar ist. Das FLT_ROUNDS-Makro ist jetzt dynamisch und spiegelt ordnungsgemäß den aktuellen Rundungsmodus wider.

#### <a name="new-and-newh"></a>\<new> und \<new.h>

- **new und delete**

   In früheren Bibliotheksversionen wurden die in der Implementierung definierten Operatorfunktionen „new“ und „delete“ aus der DLL-Datei der Laufzeitbibliothek (z. B. msvcr120.dll) exportiert. Dieser Operatorfunktionen sind immer statisch mit Ihren Binärdateien verknüpft, selbst wenn DLL-Dateien der Laufzeitbibliothek verwendet werden.

   Für nativen oder gemischten Code (`/clr`) stellt dies keinen Breaking Change dar. Für Code, der jedoch als [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) kompiliert wurde, kann diese Änderung zu Fehlern beim Kompilieren führen. Wenn Sie Code als `/clr:pure` kompilieren, müssen Sie möglicherweise `#include <new>` oder `#include <new.h>`hinzufügen, um Buildfehler aufgrund dieser Änderung zu umgehen. Die Option `/clr:pure` ist seit Visual Studio 2015 veraltet und wird seit Visual Studio 2017 nicht mehr unterstützt. Code der „rein“ sein muss, sollte zu C# portiert werden.

#### \<process.h>

- **_beginthread und _beginthreadex**

   Die [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md)- und [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)-Funktionen enthalten jetzt einen Verweis auf das Modul, in dem die Threadprozedur für die Dauer des Threads definiert wird. Dadurch wird sichergestellt, dass Module nicht entladen werden, bis ein Thread vollständig ausgeführt wurde.

#### \<stdarg.h>

- **va_start und Verweistypen**

   Beim Kompilieren von C++-Code prüft [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) nun zur Kompilierzeit, dass das übergebene Argument kein Verweistyp ist. Verweistyp-Argumente sind gemäß dem C++-Standard nicht zulässig.

#### <a name="stdioh-and-conioh"></a><a name="stdio_and_conio"></a>\<stdio.h>und\<conio.h>

- **Die printf- und scanf-Funktionsreihe werden nun inline definiert.**

   Die Definitionen aller `printf` -und- `scanf` Funktionen wurden Inline in \<stdio.h> , \<conio.h> und andere CRT-Header verschoben. Dieser Breaking Change führt zu einem Linkerfehler (LNK2019: Unresolved External Symbol (LNK2019: nicht aufgelöstes externes Symbol)) für alle Programme, die diese Funktionen ohne entsprechende CRT-Header lokal deklariert haben. Sie sollten nach Möglichkeit den Code um die CRT-Header (d.h. `#include <stdio.h>`) und die Inlinefunktionen ergänzen. Wenn Sie diese Headerdateien nicht zu Ihrem Code hinzufügen möchten, können Sie alternativ eine Bibliothek zur Linkereingabe, „legacy_stdio_definitions.lib“, hinzufügen.

   Öffnen Sie zum Hinzufügen dieser Bibliothek zu Ihrer Linkereingabe in IDE das Kontextmenü für den Projektknoten, wählen Sie **Eigenschaften** und anschließend im Dialogfeld **Projekteigenschaften** den Eintrag **Linker** aus. Bearbeiten Sie anschließend die **Linkereingabe**, um `legacy_stdio_definitions.lib` zur durch Semikolons getrennten Liste hinzuzufügen.

   Wenn Ihr Projekt mit statischen Bibliotheken verknüpft ist, die mit einem früheren Visual Studio-Release als 2015 kompiliert wurden, meldet der Linker möglicherweise ein nicht aufgelöstes externes Symbol. Diese Fehler können auf interne Definitionen für `_iob` , `_iob_func` oder Verwandte Importe für bestimmte \<stdio.h> Funktionen in Form von _IMP_verweisen \* . Microsoft empfiehlt, alle statischen Bibliotheken mit der neuesten Version von C++-Compiler und -Bibliotheken zu kompilieren, wenn Sie ein Upgrade für ein Projekt durchführen. Wenn die Bibliothek eine Drittanbieterbibliothek ohne verfügbare Quelle ist, sollten Sie entweder eine aktualisierte Binärdatei vom Drittanbieter anfordern oder die Verwendung dieser Bibliothek in einer separaten DLL kapseln, die Sie mit einer älteren Version des Compilers und Bibliotheken kompilieren.

    > [!WARNING]
    > Wenn Sie eine Verknüpfung mit Windows SDK 8.1 oder früher erstellen, tritt ggf. der Fehler „nicht aufgelöstes externes Symbol“ auf. Fügen Sie zur Behebung dieses Fehlers in diesem Fall legacy_stdio_definitions.lib zu der Linkerausgabe wie bereits beschrieben hinzu.

   Um nicht aufgelöste symbolfehler zu beheben, können Sie versuchen, die in einer Binärdatei definierten Symbole mithilfe von [dumpbin.exe](../build/reference/dumpbin-reference.md) zu überprüfen. Verwenden Sie zum Anzeigen der in einer Bibliothek definierten Symbole die folgende Befehlszeile.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets und _getws**

   Die [gets](../c-runtime-library/gets-getws.md)- und [_getws](../c-runtime-library/gets-getws.md)-Funktionen wurden entfernt. Die gets-Funktion wurde in C11 aus der C-Standardbibliothek entfernt, da keine sichere Verwendung dieser Funktion gewährleistet werden kann. Bei der _getws-Funktion handelte es sich um eine Microsoft-Erweiterung, die der gets-Funktion für Breitzeichenfolgen entsprach. Alternativen zu dieser Funktionen stellen [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)und [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)dar.

- **_cgets und _cgetws**

   Die [cets](../c-runtime-library/cgets-cgetws.md)- und [_cgetws](../c-runtime-library/cgets-cgetws.md)-Funktionen wurden entfernt. Alternativen zu diesen Funktionen stellen [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) und [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)dar.

- **Formatierung von unendlichen Werten und NaN-Werten**

   In früheren Versionen wurden unendliche und NaN-Werte mit einem Satz MSVC-spezifischer Sentinelzeichenfolgen formatiert.

  - Unendlich: 1.#INF

  - Stiller NaN: 1. #QNAN

  - Signaling-NaN: 1.#SNAN

  - Unbestimmter NaN: 1. #IND

  All diesen Formaten konnte ein Vorzeichen vorangestellt werden und sie wurden möglicherweise je nach Feldbreite und Genauigkeit unterschiedlich formatiert (in einigen Fällen führte dies zu ungewöhnlichen Auswirkungen, beispielsweise würde `printf("%.2f\n", INFINITY)` „1.#J“ zurückgeben, weil „#INF“ auf zwei Stellen gerundet werden würde). In C99 wurden neue Anforderungen an die Formatierung von unendlichen und NaN-Werten eingeführt. Die MSVC-Implementierung entspricht nun diesen Anforderungen. Die neuen Zeichenfolgen lauten wie folgt:

  - Unendlich: inf

  - Stiller NaN: nan

  - Signaling-NaN: nan(snan)

  - Unbestimmter NaN: nan(ind)

  All diesen Werten kann ein Vorzeichen vorangestellt werden. Bei Verwendung eines großgeschriebenen Formatspezifizierers (%F statt %f) werden die Zeichenfolgen wie angefordert in Großbuchstaben ausgegeben (`INF` statt `inf`).

  Die [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)-Funktionen analysieren die neuen Zeichenfolgen so, dass nun ein Roundtrip über `printf` und `scanf` für diese ausgeführt wird.

- **Formatierung und Analyse von Gleitkommawerten**

   Neue Formatierung von Gleitkommawerten und Analysealgorithmen wurden zur Verbesserung der Genauigkeit eingeführt. Diese Änderung wirkt sich auf die [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)- und [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)-Funktionsreihen sowie auf Funktionen wie [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) aus.

   Mit den alten Formatierungsalgorithmen wurde nur eine begrenzte Zifferanzahl erzeugt und die übrigen Dezimalstellen wurden mit 0 dargestellt. Sie konnten in der Regel Zeichenfolgen generieren, für die ein Roundtrip zum ursprünglichen Gleitkommawert durchgeführt wird. Wenn Sie jedoch den exakten Wert (oder den nächstliegenden Dezimalwert) benötigten, war dies nicht ausreichend. Mit den neuen Formatierungsalgorithmen werden beliebig viele Ziffern zur Darstellung des Werts (oder der angegeben Genauigkeit) generiert. Schauen Sie sich als Beispiel für die Verbesserung die Ergebnisse bei der Ausgabe einer hohen Potenz von zwei an:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Alte Ausgabe:

    ```Output
    1208925819614629200000000
    ```

   Neue Ausgabe:

    ```Output
    1208925819614629174706176
    ```

   Mit den alten Analysealgorithmen werden nur bis zu 17 signifikante Ziffern aus der Eingabezeichenfolge berücksichtigt und die restlichen Ziffern verworfen. Dieser Ansatz ist ausreichend, um einen durch die Zeichenfolge dargestellten Näherungswert zu generieren. Das Ergebnis liegt in der Regel nah am richtig gerundeten Ergebnis. Mit der neuen Implementierung werden alle vorhanden Ziffern berücksichtigt und das ordnungsgemäß gerundete Ergebnis für alle Eingaben (bis zu 768 Ziffern) generiert. Darüber hinaus berücksichtigen diese Funktionen nun den Rundungsstatus (steuerbar über fesetround).  Da diese Funktionen möglicherweise verschiedene Ergebnisse ausgeben, stellt dies einen potenziellen Breaking Behavior Change dar. Die neuen Ergebnisse sind in jedem Fall genauer als die alten Ergebnisse.

- **Analyse von Gleitkommawerten bei Hexadezimalzahlen und unendlichen Werten sowie NaN-Werten**

   Mit den Analysealgorithmen für Gleitkommawerte werden nun Zeichenfolgen mit Hexadezimal-Gleitkommawerten (z. B. die von %a- und %A-Ausgabeformatspezifizierer generierten) und alle unendlichen und NaN-Zeichenfolgen, die von den `printf`-Funktionen generiert werden, wie oben beschrieben analysiert.

- **Auffüllung mit Nullen mithilfe von %A und %a**

   Mit den %a- und %A-Formatspezifizierern werden Gleitkommawerte als Hexadezimalmantisse und binärer Exponent formatiert. In früheren Versionen wurden mit den `printf`-Funktionen die Zeichenfolgen nicht ordnungsgemäß mit Nullen aufgefüllt. Beispiel: `printf("%07.0a\n", 1.0)` hat 00x1p+0 ausgegeben, statt 0x01p+0. Dieser Fehler wurde behoben.

- **Genauigkeit von %A und %a**

   Die Standardgenauigkeit der %A- und %a-Formatspezifizierer lag in früheren Bibliotheksversionen bei 6. Die Standardgenauigkeit liegt jetzt bei 13 und entspricht somit dem C-Standard.

   Dies ist eine Laufzeitverhaltensänderung in der Ausgabe von jeder Funktion, die eine Zeichenfolge mit %A oder % verwendet. Beim alten Verhalten lautete die Ausgabe bei Verwendung des %A-Spezifizierers möglicherweise „1.1A2B3Cp+111“. Die Ausgabe für den gleichen Wert lautet nun „1.1A2B3C4D5E6F7p + 111“. Zum Wiederherstellen des alten Verhaltens können Sie die Genauigkeit angeben, z. B. %.6A. Siehe [Genauigkeitsangabe](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **%F-Spezifizierer**

   Der %F-Format-/Konvertierungsspezifizierer wird nun unterstützt. Abgesehen davon, dass unendliche und NaN-Werte mithilfe von Großbuchstaben formatiert werden, weist er die gleiche Funktionsweise wie der Formatspezifizierer „%f“ auf.

   In früheren Versionen wurden F# und N als Längenmodifizierer von der Implementierung analysiert. Dieses Verhalten geht auf segmentierte Adressräume zurück: Mit diesen Längenspezifizierern wurden ferne und nahe Zeiger wie in %Fp oder %Ns ermittelt. Dieses Verhalten wurde entfernt. Wenn „%F“ ermittelt wird, wird es nun als %F-Formatspezifizierer behandelt. Wenn „%N“ ermittelt wird, wird es nun als ungültiger Parameter behandelt.

- **Formatierung von Exponenten**

   Mit den %e- und %E-Formatspezifizierern werden Gleitkommawerte als Dezimalmantisse und Exponent formatiert. Die %g- und %G-Formatspezifizierer formatieren die Zahlen in einigen Fällen auf die gleiche Weise. In früheren Versionen wurden Zeichenfolgen immer mit Exponenten mit drei Ziffern von der CRT generiert. Beispielsweise würde `printf("%e\n", 1.0)` 1.000000e+000 ausgeben, was falsch war. C erfordert, dass bei Exponenten, die mit nur einer oder zwei Ziffern dargestellt werden können, auch nur zwei Ziffern ausgegeben werden.

   In Visual Studio 2005 wurde eine globale Übereinstimmungsoption hinzugefügt: [_set_output_format](../c-runtime-library/set-output-format.md). Ein Programm konnte diese Funktion mit dem Argument _TWO_DIGIT_EXPONENT aufrufen, um die übereinstimmende Ausgabe von Exponenten zu aktivieren. Das Standardverhalten wurde zum standardkonformen Exponentenausgabemodus geändert.

- **Validierung der Formatzeichenfolge**

   In früheren Versionen haben die `printf`- und `scanf`-Funktionen viele ungültige automatisch Formatzeichenfolgen akzeptiert, was in einigen Fällen zu ungewöhnlichen Ergebnissen geführt hat. %hlhlhld wurde beispielsweise als %d behandelt. Alle ungültigen Formatzeichenfolgen werden jetzt als ungültige Parameter behandelt.

- **Überprüfung der fopen-Moduszeichenfolgen**

   In früheren Versionen hat die `fopen`-Funktionsreihe einige ungültige Moduszeichenfolgen einfach akzeptiert, z. B. `r+b+`. Ungültige Moduszeichenfolgen werden nun erkannt und als ungültige Parameter behandelt.

- **_O_U8TEXT-Modus**

   Die [_setmode](../c-runtime-library/reference/setmode.md)-Funktion meldet jetzt ordnungsgemäß den Modus für im _O_U8TEXT-Modus geöffnete Streams. In früheren Bibliotheksversionen wurden solche Streams als in _O_WTEXT geöffnete Streams gekennzeichnet.

   Dies ist eine wichtige Änderung, wenn Ihr Code den _O_WTEXT-Modus für Streams bei der UTF-8-Codierung interpretiert. Wenn UTF_8 von Ihrer Anwendung nicht unterstützt wird, sollten Sie in Erwägung ziehen, Unterstützung für diese immer häufiger verwendete Codierung hinzuzufügen.

- **snprintf und vsnprintf**

   Die [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)- und [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)-Funktionen sind jetzt implementiert. Älterer Code stellte häufig die Versionen der Makrodefinitionen dieser Funktionen bereit, da sie nicht von der CRT-Bibliothek implementiert wurden. In neueren Versionen ist dies nicht länger erforderlich. Wenn [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) oder [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) vor dem einschließen als Makro definiert ist \<stdio.h> , schlägt die Kompilierung jetzt mit einem Fehler fehl, der angibt, wo das Makro definiert wurde.

   In der Regel kann dieser Fehler behoben werden, indem alle Deklarationen von `snprintf` oder `vsnprintf` im Benutzercode gelöscht werden.

- **tmpnam generiert verwendbare Dateinamen**

   In früheren Versionen wurden mit den `tmpnam`- und `tmpnam_s`-Funktionen Dateinamen im Stammverzeichnis des Laufwerks (z.B. \sd3c.) geniert. Mit diesen Funktionen werden jetzt verwendbare Dateinamenpfade in einem temporären Verzeichnis generiert.

- **FILE-Kapselung**

   In früheren Versionen wurde der gesamte Dateityp in öffentlich definiert \<stdio.h> , sodass der Benutzercode in eine Datei gelangen und seine internale ändern konnte. Die Bibliothek blendet nun detaillierte Informationen zur Implementierung aus. Im Rahmen dieser Änderung ist die Datei, wie Sie in definiert \<stdio.h> ist, jetzt ein nicht transparenter Typ, und auf die Member kann nicht von außerhalb der CRT selbst zugegriffen werden.

- **_outp und _inp**

   Die Funktionen [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md) und [_inpd](../c-runtime-library/inp-inpw-inpd.md) wurden entfernt.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h> und \<sys/stat.h>

- **strtof und wcstof**

   Die Funktionen `strtof` und `wcstof` konnten `errno` nicht auf ERANGE festlegen, wenn der Wert nicht als float-Eigenschaft dargestellt werden konnte. Dieser Fehler galt nur für diese zwei Funktionen. Die Funktionen `strtod`, `wcstod`, `strtold` und `wcstold` waren nicht betroffen. Dieses Problem wurde behoben und stellt einen Breaking Change für die Laufzeit dar.

- **Ausgerichtete Speicherbelegungsfunktionen**

   In früheren Versionen haben die ausgerichteten Zuordnungsfunktionen (`_aligned_malloc`, `_aligned_offset_malloc` usw.) automatisch Anforderungen für einen Block mit einer Ausrichtung von 0 (null) akzeptiert. Die angeforderte Ausrichtung muss eine Potenz von zwei sein, was bei „0“ (null) nicht der Fall ist. Angeforderte Ausrichtungen von „0“ (null) werden nun als ungültige Parameter behandelt. Dieses Problem wurde behoben und stellt einen Breaking Change für die Laufzeit dar.

- **Heapfunktionen**

   Die Funktionen `_heapadd`, `_heapset` und `_heapused` wurden entfernt. Diese Funktionen waren nicht funktionsfähig, seit die CRT für die Verwendung des Windows-Heaps aktualisiert wurde.

- **smallheap**

   Die Linkoption `smallheap` wurde entfernt. Siehe [Linkoptionen](../c-runtime-library/link-options.md).

#### \<string.h>

- **wcstok**

   Die Signatur der Funktion `wcstok` wurde geändert und erfüllt jetzt die Anforderungen des C-Standards. In früheren Versionen der Bibliothek sah die Signatur dieser Funktion wie folgt aus:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Sie verwendete internen threadspezifischen Kontext, um den Status aller Aufrufe nachzuverfolgen, wie für `strtok` durchgeführt. Die Funktion weist jetzt die Signatur `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` auf und macht erforderlich, dass der Aufrufer den Kontext als drittes Argument an die Funktion übergibt.

   Eine neue `_wcstok`-Funktion mit der alten Signatur wurde hinzugefügt, um das Portieren zu erleichtern. Beim Kompilieren von C++-Code ist auch eine Inlineüberladung von `wcstok` mit der alten Signatur vorhanden. Diese Überladung ist veraltet. In C-Code können Sie mit define_CRT_NON_CONFORMING_WCSTOK möglicherweise festlegen, dass `_wcstok` anstelle von `wcstok` verwendet wird.

#### \<time.h>

- **Suhr**

   In früheren Versionen wurde die [clock](../c-runtime-library/reference/clock.md)-Funktion mit der Windows-API [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime) implementiert. Durch diese Implementierung war die die clock-Funktion von der Systemzeit abhängig, und war daher nicht monoton. Die clock-Funktion wurde hinsichtlich [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) neu implementiert und ist jetzt monoton.

- **fstat und_utime**

   In früheren Versionen haben die [_stat](../c-runtime-library/reference/stat-functions.md)-, [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)- und [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)-Funktionen die Sommerzeit nicht ordnungsgemäß behandelt. Vor Visual Studio 2013 haben all diese Funktionen die Normalzeiten fälschlicherweise als Sommerzeit behandelt.

   In Visual Studio 2013 wurde das Problem in der **_stat** -Funktions Familie behoben, aber die ähnlichen Probleme in den Funktionen " **f** " und " **_utime** " wurden nicht korrigiert. Diese Teilkorrektur führte zu Problemen aufgrund von Inkonsistenzen zwischen den Funktionen. Die Funktionen " **f** " und " **_utime** " wurden nun korrigiert, sodass alle diese Funktionen nun die Sommerzeit ordnungsgemäß und konsistent behandeln.

- **asctime**

   In früheren Versionen hat die [asctime](../c-runtime-library/reference/asctime-wasctime.md)-Funktion einstellige Tagesangaben mit einer führenden „0“ (null) aufgefüllt, z. B. `Fri Jun 06 08:00:00 2014`. Die Spezifikation erfordert, dass diese Tage wie bei `Fri Jun  6 08:00:00 2014` mit einem führenden Leerzeichen aufgefüllt werden. Dieses Problem wurde behoben.

- **strftime und wcsftime**

   Die Funktionen `strftime` und `wcsftime` unterstützen jetzt die Formatspezifizierer %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u und %V. Darüber hinaus werden die E- und O-Modifizierer analysiert, aber ignoriert.

   Der %c-Formatspezifizierer erzeugt „Entsprechende Datum- und Uhrzeitdarstellung“ für das aktuelle Gebietsschema. Im C-Gebietsschema muss diese Darstellung mit `%a %b %e %T %Y` übereinstimmen. Dabei handelt es sich um das gleiche Format, das von `asctime` erzeugt wird. In früheren Versionen hat der Formatspezifizierer „%c“ die Zeiten nicht ordnungsgemäß formatiert und sie in der Form `MM/DD/YY HH:MM:SS` dargestellt. Dieses Problem wurde behoben.

- **timespec und TIME_UTC**

   Der \<time.h> -Header definiert nun den `timespec` -Typ und die- `timespec_get` Funktion aus dem C11-Standard. Darüber hinaus ist das TIME_UTC-Makro jetzt für die Verwendung mit der Funktion `timespec_get` definiert. Dieses Update stellt einen Breaking Change für Code dar, der einen Konflikt mit der Definition für diese Bezeichner aufweist.

- **CLOCKS_PER_SEC**

   Das CLOCKS_PER_SEC-Makro wird jetzt auf eine ganze Zahl des Typs `clock_t` erweitert, wie für C erforderlich.

#### <a name="c-standard-library"></a><a name="BK_STL"></a>C++-Standard Bibliothek

Um neue Optimierungen und Debuggingüberprüfungen zu aktivieren, unterbricht die Visual Studio-Implementierung der C++-Standardbibliothek absichtlich die binäre Kompatibilität von einer Version zur nächsten. Wenn die C++-Standardbibliothek verwendet wird, können Objektdateien und statische Bibliotheken, die unter Verwendung von verschiedenen Versionen kompiliert werden, nicht in einer Binärdatei (EXE oder DLL) vermischt werden, und C++-Standardbibliotheksobjekte können nicht zwischen Binärdateien übergeben werden, die mit verschiedenen Versionen kompiliert werden. Eine solche Kombination gibt Linkerfehler über _MSC_VER-Konflikte aus. (_MSC_VER ist das Makro, das die Hauptversion des Compilers enthält – z. b. 1800 für Visual Studio 2013.) Diese Überprüfung kann keine DLL-Mischung erkennen und keine Vermischung erkennen, die Visual Studio 2008 oder früher betrifft.

- **Includedateien der C++-Standardbibliothek**

   Es wurden einige Änderungen an der Includestruktur in den Headern der C++-Standardbibliothek vorgenommen. Header der C++-Standardbibliothek dürfen einander nicht auf unbekannte Weise enthalten. Im Allgemeinen sollten Sie Code schreiben, der sorgfältig alle entsprechend dem C++-Standard benötigten Header enthält, und nicht darauf beruht, welche Header der C++-Standardbibliothek in anderen Headern der C++-Standardbibliothek enthalten sind. Dadurch kann der Code für andere Versionen und Plattformen verwendet werden. Mindestens zwei Headeränderungen in Visual Studio 2015 wirken sich auf den Benutzercode aus. Erstens \<string> enthält nicht mehr \<iterator> . Zweitens \<tuple> deklariert jetzt `std::array` ohne Angabe von \<array> , was Code durch die folgende Kombination von Codekonstrukten unterbrechen kann: der Code weist eine Variable mit dem Namen "Array" auf, und Sie verfügen über eine using-Direktive "using namespace Std;", und Sie fügen einen C++-Standard Bibliotheks Header (z \<functional> . b.) ein \<tuple> , der nun deklariert `std::array` .

- **steady_clock**

   Die \<chrono> Implementierung von [steady_clock](../standard-library/steady-clock-struct.md) wurde geändert, um die C++-Standard Anforderungen für die steadität und monoton zu erfüllen. `steady_clock`basiert nun auf [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) und `high_resolution_clock` ist jetzt eine typedef für `steady_clock` . Aus diesem Grund ist `steady_clock::time_point` in Visual Studio jetzt ein typedef-Element für `chrono::time_point<steady_clock>`. Dies ist jedoch nicht unbedingt bei anderen Implementierungen der Fall.

- **Speicherbelegungen und Konstanten**

   Es sind nun Vergleiche der Zuordnungen erforderlich, um Konstantenargumente zu akzeptieren. Wenn Ihre Zuweisungen diese Operatoren auf folgende Weise definieren,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   sollten Sie sie aktualisieren und als const-Member deklarieren:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **const-Elemente**

   Der C++-Standard hat Container von Konstanten Elementen (z. b. Vector \<const T> oder Set \<const T> ) immer untersagt. In Visual Studio 2013 und in früheren Versionen waren solche Container zulässig. In der aktuellen Version tritt beim Kompilieren dieser Container ein Fehler auf.

- **std::allocator::deallocate**

   In Visual Studio 2013 und früheren Versionen hat `std::allocator::deallocate(p, n)` das für *n* übergebene Argument ignoriert.  Der C++-Standard erfordert, dass *n* dem Wert entspricht, der als erstes Argument für den Aufruf dem von *p* zurückgegebenen `allocate`-Spezifizierer entspricht. In der aktuellen Version wird jedoch der Wert *n* untersucht. Code, der Argumente für *n* übergibt, die sich vom Standard unterscheiden, könnte zur Laufzeit abstürzen.

- **hash_map und hash_set**

   Die nicht standardmäßigen Header Dateien \<hash_map> und \<hash_set> sind in Visual Studio 2015 veraltet und werden in einer zukünftigen Version entfernt. Verwenden Sie stattdessen \<unordered_map> und \<unordered_set>.

- **Vergleichsoperatoren und operator()**

   Assoziative Container (die- \<map> Familie) erfordern nun, dass Ihre Vergleichs Operatoren über konstant Aufruf Bare Funktionsaufruf Operatoren verfügen. Beim Ausführen des folgenden Codes tritt nun in einer Vergleichsklassendeklaration ein Fehler beim Kompilieren auf:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Ändern Sie zur Behebung dieses Problems die Funktionsdeklaration zu der folgenden:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **Typmerkmale**

   Die alten Namen für Typmerkmale aus einer früheren Version des C++-Standardentwurfs wurden entfernt. Diese wurden in C++11 auf die C++11-Werte in Visual Studio 2015 aktualisiert. In der folgenden Tabelle werden die alten und neuen Namen aufgeführt.

   |Alter Name|Neuer Name|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **launch::any- und launch::sync-Richtlinien**

   Der nicht dem Standard entsprechenden `launch::any`- und `launch::sync`-Richtlinien wurden entfernt. Stattdessen wird `launch:async | launch:deferred` für `launch::any` verwendet. Verwenden Sie `launch::deferred` für `launch::sync`. Siehe [launch-Enumeration](../standard-library/future-enums.md#launch).

#### <a name="mfc-and-atl"></a><a name="BK_MFC"></a> MFC und ATL

- **Microsoft Foundation Classes (MFC)**

   ist aufgrund seiner Größe nicht mehr in der Standardinstallation von Visual Studio enthalten. Um MFC zu installieren, wählen Sie die Option **benutzerdefinierte** Installation in Visual Studio 2015-Setup aus. Wenn Sie Visual Studio 2015 bereits installiert haben, können Sie MFC installieren, indem Sie das **Visual Studio-Setup** erneut ausführen. Wählen Sie die Installationsoption **Benutzerdefiniert**, und wählen Sie dann die Option **Microsoft Foundation Classes** aus. Sie können das **Visual Studio-Setup** in der **Systemsteuerung** über das Steuerelement **Programme und Features** oder über das Installationsmedium ausführen.

   Diese Bibliothek ist weiterhin im Visual C++ Redistributable Package enthalten.

#### <a name="concurrency-runtime"></a><a name="BK_ConcRT"></a>Concurrency Runtime

- **Yield-Makro aus „Windows.h“ weist einen Konflikt auf mit concurrency::Context::Yield**

   Die Concurrency Runtime verwendete zuvor `#undef`, um die Yield-Makrodefinition zur Vermeidung von Konflikten zwischen dem in Windows.h und der `concurrency::Context::Yield`-Funktion definierten Yield-Makro aufzuheben. `#undef` wurde entfernt, und es wurde ein neuer nicht in Konflikt stehender äquivalenter API-Aufruf, [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution), hinzugefügt. Zur Umgehung von Konflikten mit Yield können Sie entweder den Code stattdessen zum Aufrufen der Funktion `YieldExecution` aktualisieren, oder den Namen der Funktion `Yield` auf der Aufrufsite wie im folgenden Beispiel aufgeführt durch Klammern umschließen:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Verbesserungen der Übereinstimmung des Compilers mit Standards in Visual Studio 2015

Wenn Sie Code aus früheren Versionen upgraden, können auch Compilerfehler auftreten, die die Folge von Verbesserungen der Überstimmung mit Standards in Visual Studio 2015 sind. Diese Verbesserungen unterbrechen nicht die Binärkompatibilität früherer Versionen von Visual Studio, können aber zu Compilerfehlern führen, die zuvor nicht aufgetreten sind. Weitere Informationen finden Sie unter [Visual C++: Neuerungen 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

In Visual Studio 2015 können fortlaufende Verbesserungen der Compilerkonformität mitunter ändern, wie der Compiler den vorhandenen Quellcode versteht. Aus diesem Grund treten während Ihres Builds ggf. neue oder andere Fehler oder sogar Verhaltensunterschiede im Code auf, für den zuvor Builds erstellt wurden und die Ausführung ordnungsgemäß schien.

Diese Änderungen haben jedoch nur wenig oder keinen Einfluss auf den Großteil Ihres Quellcodes. Wenn Quellcode- oder andere Änderungen erforderlich sind, um diese Unterschiede zu beheben, sind diese Korrekturen eher klein und einfach. Wir haben zahlreiche Beispiele für zuvor zulässigen Quellcode, die möglicherweise geändert werden müssen *(vorher)*, und die Updates zur Korrektur *(nachher)* hinzugefügt.

Obwohl diese Unterschiede sich auf Ihren Quellcode oder andere Buildartefakte auswirken können, wirken sie sich nicht auf die Binärkompatibilität zwischen Updates für Visual Studio-Versionen aus. Ein *Breaking Change* ist schwerwiegender und kann sich auf die Kompatibilität mit Binärdateien auswirken. Diese Arten von Beeinträchtigung der Binärkompatibilität treten jedoch nur zwischen Hauptversionen von Visual Studio auf, z. B. zwischen Visual Studio 2013 und Visual Studio 2015. Informationen zu bedeutenden Änderungen, die zwischen Visual Studio 2013 und Visual Studio 2015 vorgenommen wurden, finden Sie unter [Visual Studio 2015: Änderungen bei der Übereinstimmung mit Standards](#VC_2015).

- [Verbesserungen bei der Übereinstimmung mit Standards in Visual Studio 2015](#VS_RTM)

- [Verbesserungen der Konformität in Update 1](#VS_Update1)

- [Verbesserungen bei der Übereinstimmung mit Standards in Update 2](#VS_Update2)

- [Verbesserungen der Konformität in Update 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Verbesserungen der Konformität in Visual Studio 2015

- /Zc:forScope-Option

   Die Compileroption `/Zc:forScope-` ist veraltet und wird in einem der nächsten Releases entfernt.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Diese Option wurde in der Regel für nicht dem Standard entsprechenden Code verwendet, der Schleifenvariablen gemäß dem Standard nach dem Punkt verwendet, an dem diese den Gültigkeitsbereich verlassen sollten. Dies war nur erforderlich, wenn Sie die `/Za`-Option zum Kompilieren verwendet haben, da die Verwendung einer Schleifenvariable ohne `/Za` nach dem Ende der Schleife immer zulässig ist. Wenn die Einhaltung von Standards keine Rolle spielt (z.B. wenn der Code nicht auf andere Compiler übertragbar ist), können Sie die `/Za`-Option deaktivieren (oder die Eigenschaft **Spracherweiterungen deaktivieren** auf **Nein** festlegen). Wenn Sie übertragbaren Code schreiben möchten, der den Standards entspricht, sollten Sie den Code umschreiben, indem Sie die Deklaration der Variablen an eine Stelle außerhalb der Schleifen verschieben.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` Compileroption

   Die `/Zg`-Compileroption (Funktionsprototypen generieren) ist nicht mehr verfügbar. Diese Compileroption wurde zuvor als veraltet markiert.

- Sie können Komponententests nicht mehr mit C++/CLI über die Befehlszeile mit der „mstest.exe“ ausführen. Verwenden Sie stattdessen vstest.console.exe. Siehe [Befehlszeilenoptionen für VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **änderbare-Schlüsselwort**

   Der **mutable**-Speicherklassenspezifizierer ist nicht mehr an Positionen zulässig, an denen beim Kompilieren zuvor ein Fehler aufgetreten ist. Der Compiler generiert nun den Fehler C2071 (Ungültige Speicherklasse). Gemäß dem Standard kann der **mutable**-Spezifizierer nur auf Namen von Klassendatenmembern angewendet werden und kann nicht auf als konstant oder statisch deklarierte Namen sowie nicht auf Verweismember angewendet werden.

   Beachten Sie z. B. folgenden Code:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   In früheren Versionen des Compilers war dies zulässig, jetzt generiert der Compiler jedoch den folgenden Fehler:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Entfernen Sie das redundante Schlüsselwort **mutable**, um den Fehler zu beheben.

- **char_16_t und char32_t**

   Sie können nicht mehr `char16_t` oder `char32_t` als Aliase in einer **typedef**verwenden, da diese Typen nun als integriert behandelt werden. Benutzer und Bibliotheksautoren haben in der Vergangenheit häufig `char16_t` bzw. `char32_t` als Aliasse von `uint16_t` bzw. `uint32_t` verwendet.

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   Entfernen Sie zum Aktualisieren des Codes die **typedef** -Deklarationen, und benennen Sie alle anderen Bezeichner um, die mit diesen Namen in Konflikt stehen.

- **Nichttyp-Vorlagenparameter**

   Bestimmter Code mit Nichttyp-Vorlagenparametern wird auf Typkompatibilität korrekt geprüft, wenn Sie explizite Vorlagenargumente bereitstellen. Der folgende Code wurde z.B. ohne Fehler in früheren Versionen von Visual Studio kompiliert.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   Der aktuelle Compiler generiert ordnungsgemäß einen Fehler, da der Typ des Vorlagenparameters nicht mit dem Vorlagenargument übereinstimmt (der Parameter ist ein Zeiger auf einen konstanten Member, die f-Funktion ist jedoch nicht konstant):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Stellen Sie zum Beheben dieses Fehlers im Code sicher, dass der Typ des verwendeten Vorlagenarguments mit dem deklarierten Typ des Vorlagenparameters übereinstimmt.

- **__declspec(align)**

   Der Compiler lässt `__declspec(align)` in Funktionen nicht mehr zu. Dieses Konstrukt wurde bisher ignoriert, nun wird jedoch ein Compilerfehler generiert.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Entfernen Sie zum Beheben dieses Problems `__declspec(align)` aus der Funktionsdeklaration. Da dies keine Auswirkungen hatte, ändert sich durch das Entfernen nichts.

- **Ausnahmebehandlung**

   Es gibt eine Reihe von Änderungen bei der Ausnahmebehandlung. Ausnahmeobjekte müssen kopiert oder verschoben werden können. Der folgende Code wird zwar in Visual Studio 2013 kompiliert, aber nicht in Visual Studio 2015:

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Das Problem besteht darin, dass der Kopierkonstruktor privat ist. Somit kann das Objekt nicht während des normalen Betriebs der Ausnahmebehandlung kopiert werden. Das gleiche gilt, wenn der Kopierkonstruktor als **explizit** deklariert ist.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Stellen Sie zum Aktualisieren des Codes sicher, dass der Kopierkonstruktor für Ihr Ausnahmeobjekt **öffentlich** und nicht als **explizit** deklariert ist.

   Beim Abfangen einer Ausnahme nach Wert muss das Ausnahmeobjekt ebenfalls kopiert werden können. Der folgende Code wird zwar in Visual Studio 2013 kompiliert, aber nicht in Visual Studio 2015:

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   Sie können dieses Problem beheben, indem Sie den Parametertyp für **catch** auf einen Verweis festlegen.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Zeichenfolgenliterale gefolgt von Makros**

   Der Compiler unterstützt nun benutzerdefinierte Literale. Folglich werden Zeichenfolgenliterale, auf die Makros ohne dazwischenliegende Leerzeichen folgen, als benutzerdefinierte Literale interpretiert, was zu Fehlern oder unerwarteten Ergebnissen führen kann. In vorherigen Compilern wurde der beispielsweise der folgende Code erfolgreich kompiliert:

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   Der Compiler interpretierte diesen Code als ein Zeichenfolgenliteral „Hello“ gefolgt von einem Makro, das in „there“ erweitert wird, und führte die zwei Zeichenfolgenliterale zu einer verketteten Zeichenfolge zusammen. In Visual Studio 2015 interpretiert der Compiler diese Sequenz als ein benutzerdefiniertes Literal. Da kein entsprechendes benutzerdefiniertes `_x`-Literal definiert ist, wird jedoch ein Fehler generiert.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Fügen Sie zur Behebung dieses Problems ein Leerzeichen zwischen das Zeichenfolgenliteral und das Makro ein.

- **Angrenzende Zeichenfolgenliterale**

   Auf ähnliche Weise wurden angrenzende Zeichenfolgenliterale ohne Leerzeichen aufgrund von zugehörigen Änderungen in der Zeichenfolgenanalyse als eine verkettete Zeichenfolge in den vorherigen Versionen von Visual C++ interpretiert. In Visual Studio 2015 müssen Sie ein Leerzeichen zwischen den beiden Zeichenfolgen hinzufügen. Der folgende Code muss z. B. geändert werden:

    ```cpp
    char * str = "abc""def";
    ```

   Fügen Sie ein Leerzeichen zwischen den beiden Zeichenfolgen hinzu, um dieses Problem zu beheben:

    ```cpp
    char * str = "abc" "def";
    ```

- **Platzierungsoperatoren „new“ und „delete“**

   An den **Delete** -Operator wurde eine Änderung vorgenommen, um die Konformität mit dem c++ 14-Standard zu erzielen. Detaillierte Informationen zur Standardänderung finden Sie unter [Aufhebung der Zuordnung mit C++-Größeninformationen](https://isocpp.org/files/papers/n3778.html). Durch die Änderungen wird eine Form des globalen **Delete** -Operators hinzugefügt, der einen size-Parameter annimmt. Wenn Sie zuvor einen Operator **Delete** mit der gleichen Signatur verwendet haben (um einem **Platzierungs Operator new** zu entsprechen), erhalten Sie einen Compilerfehler (nämlich c2956, der an dem Punkt auftritt, an dem die Platzierung New verwendet wird, da dies die Position im Code ist, an der der Compiler versucht, einen entsprechenden passenden **Delete** -Operator zu identifizieren). Breaking Change

   Bei der Funktion `void operator delete(void *, size_t)` hat es sich um einen **delete**-Platzierungsoperator gehandelt, der der Funktion `void * operator new(size_t, size_t)` des Platzierungsoperators **new** in C++11 entspricht. Durch die Aufhebung der Zuordnung mit C++14-Größeninformationen ist diese delete-Funktion nun eine *gewöhnliche Funktion zum Aufheben der Zuordnung* (globaler **delete**-Operator). Der Standard erfordert es, dass das Programm bei Verwendung eines Platzierungsoperators „new“, der eine entsprechenden delete-Funktion sucht und eine gewöhnliche Funktion zum Aufheben der Zuordnung ermittelt, nicht ordnungsgemäß formatiert ist.

   Nehmen Sie beispielsweise an, dass Ihr Code sowohl eine **Platzierung New** als auch eine **Platzierungs Löschung**definiert:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   Das Problem tritt aufgrund der Entsprechung in den Funktions Signaturen zwischen einem von Ihnen definierten **Platzierungs Lösch** Operator und dem neuen globalen **Delete** -Operator auf. Überlegen Sie, ob Sie einen anderen Typ als `size_t` für alle **new**- und **delete**-Platzierungsoperatoren verwenden können. Der Typ von `size_t` **typedef** ist vom Compiler abhängig. In MSVC handelt es sich um **typedef** für **unsigned int**. Eine gute Lösung hierfür stellt die Verwendung eines enumerierten Typs wie die des folgenden dar:

    ```cpp
    enum class my_type : size_t {};
    ```

   Ändern Sie dann die Definition der **Platzierung New** und **Delete** , um diesen Typ als zweites Argument anstelle von zu verwenden `size_t` . Sie müssen auch die Aufrufe von "Platzierung New" aktualisieren, um den neuen Typ zu übergeben (z. b. mit, `static_cast<my_type>` um den ganzzahligen Wert zu konvertieren) und die Definition von " **New** " und " **Delete** " aktualisieren, um Sie wieder in den ganzzahligen Typ umzuwandeln. Hierfür müssen **Sie keine** Aufzählung verwenden. ein Klassentyp mit einem `size_t` Member würde ebenfalls funktionieren.

   Eine alternative Lösung besteht darin, dass Sie möglicherweise die **Platzierung der neuen Platzierung** vollständig ausschließen können. Wenn Ihr Code die **Platzierung New** verwendet, um einen Speicherpool zu implementieren, wobei das Platzierungs Argument die Größe des zugeordneten oder gelöschten Objekts ist, kann die Funktion zum Aufheben der Zuordnung von Größenordnungen zum Ersetzen Ihres eigenen benutzerdefinierten Speicherpool Codes geeignet sein, und Sie können die Platzierungsfunktionen entfernen und einfach einen eigenen **Delete** -Operator mit zwei Argumenten anstelle der Platzierungsfunktionen verwenden.

   Wenn Sie Ihren Code nicht sofort aktualisieren möchten, können Sie mit der Compileroption `/Zc:sizedDealloc-` das alte Verhalten wiederherstellen. Wenn Sie diese Option verwenden, sind die Delete-Funktionen mit zwei Argumenten nicht vorhanden und führen nicht zu einem Konflikt mit dem **Platzierungs Lösch** Operator.

- **Union-Datenmember**

   Union-Datenmember dürfen über keine Verweistypen verfügen. Der folgende Code kompiliert zwar in Visual Studio 2013 erfolgreich, aber erzeugt in Visual Studio 2015 einen Fehler.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   Der oben genannte Code geniert die folgenden Fehler:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Ändern Sie zur Behebung dieses Fehlers die Verweistypen in einen Zeiger oder einen Wert. Für die Änderung des Typs in einen Zeiger sind Änderungen im Code erforderlich, der das Union-Feld verwendet. Durch die Änderung des Codes in einen Wert werden die in der Union gespeicherten Daten geändert, was Auswirkungen auf andere Felder hat, da Felder in Uniontypen den gleichen Speicher gemeinsam verwenden. Je nach Wertgröße kann dies ggf. auch die Größe der Union ändern.

- Anonyme Unions weisen nun eine größere Standardkonformität auf. Frühere Versionen des Compilers haben einen expliziten Konstruktor und Destruktor für anonyme Unions generiert. Diese vom Compiler generierten Funktionen werden in Visual Studio 2015 gelöscht.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   Der oben genannte Code geniert in Visual Studio 2015 den folgenden Fehler:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Geben Sie zur Behebung dieses Fehlers eigene Definitionen des Konstruktors und/oder des Destruktors an.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **Unions mit anonymen Strukturen**

   Zur Einhaltung des Standards wurde das Laufzeitverhalten für Member anonymer Strukturen in Unions geändert. Der Konstruktor für anonyme Strukturmember in einer Union wird nicht mehr implizit aufgerufen, wenn eine solche Union erstellt wird. Der Destruktor für anonyme Strukturmember in einer Union wird nicht mehr implizit aufgerufen, wenn die Union den Gültigkeitsbereich verlässt. Betrachten Sie den folgenden Code, in dem der Union-Typ „U“ eine anonyme Struktur enthält, die wiederum die benannte Memberstruktur „S“ enthält, die einen Destruktor aufweist.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Der Konstruktor für S wird in Visual Studio 2013 immer dann aufgerufen, wenn die Union erstellt wird, und der Destruktor für S wird immer dann aufgerufen, wenn der Stapel für Funktion f bereinigt wird. In Visual Studio 2015 werden jedoch weder der Konstruktor noch der Destruktor aufgerufen. Der Compiler gibt eine Warnung zu dieser Verhaltensänderung aus.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Benennen Sie zum Wiederherstellen des ursprünglichen Verhaltens die anonyme Struktur. Das Laufzeitverhalten von nicht anonymen Strukturen ist von der Compilerversion unabhängig.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Verschieben Sie alternativ den Konstruktor- und Destruktorcode in die neuen Funktionen, und fügen Sie diesen Funktionen aus der Konstruktor- und Destruktorunion Aufrufe hinzu.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **Vorlagenauflösung**

   Es wurden Änderungen an der Namensauflösung für Vorlagen vorgenommen. Bei Berücksichtigung der Kandidaten für eine Namensauflösung können potenzielle Namen in C++ ggf. eine ungültige Vorlageninstanziierung erzeugen. Diese ungültigen Instanziierungen generieren in der Regel keine Compilerfehler, dies ist das SFINAE-Prinzip (Ersetzungsfehler sind keine Fehler).

   Wenn der Compiler jetzt von SFINAE zum Instanziieren der Spezialisierung einer Klassenvorlage aufgefordert wird, handelt es sich bei allen während dieses Prozesses aufgetretenen Fehler um Compilerfehler. In früheren Versionen hat der Compiler diese Fehler ignoriert. Beachten Sie z. B. folgenden Code:

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   Beim Kompilieren mit dem aktuellen Compiler tritt der folgende Fehler auf:

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   Der Grund hierfür ist, dass die Klasse `D` zum Zeitpunkt des ersten Aufrufs von is_base_of noch nicht definiert war.

   In diesem Fall besteht die Lösung darin, diese Typmerkmale nicht zu verwenden, bis die Klasse definiert wurde. Wenn Sie die Definitionen von `B` und `D` an den Anfang der Codedatei verschieben, wird der Fehler behoben. Überprüfen Sie, wenn sich die Definitionen in Headerdateien befinden, die Reihenfolge der Include-Anweisungen für die Headerdateien, um sicherzustellen, dass alle Klassendefinitionen kompiliert werden, bevor die problematischen Vorlagen verwendet werden.

- **Kopierkonstruktoren**

   Sowohl in Visual Studio 2013 als auch in Visual Studio 2015 generiert der Compiler einen Kopierkonstruktor für eine Klasse, die über einen benutzerdefinierten Bewegungskonstruktor verfügt, jedoch über keinen benutzerdefinierten Kopierkonstruktor. In Dev14 wird dieser implizit generierte Kopierkonstruktor ebenfalls als „= delete“ gekennzeichnet.

<!--From here to VS_Update1 added 04/21/2017-->

- **Als externes „C“ deklariertes main benötigt nun einen Rückgabetyp**

   Mit dem folgenden Code wird nun C4430 generiert.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Um den Fehler zu beheben, fügen Sie den Rückgabetyp hinzu:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **typename ist in Memberinitialisierer nicht zulässig**

   Mit dem folgenden Code wird nun C2059 generiert:

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   Um den Fehler zu beheben, entfernen Sie `typename` aus dem Initialisierer:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Speicherklasse für explizite Spezialisierungen wird ignoriert**

   Im folgenden Code wird der statische Speicherklassenspezifizierer ignoriert.

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **Eine Konstante, die in static_assert innerhalb einer Klassenvorlage verwendet wird, verursacht stets einen Fehler**

   Der folgende Code bewirkt, dass `static_assert` stets einen Fehler verursacht:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Umschließen Sie zur Umgehung dieses Problems den Wert in einer **Struktur**:

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **Regeln, die für vorwärts Deklarationen erzwungen werden. (Gilt nur für C.)**

   Mit dem folgenden Code wird nun C2065 generiert:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Fügen Sie zum Beheben dieses Problems die entsprechenden Vorwärtsdeklarationen hinzu:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Konsistentere Erzwingung von Funktionszeigertypen**

   Mit dem folgenden Code wird nun C2197 generiert:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Mehrdeutige Aufrufe überladener Funktionen**

   Der folgende Code erzeugt nun C266: „N::bind“: Mehrdeutiger Aufruf einer überladenen Funktion

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   Zur Behebung des Fehlers können Sie den Aufruf von `bind: N::bind(...)` vollständig qualifizieren. Wenn diese Änderung jedoch ein Manifest durch einen nicht deklarierten Bezeichner (C2065) ist, kann es sinnvoll sein, dies mit einer **using** -Deklaration zu beheben.

   Dieses Muster tritt häufig mit „ComPtr“ und anderen Typen im Namespace `Microsoft::WRL` auf.

- **Korrigieren der falschen Adresse**

   Mit dem folgenden Code wird nun C2440 generiert: '=': Konvertierung von „type *“ in „type“ nicht möglich. Ändern Sie zum Beheben dieses Fehler „&(type)“ in „(type)“ und „(&f())“ in „(f())“.

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **Zeichenfolgenliteral ist ein konstantes Array**

   Der folgende Code erzeugt nun C2664: „void f(void *)“: Argument 1 kann nicht von „const char (*)[2]“ in „void *“ konvertiert werden

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Zur Behebung des Fehlers müssen Sie den Funktionsparametertyp in `const void*` ändern oder den Text von `h` wie im folgenden Beispiel ändern:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C++11-UDL-Zeichenfolgen**

   Der folgende Code erzeugt nun den Fehler C3688: ungültiges Literalsuffix „L“; Literaloperator oder Literaloperatorvorlage „operator ""L“ nicht gefunden

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Diesen Fehler beheben Sie, indem Sie dem Code ein Leerzeichen hinzufügen:

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Im Beispiel oben wird `MACRO` nicht mehr als zwei Token (eine Zeichenfolge gefolgt von einem Makro) analysiert. Nun erfolgt die Analyse als einzelner Token-UDL. Das Gleiche gilt für „L""L""“, was zuvor als „L""“ und „L""“ analysiert wurde und nun als „L""L“ und „""“ analysiert wird.

   Regeln für das Verketten von Zeichenfolgen stimmen nun auch mit dem Standard überein, was bedeutet, dass „L"a" "b"“ mit „L"ab"“ übereinstimmt. Frühere Versionen von Visual Studio haben die Verkettung von Zeichenfolgen mit unterschiedlicher Zeichenbreite nicht akzeptiert.

- **C++11: leeres Zeichen entfernt**

   Der folgende Code erzeugt nun den Fehler C2137: leere Zeichenkonstante

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Ändern Sie zum Beheben des Fehlers den Code folgendermaßen, um die „0“ (null) explizit festzulegen:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **MFC-Ausnahmen können nicht nach Wert abgefangen werden, da sie nicht kopierbar sind**

   Der folgende Code in einer MFC-Anwendung verursacht jetzt Fehler C2316: „D“: Kann nicht aufgefangen werden, da Destruktor und/oder copy-Konstruktor nicht verfügbar sind oder gelöscht wurden

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   Zur Korrektur des Codes können Sie den „catch“-Block in `catch (const D &)` ändern, doch die bessere Lösung ist meist das Verwenden der MFC-Makros TRY/CATCH.

- **alignof ist jetzt ein Schlüsselwort**

   Der folgende Code führt jetzt zu Fehler C2332: „class“: fehlender Tagname. Um den Code zu korrigieren, müssen Sie die Klasse umbenennen oder, wenn die Klasse die gleiche Arbeit wie " **alignof**" ausführt, einfach die Klasse durch das Schlüsselwort "New" ersetzen.

    ```cpp
    class alignof{}
    ```

- **constexpr ist jetzt ein Schlüsselwort**

   Mit dem folgenden Code wird nun Fehler C2059 generiert: Syntaxfehler: ')'. Um den Code zu korrigieren, müssen Sie Funktions- oder Variablennamen umbenennen, die mit „constexpr“ aufgerufen werden.

    ```cpp
    int constexpr() {return 1;}
    ```

- **Verschiebbare Typen dürfen nicht const sein**

   Wenn eine Funktion einen Typ zurückgibt, der verschoben werden soll, darf der Rückgabetyp nicht **const** sein.

- **Gelöschte Kopierkonstruktoren**

   Der folgende Code erzeugt nun C2280: „S::S(S &&)“: Es wurde versucht, auf eine gelöschte Funktion zu verweisen:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Verwenden Sie für `S2` direkte Initialisierung, um den Fehler zu beheben:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Konvertierung in Funktionszeiger wird nur generiert, wenn kein Lambdaausdruck erfasst wird**

   Der folgende Code führt in Visual Studio 2015 zu C2664.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Um den Fehler zu beheben, entfernen Sie `=` aus der Erfassungsliste.

- **Mehrdeutige Aufrufe im Zusammenhang mit Konvertierungsoperatoren**

   Der folgende Code erzeugt nun C2440: „Typumwandlung“: Konvertierung von „S2“ zu „S1“ nicht möglich:

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   Um den Fehler zu beheben, müssen Sie den Konvertierungsoperator explizit aufrufen:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Der folgende Code erzeugt nun den Fehler C2593: „operator=“ ist mehrdeutig:

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   Um den Fehler zu beheben, müssen Sie den Konvertierungsoperator explizit aufrufen:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Korrigieren einer ungültigen Kopierinitialisierung in nicht statischer Datenmemberinitialisierung**

   Der folgende Code erzeugt nun den Fehler C2664: „S1::S1(S1 &&)“: Konvertierung von Argument 1 von „bool“ zu „const S1 &“ nicht möglich:

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Verwenden Sie direkte Initialisierung, um den Fehler zu korrigieren:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Zugreifen auf Konstruktoren in decltype-Anweisungen**

   Der folgende Code erzeugt nun C2248: „S::S“: Zugriff auf in der Klasse „S“ deklarierten privaten Member nicht möglich:

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   Fügen Sie zur Behebung des Fehlers eine „friend“-Deklaration für `S2` in `S` hinzu:

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Standardkonstruktor von Lambdaausdrücken wird implizit gelöscht**

   Der folgende Code erzeugt nun den Fehler C3497: Sie können keine Instanz eines Lambdaelements erstellen:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Um den Fehler zu beheben, entfernen Sie die Notwendigkeit des Aufrufs des Standardkonstruktors. Wenn das Lambda nichts erfasst, kann er in einen Funktionszeiger umgewandelt werden.

- **Lambdaausdrücke mit einem gelöschten Zuweisungsoperator**

   Mit dem folgenden Code wird nun Fehler C2280 generiert:

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   Um den Fehler zu beheben, ersetzen Sie den Lambda durch eine „functor“-Klasse, oder entfernen Sie die Notwendigkeit der Verwendung des Zuweisungsoperators.

- **Verschieben eines Objekt mit einem gelöschten Kopierkonstruktor**

   Der folgende Code erzeugt nun den Fehler C2280: „moveable::moveable(const moveable &)“: Versuch des Verweises auf eine gelöschte Funktion

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   Verwenden Sie zur Behebung des Fehlers stattdessen `std::move`:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Lokale Klasse kann nicht auf andere lokale Klasse verweisen, die später in derselben Funktion definiert ist**

   Der folgende Code erzeugt nun den Fehler C2079: „s“ verwendet die nicht definierte Struktur "main::S2"

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   Verschieben Sie die Definition von `S2` zur Behebung des Fehlers nach oben:

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **Basiskonstruktor mit protected-Zugriffsmodifizierer kann nicht im Körper eines abgeleiteten Konstruktors aufgerufen werden**

   Der folgende Code erzeugt nun den Fehler C2248: „S1::S1“: Zugriff auf in der Klasse „S1“ deklarierten geschützten Member nicht möglich

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   Entfernen Sie zur Behebung des Fehlers in `S2` den Aufruf von `S1()` aus dem Konstruktor, und verschieben Sie ihn bei Bedarf in eine andere Funktion.

- **{}verhindert Konvertierung in Zeiger**

   Der folgende Code erzeugt nun C2439 „S::p“: Member konnte nicht initialisiert werden

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Entfernen Sie zur Behebung des Fehlers die Klammern um die `0`, oder verwenden Sie stattdessen **nullptr**, wie im folgenden Beispiel gezeigt:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Falsche Makrodefinition und -nutzung mit Klammern**

   Das folgende Beispiel erzeugt nun den Fehler C2008: ";": Unerwartetes Zeichen in Makrodefinition

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Ändern Sie zum Beheben des Problems die oberste Zeile in `#define A();`.

   Der folgende Code erzeugt nun den Fehler C2059: Syntaxfehler: „)“

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Entfernen Sie das Leerzeichen zwischen A und (), um den Code zu korrigieren.

   Der folgende Code erzeugt nun den Fehler C2091: Funktion gibt Funktion zurück:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Um den Fehler zu beheben, entfernen Sie die Klammern nach DECLARE in S: `DECLARE;`.

   Der folgende Code erzeugt nun den Fehler C2062: Typ „int“ wurde nicht erwartet

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Definieren Sie zur Behebung des Problems `A` wie folgt:

    ```cpp
    #define A int
    ```

- **Zusätzliche Klammern in Deklarationen**

   Der folgende Code erzeugt nun den Fehler C2062: Typ „int“ wurde nicht erwartet

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Entfernen Sie die Klammern um `j`, um den Fehler zu beheben. Wenn die Klammern aus Gründen der Übersichtlichkeit benötigt werden, verwenden Sie ein **typedef**-Element.

- **Vom Compiler generierte Konstruktoren und __declspec(novtable)**

   In Visual Studio 2015 ist es wahrscheinlicher, dass vom Compiler generierte Inline-Konstruktoren von abstrakten Klassen mit virtuellen Basisklassen zu falscher Nutzung von `__declspec(novtable)` in Kombination mit `__declspec(dllimport)` führen.

- **auto erfordert einzelnen Ausdruck in direct-list-initialization**

   Der folgende Code erzeugt nun Fehler C3518: "testPositions": In einem „direct-list-initialization“-Kontext kann der Typ für „auto“ nur aus einem einzelnen Initialisierungsausdruck hergeleitet werden

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Eine Möglichkeit zur Behebung des Fehlers ist das Initialisieren von `testPositions`. Dabei wird wie folgt vorgegangen:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Überprüfen von Typen und Verweisen auf Typen für is_convertible**

   Der folgende Code bewirkt nun, dass die statische Assertion fehlschlägt.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Ändern Sie zum Beheben des Fehlers `static_assert` so, dass Zeiger mit `D` und `B2` verglichen werden:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **Deklarationen von __declspec(novtable) müssen einheitlich sein**

   Deklarationen von `__declspec` müssen über alle Bibliotheken hinweg einheitlich sein. Der folgende Code erzeugt nun einen Verstoß gegen eine Regel mit einer Definition:

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

### <a name="conformance-improvements-in-update-1"></a><a name="VS_Update1"></a> Verbesserungen bei der Übereinstimmung mit Standards in Update 1

- **Private virtuelle Basisklassen und indirekte Vererbung**

   In früheren Versionen des Compilers war es abgeleiteten Klassen möglich, Memberfunktionen ihrer indirekt abgeleiteten `private virtual`-Basisklassen aufzurufen. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler akzeptiert auf diese Weise erstellten Code nicht mehr und gibt dafür den Compilerfehler C2280 aus.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   Beispiel (vorher)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   Beispiel (nachher)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \- oder -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Überladener Operator „new“ und „delete“**

   In früheren Versionen des Compilers konnte ein **new**-Platzierungsoperator, der kein Member war, und ein **delete**-Platzierungsoperator, der kein Member war, statisch deklariert werden und in anderen Namespaces als dem globalen deklariert werden.  Durch dieses alte Verhalten entstand das Risiko, dass das Programm die Operatoren **new** oder **delete** nicht in der vom Programmierer beabsichtigten Implementierung aufruft, was zu einem schlechten Laufzeitverhalten ohne Rückmeldung führte. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2323 als Ergebnis aus.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   Beispiel (vorher)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   Beispiel (nachher)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   Auch wenn der Compiler keine bestimmte Diagnose erhält, wird der Inline Operator **New** als falsch formatiert betrachtet.

- **Aufrufen von ' Operator *Type*() ' (benutzerdefinierte Konvertierung) für nicht Klassentypen**

   Frühere Versionen ließen den Aufruf von 'operator *type*()' für Nichtklassentypen zu und ignorierten den Aufruf stumm. Durch dieses alte Verhalten entstand die Gefahr der stummen Erzeugung von ungültigem Code, was zu unvorhersehbarem Laufzeitverhalten führt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C2228 als Ergebnis aus.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   Beispiel (vorher)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   Beispiel (nachher)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **Redundanter Typname in ausführlichen Typspezifizierern**

   Frühere Versionen des Compilers ließen **typename** in ausführlichen Typbezeichnern zu. Auf diese Weise erstellter Code ist jedoch semantisch inkorrekt. Der Compiler akzeptiert in dieser Weise erstellten Code nicht mehr und gibt den Compilerfehler C3406 als Ergebnis aus.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   Beispiel (vorher)

    ```cpp
    template <typename class T>
    class container;
    ```

   Beispiel (nachher)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **Typableitung von Arrays aus einer Initialisiererliste**

   In früheren Versionen des Compilers wurde die Typableitung von Arrays aus einer Initialisiererliste nicht unterstützt. Der Compiler unterstützt jetzt diese Form der Typableitung. Das kann zur Folge haben, dass Aufrufe an Funktionsvorlagen mithilfe von Initialisiererlisten jetzt möglicherweise nicht mehr eindeutig sind, oder es wird eine andere Überladung gewählt als in früheren Versionen des Compilers. Um diese Probleme zu beheben, muss das Programm jetzt die vom Programmierer beabsichtigte Überladung explizit angeben.

   Wenn dieses neue Verhalten bewirkt, dass ein anderer Kandidat bei der Überladungsauflösung als ebenso gut wie der historische Kandidat angesehen wird, wird der Aufruf mehrdeutig, und der Compiler gibt den Compilerfehler C2668 als Ergebnis aus.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion (vorher)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   Beispiel 1: Mehrdeutiger Aufruf einer überladenen Funktion (nachher)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   Wenn dieses neue Verhalten bewirkt, dass ein anderer Kandidat bei der Überladungsauflösung als bessere Übereinstimmung als der historische Kandidat angesehen wird, wird der Aufruf eindeutig zum neuen Kandidaten aufgelöst, was eine Änderung im Verhalten des Programms bewirkt, die vermutlich von den Absichten des Programmierers abweicht.

   Beispiel 2: Änderung an der Überladungsauflösung (vorher)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   Beispiel 2: Änderung an der Überladungsauflösung (nachher)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **Wiederherstellung von Warnungen der switch-Anweisung**

   In früheren Versionen des Compilers wurden einige Warnungen, die sich auf **switch**-Anweisungen bezogen, entfernt. Diese Warnungen wurden jetzt wiederhergestellt. Der Compiler gibt jetzt die wiederhergestellten Warnungen aus, und Warnungen, die sich auf bestimmte Fälle (einschließlich des Standardfalls) bezogen, werden jetzt in der Zeile ausgegeben, die den Verstoß enthält, statt in der letzten Zeile der switch-Anweisung. Die Ausgabe dieser Warnungen in anderen Zeilen als bisher kann zur Folge haben, dass Warnungen, die früher mithilfe von `#pragma warning(disable:####)` unterdrückt wurden, möglicherweise nicht mehr wie beabsichtigt unterdrückt werden. Möglicherweise ist erforderlich, dass Sie die `#pragma warning(disable:####)`-Anweisung in eine Zeile oberhalb des ersten Verstoßes verschieben, um diese Warnungen wie beabsichtigt zu unterdrücken. Im Folgenden werden die wiederhergestellten Warnungen aufgeführt:

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   Beispiel für C4063 (vorher)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   Beispiel für C4063 (nachher)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   Beispiele für die anderen wiederhergestellten Warnungen stehen in deren Dokumentation zur Verfügung.

- **#include: Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers haben die Verwendung des Bezeichners '..' für das übergeordnete Verzeichnis im Pfadnamen von `#include`-Anweisungen nicht erkannt. Bei in dieser Weise erstelltem Code wird normalerweise die Absicht verfolgt, Header einzuschließen, die sich außerhalb des Projekts befinden, und dazu werden fälschlicherweise projektrelative Pfade verwendet. Bei diesem alten Verhalten ergab sich die Gefahr, dass das Programm möglicherweise mit Einschluss einer anderen als der vom Programmierer beabsichtigten Quelldatei compiliert wurde oder dass diese relativen Pfade nicht auf andere Buildumgebungen portiert werden konnten. Der Compiler erkennt jetzt in dieser Weise erstellten Code und benachrichtigt den Programmierer mit der optionalen Compilerwarnung C4464, sofern diese aktiviert ist.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   Beispiel (vorher)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   Beispiel (nachher)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   Darüber hinaus wird empfohlen, den Bezeichner „..“ für das übergeordnete Verzeichnis nicht zum Festlegen der Includeverzeichnisse des Projekts zu verwenden, obwohl der Compiler keine spezifische Diagnose meldet.

- **#pragma optimize() erstreckt sich über das Ende der Headerdatei hinaus** (betrifft nur `/Wall` `/WX`)

   In früheren Versionen wurden Änderungen an den Optimierungseinstellungen nicht erkannt, die zum Escapen einer in einer Übersetzungseinheit eingeschlossenen Headerddatei dienen. Der Compiler erkennt jetzt in dieser Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C4426 von der Position des `#include`-Verstoßes in Kenntnis, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn die Änderungen im Konflikt mit den Optimierungseinstellungen stehen, die durch die Befehlszeilenargumente für den Compiler festgelegt wurden.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   Beispiel (vorher)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   Beispiel (nachher)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **Nicht übereinstimmende Festlegung von „#pragma warning(push)“** und **#pragma warning(pop)** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers konnten keine `#pragma warning(push)`-Statusänderungen erkennen, die in Kombination mit `#pragma warning(pop)`-Statusänderungen in einer anderen Quelldatei auftraten, was selten beabsichtigt ist. Dieses alte Verhalten brachte die Gefahr mit sich, dass das Programm mit anderen Warnungseinstellungen als den vom Programmierer vorgesehenen kompiliert wurde, was möglicherweise zu einem schlechten Laufzeitverhalten führt. Der Compiler erkennt jetzt auf diese Weise erstellten Code und setzt den Programmierer mit der optionalen Compilerwarnung C5031 von der Position der `#pragma warning(pop)`-Übereinstimmung in Kenntnis, sofern diese aktiviert ist. Diese Warnung enthält einen Hinweis, der auf den Speicherort der entsprechenden „#pragma warning(push)“ verweist.

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   Beispiel (vorher)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   Beispiel (nachher)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   Wenngleich ungewöhnlich, wird Code mitunter absichtlich auf diese Weise geschrieben. Auf diese Weise erstellter Code ist empfindlich gegenüber Änderungen an der `#include`-Reihenfolge. Wir empfehlen, dass Quellcodedateien den Warnungsstatus nach Möglichkeit eigenständig verwalten sollten.

- **Nicht zugeordnete „#pragma warning“ (push)** (betrifft nur `/Wall` `/WX`)

   Frühere Versionen des Compilers haben nicht zugeordnete `#pragma warning(push)` -Statusänderungen am Ende einer Übersetzungseinheit nicht erkannt. Der Compiler erkennt jetzt auf diese Weise erstellten Code und informiert den Programmierer mit der optionalen Compilerwarnung C5032 über die Position der fehlenden `#pragma warning(push)`-Übereinstimmung, sofern diese aktiviert ist. Diese Warnung wird nur ausgegeben, wenn in der Übersetzungseinheit keine Kompilierfehler auftreten.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   Beispiel (vorher)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   Beispiel (nachher)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **Möglicherweise werden weitere Warnungen als Folge der verbesserten Statusnachverfolgung bei „#pragma warning“ angezeigt**

   In früheren Versionen des Compilers wurden Statusänderungen bei „#pragma warning“ nicht hinreichend gut nachverfolgt, um alle beabsichtigten Warnungen auszugeben. Durch dieses Verhalten bestand die Gefahr, dass bestimmte Warnungen unter anderen als den vom Programmierer beabsichtigten Umständen effektiv unterdrückt wurden. Die Nachverfolgung des Status von `#pragma warning` erfolgt nun auf stabilere Weise – insbesondere im Zusammenhang mit `#pragma warning`-Statusänderungen in Vorlagen – und gibt optional die neuen Warnungen C5031 und C5032 aus, die den Programmierer bei der Suche nach unbeabsichtigter Verwendung von `#pragma warning(push)` und `#pragma warning(pop)` unterstützen sollen.

   Als Ergebnis der verbesserten Nachverfolgung des Status von `#pragma warning` können jetzt Warnungen ausgegeben werden, die früher fälschlicherweise unterdrückt wurden oder mit falsch identifizierten Problemen zusammenhingen.

- **Verbesserte Erkennung von unerreichbarem Code**

   Änderungen an der C++-Standardbibliothek und eine im Vergleich mit früheren Versionen des Compilers verbesserte Möglichkeit zur Inlineausführung von Funktionsaufrufen ermöglichen dem Compiler jetzt unter Umständen den Nachweis, dass bestimmter Code unerreichbar ist. Dieses neue Verhalten kann zu neuen und häufiger ausgegebenen Instanzen von Warnung C4720 führen.

    ```Output
    warning C4720: unreachable code
    ```

   In vielen Fällen wird diese Warnung nur beim Kompilieren mit aktivierten Optimierungen ausgegeben, da bei den Optimierungen mehr Funktionsaufrufe inline erfolgen, redundanter Code eliminiert wird oder auf andere Weise die Möglichkeit geschaffen wird, bestimmten Code als unerreichbar zu erkennen. Wir haben festgestellt, dass neue Instanzen von Warning C4720 häufig in **try/catch-** Blöcken aufgetreten sind, insbesondere in Bezug auf die Verwendung von [Std:: Find](../standard-library/algorithm-functions.md#find).

   Beispiel (vorher)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   Beispiel (nachher)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

### <a name="conformance-improvements-in-update-2"></a><a name="VS_Update2"></a>Verbesserungen der Konformität in Update 2

- **Zusätzliche Warnungen und Fehler können als Ergebnis der Teilunterstützung für den Ausdruck SFINAE ausgegeben werden**

   In früheren Versionen des Compilers werden bestimmte Arten von Ausdrücken in **decltype**-Spezifizierern nicht analysiert, weil der Ausdruck SFINAE nicht unterstützt wird. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler analysiert diese Ausdrücke jetzt und hat aufgrund kontinuierlicher Konformitätsverbesserungen eine Teilunterstützung für den Ausdruck SFINAE. Daher gibt der Compiler jetzt Warnungen und Fehler aus, die er in Ausdrücken findet, die von früheren Versionen des Compilers nicht analysiert werden.

   Wenn aufgrund dieses neuen Verhaltens ein **decltype**-Ausdruck analysiert wird, der einen Typ enthält, der noch nicht deklariert ist, gibt der Compiler den Compilerfehler C2039 aus.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Beispiel 1: Verwendung eines nicht deklarierten Typs (vorher)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   Beispiel 1 (nachher)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   Wenn aufgrund dieses neuen Verhaltens ein **decltype**-Ausdruck analysiert wird, in dem das erforderliche **typename**-Schlüsselwort für die Angabe fehlt, dass ein abhängiger Name ein Typ ist, gibt der Compiler die Compilerwarnung C4346 zusammen mit dem Compilerfehler C2923 aus.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Beispiel 2: der abhängige Name ist kein Typ (vorher)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   Beispiel 2 (nachher)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- `volatile` **– Membervariablen mit diesem Schlüsselwort verhindern implizit definierte Konstruktoren und Zuweisungsoperatoren**

   In früheren Versionen des Compilers ist es für eine Klasse zulässig, die Membervariablen des Typs **volatile** enthält, dass Kopier-/Verschiebe-Standardkonstruktoren und Kopier-/Verschiebe-Standardzuweisungsoperatoren automatisch generiert werden. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Der Compiler betrachtet nun eine Klasse, die über **flüchtige** Element Variablen verfügt, um nicht triviale Konstruktions-und Zuweisungs Operatoren zu haben, wodurch verhindert wird, dass Standard Implementierungen dieser Operatoren automatisch generiert werden. Ist eine solche Klasse ein Member einer Union (oder einer anonymen Union innerhalb einer Klasse), werden Kopier-/Bewegungskonstruktoren und Kopier-/Bewegungszuweisungsoperatoren der Union (oder die Klasse, die die anonyme Union enthält) implizit als gelöscht definiert. Wird versucht, die Union (oder die Klasse, die die anonyme Union enthält) zu erstellen oder zu kopieren, ohne sie explizit zu definieren, tritt ein Fehler auf, und der Compiler gibt daher den Compilerfehler C2280 aus.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   Beispiel (vorher)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   Beispiel (nachher)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **Statische Memberfunktionen unterstützen keine cv-Qualifizierer**

   In früheren Versionen von Visual Studio 2015 ist es zulässig, dass statische Memberfunktionen CV-Qualifizierer haben. Diese Verhalten wird von einer Regression in Visual Studio 2015 und Visual Studio 2015 Update 1 verursacht. Visual Studio 2013 sowie vorherige Versionen des Compilers lehnen Code, der auf diese Weise geschrieben ist, ab. Das Verhalten von Visual Studio 2015 und Visual Studio 2015 Update 1 ist fehlerhaft und entspricht nicht dem C++-Standard.  Visual Studio 2015 Update 2 weist Code, der in dieser Weise geschrieben ist, zurück und gibt stattdessen den Compilerfehler C2511 aus.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   Beispiel (vorher)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   Beispiel (nachher)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Vorwärtsdeklarationen einer Enumeration sind in WinRT-Code nicht zulässig** (betrifft nur `/ZW`)

   In Code, der für Windows-Runtime (WinRT) kompiliert wird, darf es keine Vorwärtsdeklarationen von **enum**-Typen geben. Dies gilt gleichermaßen für die Kompilierung von verwaltetem C++-Code für .NET Framework mit dem Compilerschalter `/clr`. Dieses Verhalten stellt sicher, dass die Größe einer Enumeration immer bekannt ist und richtig in das WinRT-Typsystem übertragen werden kann. Der Compiler lehnt in dieser Weise geschriebenen Code ab und gibt den Compilerfehler C2599 zusammen mit dem Compilerfehler C3197 aus.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   Beispiel (vorher)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   Beispiel (nachher)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **new- oder delete-Funktionen eines überladenen Nicht-Memberoperators dürfen nicht inline deklariert werden** (Level 1 (`/W1`) standardmäßig aktiviert)

   Frühere Versionen des Compilers geben keine Warnung aus, wenn new- oder delete-Funktionen eines Nicht-Memberoperators inline deklariert werden. In dieser Weise geschriebener Code ist nicht wohlgeformt (keine Diagnose erforderlich) und kann zu Arbeitsspeicherproblemen führen, die sich aus nicht zusammengehörigen new- und delete-Operatoren ergeben (insbesondere bei Verwendung von Zuordnungsaufhebung mit Größenangabe), die sich nur schwer diagnostizieren lassen. Der Compiler gibt jetzt die Warnung C4595 aus, um Code erkennen zu können, der in dieser Weise geschrieben ist.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   Beispiel (vorher)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   Beispiel (nachher)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   Ein Korrigieren von Code, der in dieser Weise geschrieben ist, kann erfordern, dass die Operatordefinitionen aus einer Headerdatei in eine entsprechende Quelldatei verschoben werden.

### <a name="conformance-improvements-in-update-3"></a><a name="VS_Update3"></a> Verbesserungen bei der Übereinstimmung mit Standards in Update 3

- **std::is_convertable erkennt jetzt Selbstzuweisung** (Standardbibliothek)

   Frühere Versionen des Typmerkmals `std::is_convertable` erkannten die Selbstzuweisung eines Klassentyps nicht ordnungsgemäß, wenn der Kopierkonstruktor gelöscht wurde oder privat war. Jetzt ist `std::is_convertable<>::value` bei Anwendung auf einen Klassentyp mit einem gelöschten oder privaten Kopierkonstruktor richtig auf **FALSE** festgelegt.

   Dieser Änderung ist keine Compilerdiagnose zugeordnet.

   Beispiel

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   In früheren Versionen des Compilers wurden die statischen Assertionen unten in diesem Beispiel übergeben, da `std::is_convertable<>::value` fälschlicherweise auf **TRUE** festgelegt war. Jetzt ist `std::is_convertable<>::value` richtig auf **FALSE** festgelegt, wodurch ein Fehler in den statischen Assertionen verursacht wird.

- **Standardmäßig verwendete und gelöschte triviale Kopier- und Verschiebekonstruktoren beachten Zugriffsspezifizierer**

   In früheren Versionen des Compilers wurden die Zugriffsspezifizierer von als Standard festgelegten und gelöschten trivialen Kopier- und Verschiebekonstruktoren nicht geprüft, ehe ihr Aufrufen erlaubt wurde. Dieses alte Verhalten war falsch und entsprach nicht dem C++-Standard. Durch dieses alte Verhalten entstand in einigen Fällen die Gefahr der stummen Erzeugung von ungültigem Code, was zu unvorhersehbarem Laufzeitverhalten führt. Der Compiler prüft jetzt den Zugriffsspezifizierer von als Standard festgelegten und gelöschten trivialen Kopier- und Verschiebekonstruktoren, um zu bestimmen, ob diese aufgerufen werden können. Falls nicht, gibt der Compiler die Warnung C2248 aus.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   Beispiel (vorher)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   Beispiel (nachher)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **Attributierter ATL-Code veraltet** (Level 1 (`/W1`) standardmäßig EIN)

   Frühere Versionen des Compilers haben attributierten ATL-Code unterstützt. In der nächsten Phase der Aufhebung der Unterstützung von attributiertem ATL-Code, die [in Visual Studio 2008 begann](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008), gilt attributierter ATL-Code nun als veraltet. Der Compiler gibt jetzt die Warnung C4467 aus, um diese Art von veraltetem Code erkennen zu können.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Wenn Sie attributierten ATL-Code bis zur Aufhebung der Unterstützung durch den Compiler weiter nutzen möchten, können Sie diese Warnung deaktivieren, indem Sie das Befehlszeilenargument `/Wv:18` oder `/wd:4467` an den Compiler übergeben oder `#pragma warning(disable:4467)` zu Ihrem Quellcode hinzufügen.

   Beispiel 1 (vorher)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Beispiel 1 (nachher)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Mitunter müssen oder möchten Sie ggf. eine IDL-Datei erstellen, um die Nutzung veralteter ATL-Attribute zu vermeiden (siehe den folgenden Beispielcode).

   Beispiel 2 (vorher)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   Erstellen Sie zunächst die *idl-Datei. Die generierte Datei vc140.idl kann zum Abrufen einer \*.idl-Datei verwendet werden, die die Schnittstellen und Anmerkungen enthält.

   Fügen Sie als Nächstes Ihrem Build einen MIDL-Schritt hinzu, um sicherzustellen, dass die C++-Schnittstellendefinitionen generiert werden.

   Beispiel 2: IDL (nachher)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   Verwenden Sie dann ATL direkt in der Implementierungsdatei (siehe den folgenden Beispielcode).

   Beispiel 2: Implementierung (nachher)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **Vorkompilierte Headerdateien (PCH) und nicht übereinstimmende #include-Anweisungen** (wirkt sich nur auf `/Wall` `/WX` aus)

   Frühere Version des Compilers haben bei Verwendung vorkompilierter Headerdateien (PCH) nicht übereinstimmende `#include`-Direktiven in Quelldateien zwischen `-Yc`- und `-Yu`-Kompilierungen akzeptiert. Auf diese Weise geschriebener Code wird vom Compiler nicht mehr akzeptiert.   Der Compiler gibt nun die Compilerwarnung CC4598 aus, um bei Verwenden von PCH-Dateien nicht übereinstimmende `#include`-Direktiven zu bestimmen.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Beispiel (vorher):

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Beispiel (nachher)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Vorkompilierte Headerdateien (PCH) und nicht übereinstimmende include-Anweisungen** (wirkt sich nur auf `/Wall` `/WX` aus)

   Frühere Version des Compilers haben bei Verwendung vorkompilierter Headerdateien (PCH) nicht übereinstimmende Befehlszeilenargumente des Typs „include directory“ (`-I`) für den Compiler zwischen `-Yc`- und `-Yu`-Kompilierungen akzeptiert. Auf diese Weise geschriebener Code wird vom Compiler nicht mehr akzeptiert. Der Compiler gibt nun die Compilerwarnung CC4599 aus, um bei Verwenden von PCH-Dateien nicht übereinstimmende Befehlszeilenargumente des Typs „include-Verzeichnis“ (`-I`) zu bestimmen.

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   Beispiel (vorher)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   Beispiel (nachher)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013: Änderungen bei der Konformität mit Standards

### <a name="compiler"></a>Compiler

- Das Schlüsselwort **Final** generiert nun einen nicht aufgelösten symbolfehler, wenn es zuvor kompiliert worden wäre:

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   In früheren Versionen wurde kein Fehler ausgegeben, weil der-Befehl ein **virtueller** -Befehl war. Dennoch stürzt das Programm zur Laufzeit ab. Jetzt wird ein Linkerfehler ausgegeben, da die Klasse endgültig ist. In diesem Beispiel kann das Objekt, das die Definition von `S2::f` enthält, verknüpft werden, um den Fehler zu beheben.

- Wenn Sie Friend-Funktionen in Namespaces verwenden, müssen Sie die Friend-Funktion erneut deklarieren, bevor Sie auf sie verweisen. Andernfalls wird ein Fehler ausgegeben, da der Compiler jetzt dem C++-Standard der internationalen Organisation für Normung entspricht. Beispielsweise wird das folgende Beispiel nicht mehr kompiliert:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   Um diesen Code zu korrigieren, deklarieren Sie die **Friend** -Funktion:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- Der C++-Standard lässt keine explizite Spezialisierung in einer Klasse zu. Obwohl der Microsoft C++-Compiler dies in manchen Fällen zulässt, wird im folgenden Beispiel jedoch ein Fehler generiert, da der Compiler die zweite Funktion nicht als Spezialisierung der ersten betrachtet.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   Um diesen Code zu korrigieren, ändern Sie die zweite Funktion:

    ```cpp
    template <> void f(char& val);
    ```

- Im folgenden Beispiel können die beiden Funktionen mit dem Compiler nicht mehr unterschieden werden, und es wird jetzt ein Fehler ausgegeben:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   Um diesen Code zu korrigieren, müssen Sie den Aufruf verdeutlichen:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- Bevor der Compiler mit ISO C++11 kompatibel gemacht wurde, wurde der folgende Code kompiliert und führte dazu, dass `x` in den Typ **int** aufgelöst wurde:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Dieser Code wird nun `x` in einen Typ von aufgelöst `std::initializer_list<int>` und verursacht einen Fehler in der nächsten Zeile, die versucht, dem `x` Typ **int**zuzuweisen. (Standardmäßig ist keine Konvertierung vorhanden.) Um diesen Code zu korrigieren, verwenden Sie **int** , um **Auto**zu ersetzen:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Die Aggregatinitialisierung ist nicht mehr zulässig, wenn der Typ des rechten Werts nicht dem Typ des linken Werts entspricht, der initialisiert wird, und es wird ein Fehler ausgegeben, da der ISO C++11-Standard erfordert, dass die einheitliche Initialisierung ohne einschränkende Konvertierungen funktioniert. Bisher wurde die [Compilerwarnung C4242 (Level 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) anstelle eines Fehlers ausgegeben, wenn eine einschränkende Konvertierung verfügbar war.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Um diesen Code zu korrigieren, fügen Sie eine explizite einschränkende Konvertierung hinzu:

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- Die folgende Initialisierung ist nicht mehr zulässig:

    ```cpp
    void *p = {{0}};
    ```

   Um diesen Code zu korrigieren, verwenden Sie eines dieser Formulare:

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- Namenssuche wurde geändert. Der folgende Code wird im C++-Compiler in Visual Studio 2012 und Visual Studio 2013 unterschiedlich aufgelöst:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   In Visual Studio 2012 wurde `E1` im Ausdruck `E1::b` im globalen Gültigkeitsbereich in `::E1` aufgelöst. In Visual Studio 2013 wird `E1` im Ausdruck `E1::b` in die Definition `typedef E2` in `main()` aufgelöst und weist den Typ `::E2` auf.

- Das Objektlayout wurde geändert. Auf x64-Computern kann sich das Objektlayout einer Klasse gegenüber vorherigen Versionen möglicherweise ändern. Wenn Sie über eine **virtuelle** Funktion verfügt, aber keine Basisklasse hat, die über eine **virtuelle** Funktion verfügt, fügt das Objektmodell des Compilers nach dem Layout des Datenelements einen Zeiger in eine **virtuelle** Funktions Tabelle ein. Dies bedeutet, dass das Layout möglicherweise nicht in allen Fällen optimal ist. In vorherigen Releases wurde mithilfe einer Optimierung für x64 versucht, das Layout zu verbessern. Da dies jedoch in komplexen Codesituationen nicht richtig funktionierte, wurde diese Optimierung in Visual Studio 2013 entfernt. Betrachten Sie z. B. diesen Code:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- In Visual Studio 2013 ist das Ergebnis von `sizeof(S2)` für x64 gleich 48, doch in früheren Releases ergibt dies 32. Damit die Auswertung im C++-Compiler von Visual Studio 2013 für x64 den Wert „32“ zurückgibt, müssen Sie eine Dummy-Basisklasse mit einer **virtuellen** Funktion hinzufügen:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Wenn Sie Positionen im Code finden möchten, die von einer früheren Version optimiert wurden, verwenden Sie einen Compiler aus diesem Release mit der `/W3` -Compileroption, und aktivieren Sie Warning C4370. Beispiel:

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Vor Visual Studio 2013 gab dieser Code diese Meldung aus: Warnung C4370: 'S2' : Durch bessere Verpackung wurde das Klassenlayout geändert, das vorher eine andere Compilerversion hatte.

   Der x86-Compiler weist in allen Versionen des Compilers dasselbe Problem aufgrund eines nicht optimalen Layouts auf. Wenn dieser Code beispielsweise für x86 kompiliert wird:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Das Ergebnis von `sizeof(S)` lautet 24. Dies kann jedoch auf 16 reduziert werden, wenn Sie die oben erwähnte Problemumgehung für x64 verwenden:

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>Standardbibliothek

Der C++-Compiler in Visual Studio 2013 erkennt Konflikte im _ITERATOR_DEBUG_LEVEL, das in Visual Studio 2010 implementiert wurde, sowie RuntimeLibrary-Konflikte. Diese Konflikte treten auf, wenn die Compileroptionen `/MT` (statisches Release), `/MTd` (statisches Debuggen), `/MD` (dynamisches Release) und `/MDd` (dynamisches Debuggen) kombiniert werden.

- Wenn der Code die simulierten Aliasvorlagen der vorherigen Version bestätigt, müssen Sie ihn ändern. Beispielsweise müssen Sie statt `allocator_traits<A>::rebind_alloc<U>::other` jetzt `allocator_traits<A>::rebind_alloc<U>` verwenden. Obwohl `ratio_add<R1, R2>::type` nicht mehr notwendig ist und nun empfohlen wird, `ratio_add<R1, R2>` zu verwenden, wird der erste dennoch kompiliert, da für `ratio<N, D>` ein "Typ " typedef für ein reduziertes Verhältnis erforderlich ist. Dies ist derselbe Typ, wenn er bereits reduziert ist.

- Sie müssen `#include <algorithm>` verwenden, wenn Sie `std::min()` oder `std::max()` aufrufen.

- Wenn Ihr vorhandener Code die simulierten Bereichs bezogenen Enumerationen der vorherigen Version verwendet – herkömmliche nicht Bereichs bezogene Enumerationen, die in Namespaces integriert sind – müssen Sie ihn ändern. Wenn Sie z. B. auf den Typ `std::future_status::future_status` verwiesen haben müssen Sie jetzt `std::future_status` verwenden. Die meisten Codes bleiben jedoch unberührt, `std::future_status::ready` wird beispielsweise weiterhin kompiliert.

- `explicit operator bool()` ist strenger als der Operator „unspecified-bool-type()“. `explicit operator bool()` ermöglicht explizite Konvertierungen in „bool“ – bei `shared_ptr<X> sp` sind z.B. `static_cast<bool>(sp)` und `bool b(sp)` und „kontextbedingte Konvertierungen“ gültig, die auf „bool“ getestet werden können – z.B. `if (sp)`, `!sp` oder `sp &&`. Allerdings verbietet `explicit operator bool()` implizite Konvertierungen in „bool“, sodass Sie `bool b = sp;` nicht verwenden können, und bei einem bestimmten Bool-Rückgabetyp können Sie `return sp` nicht verwenden.

- Da echte variadic-Vorlagen nun implementiert wurden, haben _VARIADIC_MAX und verknüpfte Makros keine Auswirkungen. Wenn Sie noch _VARIADIC_MAX definieren, wird es ignoriert. Wenn Sie die Makromaschinerie bestätigt haben, die dazu dienen sollten, simulierte variadic Vorlagen auf andere Weise zu unterstützen, müssen Sie den Code ändern.

- Zusätzlich zu gewöhnlichen Schlüsselwörtern verbieten Header der C++-Standardbibliothek jetzt die Makroersetzung der kontextbezogenen Schlüsselwörter **override** und **final**.

- `reference_wrapper`, `ref()` und `cref()` verbieten jetzt, temporäre Objekte zu binden.

- \<random>erzwingt jetzt streng die Vorbedingungen für die Kompilierzeit.

- Verschiedene Typmerkmale der C++-Standardbibliothek haben die Vorbedingung „T muss ein vollständiger Typ sein“. Obwohl der Compiler diese jetzt strenger erzwingt, wird sie möglicherweise nicht in allen Situationen erzwungen. (Da Verletzungen von Vorbedingungen für die C++-Standardbibliothek kein undefiniertes Verhalten auslösen, garantiert der Standard keine Erzwingung.)

- Die C++-Standardbibliothek unterstützt nicht `/clr:oldSyntax`.

- Die c++ 11-Spezifikation für common_type<> hatte unerwartete und unerwünschte Konsequenzen. insbesondere wird common_type \<int, int> :: Type Return int&&. Daher implementiert der Compiler die vorgeschlagene Auflösung für das Bibliotheks-Arbeitsgruppen Problem 2141, das common_type \<int, int=""> :: Type Return int zurückgibt.

   Als Nebeneffekt dieser Änderung funktioniert der Identitäts Fall nicht mehr (common_type \<T> nicht immer zu Typ t). Dieses Verhalten entspricht der vorgeschlagenen Lösung, beeinträchtigt jedoch den Code, der auf dem vorherigen Verhalten beruhte.

   Wenn ein Identitätstypmerkmal erforderlich ist, verwenden Sie nicht `std::identity` , das kein Standard ist und in \<type_traits> definiert ist, da es nicht bei \<void>funktioniert. Implementieren Sie stattdessen Ihr eigenes Identitätstypmerkmal, um Ihre Anforderungen zu erfüllen. Ein Beispiel:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC und ATL

- **Nur Visual Studio 2013**: die MFC MBCS-Bibliothek ist nicht in Visual Studio enthalten, da Unicode so beliebt ist und die Verwendung von MBCS erheblich abgelehnt wurde. Durch diese Änderung orientiert sich MFC näher am Windows SDK, da viele der neuen Steuerelemente und der Meldungen ausschließlich in Unicode vorliegen. Wenn Sie die MFC-Bibliothek für MBCS jedoch weiterhin verwenden müssen, können Sie Sie im Microsoft Download Center unter [Multibyte-MFC-Bibliothek für Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770)herunterladen. Diese Bibliothek ist weiterhin im Visual C++ Redistributable Package enthalten.  (Hinweis: Die MBCS-DLL ist in den C++-Setupkomponenten in Visual Studio 2015 und höher enthalten).

- Zugriff auf das MFC-Menüband wurde geändert.  Anstelle einer Architektur mit einer Ebene gibt es jetzt eine hierarchische Architektur. Sie können das alte Verhalten weiterhin verwenden, indem Sie `CRibbonBar::EnableSingleLevelAccessibilityMode()` aufrufen.

- Die Methode `CDatabase::GetConnect` wurde entfernt. Zur Verbesserung der Sicherheit wird die Verbindungszeichenfolge nun verschlüsselt gespeichert und nur bei Bedarf entschlüsselt. Sie kann nicht als Nur-Text zurückgegeben werden.  Die Zeichenfolge kann mit der Methode `CDatabase::Dump` abgerufen werden.

- Die Signatur von `CWnd::OnPowerBroadcast` wurde geändert. Die Signatur dieses Meldungshandlers wird geändert, um ein LPARAM als zweiten Parameter zu akzeptieren.

- Signaturen werden zum anzupassen der Meldungshandler geändert. Die Parameterlisten der folgenden Funktionen wurden geändert, um neu hinzugefügte ON_WM_*-Meldungshandler zu verwenden:

  - `CWnd::OnDisplayChange` wurde in (UINT, int, int) anstatt (WPARAM, LPARAM) geändert, sodass das neue ON_WM_DISPLAYCHANGE-Makro in der Meldungszuordnung verwendet werden kann.

  - `CFrameWnd::OnDDEInitiate` wurde in (CWnd*, UINT, UNIT) anstatt (WPARAM, LPARAM) geändert, sodass das neue ON_WM_DDE_INITIATE-Makro in der Meldungszuordnung verwendet werden kann.

  - `CFrameWnd::OnDDEExecute` wurde in (CWnd*, HANDLE) anstatt (WPARAM, LPARAM) geändert, sodass das neue ON_WM_DDE_EXECUTE-Makro in der Meldungszuordnung verwendet werden kann.

  - `CFrameWnd::OnDDETerminate` wurde in den Parameter (CWnd*) anstatt (WPARAM, LPARAM) geändert, sodass das neue ON_WM_DDE_TERMINATE-Makro in der Meldungszuordnung verwendet werden kann.

  - `CMFCMaskedEdit::OnCut` wurde in keine Parameter anstatt (WPARAM, LPARAM) geändert, damit das neue ON_WM_CUT-Makro in der Meldungszuordnung verwendet werden kann.

  - `CMFCMaskedEdit::OnClear` wurde in keine Parameter anstatt (WPARAM, LPARAM) geändert, damit das neue ON_WM_CLEAR-Makro in der Meldungszuordnung verwendet werden kann.

  - `CMFCMaskedEdit::OnPaste` wurde in keine Parameter anstatt (WPARAM, LPARAM) geändert, damit das neue ON_WM_PASTE-Makro in der Meldungszuordnung verwendet werden kann.

- `#ifdef`-Anweisungen wurden aus MFC-Headerdateien entfernt. Zahlreiche `#ifdef`-Anweisungen in den MFC-Headerdateien, die sich auf ältere, nicht unterstützte Versionen von Windows beziehen (WINVER &lt; 0x0501), wurden entfernt.

- ATL DLL (atl120.dll) wurde entfernt. ATL wird jetzt als Header und als statische Bibliothek (atls.lib) bereitgestellt.

- Atlsd.lib, atlsn.lib und atlsnd.lib wurden entfernt. Atls.lib weist keine(n) für Debuggen/Release spezifischen Zeichensatzabhängigkeiten oder Code mehr auf. Da die Funktionsweise für Unicode/ANSI und Debuggen/Release identisch ist, ist nur eine Version der Bibliothek erforderlich.

- Das ATL-/MFC-Ablaufverfolgungstool wird zusammen mit ATL-DLL entfernt, und der Ablaufverfolgungsmechanismus wird vereinfacht. Der `CTraceCategory`-Konstruktor akzeptiert jetzt einen Parameter (den Kategorienamen), und mit den TRACE-Makros werden die CRT-Debugberichtsfunktionen aufgerufen.

## <a name="visual-studio-2012-breaking-changes"></a>Breaking Changes in Visual Studio 2012

### <a name="compiler"></a>Compiler

- Die Compileroption `/Yl` wurde geändert. Standardmäßig verwendet der Compiler diese Option, die unter bestimmten Umständen zu Fehlern des Typs LNK2011 führen kann. Weitere Informationen finden Sie unter [/Yl (PCH-Verweis für Debugbibliothek einfügen)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- In Code, der mit `/clr` kompiliert wird, definiert das Klassenschlüsselwort **enum** eine C++11-Enumeration und keine CLR-Enumeration (Common Language Runtime). Um eine CLR-Enumeration zu definieren, müssen Sie beim Zugriff darauf explizit sein.

- Verwenden Sie das Schlüsselwort „template“, um einen abhängigen Namen (Kompatibilität mit dem Standard der Sprache C++) explizit zu unterscheiden. Im folgenden Beispiel ist das hervorgehobene Schlüsselwort „template“ erforderlich, um die Mehrdeutigkeit zu beseitigen. Weitere Informationen finden Sie unter [Namensauflösung für abhängige Typen](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Der Konstantenausdruck des Typs „float“ ist nicht mehr als ein „template“-Argument zulässig, wie im folgenden Beispiel gezeigt.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Code, der mit der Befehlszeilenoption `/GS` kompiliert wird und eine Um-eins-daneben-Schwachstelle aufweist, kann zur Laufzeit zur Beendigung des Prozesses führen (siehe das folgende Pseudocodebeispiel).

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Die standardmäßige Architektur für x86-Builds wurde in SSE2 geändert. Daher kann der Compiler SSE-Anweisungen ausgeben und XMM-Register für Gleitkommaberechnungen verwenden. Wenn Sie zum früheren Verhalten zurückkehren möchten, verwenden Sie das Compilerflag `/arch:IA32`, um die Architektur als IA32 anzugeben.

- Der Compiler gibt möglicherweise die [Compilerwarnungen (Level 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) und C4701 aus, was zuvor nicht der Fall war. Der Compiler überprüft strenger die Nutzung nicht initialisierter lokaler Variablen des Typs „Zeiger“.

- Wenn das neue Linkerflag `/HIGHENTROPYVA` angegeben ist, verursacht Windows 8 Speicherzuordnungen, um eine 64-Bit-Adresse zurückzugeben. (Vor Windows 8 haben solche Zuordnungen häufiger Adressen zurückgegeben, die kleiner als 2 GB waren.) Diese Änderung kann Fehler beim Abschneiden von Zeigern in vorhandenem Code verfügbar machen. Dieser Schalter ist standardmäßig aktiviert. Geben Sie `/HIGHENTROPYVA:NO` an, um dieses Verhalten zu deaktivieren.

- Der verwaltete Compiler (Visual Basic/C#) unterstützt auch `/HIGHENTROPYVA` für verwaltete Builds.  In diesem Fall ist `/HIGHENTROPYVAswitch` jedoch standardmäßig deaktiviert.

### <a name="ide"></a>IDE

- Wenngleich nicht empfohlen wird, Windows Forms-Anwendungen in C++/CLI zu erstellen, wird die Wartung vorhandener C++/CLI UI-Anwendungen unterstützt. Wenn Sie eine Windows Forms-Anwendung oder andere .NET UI-Anwendung erstellen müssen, verwenden Sie C# oder Visual Basic. Verwenden Sie C++/CLI nur zu Interoperabilitätszwecken.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Parallel Patterns- und Concurrency Runtime-Bibliothek

Die `SchedulerType`-Enumeration von `UmsThreadDefault` ist veraltet. Bei Angabe von `UmsThreadDefault` wird eine veraltete Warnung generiert, und intern erfolgt eine Zuordnung zurück zum `ThreadScheduler`.

### <a name="standard-library"></a>Standardbibliothek

- Als Folge eines Breaking Change zwischen den Standards C++98/03 und C++11 erfolgt bei Verwendung expliziter Vorlagenargumente zum Aufrufen von `make_pair()`, z. B. `make_pair<int, int>(x, y)`, in Visual C++ in Visual Studio 2012 in der Regel keine Kompilierung. Die Lösung besteht darin, immer `make_pair()` ohne explizite Vorlagen Argumente aufzurufen – wie in `make_pair(x, y)` . Bei Angeben expliziter Vorlagenargumente wird der Zweck der Funktion verfehlt. Wenn eine präzise Steuerung des resultierenden Typs erforderlich ist, verwenden Sie `pair` anstelle von `make_pair`, wie in `pair<short, short>(int1, int2)`.

- Eine weitere Breaking Change zwischen den Standards c++ 98/03 und c++ 11: Wenn eine implizit in B konvertiert und b implizit in c konvertierbar ist, aber nicht implizit in c konvertiert werden kann, c++ 98/03 und Visual Studio 2010 `pair<A, X>` (implizit oder explizit) in konvertiert werden dürfen `pair<C, X>` . (Der andere Typ, "X", ist hier nicht von Interesse und nicht spezifisch für den ersten Typ im Paar.) Der C++-Compiler in Visual Studio 2012 erkennt, dass ein nicht implizit in C konvertierbar ist, und entfernt die paar Konvertierung aus der Überladungs Auflösung. Diese Änderung wirkt sich auf viele Szenarios positiv aus. Durch das Überladen von `func(const pair<int, int>&)` und `func(const pair<string, string>&)` und das Aufrufen von `func()` mit `pair<const char *, const char *>` erfolgt die Kompilierung beispielsweise mit dieser Änderung. Diese Änderung unterbricht jedoch Code, der auf aggressiven Paarkonvertierungen beruhte. Solcher Code kann normalerweise korrigiert werden, wenn ein Teil der Konvertierung explizit erfolgt, z.B. indem `make_pair(static_cast<B>(a), x)` an eine Funktion übergeben wird, die `pair<C, X>` erwartet.

- Visual Studio 2010 simulierte variadic-Vorlagen, wie z. B. `make_shared<T>(arg1, arg2, argN)`, bis zu einem Grenzwert von 10 Argumenten, um Überladungen und Spezialisierungen mithilfe von Präprozessormechanismen zu entfernen. In Visual Studio 2012 wurde dieser Grenzwert auf fünf Argumente verringert, um Kompilierzeiten und die Nutzung des Compilerspeichers für die Mehrheit der Benutzer zu verbessern. Allerdings können Sie den vorherigen Grenzwert festlegen, indem Sie _VARIADIC_MAX projektweit explizit auf 10 festlegen.

- C++11 17.6.4.3.1 [macro.names]/2 verbietet die Makroersetzung von Schlüsselwörtern, wenn Header der C++-Standardbibliothek enthalten sind. Die Header geben jetzt Compilerfehler aus, wenn sie Schlüsselwörter erkennen, die durch Makros ersetzt wurden. (Durch definieren _ALLOW_KEYWORD_MACROS kann dieser Code kompiliert werden, aber wir raten dringend davon ab.) Als Ausnahme ist die Makro Form von `new` standardmäßig zulässig, da die Header sich mithilfe von umfassend verteidigen `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")` . Bei Festlegung von _ENFORCE_BAN_OF_MACRO_NEW erfolgt genau das, was der Name schon sagt.

- Um verschiedene Optimierungen und Debugüberprüfungen zu implementieren, unterbricht die Visual Studio-Implementierung der C++-Standardbibliothek absichtlich die binäre Kompatibilität zwischen Versionen von Visual Studio (2005, 2008, 2010, 2012). Wenn die C++-Standardbibliothek verwendet wird, dürfen Objektdateien und statische Bibliotheken, die unter Verwendung verschiedener Versionen kompiliert werden, nicht in einer Binärdatei (EXE oder DLL) gemischt werden, und C++-Standardbibliotheksobjekte dürfen nicht zwischen Binärdateien übergeben werden, die mit verschiedenen Versionen kompiliert werden. Das Mischen von Objektdateien und statischen Bibliotheken (unter Verwendung der C++-Standardbibliothek), die mit Visual Studio 2010 kompiliert wurden, mit denjenigen, die mit dem C++-Compiler in Visual Studio 2012 kompiliert wurden, löst Linkerfehler aufgrund des Konflikts von _MSC_VER aus. _MSC_VER ist das Makro, das die Hauptversion des Compilers (1700 für _MSC_VER Visual C++ in Visual Studio 2012) enthält. Diese Überprüfung kann weder eine gemischte DLL-Verwendung noch eine gemischte Verwendung erkennen, die Visual Studio 2008 oder früher betrifft.

- Zusätzlich zum Erkennen von Konflikten bei _ITERATOR_DEBUG_LEVEL, das in Visual Studio 2010 implementiert wurde, erkennt der C++-Compiler in Visual Studio 2012 Runtimebibliothekskonflikte. Diese Konflikte treten auf, wenn die Compileroptionen `/MT` (statisches Release), `/MTd` (statisches Debuggen), `/MD` (dynamisches Release) und `/MDd` (dynamisches Debuggen) kombiniert werden.

- `operator<()`, `operator>()`, `operator<=()` und `operator>=()` waren zuvor für die Containerreihen `std::unordered_map` und `stdext::hash_map` verfügbar, auch wenn die zugehörigen Implementierungen nicht nützlich waren. Diese nicht standardmäßigen Operatoren wurden in Visual C++ in Visual Studio 2012 entfernt. Darüber hinaus wurde die Implementierung von `operator==()` und `operator!=()` für die `std::unordered_map`-Reihe erweitert, sodass die Reihe `stdext::hash_map` abgedeckt ist. (Es wird empfohlen, die Verwendung der `stdext::hash_map`-Reihe in neuem Code zu vermeiden.)

- C++11 22.4.1.4 [locale.codecvt] gibt an, dass `codecvt::length()` und `codecvt::do_length()` änderbare `stateT&`-Parameter verwenden sollten, Visual Studio 2010 hat jedoch `const stateT&` verwendet. Der C++-Compiler in Visual Studio 2012 verwendet `stateT&` gemäß den Vorgaben des Standards. Dieser Unterschied ist wichtig für alle, die versuchen, die virtuelle Funktion `do_length()` zu überschreiben.

### <a name="crt"></a>CRT

- Der C Runtime-Heap (CRT), der für „new“ und „malloc()“ verwendet wird, ist nicht mehr privat. Die CRT verwendet jetzt den Prozessheap. Dies bedeutet, dass der Heap nicht zerstört wird, wenn eine DLL entladen wird, sodass DLLs, die statisch mit der CRT verknüpfen, sicherstellen müssen, dass der durch den DLL-Code zugewiesene Arbeitsspeicher bereinigt wird, bevor er entladen wird.

- Die Funktion `iscsymf()` bestätigt mit negativen Werten.

- Die `threadlocaleinfostruct`-Struktur wurde geändert, damit die Änderungen an Gebietsschemafunktionen berücksichtigt werden.

- CRT-Funktionen, die entsprechende systeminterne Funktionen wie `memxxx()` und `strxxx()`aufweisen, wurden aus intrin.h entfernt. Wenn Sie intrin.h nur für diese Funktionen hinzugefügt haben, müssen Sie jetzt die entsprechenden CRT-Header hinzufügen.

### <a name="mfc-and-atl"></a>MFC und ATL

- Die Fusion-Unterstützung (afxcomctl32. h) wurde entfernt. Daher wurden alle in definierten Methoden \<afxcomctl32.h> entfernt. Header Dateien \<afxcomctl32.h> und \<afxcomctl32.inl> wurden gelöscht.

- Der Name wurde von `CDockablePane::RemoveFromDefaultPaneDividier` in `CDockablePane::RemoveFromDefaultPaneDivider` geändert.

- Die Signatur von `CFileDialog::SetDefExt` wurde für die Verwendung von LPCTSTR geändert. Deshalb sind Unicode-Builds betroffen.

- Veraltete ATL-Ablaufverfolgungskategorien wurden entfernt.

- Die Signatur von `CBasePane::MoveWindow` wurde so geändert, dass `const CRect` verwendet wird.

- Die Signatur von `CMFCEditBrowseCtrl::EnableBrowseButton` wurde geändert.

- `m_fntTabs` und `m_fntTabsBold` aus `CMFCBaseTabCtrl` entfernt.

- Es wurde ein Parameter zu den `CMFCRibbonStatusBarPane`-Konstruktoren hinzugefügt. (Dies ist ein Standardparameter, weshalb kein Eingriff in den Quellcode erforderlich ist.)

- Es wurde ein Parameter zu dem `CMFCRibbonCommandsListBox`-Konstruktor hinzugefügt. (Dies ist ein Standardparameter, weshalb kein Eingriff in den Quellcode erforderlich ist.)

- Die `AFXTrackMouse`-API (und der zugehörige TIMERPROC) wurde entfernt. Verwenden Sie stattdessen die Win32-API `TrackMouseEvent`.

- Es wurde ein Parameter zu dem `CFolderPickerDialog`-Konstruktor hinzugefügt. (Dies ist ein Standardparameter, weshalb kein Eingriff in den Quellcode erforderlich ist.)

- Die Größe der `CFileStatus`-Struktur wurde geändert: Der `m_attribute`-Member wurde von BYTE in DWORD geändert (entsprechend dem Wert, der von `GetFileAttributes` zurückgegeben wird).

- `CRichEditCtrl` und `CRichEditView` nutzen in Unicode-Builds MSFTEDIT_CLASS (RichEdit 4.1-Steuerelement) anstelle von RICHEDIT_CLASS (RichEdit 3.0-Steuerelement).

- `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` wurde entfernt, da unter Windows Vista, Windows 7 und Windows 8 immer „TRUE“ festgelegt ist.

- `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` wurde entfernt, da unter Windows Vista, Windows 7 und Windows 8 immer „TRUE“ festgelegt ist.

- `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea` wurde entfernt. Rufen Sie die Windows-API unter Windows Vista, Windows 7 und Windows 8 direkt auf.

- `AFX_GLOBAL_DATA::DwmDefWindowProc` wurde entfernt. Rufen Sie die Windows-API unter Windows Vista, Windows 7 und Windows 8 direkt auf.

- `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` wurde in `IsDwmCompositionEnabled` umbenannt, um einen Namenskonflikt zu vermeiden.

- Die Bezeichner für verschiedene interne MFC-Timer wurden geändert und die Definitionen in afxres.h (AFX_TIMER_ID_*) verschoben.

- Die Signatur der `OnExitSizeMove`-Methode wurde in Übereinstimmung mit dem Makro ON_WM_EXITSIZEMOVE geändert:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Name und Signatur von `OnDWMCompositionChanged` wurden in Übereinstimmung mit dem Makro ON_WM_DWMCOMPOSITIONCHANGED geändert:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Die Signatur der `OnMouseLeave`-Methode wurde in Übereinstimmung mit dem Makro ON_WM_MOUSELEAVE geändert:

  - `CMFCCaptionBar`

  - `CMFCColorBar`

  - `CMFCHeaderCtrl`

  - `CMFCProperySheetListBox`

  - `CMFCRibbonBar`

  - `CMFCRibbonPanelMenuBar`

  - `CMFCRibbonRichEditCtrl`

  - `CMFCSpinButtonCtrl`

  - `CMFCToolBar` ReplaceThisText

  - `CMFCToolBarComboBoxEdit`

  - `CMFCToolBarEditCtrl`

  - `CMFCAutoHideBar`

- Die Signatur von `OnPowerBroadcast` wurde in Übereinstimmung mit dem Makro ON_WM_POWERBROADCAST geändert:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

- Die Signatur von `OnStyleChanged` wurde in Übereinstimmung mit dem Makro ON_WM_STYLECHANGED geändert:

  - `CMFCListCtrl`

  - `CMFCStatusBar`

- Die interne Methode `FontFamalyProcFonts` wurde in `FontFamilyProcFonts` umbenannt.

- Zahlreiche globale statische `CString`-Objekte und die folgenden Klassenmembervariablen wurden entfernt, um Speicherverluste in bestimmten Situationen zu vermeiden (durch #defines ersetzt):

  - `CKeyBoardManager::m_strDelimiter`

  - `CMFCPropertyGridProperty::m_strFormatChar`

  - `CMFCPropertyGridProperty::m_strFormatShort`

  - `CMFCPropertyGridProperty::m_strFormatLong`

  - `CMFCPropertyGridProperty::m_strFormatUShort`

  - `CMFCPropertyGridProperty::m_strFormatULong`

  - `CMFCPropertyGridProperty::m_strFormatFloat`

  - `CMFCPropertyGridProperty::m_strFormatDouble`

  - `CMFCToolBarImages::m_strPngResType`

  - `CMFCPropertyGridProperty::m_strFormat`

- Die Signatur von `CKeyboardManager::ShowAllAccelerators` wurde geändert. Der Parameter zum Trennen von Beschleunigern wurde entfernt.

- `CPropertyPage::GetParentSheet` wurde hinzugefügt. Rufen Sie dies in der Klasse `CPropertyPage` anstelle von `GetParent` auf, um das ordnungsgemäße übergeordnete Blattfenster abzurufen, welches das übergeordnete bzw. über-übergeordnete Fenster für `CPropertyPage` sein kann. Möglicherweise müssen den Code so ändern, dass `GetParentSheet` anstatt `GetParent` aufgerufen wird.

- Unausgeglichenes #pragma warning(push) in ATLBASE.H korrigiert, was die fälschliche Deaktivierung von Warnungen verursacht hat. Diese Warnungen werden nun ordnungsgemäß aktiviert, nachdem ATLBASE.H analysiert wurde.

- Auf D2D bezogene Methoden aus AFX_GLOBAL_DATA in _AFX_D2D_STATE verschoben:

  - `GetDirectD2dFactory`

  - `GetWriteFactory`

  - `GetWICFactory`

  - `InitD2D`

  - `ReleaseD2DRefs`

  - `IsD2DInitialized`

  - `D2D1MakeRotateMatrix`

  - Anstatt `afxGlobalData.IsD2DInitialized` aufzurufen, rufen Sie beispielsweise `AfxGetD2DState->IsD2DInitialized` auf.

- Veraltete ATL*.CPP-Dateien aus dem Ordner \atlmfc\include\ entfernt.

- `afxGlobalData`-Initialisierung in bedarfsgesteuert geändert anstatt zur CRT-Initialisierungszeit verschoben, um `DLLMain`-Anforderungen zu erfüllen.

- Die Methode `RemoveButtonByIndex` wurde zur Klasse `CMFCOutlookBarPane` hinzugefügt.

- `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` wurde in `IsFrequentlyUsedCmd` korrigiert.

- Es wurden mehrere Instanzen von `RestoreOriginalstate` in `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)` korrigiert.

- Es wurden nicht verwendete Methoden aus `CDockablePane` entfernt: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo` und `CanAdjustLayout`.

- Die statischen `CDockablePane`-Membervariablen `m_bCaptionText` und `m_bHideDisabledButtons` wurden entfernt.

- Es wurde eine `DeleteString`-Überschreibungsmethode zu `CMFCFontComboBox` hinzugefügt.

- Es wurden nicht verwendete Methoden aus `CPane` entfernt: `GetMinLength` und `IsLastPaneOnLastRow`.

- `CPane::GetDockSiteRow(CDockingPanesRow *)` wurde in `CPane::SetDockSiteRow` umbenannt.

## <a name="visual-studio-2010-breaking-changes"></a>Breaking Changes in Visual Studio 2010

### <a name="compiler"></a>Compiler

- Das Schlüsselwort " **Auto** " hat eine neue Standardbedeutung. Da die alte Bedeutung nur selten verwendet wird, sind die meisten Anwendungen von dieser Änderung nicht betroffen.

- Das neue **static_assert** -Schlüsselwort wird eingeführt, wodurch ein namens Konflikt verursacht wird, wenn bereits ein Bezeichner mit diesem Namen im Code vorhanden ist.

- Die Unterstützung der neuen Lambda-Notation schließt die Unterstützung für das Codieren einer GUID ohne Anführungszeichen in einem IDL uuid-Attribut aus.

- .NET Framework 4 führt das Konzept von Ausnahmen zu beschädigtem Zustand ein. Diese Ausnahmen hinterlassen einen Prozess in einem nicht korrigierbaren beschädigten Zustand. Standardmäßig können Sie eine Ausnahme zu einem beschädigten Zustand selbst mit der Compileroption /EHa nicht abfangen, die alle anderen Ausnahmen abfängt.                 Um eine Ausnahme zu beschädigtem Zustand explizit abzufangen zu können, verwenden Sie __try-\__except-Anweisungen. Oder wenden Sie das Attribut [HandledProcessCorruptedStateExceptions] an, um eine Funktion zum Abfangen von Ausnahmen zum beschädigten Zustand zu aktivieren.  Diese Änderung betrifft in erster Linie Programmierer, die Ausnahmen zu beschädigtem Zustand möglicherweise abfangen müssen. Die acht Ausnahmen sind STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE.                 Weitere Informationen zu diesen Ausnahmen finden Sie unter [GetExceptionCode](/windows/win32/Debug/getexceptioncode)-Makro.

- Die überarbeitete Compileroption `/GS` schützt umfassender als in früheren Versionen vor Pufferüberläufen. Diese Version kann im Stapel zusätzliche Sicherheitsüberprüfungen hinzufügen, die die Leistung verringern können. Verwenden Sie das neue Schlüsselwort `__declspec(safebuffers)`, um den Compiler anzuweisen, keine Sicherheitsüberprüfungen für eine bestimmte Funktion hinzuzufügen.

- Wenn Sie den Code mit den beiden Compileroptionen `/GL` (Optimierung des gesamten Programms) und `/clr` (Common Language Runtime-Kompilierung) kompilieren, wird die Option `/GL` ignoriert. Diese Änderung wurde vorgenommen, da die Kombination von Compileroptionen nur wenig Vorteile geboten hat. Durch diese Änderung wird die Leistung des Builds verbessert.

- Die Unterstützung von Trigraphen ist in Visual Studio 2010 standardmäßig deaktiviert. Verwenden Sie die Compileroption `/Zc:trigraphs`, um die Unterstützung von Trigraphen zu aktivieren. Ein Trigraph besteht aus zwei aufeinander folgenden Fragezeichen (??) gefolgt von einem eindeutigen dritten Zeichen. Der Compiler ersetzt einen Trigraphen durch ein entsprechendes Interpunktionszeichen. Der Compiler ersetzt beispielsweise den Trigraphen `??=` durch das Zeichen „#“. Verwenden Sie Trigraphen in C-Quelldateien, die einen Zeichensatz aufweisen, der für einige Interpunktionszeichen keine passenden grafischen Darstellungen enthält.

- Der Linker unterstützt nicht mehr die Optimierung für Windows 98. Die Option `/OPT` (Optimierungen) erzeugt einen Fehler zur Kompilierzeit, wenn Sie `/OPT:WIN98` oder `/OPT:NOWIN98` angeben.

- Die standardmäßigen Compileroptionen, die von den Buildsystemeigenschaften RuntimeLibrary und DebugInformationFormat angegeben werden, wurden geändert. Diese Buildeigenschaften werden standardmäßig in Projekten angegeben, die mit den Visual C++-Versionen 7.0 bis 10.0 erstellt wurden. Wenn Sie ein Projekt migrieren, das mit Visual C++ 6.0 erstellt wurde, erwägen Sie, einen Wert für diese Eigenschaften anzugeben.

- In Visual Studio 2010 entspricht die „RuntimeLibrary“-Eigenschaft der „MultiThreaded“-Eigenschaft (`/MD`) und die „DebugInformationFormat“-Eigenschaft der „ProgramDatabase“-Eigenschaft (`/Zi`). In Visual C++ 9.0 ist RuntimeLibrary = MultiThreaded (`/MT`) und DebugInformationFormat = Disabled.

### <a name="clr"></a>CLR

- Die Microsoft C#- und Visual Basic-Compiler können jetzt eine nicht primäre Interopassembly (Nicht-PIA) erzeugen. Eine Nicht-PIA-Assembly kann COM-Typen ohne die Bereitstellung der entsprechenden primären Interopassembly (PIA) verwenden. Bei der Nutzung von Nicht-PIA-Assemblys, die mit Visual C# oder Visual Basic erstellt wurden, müssen Sie die PIA-Assembly an den Compile-Befehl verweisen, bevor Sie auf Nicht-PIA-Assemblys verweisen, die die Bibliothek verwenden.

### <a name="visual-studio-c-projects-and-msbuild"></a>Visual Studio C++-Projekte und MSBuild

- Visual Studio C++-Projekte basieren jetzt auf dem MSBuild-Tool. Infolgedessen verwenden Projektdateien ein neues XML-Format und das Dateisuffix VCXPROJ. Visual Studio 2010 konvertiert Projektdateien aus früheren Versionen von Visual Studio automatisch in das neue Dateiformat. Ein vorhandenes Projekt ist betroffen, wenn es vom vorherigen Buildtool, VCBUILD.exe, oder Projektdateisuffix, VCPROJ, abhängt.

- In früheren Versionen unterstützte Visual C++ die späte Auswertung von Eigenschaftenblättern. Beispiel: Ein übergeordnetes Eigenschaftenblatt konnte ein untergeordnetes Eigenschaftenblatt importieren, und das übergeordnete Element konnte eine Variable verwenden, die im untergeordneten Element definiert ist, um andere Variablen zu definieren. Die späte Auswertung ermöglichte dem übergeordneten Element das Verwenden der untergeordneten Variablen, ehe das Eigenschaftenblatt des untergeordneten Elements importiert wurde. In Visual Studio 2010 kann eine Projektblattvariable nicht vor ihrer Definition verwendet werden, da MSBuild nur die frühe Auswertung unterstützt.

### <a name="ide"></a>IDE

- Das Dialogfeld zum Beenden von Anwendungen beendet eine Anwendung nicht mehr. Wenn in früheren Versionen die Funktion `abort()` oder `terminate()` die Verkaufsversion einer Anwendung geschlossen hat, zeigte die C-Laufzeitbibliothek im Konsolenfenster oder Dialogfeld eine Meldung zur Beendigung der Anwendung an. Ein Teil der Meldung lautet ungefähr so: „Diese Anwendung hat ein nicht ordnungsgemäßes Beenden der Runtime angefordert. Weitere Informationen erhalten Sie von dem für die Anwendung zuständigen Supportteam.“ Die Meldung zum Beenden der Anwendung war redundant, da Windows daraufhin den aktuellen Beendigungs Handler angezeigt hat, der normalerweise das Dialogfeld Windows-Fehlerberichterstattung (Dr. Watson) oder den Visual Studio-Debugger war. Ab Visual Studio 2010 zeigt die C-Laufzeitbibliothek die Meldung nicht mehr an. Darüber hinaus hindert die Laufzeit die Anwendung am Beenden, bevor ein Debugger gestartet wird. Dies ist nur dann eine bedeutende Änderung, wenn Sie vom früheren Verhalten der Meldung zum Beenden der Anwendung abhängig sind.

- Insbesondere in Visual Studio 2010 funktioniert IntelliSense nicht bei C++-/CLI-Code oder Attributen, **Alle Verweise suchen** funktioniert nicht bei lokalen Variablen, und „Codemodell“ ruft keine Typnamen aus importierten Assemblys ab und löst Typen nicht in ihre vollqualifizierten Namen auf.

### <a name="libraries"></a>Bibliotheken

- Die SafeInt-Klasse ist in Visual C++ und nicht mehr als separater Download erhältlich. Dies ist nur ein Breaking Change, wenn Sie eine Klasse entwickelt haben, die ebenfalls den Namen „SafeInt“ trägt.

- Das Bereitstellungsmodell für Bibliotheken verwendet nicht mehr Manifeste, um eine bestimmte Version einer DLL (Dynamic Link Library) zu suchen. Stattdessen enthält der Name jeder DLL ihre Versionsnummer, und Sie können die Bibliothek anhand dieses Namens finden.

- In früheren Versionen von Visual Studio konnten die Laufzeitbibliotheken neu erstellt werden. Das Erstellen eigener Kopien der C-Runtimebibliotheksdateien wird von Visual Studio 2010 nicht mehr unterstützt.

### <a name="standard-library"></a>Standardbibliothek

- Der \<iterator> Header wird nicht mehr automatisch von vielen anderen Header Dateien eingeschlossen. Fügen Sie stattdessen diesen Header explizit hinzu, wenn Sie Unterstützung für die im Header definierten eigenständigen Iteratoren benötigen. Ein vorhandenes Projekt ist betroffen, wenn es vom vorherigen Buildtool, „VCBUILD.exe“, oder Projektdateisuffix, „.vcproj.iterator“, abhängt.

- In der \<algorithm> Kopfzeile werden die Funktionen checked_ * und unchecked_ \* entfernt. Im>- \<iterator> Header wird die- `checked_iterator` Klasse entfernt, und die- `unchecked_array_iterator` Klasse wurde hinzugefügt.

- Der Konstruktor `CComPtr::CComPtr(int)` wurde entfernt. Dieser Konstruktor erlaubte das Erstellen des `CComPtr`-Objekts aus dem NULL-Makro, war aber unnötig und ermöglichte unsinnige Konstruktionen auf Basis ganzer Zahlen ungleich null.

   Ein `CComPtr` kann immer noch aus NULL erstellt werden, was als 0 definiert ist. Dies misslingt jedoch, wenn das Erstellen basierend auf einer anderen ganzen Zahl als dem Literal 0 erfolgt. Verwenden Sie stattdessen " **nullptr** ".

- Die folgenden `ctype`-Memberfunktionen wurden entfernt: `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Wenn eine Anwendung eine dieser Memberfunktionen verwendet, müssen Sie sie durch die entsprechende nicht sichere Version ersetzen: `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>CRT-, MFC- und ATL-Bibliotheken

- Das Erstellen von CRT-, MFC- und ATL-Bibliotheken durch die Benutzer wird nicht mehr unterstützt. Beispielsweise wird keine entsprechende NMAKE-Datei bereitgestellt. Benutzer haben jedoch weiterhin Zugriff auf den Quellcode für diese Bibliotheken. Und ein Dokument, in dem die MSBuild-Optionen beschrieben werden, die Microsoft zum Erstellen dieser Bibliotheken verwendet, wird wahrscheinlich in einem Blog des Visual C++-Teams veröffentlicht.

- MFC-Unterstützung für IA64 wurde entfernt. Unterstützung für CRT und ATL für IA64 wird jedoch weiter geboten.

- Ordnungszahlen werden nicht mehr in MFC-Moduldefinitionsdateien (.def) wiederverwendet. Diese Änderung bedeutet, dass sich Ordnungszahlen zwischen Nebenversionen nicht unterscheiden. Außerdem wird die Binärkompatibilität für Service Packs und Quick Fix Engineering-Versionen verbessert.

- Zur `CDocTemplate`-Klasse wurde eine neue virtuelle Funktion hinzugefügt. Diese neue virtuelle Funktion heißt [CDocTemplate-Klasse](../mfc/reference/cdoctemplate-class.md). Die vorherige Version von `OpenDocumentFile` hatte zwei Parameter. Die neue Version hat drei Parameter. Zur Unterstützung des Neustart-Managers müssen alle von `CDocTemplate` abgeleiteten Klassen die Version mit drei Parametern implementieren. Der neue Parameter lautet `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Makros und Umgebungsvariablen

- Die Umgebungsvariable __MSVCRT_HEAP_SELECT wird nicht mehr unterstützt. Diese Umgebungsvariable wurde ersatzlos entfernt.

### <a name="microsoft-macro-assembler-reference"></a>Referenz zum Microsoft Macro Assembler

- Mehrere Direktiven wurden aus der Referenz zum Microsoft Macro Assembler-Compiler entfernt. Die folgenden Anweisungen wurden entfernt: `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087` und `.NO87`.

## <a name="visual-studio-2008-breaking-changes"></a>Breaking Changes in Visual Studio 2008

### <a name="compiler"></a>Compiler

- Die Plattformen Windows 95, Windows 98, Windows ME und Windows NT werden nicht mehr unterstützt. Diese Betriebssysteme wurden aus der Liste der Zielplattformen entfernt.

- Der Compiler unterstützt mehrere Attribute nicht mehr, die direkt mit dem ATL-Server verknüpft sind. Die folgenden Attribute werden nicht mehr unterstützt:

  - perf_counter

  - perf_object

  - perfmon

  - request_handler

  - soap_handler

  - soap_header

  - soap_method

  - tag_name

### <a name="visual-studio-c-projects"></a>Visual Studio C++-Projekte

- Wenn Sie Projekte aus früheren Versionen von Visual Studio aktualisieren, müssen Sie möglicherweise die Makros WINVER und _WIN32_WINNT so ändern, dass sie größer gleich 0x0500 sind.

- Ab Visual Studio 2008 bietet der Assistent für neue Projekte keine Option zum Erstellen eines SQL Server-Projekts in C++. SQL Server-Projekte, die mit einer früheren Version von Visual Studio erstellt wurde, werden dennoch kompiliert und funktionieren ordnungsgemäß.

- Die Windows-API-Headerdatei „Winable.h“ wurde entfernt. Nehmen Sie stattdessen „Winuser.h“.

- Die Windows-API-Bibliothek „Rpcndr.lib“ wurde entfernt. Stellen Sie stattdessen eine Verknüpfung mit „rpcrt4.lib“ her.

### <a name="crt"></a>CRT

- Unterstützung für Windows 95, Windows 98, Windows Millennium Edition und Windows NT 4.0 wurde entfernt.

- Die folgenden globalen Variablen wurden entfernt:

  - _osplatform

  - _osver

  - _winmajor

  - _winminor

  - _winver

- Die folgenden Funktionen wurden entfernt. Verwenden Sie stattdessen die Windows-API-Funktion `GetVersion` oder `GetVersionEx`:

  - _get_osplatform

  - _get_osver

  - _get_winmajor

  - _get_winminor

  - _get_winver

- Die Syntax für SAL-Anmerkungen wurde geändert. Weitere Informationen finden Sie unter [SAL-Anmerkungen](../c-runtime-library/sal-annotations.md).

- Der IEEE-Filter unterstützt jetzt den SSE-4.1-Anweisungssatz. Weitere Informationen finden Sie unter [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Die C-Laufzeitbibliotheken in Visual Studio sind nicht mehr von der System-DLL „msvcrt.dll“ abhängig.

### <a name="standard-library"></a>Standardbibliothek

- Unterstützung für Windows 95, Windows 98, Windows Millennium Edition und Windows NT 4.0 wurde entfernt.

- Beim Kompilieren im Debugmodus mit angegebenem _HAS_ITERATOR_DEBUGGING (ersetzt durch [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) nach Visual Studio 2010) bestätigt eine Anwendung nun, wenn ein Iterator versucht, sich über die Grenzen eines zugrunde liegenden Containers zu inkrementieren oder zu dekrementieren.

- Die Membervariable „c“ der stack-Klasse ist nun als geschützt deklariert. Diese Membervariable war zuvor als öffentlich deklariert.

- Das Verhalten von `money_get::do_get` wurde geändert. Zuvor wurden bei der Analyse eines Geldbetrags mit mehr Nachkommaziffern als von `frac_digits` oder `do_get` angefordert alle verwendet. Nun beendet `do_get` die Analyse, nachdem die höchste Anzahl der Zeichen von `frac_digits` verwendet wurde.

### <a name="atl"></a>ATL

- ATL kann nicht ohne eine Abhängigkeit von CRT erstellt werden. In früheren Versionen konnten Sie #define ATL_MIN_CRT verwenden, um ein ATL-Projekt minimal abhängig von CRT zu machen. In Visual Studio 2008 sind alle ATL-Projekte minimal abhängig von CRT, und zwar unabhängig davon, ob ATL_MIN_CRT definiert ist.

- Die Codebasis von ATL-Server wurde als freigegebenes Quellcodeprojekt auf CodePlex veröffentlicht und wird nicht als Teil von Visual Studio installiert. Die Datencodierungs- und -decodierungsklassen in atlenc.h und Hilfsfunktionen und -klassen in atlutil.h und atlpath.h wurden beibehalten und sind jetzt Bestandteil der ATL-Bibliothek. Mehrere Dateien, die mit ATL-Server verknüpft sind, gehören nicht mehr zu Visual Studio.

- Einige Funktionen sind nicht mehr in der DLL enthalten. Sie befinden sich weiter in der Importbibliothek. Dies betrifft Code nicht, der die Funktionen statisch verwendet. Dies wirkt sich nur auf Code aus, der diese Funktionen dynamisch verwendet.

- Die Makros PROP_ENTRY und PROP_ENTRY_EX wurden als veraltet eingestuft und aus Sicherheitsgründen durch die Makros PROP_ENTRY_TYPE und PROP_ENTRY_TYPE_EX ersetzt.

### <a name="atlmfc-shared-classes"></a>Freigegebene ATL-/MFC-Klassen

- ATL kann nicht ohne eine Abhängigkeit von CRT erstellt werden. In früheren Versionen konnten Sie `#define ATL_MIN_CRT` verwenden, um ein ATL-Projekt minimal abhängig von CRT zu machen. In Visual Studio 2008 sind alle ATL-Projekte minimal abhängig von CRT, und zwar unabhängig davon, ob ATL_MIN_CRT definiert ist.

- Die Codebasis von ATL-Server wurde als freigegebenes Quellcodeprojekt auf CodePlex veröffentlicht und wird nicht als Teil von Visual Studio installiert. Die Datencodierungs- und -decodierungsklassen in atlenc.h und Hilfsfunktionen und -klassen in atlutil.h und atlpath.h wurden beibehalten und sind jetzt Bestandteil der ATL-Bibliothek. Mehrere Dateien, die mit ATL-Server verknüpft sind, gehören nicht mehr zu Visual Studio.

- Einige Funktionen sind nicht mehr in der DLL enthalten. Sie befinden sich weiter in der Importbibliothek. Dies betrifft Code nicht, der die Funktionen statisch verwendet. Dies wirkt sich nur auf Code aus, der diese Funktionen dynamisch verwendet.

### <a name="mfc"></a>MFC

- `CTime`-Klasse: Die `CTime`-Klasse akzeptiert jetzt Datumsangaben beginnend mit 1.1.1900 unserer Zeitrechnung. anstatt 01.01.1970.

- Aktivierreihenfolge von Steuerelementen in MFC-Dialogfeldern: Die richtige Aktivierreihenfolge mehrerer Steuerelemente in einem MFC-Dialogfeld ist gestört, wenn ein MFC-ActiveX-Steuerelement in die Aktivierreihenfolge eingefügt wird. Diese Änderung behebt dieses Problem.

   Erstellen Sie beispielsweise eine MFC-Dialogfeldanwendung, die über ein ActiveX-Steuerelement und mehrere Bearbeitungssteuerelemente verfügt. Positionieren Sie das ActiveX-Steuerelement in der Mitte der Aktivierreihenfolge der Bearbeitungssteuerelemente. Starten Sie die Anwendung, klicken Sie auf ein Bearbeitungs Steuerelement, dessen Aktivier Reihenfolge nach dem ActiveX-Steuerelement und dann auf Tab. vor dieser Änderung ging der Fokus auf das Bearbeitungs Steuerelement, das dem ActiveX-Steuerelement folgt, anstatt auf das nächste Bearbeitungs Steuerelement in der aktivi

- `CFileDialog`Klasse: benutzerdefinierte Vorlagen für die `CFileDialog` Klasse können nicht automatisch zu Windows Vista portiert werden. Sie sind immer noch verwendbar ist, verfügen jedoch nicht über die zusätzliche Funktionalität oder das Aussehen von Dialogfeldern im Windows Vista-Stil.

- `CWnd`-Klasse und `CFrameWnd`-Klasse: Die Methode `CWnd::GetMenuBarInfo` wurde entfernt.

   Die Methode `CFrameWnd::GetMenuBarInfo` ist jetzt eine nicht virtuelle Methode. Weitere Informationen finden Sie unter **Funktion „GetMenuBarInfo“** im Windows SDK.

- MFC ISAPI-Unterstützung: MFC unterstützt das Erstellen von Anwendungen mit der ISAPI (Internet Server Application Programming Interface) nicht mehr. Wenn Sie eine ISAPI-Anwendung erstellen möchten, rufen Sie die ISAPI-Erweiterungen direkt auf.

- Veraltete ANSI-APIs: Die ANSI-Versionen mehrerer MFC-Methoden sind veraltet. Verwenden Sie in Ihren künftigen Anwendungen die Unicode-Versionen dieser Methoden. Weitere Informationen finden Sie unter **Buildanforderungen für allgemeine Windows Vista**-Steuerelemente.

## <a name="visual-studio-2005-breaking-changes"></a>Breaking Changes in Visual Studio 2005

### <a name="crt"></a>CRT

- Zahlreiche Funktionen sind veraltet. Siehe **Veraltete CRT-Funktionen**.

- Viele Funktionen überprüfen jetzt ihre Parameter und halten die Ausführung an, falls ungültige Parameter angegeben wurden. Durch diese Überprüfung wird möglicherweise Code unterbrochen, der ungültige Parameter übergibt und sich darauf verlässt, dass die Funktion sie ignoriert oder bloß einen Fehlercode zurückgibt. Siehe **Parameter Validierung**.

- Der Deskriptorwert „-2“ wird jetzt verwendet, um anzugeben, dass `stdout` und `stderr` nicht für die Ausgabe verfügbar sind, z. B. bei einer Windows-Anwendung ohne Konsolenfenster. Der bisher verwendete Wert war -1. Weitere Informationen finden Sie unter [_fileno](../c-runtime-library/reference/fileno.md).

- Die Singlethread-CRT-Bibliotheken (libc.lib und libcd.lib) wurden entfernt. Verwenden Sie die Multithread-CRT-Bibliotheken. Das Compilerflag `/ML` wird nicht mehr unterstützt. Nicht sperrende Versionen einiger Funktionen wurden in Fällen hinzugefügt, in denen der Leistungsunterschied zwischen Multithreadcode und Singlethreadcode erheblich sein kann.

- Die Überladung von pow, double pow (Int, Int) wurde entfernt, um besser dem Standard zu entsprechen.

- Der Formatspezifizierer „%n“ wird standardmäßig in der printf-Funktionsreihe nicht mehr unterstützt, da er grundsätzlich unsicher ist. Gemäß des Standardverhaltens, wenn „%n“ angetroffen wird, wird der ungültige Parameterhandler aufgerufen. Verwenden Sie `_set_printf_count_output`, um die Unterstützung von „%n“ zu aktivieren (siehe auch `_get_printf_count_output`).

- `sprintf` gibt jetzt das negative Vorzeichen einer Null mit Vorzeichen aus.

- `swprintf` wurde geändert, um dem Standard zu entsprechen. Es erfordert jetzt einen size-Parameter. Die Form von `swprintf` ohne size-Parameter wurde als veraltet markiert.

- `_set_security_error_handler` wurde entfernt. Entfernen Sie alle Aufrufe der Funktion. Der Standardhandler bietet eine viel sicherere Möglichkeit des Umgangs mit Sicherheitsfehlern.

- `time_t` ist jetzt ein 64-Bit-Wert (sofern _USE_32BIT_TIME_T definiert ist).

- Die Funktionen `_spawn` und `_wspawn` lassen `errno` gemäß des C-Standards bei Erfolg unverändert.

- RTC verwendet jetzt standardmäßig Breitzeichen.

- Wortunterstützungsfunktionen zur Gleitkommasteuerung sind für Anwendungen veraltet, die mit `/CLR` oder `/CLR:PURE` kompiliert wurden. Folgende Funktionen sind betroffen: `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87` und `_statusfp`. Sie können die Warnung zur Veraltung deaktivieren, indem Sie _CRT_MANAGED_FP_NO_DEPRECATE definieren. Doch die Verwendung dieser Funktionen in verwaltetem Code ist unvorhersehbar und wird nicht unterstützt.

- Einige Funktionen geben jetzt Const-Zeiger zurück. Das alte, Nicht-Const-Verhalten kann durch Definition von _CONST_RETURN reaktiviert werden. Die folgenden Funktionen sind betroffen:

  - memchr, wmemchr

  - strchr, wcschr, _mbschr, _mbschr_l

  - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

  - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

  - strstr, wcsstr, _mbsstr, _mbsstr_l

- Beim Verknüpfen mit Setargv.obj oder Wsetargv.obj ist es nicht mehr möglich, die Erweiterung eines Platzhalterzeichens in der Befehlszeile zu unterdrücken, indem es in doppelte Anführungszeichen gesetzt wird. Weitere Informationen finden Sie unter [Erweitern von Platzhalterargumenten](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Standardbibliothek (2005)

- Die Ausnahme Klasse (in der \<exception> Kopfzeile) wurde in den- `std` Namespace verschoben. In früheren Versionen befand sich diese Klasse im globalen Namespace. Zum Beheben von Fehlern, die angeben, dass die exception-Klasse nicht gefunden werden kann, müssen Sie zu Ihrem Code die folgende using-Anweisung hinzufügen: `using namespace std;`

- Wenn `valarray::resize()` aufgerufen wird, geht der Inhalt von `valarray` verloren und wird durch Standardwerte ersetzt. Die Methode `resize()` dient zum erneuten Initialisieren von `valarray`, ohne dass ein dynamisches Wachsen wie bei einem Vektor erfolgt.

- Debugiteratoren: Bei Anwendungen, die mit einer Debugversion der C-Laufzeitbibliothek erstellt wurden und Iteratoren falsch verwenden, erfolgen möglicherweise zur Laufzeit Assert-Vorgänge. Zum Deaktivieren dieser Assert-Vorgänge müssen Sie _HAS_ITERATOR_DEBUGGING (ersetzt durch [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) nach Visual Studio 2010) auf 0 festlegen. Weitere Informationen finden Sie [unter Unterstützung für iteratordebugging](../standard-library/debug-iterator-support.md) .

## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003: Bedeutende Änderungen

### <a name="compiler"></a>Compiler

- Schließende Klammern sind jetzt für die definierte Präprozessordirektive (C2004) erforderlich.

- Explizite Spezialisierungen finden in der primären Vorlage keine Vorlagenparameter mehr ([Compilerfehler C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Auf einen geschützten Member (n) kann nur über eine Memberfunktion einer Klasse (B) zugegriffen werden, die von der Klasse (A) erbt, deren Member (n) ist ([Compilerfehler C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Verbesserte Zugriffsprüfungen im Compiler erkennen jetzt Basisklassen, auf die nicht zugegriffen werden kann ([Compilerfehler C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Eine Ausnahme kann nicht abgefangen werden, wenn auf den Destruktor und/oder Kopierkonstruktor nicht zugegriffen werden kann (C2316).

- Standardargumente für Zeiger auf Funktionen sind nicht mehr zulässig ([Compilerfehler C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Ein statischer Datenmember darf nicht über eine abgeleitete Klasse initialisiert werden ([Compilerfehler C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Die Initialisierung einer **typedef** ist gemäß dem Standard nicht zulässig und erzeugt nun einen Compilerfehler ([Compilerfehler C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- **bool** ist nun ein geeigneter Typ ([Compilerfehler C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- Eine UDC kann jetzt mit überladenen Operatoren Mehrdeutigkeit erzeugen ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Mehr Ausdrücke gelten jetzt als gültige NULL-Zeigerkonstanten ([Compilerfehler C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- template<> ist nun an Stellen erforderlich, an denen der Compiler sie zuvor impliziert hat ([Compilerfehler C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Die explizite Spezialisierung einer Memberfunktion außerhalb der Klasse ist nicht gültig, wenn die Funktion bereits über eine Vorlagenklassenspezialisierung explizit spezialisiert wurde ([Compilerfehler C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Nichttyp-Vorlagenparameter für Gleitkommas sind nicht mehr zulässig ([Compilerfehler C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Klassenvorlagen sind nicht als Vorlagentypargumente zulässig (C3206).

- Friend-Funktionsnamen werden im enthaltenden Namespace nicht mehr eingeführt ([Compilerfehler C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Zusätzliche Kommas in Makros werden vom Compiler nicht mehr akzeptiert (C4002).

- Ein Objekt des POD-Typs, das mit der Initialisierung des Formulars '()' erstellt wurde, wird mit 'default' initialisiert (C4345).

- TypeName ist jetzt erforderlich, wenn ein abhängiger Name als Typ behandelt wird ([Compilerwarnung (Stufe 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funktionen, die fälschlicherweise als Vorlagenspezialisierungen eingestuft wurden, werden nicht mehr so eingestuft (C4347).

- Statische Datenmember können nicht über eine abgeleitete Klasse initialisiert werden (C4356).

- Eine Klassenvorlagenspezialisierung muss vor ihrer Verwendung in einem Rückgabetyp definiert werden ([Compilerwarnung (Stufe 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Der Compiler meldet jetzt nicht erreichbaren Code (C4702).

## <a name="see-also"></a>Weitere Informationen

[Neuerungen bei Visual C++ in Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
