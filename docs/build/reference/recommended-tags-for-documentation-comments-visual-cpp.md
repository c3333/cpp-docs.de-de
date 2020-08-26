---
title: Empfohlene Tags für Dokumentations Kommentare (C++-Dokumentations Kommentare)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 9f41e450215e2bce02dbaf66910fc2fc1a131a99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836854"
---
# <a name="recommended-tags-for-documentation-comments"></a>Empfohlene Tags für Dokumentationskommentare

Der MSVC-Compiler verarbeitet Dokumentations Kommentare in Ihrem Code und erstellt für jedes kompiand eine XDC-Datei, und xdcmake.exe verarbeitet die XDC-Dateien in eine XML-Datei. Die Verarbeitung der XML-Datei zum Erstellen der Dokumentation muss an Ihrem Standort implementiert werden.

Tags werden auf der Basis von Konstrukten wie Typen und Typmember verarbeitet.

Tags müssen Typen oder Membern unmittelbar vorangestellt werden.

> [!NOTE]
> Dokumentationskommentare können nicht für einen Namespace oder außerhalb der Definition für Eigenschaften und Ereignisse angewendet werden. Dokumentationskommentare müssen auf die Klassendeklarationen angewendet werden.

Der Compiler verarbeitet alle Tags, die gültige XML sind. Die folgenden Tags stellen häufig verwendete Funktionen in der Benutzerdokumentation bereit:

[`<c>`](c-visual-cpp.md)
[`<code>`](code-visual-cpp.md)
[`<example>`](example-visual-cpp.md)
[`<exception>`](exception-visual-cpp.md)<sup>1</sup> 
 1 [`<include>`](include-visual-cpp.md) <sup>1</sup> 
 [`<list>`](list-visual-cpp.md) 1 
 [`<para>`](para-visual-cpp.md) 
 [`<param>`](param-visual-cpp.md) <sup>1</sup> 
 1 [`<paramref>`](paramref-visual-cpp.md) <sup>1</sup> 
 1 [`<permission>`](permission-visual-cpp.md) <sup>1</sup> 
 [`<remarks>`](remarks-visual-cpp.md) 1 
 [`<returns>`](returns-visual-cpp.md) 
 [`<see>`](see-visual-cpp.md) <sup>1</sup> 
 1 [`<seealso>`](seealso-visual-cpp.md) <sup>1</sup>
[`<summary>`](summary-visual-cpp.md)
[`<value>`](value-visual-cpp.md)

1. Der Compiler überprüft die Syntax.

In der aktuellen Version unterstützt der MSVC-Compiler nicht `<paramref>` , ein Tag, das von anderen Visual Studio-Compilern unterstützt wird. Möglicherweise unterstützt Visual C++ `<paramref>` in einem zukünftigen Release.

## <a name="see-also"></a>Weitere Informationen

[XML-Dokumentation](xml-documentation-visual-cpp.md)
