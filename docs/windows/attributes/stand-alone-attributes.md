---
title: Eigenständige Attribute (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166169"
---
# <a name="stand-alone-attributes"></a>Eigenständige Attribute

Ein eigenständiges Attribut kann nicht für ein C++ Schlüsselwort verwendet werden, ähnelt aber eher einer Codezeile. Für eigenständige Attribut Anweisungen ist am Ende der Zeile ein Semikolon erforderlich.

## <a name="stand-alone-attribute-list"></a>Liste der eigenständigen Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten Header Datei aus.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[db_command](db-command.md)|Erstellt einen OLE DB-Befehl.|
|[emitidl](emitidl.md)|Bestimmt, ob alle nachfolgenden IDL-Attribute verarbeitet und in der generierten IDL-Datei abgelegt werden.|
|[idl_module](idl-module.md)|Gibt einen Einstiegspunkt in einer DLL an.|
|[idl_quote](idl-quote.md)|Ermöglicht die Verwendung von IDL-Konstrukten, die in der aktuellen Version von Visual C++ nicht unterstützt werden und die Sie an die generierte IDL-Datei weiterleiten.|
|[import](import.md)|Gibt eine andere IDL-, ODL-oder h-Datei an, die Definitionen enthält, auf die Sie aus der IDL-Hauptdatei verweisen möchten.|
|[importidl](importidl.md)|Fügt die angegebene IDL-Datei in die generierte IDL-Datei ein.|
|[importlib](importlib.md)|Stellt Typen, die bereits in einer anderen Typbibliothek kompiliert wurden, der erstellten Typbibliothek zur Verfügung.|
|[include](include-cpp.md)|Gibt eine oder mehrere Header Dateien an, die in die generierte IDL-Datei eingeschlossen werden sollen.|
|[includelib](includelib-cpp.md)|Bewirkt, dass eine IDL-oder h-Datei in der generierten IDL-Datei enthalten ist.|
|[library_block](library-block.md)|Platziert ein Konstrukt innerhalb des Bibliotheks Blocks der IDL-Datei.|
|[module](module-cpp.md)|Definiert den Bibliotheksblock in der IDL-Datei.|
|[no_injected_text](no-injected-text.md)|Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.|
|[pragma](pragma.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten IDL-Datei aus.|

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Verwendung](attributes-by-usage.md)
