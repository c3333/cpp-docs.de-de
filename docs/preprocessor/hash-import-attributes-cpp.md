---
title: '#import-Attribute (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: fc2af69025d47a9ea6cea0e2c9e1423151b01606
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215292"
---
# <a name="import-attributes-c"></a>#Import Attribute (C++)

Enthält Links zu Attributen, die mit der `#import`-Direktive verwendet werden.

**Microsoft-spezifisch**

Die folgenden Attribute sind für die `#import`-Direktive verfügbar.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Benennt für C++ reservierte Wörter um, indem dem Variablennamen zwei Unterstriche (__) angefügt werden, um potenzielle Namenskonflikte zu vermeiden.|
|[auto_search](../preprocessor/auto-search.md)|Gibt an, dass, wenn auf eine Typbibliothek mit #import verwiesen wird und diese selbst auf eine andere Typbibliothek verweist, der Compiler einen impliziten #import für die andere Typbibliothek ausführen kann.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Gibt an, dass die Typbibliothek in die TLH-Datei geschrieben wird und der vom Attribut generierte Code beibehalten wird.|
|[exclude](../preprocessor/exclude-hash-import.md)|Schließt Elemente aus den Headerdateien der Typbibliothek aus, die generiert werden.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Gibt an, welches Präfix beim Benennen von Eigenschaften und Methoden der oberen Ebene verwendet werden soll.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Gibt alternative Präfixe für drei Eigenschaftenmethoden an.|
|[implementation_only](../preprocessor/implementation-only.md)|Unterdrückt die Generierung der TLH-Headerdatei (die primäre Headerdatei).|
|[include()](../preprocessor/include-parens.md)|Deaktiviert den automatische Ausschluss.|
|[inject_statement](../preprocessor/inject-statement.md)|Fügt das Argument als Quelltext in den Header der Typbibliothek ein.|
|[named_guids](../preprocessor/named-guids.md)|Weist den Compiler an, GUID-Variablen im alten Stil der Form `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`und `DIID_MyDispInterface`zu definieren und zu initialisieren.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Deaktiviert den automatische Ausschluss.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Ändert die Art, mit der der Compiler Wrapperfunktionen für Methoden der dualen Schnittstelle generiert.|
|[no_implementation](../preprocessor/no-implementation.md)|Unterdrückt die Generierung des TLI-Headers, der die Implementierungen der Wrappermemberfunktionen enthält.|
|[no_namespace](../preprocessor/no-namespace.md)|Gibt an, dass der Name des Namespaces nicht vom Compiler generiert wird.|
|[no_registry](../preprocessor/no-registry.md)|Weist den Compiler an, in der Registrierung nicht nach Typbibliotheken zu suchen.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Verfügt über die gleiche Funktionalität wie das [no_namespace](../preprocessor/no-namespace.md) -Attribut, wird jedoch für Typbibliotheken verwendet, die die #Import-Direktive mit dem [auto_search](../preprocessor/auto-search.md) -Attribut verwenden.|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Unterdrückt die Erstellung von intelligenten Zeigern für alle Schnittstellen in der Typbibliothek.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Weist den Compiler an, Wrapper Funktionen auf niedriger Ebene für Dispinterface-Methoden und-Eigenschaften zu generieren, die `IDispatch::Invoke` aufzurufen und den HRESULT-Fehlercode zurückgeben.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Unterdrückt die Generierung von Wrapper Funktionen für die Fehlerbehandlung und [Eigenschafts](../cpp/property-cpp.md) Deklarationen, die diese Wrapper Funktionen verwenden.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Gibt ein anderes Präfix an, um Namenskonflikte zu vermeiden.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Deaktiviert die Verwendung COM-Unterstützungsklassen in den Wrapperfunktionen auf hoher Ebene und erzwingt stattdessen die Verwendung von Datentypen auf niedriger Ebene.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Gibt alternative Präfixe für drei Eigenschaftenmethoden an.|
|[rename](../preprocessor/rename-hash-import.md)|Umgeht Probleme mit Namenskonflikten.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Benennt den Namespace, der die Inhalte der Typbibliothek enthält, um.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Verfügt über die gleiche Funktionalität wie das [rename_namespace](../preprocessor/rename-namespace.md) -Attribut, wird jedoch für Typbibliotheken verwendet, die die #Import-Direktive mit dem [auto_search](../preprocessor/auto-search.md) -Attribut verwenden.|
|[tlbid](../preprocessor/tlbid.md)|Ermöglicht das Laden anderer Bibliotheken als der primären Typbibliothek.|

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[#Import-Direktive](../preprocessor/hash-import-directive-cpp.md)
