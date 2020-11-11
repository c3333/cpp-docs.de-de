---
title: /guard:ehcont (EH-Fortsetzungsmetadaten aktivieren)
description: 'Referenzhandbuch zur Microsoft C++/Guard: ehconfiguration-Compileroption.'
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: ea6a225dce9bf76ff2dc69945916c006a0d5ec0b
ms.sourcegitcommit: 25f6d52eb9e5d84bd0218c46372db85572af81da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94448372"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>`/guard:ehcont` (Eh-Fortsetzungs Metadaten aktivieren)

Aktiviert die Generierung von eh-Fortsetzungs Metadaten (EHAs) durch den Compiler.

## <a name="syntax"></a>Syntax

> **`/guard:ehcont`** [ **`-`** ]

## <a name="remarks"></a>Bemerkungen

Die- **`/guard:ehcont`** Option bewirkt, dass der Compiler eine sortierte Liste der relativen virtuellen Adressen (RVA) aller gültigen Fortsetzungs Ziele für die Ausnahmebehandlung für eine Binärdatei generiert. Sie wird während der Laufzeit für `NtContinue` die `SetThreadContext` Validierung des Anweisungs Zeigers verwendet. Standardmäßig **`/guard:ehcont`** ist deaktiviert und muss explizit aktiviert werden. Um diese Option explizit zu deaktivieren, verwenden Sie **`/guard:ehcont-`** .

Die **`/guard:ehcont`** Option ist in Visual Studio 2019, Version 16,7 und höher, verfügbar. Das Feature wird für 64-Bit-Prozesse auf einem 64-Bit-Betriebssystem unterstützt.

Die [Steuerungs Technologie für die Ablauf Steuerung (CET)](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf) ist ein Hardware basiertes Sicherheits Feature, das Schutz vor Return-Oriented-Programmierungs Angriffen (auf der Grundlage von auf der Basis von) Er verwaltet einen "Schatten Stapel" für jede aufrufsstapel, um die Ablauf Steuerungs Integrität zu erzwingen.

Wenn Schatten Stapel verfügbar sind, um die Verwendung von ROP-Angriffen zu verhindern, fahren Angreifer mit anderen exploittechniken fort. Eine Methode, die Sie verwenden können, besteht darin, den Anweisungs Zeiger Wert innerhalb der [Kontext](/windows/win32/api/winnt/ns-winnt-context) Struktur zu beschädigen. Diese Struktur wird an Systemaufrufe weitergeleitet, die die Ausführung eines Threads umleiten, `NtContinue` z [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) . b [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) ., und. Die `CONTEXT` Struktur wird im Arbeitsspeicher gespeichert. Die Beschädigung des Anweisungs Zeigers, der in enthalten ist, kann dazu führen, dass die Ausführung der Ausführung durch die Systemaufrufe an eine von Angreifern Derzeit `NTContinue` kann mit einem beliebigen Fortsetzungs Punkt aufgerufen werden. Daher ist es von entscheidender Bedeutung, den Anweisungs Zeiger zu validieren, wenn Schatten Stapel aktiviert sind.

`RtlRestoreContext` und `NtContinue` werden beim Entladen der strukturierten Ausnahmebehandlung (SEH) zum Entladen in den Zielframe verwendet, der den **`__except`** Block enthält. **`__except`** Es ist nicht zu erwarten, dass sich der Anweisungs Zeiger des Blocks auf dem Schatten Stapel befindet, da er die Validierung des Anweisungs Zeigers fehlschlägt. Der **`/guard:ehcont`** Compilerschalter generiert eine "eh-Fortsetzungs Tabelle". Sie enthält eine sortierte Liste der RVAs aller gültigen Fortsetzungs Ziele für die Ausnahmebehandlung in der Binärdatei. `NtContinue` prüft zunächst den Schatten Stapel auf den vom Benutzer bereitgestellten Anweisungs Zeiger, und wenn der Anweisungs Zeiger dort nicht gefunden wird, wird die eh-Fortsetzungs Tabelle in der Binärdatei überprüft, die den Anweisungs Zeiger enthält. Wenn die enthaltende Binärdatei nicht mit der Tabelle kompiliert wurde, kann aus Gründen der Kompatibilität mit Legacy Binärdateien `NtContinue` fortgesetzt werden. Es ist wichtig, zwischen Legacy-Binärdateien zu unterscheiden, die keine EHAND-Daten enthalten, und Binärdateien, die ehint-Daten, aber keine Tabelleneinträge enthalten. Der erste Wert ermöglicht alle Adressen innerhalb der Binärdatei als gültige Fortsetzungs Ziele. Letztere lässt keine Adresse in der Binärdatei als gültiges Fortsetzungs Ziel zu.

Die **`/guard:ehcont`** -Option muss an den Compiler und den Linker weitergegeben werden, um die RVAs für ein Fortsetzungs Ziel für eine Binärdatei zu generieren. Wenn die Binärdatei mit einem einzigen `cl` -Befehl erstellt wird, übergibt der Compiler die Option an den Linker. Der Compiler übergibt auch die [`/guard:cf`](guard-enable-control-flow-guard.md) Option an den Linker. Wenn Sie separat kompilieren und verknüpfen, müssen diese Optionen sowohl für den Compiler als auch für den Linker-Befehl festgelegt werden.

Sie können Code, der mit kompiliert wurde **`/guard:ehcont`** , mit Bibliotheken und Objektdateien verknüpfen, die ohne ihn kompiliert wurden. Der Linker gibt in einem der folgenden Szenarien einen schwerwiegenden Fehler zurück:

- Ein Code Abschnitt hat eine "lokale Entladung". Weitere Informationen finden Sie unter ungewöhnliche Beendigung in der [try-schließlich-Anweisung](../../cpp/try-finally-statement.md#abnormal-termination).

- Ein eh-Abschnitt (XData) enthält Zeiger auf einen Code Abschnitt und ist nicht für Seh.

- Die Zeiger sind für Seh, aber die Objektdatei wurde nicht mithilfe von Verknüpfungen auf Funktionsebene ([/Gy](gy-enable-function-level-linking.md)) kompiliert, um COMDATs zu erstellen.

Der Linker gibt einen schwerwiegenden Fehler zurück, da er in diesen Szenarien keine Metadaten generieren kann. Das Auslösen einer Ausnahme führt wahrscheinlich zu einem Absturz zur Laufzeit.

Für Seh-Abschnitts Informationen, die in COMDATs gefunden werden, aber nicht mit kompiliert **`/guard:ehcont`** wurden, gibt der Linker Warning **LNK4291** aus. In diesem Fall generiert der Linker korrekte, aber konservative Metadaten für den Abschnitt. Verwenden Sie [/Ignore (bestimmte Warnungen ignorieren)](ignore-ignore-specific-warnings.md), um diese Warnung zu ignorieren.

Wenn der Linker keine Metadaten generieren kann, gibt er einen der folgenden Fehler aus:

- `LNK2046: module contains _local_unwind but was not compiled with /guard:ehcont`

- `LNK2047: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

Um zu überprüfen, ob eine Binärdatei ehcont-Daten enthält, suchen Sie nach den folgenden Elementen, wenn Sie die Lade Konfiguration der Binärdatei sichern:

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung** aus.

1. Wählen Sie die Eigenschaft **eh-Fortsetzungs Metadaten aktivieren** aus.

1. Wählen Sie im Dropdown-Steuerelement **Ja (/Guard: ehtt)** aus, um die eh-Fortsetzungs Metadaten zu aktivieren, oder **Nein (/Guard: ehint-)** , um es zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[/Guard (Ablauf Steuerungs Schutz aktivieren)](guard-enable-control-flow-guard.md)\
[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-CompilerCommand-Line Syntax](compiler-command-line-syntax.md)
