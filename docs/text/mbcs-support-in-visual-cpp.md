---
title: MBCS-Unterstützung in Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375795"
---
# <a name="mbcs-support-in-visual-c"></a>MBCS-Unterstützung in Visual C++

Wenn das Visual C++-Entwicklungssystem (einschließlich des integrierten Quellcodeeditors, des Debuggers und der Befehlszeilentools) auf einer MBCS-fähigen Windows-Version ausgeführt wird, ist ES MBCS-aktiviert, mit Ausnahme des Speicherfensters.

Das Speicherfenster interpretiert keine Datenbytes als MBCS-Zeichen, obwohl sie als ANSI- oder Unicode-Zeichen interpretiert werden können. ANSI-Zeichen haben immer eine Größe von 1 Byte und Unicode-Zeichen sind 2 Byte groß. Bei MBCS können Zeichen 1 oder 2 Byte groß sein, und ihre Interpretation hängt davon ab, welche Codepage verwendet wird. Aus diesem Grund ist es für das Speicherfenster schwierig, MBCS-Zeichen zuverlässig anzuzeigen. Das Speicherfenster kann nicht wissen, welches Byte der Anfang eines Zeichens ist. Der Entwickler kann die Bytewerte im Speicherfenster anzeigen und den Wert in Tabellen nachschlagen, um die Zeichendarstellung zu bestimmen. Dies ist möglich, weil der Entwickler die Startadresse einer Zeichenfolge auf der Grundlage des Quellcodes kennt.

Visual C++ akzeptiert Doppelbyte-Zeichen, wo immer dies angebracht ist. Dazu gehören Pfadnamen und Dateinamen in Dialogfeldern und Texteinträge im Visual C++-Ressourceneditor (z. B. statischer Text im Dialogeditor und statische Texteinträge im Symboleditor). Darüber hinaus erkennt der Präprozessor einige Doppelbyte-Direktiven, `#include` z. B. `code_seg` Dateinamen in Anweisungen und als Argumente für die und `data_seg` Pragmas. Im Quellcode-Editor werden Doppelbytezeichen in Kommentaren und Zeichenfolgenliteralen akzeptiert, jedoch nicht in C/C++-Sprachelementen (z. B. Variablennamen).

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Unterstützung für den Eingabemethoden-Editor (IME)

Anwendungen, die für ostasiatische Märkte geschrieben wurden und MBCS (z. B. Japan) verwenden, unterstützen normalerweise das Windows-IME für die Eingabe von Ein- und Zweibytezeichen. Die Visual C++-Entwicklungsumgebung enthält vollständige Unterstützung für den IME.

Japanische Tastaturen unterstützen keine Kanji-Zeichen direkt. Das IME wandelt eine phonetische Zeichenfolge, die in einem der anderen japanischen Alphabete (Romaji, Katakana oder Hiragana) eingegeben wird, in seine möglichen Kanji-Darstellungen um. Wenn Mehrdeutigkeit besteht, können Sie aus mehreren Alternativen auswählen. Wenn Sie das beabsichtigte Kanji-Zeichen ausgewählt `WM_CHAR` haben, übergibt der IME zwei Nachrichten an die steuernde Anwendung.

Der IME, der durch\` die Tastenkombination ALT+ aktiviert wird, wird als eine Reihe von Schaltflächen (ein Indikator) und ein Konvertierungsfenster angezeigt. Die Anwendung positioniert das Fenster an der Texteinfügemarke. Die Anwendung `WM_MOVE` muss `WM_SIZE` das Konvertierungsfenster verarbeiten und anzeigen, indem sie das Konvertierungsfenster neu positioniert, um dem neuen Speicherort oder der neuen Größe des Zielfensters zu entsprechen.

Wenn Benutzer Ihrer Anwendung kanji-Zeichen eingeben können sollen, muss die Anwendung Windows IME-Nachrichten verarbeiten. Weitere Informationen zur IME-Programmierung finden Sie unter [Eingabemethoden-Manager](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Visual C++-Debugger

Der Visual C++-Debugger bietet die Möglichkeit, Haltepunkte für IME-Nachrichten festzulegen. Darüber hinaus kann das Speicherfenster Doppelbytezeichen anzeigen.

## <a name="command-line-tools"></a>Befehlszeilentools

Die Visual C++-Befehlszeilentools, einschließlich compiler, NMAKE und resource compiler (RC. EXE) sind MBCS-fähig. Sie können die /c-Option des Ressourcencompilers verwenden, um die Standardcodepage beim Kompilieren der Anwendungsressourcen zu ändern.

Um das Standardgebietsschema zur Kompilierungszeit des Quellcodes zu ändern, verwenden Sie [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Grafische Tools

Die Visual C++ Windows-basierten Tools, z. B. Spy++ und die Tools zum Bearbeiten von Ressourcen, unterstützen IME-Zeichenfolgen vollständig.

## <a name="see-also"></a>Siehe auch

[Unterstützung von Mehrbyte-Zeichensätzen (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Tipps für die MBCS-Programmierung](../text/mbcs-programming-tips.md)
