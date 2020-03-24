---
title: Klassenattribute (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: 5e10b7831e59211b73ce947ac21e43bc1a8af1c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167315"
---
# <a name="class-attributes"></a>Klassenattribute

Die folgenden Attribute gelten für das [Class](../../cpp/class-cpp.md) C++ -Schlüsselwort.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[Aggregierbar](aggregatable.md)|Gibt an, dass die Klasse Aggregationen unterstützt.|
|[Aggregate](aggregates.md)|Gibt an, dass ein Steuerelement die Zielklasse aggregiert.|
|[appobject](appobject.md)|Identifiziert die Co-Klasse als Anwendungs Objekt, das einer Full. exe-Anwendung zugeordnet ist, und gibt an, dass die Funktionen und Eigenschaften der Co-Klasse in dieser Typbibliothek global verfügbar sind.|
|[case](case-cpp.md)|Wird mit dem [Switch_type](switch-type.md) -Attribut in einer Union verwendet.|
|[coclass](coclass.md)|Erstellt ein ActiveX-Steuerelement.|
|[com_interface_entry](com-interface-entry-cpp.md)|Fügt einer COM-Zuordnung einen Schnittstellen Eintrag hinzu.|
|[Steuerelement](control.md)|Gibt an, dass der benutzerdefinierte Typ ein Steuerelement ist.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[db_command](db-command.md)|Erstellt einen OLE DB-Befehl.|
|[db_param](db-param.md)|Ordnet die angegebene Member-Variable einem Eingabe-oder Ausgabeparameter zu und begrenzt die Variable.|
|[db_source](db-source.md)|Erstellt eine Verbindung mit einer Datenquelle.|
|[db_table](db-table.md)|Öffnet eine OLE DB Tabelle.|
|[Standardwert](default-cpp.md)|Gibt an, dass die benutzerdefinierte Schnittstelle oder Disp-Schnittstelle innerhalb einer Co-Klasse die Standard-Programmierschnittstelle darstellt.|
|[defaultvtable](defaultvtable.md)|Definiert eine Schnittstelle als standardmäßige Vtable-Schnittstelle für ein Steuerelement.|
|[event_receiver](event-receiver.md)|Erstellt einen Ereignis Empfänger.|
|[event_source](event-source.md)|Erstellt eine Ereignisquelle.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der **Hilfe** Datei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstringcontext](helpstringcontext.md)|Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[hidden](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[implements](implements-cpp.md)|Gibt Dispatch-Schnittstellen an, die als Member der IDL-Co-Klasse erzwungen werden.|
|[implements_category](implements-category.md)|Gibt implementierte Komponenten Kategorien für die-Klasse an.|
|[module](module-cpp.md)|Definiert den Bibliotheksblock in der IDL-Datei.|
|[noncreatable](noncreatable.md)|Definiert ein Objekt, das nicht allein instanziiert werden kann.|
|[progid](progid.md)|Definiert die ProgID für ein Steuerelement.|
|[registration_script](registration-script.md)|Führt das angegebene Registrierungs Skript aus.|
|[requestedit](requestedit.md)|Gibt an, dass die Eigenschaft die `OnRequestEdit`-Benachrichtigung unterstützt.|
|[Quelle](source-cpp.md)|Gibt die Quell Schnittstellen des Steuer Elements für Verbindungspunkte in einer Klasse an. Bei einer Eigenschaft oder Methode gibt das `source` Attribut an, dass das Element ein Objekt zurückgibt, oder `VARIANT`, das eine Quelle von Ereignissen ist.|
|[support_error_info](support-error-info.md)|Unterstützt die Fehlerberichterstattung für das Zielobjekt.|
|[threading](threading-cpp.md)|Gibt das Threading Modell für ein Steuerelement an.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|
|[version](version-cpp.md)|Identifiziert eine bestimmte Version in mehreren Versionen einer Klasse.|
|[vi_progid](vi-progid.md)|Gibt eine Versions unabhängige Form der ProgID an.|

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Verwendung](attributes-by-usage.md)
