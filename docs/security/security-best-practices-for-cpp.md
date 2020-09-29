---
title: Empfohlene Vorgehensweisen bezüglich der Sicherheit in C++
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 63c5567cf1b06d52aa4b458a9ca127039e5c5daf
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499588"
---
# <a name="security-best-practices-for-c"></a>Empfohlene Vorgehensweisen bezüglich der Sicherheit in C++

Dieser Artikel enthält Informationen über Sicherheitstools und Vorgehensweisen. Ihre Verwendung macht eine Anwendung zwar nicht immun gegen Angriffe, aber sie verringert die Wahrscheinlichkeit erfolgreicher Angriffe.

## <a name="visual-c-security-features"></a>Visual C++-Sicherheitsfunktionen

Diese Sicherheitsfunktionen sind in den Microsoft C++-Compiler und-Linker integriert:

[`/guard` (Ablauf Steuerungs Schutz aktivieren)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Veranlasst den Compiler, die Ablauf Steuerung für indirekte Aufruf Ziele zum Zeitpunkt der Kompilierung zu analysieren und dann Code einzufügen, um die Ziele zur Laufzeit zu überprüfen.

[`/GS` (Puffer-Sicherheitsüberprüfung)](../build/reference/gs-buffer-security-check.md)<br/>
Der Compiler wird angewiesen, Überlauferkennungscode in Funktionen einzufügen, die Angriffen ausgesetzt sein können. Wenn ein Überlauf erkannt wird, wird die Programmausführung angehalten. Diese Option ist standardmäßig aktiviert.

[`/SAFESEH` (Abbild verfügt über sichere Ausnahmehandler)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Der Linker wird angewiesen, dem Ausgabeabbild eine Tabelle mit den Adressen aller Ausnahmehandler hinzuzufügen. Zur Laufzeit verwendet das Betriebssystem diese Tabelle, um sicherzustellen, dass nur rechtmäßige Ausnahmehandler ausgeführt werden. Dadurch wird verhindert, dass in böswilligen Angriffen zur Laufzeit eingeschleuste Ausnahmehandler ausgeführt werden. Diese Option ist standardmäßig deaktiviert.

[`/NXCOMPAT`](../build/reference/nxcompat.md), [ `/NXCOMPAT` (Kompatibel mit der Daten Ausführungs Verhinderung)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) Diese Compileroptionen und Linkeroptionen aktivieren die Kompatibilität mit der Daten Ausführungs Verhinderung. DEP schützt die CPU vor der Ausführung von Seiten, die keine Codepages sind.

[`/analyze` (Code Analyse)](../build/reference/analyze-code-analysis.md)<br/>
Diese Compileroption aktiviert die Codeanalyse, die über potentielle Sicherheitslücken wie Pufferüberlauf, nicht initialisierten Speicher, Dereferenzierung von NULL-Zeigern und Speicherverlusten Bericht erstattet. Diese Option ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Übersicht über die Code Analyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md).

[`/DYNAMICBASE` (Adressraum Layout Randomization verwenden)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Diese Linkeroption ermöglicht das Erstellen eines ausführbaren Images, das am Anfang der Ausführung an anderen Orten im Arbeitsspeicher geladen werden kann. Durch diese Option lässt sich die Position des Stapels im Arbeitsspeicher auch schlechter vorhersagen.

## <a name="security-enhanced-crt"></a>CRT mit erweiterter Sicherheit

Die C-Laufzeitbibliothek (CRT) wurde um sichere Versionen von Funktionen erweitert, die ein Sicherheitsrisiko darstellen, z. B. die aufwerfen, die ungeprüfte `strcpy`-Funktion zum Kopieren von Zeichenfolgen. Da die älteren, nicht sicheren Versionen dieser Funktionen jetzt veraltet sind, verursacht ihre Verwendung Compilerwarnungen. Es wird empfohlen, die sicheren Versionen dieser CRT-Funktionen zu verwenden, anstatt die Compilerwarnungen zu unterdrücken. Weitere Informationen finden Sie unter [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>SafeInt-Bibliothek

Die [safeint-Bibliothek](../safeint/safeint-library.md) hilft beim Vermeiden von ganz Zahl Überläufen und anderen ausnutzbaren Fehlern, die auftreten können, wenn die Anwendung mathematische Vorgänge ausführt. Die `SafeInt` Bibliothek enthält die [safeint-Klasse](../safeint/safeint-class.md), die [safeintexception-Klasse](../safeint/safeintexception-class.md)und mehrere [safeint-Funktionen](../safeint/safeint-functions.md).

Die `SafeInt`-Klasse schützt vor Ganzzahlüberlauf und Exploits vom Typ "Division durch 0". Sie können sie zum Behandeln von Vergleichen zwischen Werten unterschiedlicher Typen verwenden. Es werden zwei Richtlinien zur Fehlerbehandlung bereitstellt. Gemäß Standardrichtlinie löst die `SafeInt`-Klasse eine `SafeIntException`-Klassenausnahme aus, um zu berichten, warum ein mathematischer Vorgang nicht abgeschlossen werden kann. Gemäß der zweiten Richtlinie beendet die `SafeInt`-Klasse die Programmausführung. Sie können auch eine benutzerdefinierte Richtlinie definieren.

Jede `SafeInt`-Funktion schützt einen mathematischen Vorgang vor einem als Angriffspunkt geeigneten Fehler. Sie können zwei verschiedene Arten von Parametern verwenden, ohne sie in den gleichen Typ konvertieren zu müssen. Verwenden Sie die `SafeInt`-Klasse, um mehrere mathematische Vorgänge zu schützen.

## <a name="checked-iterators"></a>Checked Iterators

Ein überprüfter Iterator erzwingt Containergrenzen. Wenn ein überprüfter Iterator außerhalb der zulässigen Grenzen liegt, wird eine Ausnahme generiert und die Programmausführung beendet. Ein überprüfter Iterator bietet andere Ebenen der Antwort, die von Werten abhängen, die Präprozessordefinitionen wie und zugewiesen werden `_SECURE_SCL_THROWS` `_ITERATOR_DEBUG_LEVEL` . Beispielsweise `_ITERATOR_DEBUG_LEVEL=2` stellt ein aktivierter Iterator in eine umfassende Richtigkeit von Prüfungen im Debugmodus bereit, die mithilfe von Assertionen zur Verfügung gestellt werden. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../standard-library/checked-iterators.md) und [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) .

## <a name="code-analysis-for-managed-code"></a>Codeanalyse für verwalteten Code

Codeanalyse für verwalteten Code, auch bekannt als FxCop, überprüft Assemblys auf Übereinstimmung mit den .NET Framework-Entwurfsrichtlinien. FxCop analysiert den Code und die Metadaten in jeder Assembly und prüft in den folgenden Bereichen auf Fehler:

- Bibliotheksentwurf

- Lokalisierung

- Namenskonventionen

- Leistung

- Sicherheit

## <a name="windows-application-verifier"></a>Windows Application Verifier

Der [Application Verifier (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) kann Ihnen helfen, potenzielle Probleme mit der Anwendungs Kompatibilität, Stabilität und Sicherheit zu erkennen.

Der AppVerifier überwacht, wie eine Anwendung das Betriebssystem verwendet. Dateisystem, Registrierung, Arbeitsspeicher und APIs werden beobachtet, während die Anwendung ausgeführt wird, und es werden Quellcodepatches für die erkannten Probleme empfohlen.

Sie können den AppVerifier wie folgt verwenden:

- Auf potenzielle durch allgemeine Programmierfehler verursachte Anwendungskompatibilitätsfehler prüfen.

- Eine Anwendung auf speicherbezogene Probleme untersuchen.

- Potenzielle Sicherheitsprobleme in einer Anwendung aufdecken.

## <a name="windows-user-accounts"></a>Windows-Benutzerkonten

Das Verwenden von Windows-Benutzerkonten, die zur Gruppe der Administratoren gehören, setzt Entwickler und – durch entsprechende Erweiterung – auch Kunden Sicherheitsrisiken aus. Weitere Informationen finden Sie unter [Ausführen als Mitglied der Gruppe "Benutzer](running-as-a-member-of-the-users-group.md) " und [so, wie sich die Benutzerkontensteuerung (User Account Control, UAC) auf Ihre Anwendung auswirkt](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Leitfaden für spekulative Ausführungs seitige Kanäle

Informationen dazu, wie Sie in C++ Software die Sicherheitsrisiken für die spekulative Ausführungs seitige Kanal Hardware erkennen und mindern, finden Sie unter [C++ Developer Guidance for spekulative Execution Side Channels](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Siehe auch

<xref:System.Security> <br/>
[Sicherheit](/dotnet/standard/security/index)<br/>
[Auswirkungen der Benutzerkontensteuerung (User Account Control, UAC) auf Ihre Anwendung](how-user-account-control-uac-affects-your-application.md)
