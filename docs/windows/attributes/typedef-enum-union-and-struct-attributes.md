---
title: Typedef-, Aufzählungs-, Union-undC++ struct-Attribute (com)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: fdc380cdc207361a145862f87d809a4bcea01c27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214473"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>typedef-, enum-, union- und struct-Attribute

Die folgenden Attribute gelten für die Schlüsselwörter " [typedef](../../cpp/aliases-and-typedefs-cpp.md)", " [struct](../../cpp/struct-cpp.md)" und " [Denum](../../cpp/enumerations-cpp.md) C++ ".

### <a name="typedef"></a>Typedef

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[case](case-cpp.md)|Wird mit dem [Switch_type](switch-type.md) -Attribut in einer **Union**verwendet.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[first_is](first-is.md)|Gibt den Index des ersten Array Elements an, das übertragen werden soll.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der Hilfedatei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[library_block](library-block.md)|Platziert ein Konstrukt innerhalb des Bibliotheks Blocks der IDL-Datei.|
|[ptr](ptr.md)|Legt einen Zeiger als vollständigen Zeiger fest.|
|[öffentlich](public-cpp-attributes.md)|Stellt sicher, dass eine typedef in die Typbibliothek wechselt, auch wenn in der IDL-Datei nicht auf Sie verwiesen wird.|
|[ref](ref-cpp.md)|Bezeichnet einen Verweis Zeiger.|
|[switch_is](switch-is.md)|Gibt den Ausdruck oder den Bezeichner an, der als uniondiskriminant fungiert, der das Unionmember auswählt.|
|[switch_type](switch-type.md)|Identifiziert den Typ der Variablen, die als uniondiskriminant verwendet wird.|
|[unique](unique-cpp.md)|Gibt einen eindeutigen Zeiger an.|
|[wire_marshal](wire-marshal.md)|Gibt einen Datentyp an, der anstelle eines anwendungsspezifischen Datentyps für die Übertragung verwendet wird.|

### <a name="enum"></a>enum

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|
|[v1_enum](v1-enum.md)|Weist an, dass der angegebene enumerierte Typ als 32-Bit-Entität und nicht als 16-Bit-Standardwert übertragen wird.|

### <a name="union"></a>union

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[first_is](first-is.md)|Gibt den Index des ersten Array Elements an, das übertragen werden soll.|
|[last_is](last-is.md)|Gibt den Index des letzten Array Elements an, das übertragen werden soll.|
|[length_is](length-is.md)|Gibt die Anzahl der zu übertragenden Array Elemente an.|
|[max_is](max-is.md)|Legt den maximalen Wert für einen gültigen Array Index fest.|
|[size_is](size-is.md)|Gibt die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger, Größen Zeiger auf Größen Zeiger und einzelne oder mehrdimensionale Arrays an.|
|[unique](unique-cpp.md)|Gibt einen eindeutigen Zeiger an.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|

### <a name="nonencapsulated-union"></a>Nicht gekapselt Union

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[ms_union](ms-union.md)|Steuert die Ausrichtung der Netzwerkdaten Darstellung von nicht gekapselten Unions.|
|[no_injected_text](no-injected-text.md)|Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.|

### <a name="struct"></a>struct

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[Aggregierbar](aggregatable.md)|Gibt an, dass die Klasse Aggregationen unterstützt.|
|[Aggregate](aggregates.md)|Gibt an, dass ein Steuerelement die Zielklasse aggregiert.|
|[appobject](appobject.md)|Identifiziert die Co-Klasse als Anwendungs Objekt, das einer Full. exe-Anwendung zugeordnet ist, und gibt an, dass die Funktionen und Eigenschaften der Co-Klasse in dieser Typbibliothek global verfügbar sind.|
|[coclass](coclass.md)|Erstellt ein ActiveX-Steuerelement.|
|[com_interface_entry](com-interface-entry-cpp.md)|Fügt einer COM-Zuordnung einen Schnittstellen Eintrag hinzu.|
|[Steuerelement](control.md)|Gibt an, dass der benutzerdefinierte Typ ein Steuerelement ist.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[db_column](db-column.md)|Bindet eine angegebene Spalte an das Rowset.|
|[db_command](db-command.md)|Erstellt einen OLE DB-Befehl.|
|[db_param](db-param.md)|Ordnet die angegebene Member-Variable einem Eingabe-oder Ausgabeparameter zu und begrenzt die Variable.|
|[db_source](db-source.md)|Erstellt eine Verbindung mit einer Datenquelle.|
|[db_table](db-table.md)|Öffnet eine OLE DB Tabelle.|
|[Standardwert](default-cpp.md)|Gibt an, dass die benutzerdefinierte Schnittstelle oder Disp-Schnittstelle innerhalb einer Co-Klasse die Standard-Programmierschnittstelle darstellt.|
|[defaultvtable](defaultvtable.md)|Definiert eine Schnittstelle als standardmäßige Vtable-Schnittstelle für ein Steuerelement.|
|[event_receiver](event-receiver.md)|Erstellt einen Ereignis Empfänger.|
|[event_source](event-source.md)|Erstellt eine Ereignisquelle.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[first_is](first-is.md)|Gibt den Index des ersten Array Elements an, das übertragen werden soll.|
|[hidden](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[implements_category](implements-category.md)|Gibt implementierte Komponenten Kategorien für die-Klasse an.|
|[last_is](last-is.md)|Gibt den Index des letzten Array Elements an, das übertragen werden soll.|
|[length_is](length-is.md)|Gibt die Anzahl der zu übertragenden Array Elemente an.|
|[max_is](max-is.md)|Legt den maximalen Wert für einen gültigen Array Index fest.|
|[requires_category](requires-category.md)|Gibt die erforderlichen Komponenten Kategorien der Zielklasse an.|
|[size_is](size-is.md)|Gibt die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger, Größen Zeiger auf Größen Zeiger und einzelne oder mehrdimensionale Arrays an.|
|[Quelle](source-cpp.md)|Gibt für eine Klasse die Quell Schnittstellen der COM-Objekte für Verbindungspunkte an. Gibt für eine Eigenschaft oder Methode an, dass der Member ein Objekt oder eine Variante zurückgibt, das eine Quelle von Ereignissen ist.|
|[threading](threading-cpp.md)|Gibt das Threading Modell für ein COM-Objekt an.|
|[unique](unique-cpp.md)|Gibt einen eindeutigen Zeiger an.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|
|[version](version-cpp.md)|Identifiziert eine bestimmte Version in mehreren Versionen einer Klasse.|
|[vi_progid](vi-progid.md)|Gibt eine Versions unabhängige Form der ProgID an.|

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Verwendung](attributes-by-usage.md)
