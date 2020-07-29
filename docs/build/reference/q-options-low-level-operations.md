---
title: /Q-Optionen (Operationen auf niedriger Ebene)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: f5342071cef76bcc736f128c344279898a61c462
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231493"
---
# <a name="q-options-low-level-operations"></a>/Q-Optionen (Operationen auf niedriger Ebene)

Mit den **/Q** -Compileroptionen können Sie die folgenden Compilervorgänge auf niedriger Ebene ausführen:

- [/Qfast_transcendentals (Erzwingen von schnellen transzendenten)](qfast-transcendentals-force-fast-transcendentals.md): generiert schnelle transzendente.

- [/QIfist (unterdrücken _ftol)](qifist-suppress-ftol.md): `_ftol` unterdrückt, wenn eine Konvertierung von einem Gleit kommatyp in einen ganzzahligen Typ erforderlich ist (nur x86).

- [/Qimprecise_fwaits (Remove-Vorgänge innerhalb von try-Blöcken)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): entfernt `fwait` Befehle in- **`try`** Blöcken.

- [/QIntel-JCC-Erratum](qintel-jcc-erratum.md): verringert die Leistungseinbußen, die durch den Intel Jump Conditional Code (JCC)-Erratum-mikrocodeupdate verursacht werden.

- [/QPAR (Auto-parallelizer)](qpar-auto-parallelizer.md): ermöglicht die automatische Parallelisierung von Schleifen, die mit der [#pragma Loop ()](../../preprocessor/loop.md) -Direktive gekennzeichnet sind.

- [/QPAR-Report (Berichts Ebene mit automatischer Parallelisierung)](qpar-report-auto-parallelizer-reporting-level.md): aktiviert Berichterstattungs Ebenen für die automatische Parallelisierung.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): unterdrückt Optimierungen für Gleit Komma Register Ladevorgänge und für Verschiebungen zwischen Arbeitsspeicher und MMX-Registern.

- [/Qspectre](qspectre.md): generiert Anweisungen, um bestimmte Spectre-Sicherheitslücken zu mindern.

- [/Qspectre-Load](qspectre-load.md): generiert Anweisungen zur Entschärfung von Spectre-Sicherheitsrisiken auf der Grundlage von Belastungen.

- [/Qspectre-Load-CF](qspectre-load-cf.md): generiert Anweisungen zur Abwehr von Spectre-Sicherheitsrisiken basierend auf Ablauf Steuerungs Anweisungen, die geladen werden.

- [/Qvec-Report (Auto-Vectorizer-Berichts Ebene)](qvec-report-auto-vectorizer-reporting-level.md): aktiviert Berichterstattungs Ebenen für die automatische Vektorisierung.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
