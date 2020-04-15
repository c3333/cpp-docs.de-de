---
title: Empfohlene Tags für Dokumentationskommentare (C++-Dokumentationskommentare)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336173"
---
# <a name="recommended-tags-for-documentation-comments"></a>Empfohlene Tags für Dokumentationskommentare

Der MSVC-Compiler verarbeitet Dokumentationskommentare in Ihrem Code und erstellt eine .xdc-Datei für jedes Kompiland, und xdcmake.exe verarbeitet die .xdc-Dateien in einer XML-Datei. Die Verarbeitung der XML-Datei zum Erstellen der Dokumentation muss an Ihrem Standort implementiert werden.

Tags werden auf der Basis von Konstrukten wie Typen und Typmember verarbeitet.

Tags müssen Typen oder Membern unmittelbar vorangestellt werden.

> [!NOTE]
> Dokumentationskommentare können nicht für einen Namespace oder außerhalb der Definition für Eigenschaften und Ereignisse angewendet werden. Dokumentationskommentare müssen auf die Klassendeklarationen angewendet werden.

Der Compiler verarbeitet alle Tags, die gültige XML sind. Die folgenden Tags stellen häufig verwendete Funktionen in der Benutzerdokumentation bereit:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<Code->](code-visual-cpp.md)|[\<Beispiel>](example-visual-cpp.md)|
|Ausnahme>1 [ \< ](exception-visual-cpp.md)|[ \<>](include-visual-cpp.md)1|[\<Liste>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|param>1 [ \< ](param-visual-cpp.md)|paramref>1 [ \< ](paramref-visual-cpp.md)|
|Erlaubnis>1 [ \< ](permission-visual-cpp.md)|[\<Bemerkungen>](remarks-visual-cpp.md)|[\<gibt>zurück](returns-visual-cpp.md)|
|siehe>1 [ \< ](see-visual-cpp.md)|siehe auch>1 [ \< ](seealso-visual-cpp.md)|[\<Zusammenfassung>](summary-visual-cpp.md)|
|[\<Wert>](value-visual-cpp.md)|||

1. Der Compiler überprüft die Syntax.

In der aktuellen Version unterstützt `<paramref>`der MSVC-Compiler kein Tag, das von anderen Visual Studio-Compilern unterstützt wird. Möglicherweise unterstützt Visual C++ `<paramref>` in einem zukünftigen Release.

## <a name="see-also"></a>Siehe auch

[XML-Dokumentation](xml-documentation-visual-cpp.md)
