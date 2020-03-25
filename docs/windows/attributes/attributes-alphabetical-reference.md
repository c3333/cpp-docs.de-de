---
title: Alphabetische Attributreferenz
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: dbbb406765c0664f2cd332524a61713f9c67cf9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167510"
---
# <a name="attributes-alphabetical-reference"></a>Alphabetische Attributreferenz

Die folgenden Attribute sind im Microsoft C++ -Compiler verfügbar:

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[Aggregierbar](aggregatable.md)|Gibt an, dass ein Steuerelement von einem anderen Steuerelement aggregiert werden kann.|
|[Aggregate](aggregates.md)|Gibt an, dass ein Steuerelement die Zielklasse aggregiert.|
|[appobject](appobject.md)|Identifiziert die Co-Klasse als Anwendungs Objekt, das einer vollständigen exe-Anwendung zugeordnet ist, und gibt an, dass die Funktionen und Eigenschaften der Co-Klasse in dieser Typbibliothek global verfügbar sind.|
|[async_uuid](async-uuid.md)|Gibt die UUID an, die den mittlerer l-Compiler anweist, sowohl synchrone als auch asynchrone Versionen einer COM-Schnittstelle zu definieren.|
|[attribute](attribute.md)|Ermöglicht es Ihnen, ein benutzerdefiniertes Attribut zu erstellen.|
|[bindable](bindable.md)|Gibt an, dass die Eigenschaft die Datenbindung unterstützt.|
|[call_as](call-as.md)|Ermöglicht, dass eine nicht Remote fähige Funktion einer Remote Funktion zugeordnet wird.|
|[case](case-cpp.md)|Wird mit dem [Switch_type](switch-type.md) -Attribut in einer Union verwendet.|
|[coclass](coclass.md)|Erstellt ein COM-Objekt, das eine COM-Schnittstelle implementieren kann.|
|[com_interface_entry](com-interface-entry-cpp.md)|Fügt einer COM-Zuordnung einen Schnittstellen Eintrag hinzu.|
|[Steuerelement](control.md)|Gibt an, dass der benutzerdefinierte Typ ein Steuerelement ist.|
|[cpp_quote](cpp-quote.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten Header Datei aus.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen, eigene Attribute zu definieren.|
|[db_accessor](db-accessor.md)|Bindet Spalten in einem Rowset und bindet diese an die entsprechenden accessorzuordnungen.|
|[db_column](db-column.md)|Bindet eine angegebene Spalte an das Rowset.|
|[db_command](db-command.md)|Führt einen OLE DB-Befehl aus.|
|[db_param](db-param.md)|Ordnet die angegebene Member-Variable einem Eingabe-oder Ausgabeparameter zu.|
|[db_source](db-source.md)|Erstellt und kapselt eine Verbindung über einen Anbieter in eine Datenquelle.|
|[db_table](db-table.md)|Öffnet eine OLE DB Tabelle.|
|[Standardwert](default-cpp.md)|Gibt an, dass die benutzerdefinierte Schnittstelle oder Disp-Schnittstelle innerhalb einer Co-Klasse die Standard-Programmierschnittstelle darstellt.|
|[defaultbind](defaultbind.md)|Gibt die einzelne, bindbare Eigenschaft an, die das Objekt am besten darstellt.|
|[defaultcollelem](defaultcollelem.md)|Wird zur Optimierung des Visual Basic Codes verwendet.|
|[defaultvalue](defaultvalue.md)|Ermöglicht die Angabe eines Standardwerts für einen eingegebenen optionalen Parameter.|
|[defaultvtable](defaultvtable.md)|Definiert eine Schnittstelle als standardmäßige Vtable-Schnittstelle für ein Steuerelement.|
|[dispinterface](dispinterface.md)|Fügt eine Schnittstelle in die IDL-Datei als Verteilschnittstelle ein.|
|[displaybind](displaybind.md)|Gibt eine Eigenschaft an, die dem Benutzer als Bindable angezeigt werden soll.|
|[dual](dual.md)|Fügt eine Schnittstelle in die IDL-Datei als duale Schnittstelle ein.|
|[emitidl](emitidl.md)|Bestimmt, ob alle nachfolgenden IDL-Attribute verarbeitet und in der generierten IDL-Datei abgelegt werden.|
|[entry](entry.md)|Gibt eine exportierte Funktion oder Konstante in einem Modul an, indem der Einstiegspunkt in der DLL identifiziert wird.|
|[event_receiver](event-receiver.md)|Erstellt einen Ereignis Empfänger.|
|[event_source](event-source.md)|Erstellt eine Ereignisquelle.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[first_is](first-is.md)|Gibt den Index des ersten Array Elements an, das übertragen werden soll.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der Hilfedatei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstring](helpstring.md)|Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der dll an, die verwendet werden soll, um die Suche nach Dokument Zeichenfolgen (Lokalisierung) auszuführen.|
|[hidden](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[id](id.md)|Gibt eine DISPID für eine Element Funktion an (entweder eine Eigenschaft oder eine Methode in einer Schnittstelle oder einer dispinterface).|
|[idl_module](idl-module.md)|Gibt einen Einstiegspunkt in einer DLL an.|
|[idl_quote](idl-quote.md)|Ermöglicht das Verwenden von Attributen oder IDL-Konstrukten, die in der aktuellen Version von Visual C++nicht unterstützt werden.|
|[iid_is](iid-is.md)|Gibt die IID der COM-Schnittstelle an, auf die durch einen Schnittstellen Zeiger gezeigt wird.|
|[immediatebind](immediatebind.md)|Gibt an, dass die Datenbank sofort über alle Änderungen an einer Eigenschaft eines Daten gebundenen Objekts benachrichtigt wird.|
|[implements](implements-cpp.md)|Gibt Dispatch-Schnittstellen an, die als Member der IDL-Co-Klasse erzwungen werden.|
|[implements_category](implements-category.md)|Gibt implementierte Komponenten Kategorien für die-Klasse an.|
|[import](import.md)|Gibt eine andere IDL-, ODL-oder Header Datei an, die Definitionen enthält, auf die Sie aus der IDL-Hauptdatei verweisen möchten.|
|[importidl](importidl.md)|Fügt die angegebene IDL-Datei in die generierte IDL-Datei ein.|
|[importlib](importlib.md)|Stellt Typen, die bereits in einer anderen Typbibliothek kompiliert wurden, der erstellten Typbibliothek zur Verfügung.|
|[in](in-cpp.md)|Gibt an, dass ein Parameter von der aufrufenden Prozedur an die aufgerufene Prozedur übergeben werden soll.|
|[include](include-cpp.md)|Gibt eine oder mehrere Header Dateien an, die in die generierte IDL-Datei eingeschlossen werden sollen.|
|[includelib](includelib-cpp.md)|Bewirkt, dass eine IDL-oder h-Datei in der generierten IDL-Datei enthalten ist.|
|[last_is](last-is.md)|Gibt den Index des letzten Array Elements an, das übertragen werden soll.|
|[lcid](lcid.md)|Ermöglicht es Ihnen, einen Gebiets Schema Bezeichner an eine Funktion zu übergeben.|
|[length_is](length-is.md)|Gibt die Anzahl der zu übertragenden Array Elemente an.|
|[library_block](library-block.md)|Platziert ein Konstrukt innerhalb des Bibliotheks Blocks der IDL-Datei.|
|[licensed](licensed.md)|Gibt an, dass die Co-Klasse, auf die Sie angewendet wird, lizenziert ist und mit `IClassFactory2`instanziiert werden muss.|
|[local](local-cpp.md)|Ermöglicht es Ihnen, den Mittel l-Compiler als Header Generator zu verwenden, wenn er im Schnittstellen Header verwendet wird. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.|
|[max_is](max-is.md)|Legt den maximalen Wert für einen gültigen Array Index fest.|
|[module](module-cpp.md)|Definiert den Bibliotheksblock in der IDL-Datei.|
|[ms_union](ms-union.md)|Steuert die Ausrichtung der Netzwerkdaten Darstellung von nicht gekapselten Unions.|
|[no_injected_text](no-injected-text.md)|Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.|
|[nonbrowsable](nonbrowsable.md)|Gibt an, dass ein Schnittstellenmember nicht in einem Eigenschaften Browser angezeigt werden soll.|
|[noncreatable](noncreatable.md)|Definiert ein Objekt, das nicht allein instanziiert werden kann.|
|[nonextensible](nonextensible.md)|Gibt an, dass die `IDispatch` Implementierung nur die Eigenschaften und Methoden enthält, die in der Schnittstellen Beschreibung aufgeführt sind, und kann zur Laufzeit nicht mit zusätzlichen Elementen erweitert werden.|
|[object](object-cpp.md)|Identifiziert eine benutzerdefinierte Schnittstelle. Synonym mit benutzerdefiniertem Attribut.|
|[odl](odl.md)|Identifiziert eine Schnittstelle als Object Description Language (ODL)-Schnittstelle.|
|[oleautomation](oleautomation.md)|Gibt an, dass eine Schnittstelle mit Automation kompatibel ist.|
|[optional](optional-cpp.md)|Gibt einen optionalen Parameter für eine Member-Funktion an.|
|[out](out-cpp.md)|Gibt die Zeigerparameter an, die von der aufgerufenen Prozedur an die aufrufende Prozedur zurückgegeben werden (vom Server an den Client).|
|[pointer_default](pointer-default.md)|Gibt das Standard Zeiger Attribut für alle Zeiger außer auf der obersten Ebene an, die in Parameterlisten angezeigt werden.|
|[pragma](pragma.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten IDL-Datei aus.|
|[progid](progid.md)|Gibt die ProgID für ein COM-Objekt an.|
|[propget](propget.md)|Gibt eine Eigenschaften Accessor (Get)-Funktion an.|
|[propput](propput.md)|Gibt eine Eigenschaftseinstellungsfunktion an.|
|[propputref](propputref.md)|Gibt eine Eigenschafts Einstellungs Funktion an, die einen Verweis anstelle eines Werts verwendet.|
|[ptr](ptr.md)|Legt einen Zeiger als vollständigen Zeiger fest.|
|[öffentlich](public-cpp-attributes.md)|Stellt sicher, dass eine typedef in die Typbibliothek wechselt, auch wenn in der IDL-Datei nicht auf Sie verwiesen wird.|
|[range](range-cpp.md)|Gibt einen Bereich zulässiger Werte für Argumente oder Felder an, deren Werte zur Laufzeit festgelegt werden.|
|[rdx](rdx.md)|Erstellt oder ändert einen Registrierungsschlüssel.|
|[readonly](readonly-cpp.md)|Untersagt die Zuweisung zu einer Variablen.|
|[ref](ref-cpp.md)|Bezeichnet einen Verweis Zeiger.|
|[registration_script](registration-script.md)|Führt das angegebene Registrierungs Skript aus.|
|[requestedit](requestedit.md)|Gibt an, dass die Eigenschaft die `OnRequestEdit`-Benachrichtigung unterstützt.|
|[requires_category](requires-category.md)|Gibt erforderliche Komponenten Kategorien für die Klasse an.|
|[restricted](restricted.md)|Gibt an, dass eine Bibliothek oder ein Member eines Moduls, einer Schnittstelle oder einer dispinterface nicht willkürlich aufgerufen werden kann.|
|[retval](retval.md)|Gibt den Parameter an, der den Rückgabewert des Members empfängt.|
|[satype](satype.md)|Gibt den Datentyp des `SAFEARRAY`an.|
|[size_is](size-is.md)|Gibt die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger, Größen Zeiger auf Größen Zeiger und einzelne oder mehrdimensionale Arrays an.|
|[Quelle](source-cpp.md)|Gibt an, dass ein Member einer Klasse, Eigenschaft oder Methode eine Quelle von Ereignissen ist.|
|[string](string-cpp.md)|Gibt an, dass das eindimensionale **char**-, **wchar_t**-, `byte`-oder äquivalente Array oder der Zeiger auf ein solches Array als Zeichenfolge behandelt werden muss.|
|[support_error_info](support-error-info.md)|Unterstützt die Fehlerberichterstattung für das Zielobjekt.|
|[switch_is](switch-is.md)|Gibt den Ausdruck oder den Bezeichner an, der als uniondiskriminant fungiert, der das Unionmember auswählt.|
|[switch_type](switch-type.md)|Identifiziert den Typ der Variablen, die als uniondiskriminant verwendet wird.|
|[synchronize](synchronize.md)|Synchronisiert den Zugriff auf eine Methode.|
|[threading](threading-cpp.md)|Gibt das Threading Modell für ein COM-Objekt an.|
|[transmit_as](transmit-as.md)|Weist den Compiler an, einen dargestellten Typ, der Client-und Server Anwendungen bearbeitet, mit einem übertragenen Typ zuzuordnen.|
|[uidefault](uidefault.md)|Gibt an, dass der Typinformationsmember der Standard Member für die Anzeige in der Benutzeroberfläche ist.|
|[unique](unique-cpp.md)|Gibt einen eindeutigen Zeiger an.|
|[usesgetlasterror](usesgetlasterror.md)|Weist den Aufrufer an, dass der Aufrufer bei einem Fehler beim Aufrufen dieser Funktion `GetLastError` aufrufen kann, um den Fehlercode abzurufen.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|
|[v1_enum](v1-enum.md)|Weist an, dass der angegebene enumerierte Typ als 32-Bit-Entität und nicht als 16-Bit-Standardwert übertragen wird.|
|[vararg](vararg.md)|Gibt an, dass die Funktion eine Variable Anzahl von Argumenten akzeptiert.|
|[version](version-cpp.md)|Identifiziert eine bestimmte Version in mehreren Versionen einer Schnittstelle oder Klasse.|
|[vi_progid](vi-progid.md)|Gibt eine Versions unabhängige Form der ProgID an.|
|[wire_marshal](wire-marshal.md)|Gibt einen Datentyp an, der anstelle eines anwendungsspezifischen Datentyps für die Übertragung verwendet wird.|

## <a name="see-also"></a>Weitere Informationen

[C++-Attribute für COM und .NET](cpp-attributes-com-net.md)<br/>
[Attribute nach Gruppen](attributes-by-group.md)<br/>
[Attribute nach Verwendung](attributes-by-usage.md)
