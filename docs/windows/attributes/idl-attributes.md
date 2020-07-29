---
title: IDL-Attribute (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 8cceae2f1c4880b72f1ffc30070d6aa6bf8e3a51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211969"
---
# <a name="idl-attributes"></a>IDL-Attribute

Normalerweise bedeutete die Verwaltung einer IDL-Datei Folgendes:

- Machen Sie sich mit der Struktur und Syntax einer IDL-Datei vertraut, um Sie ändern zu können.

- Verlassen Sie sich auf einen Assistenten, mit dem Sie einige Aspekte der IDL-Datei ändern können.

Nun können Sie die IDL-Datei in einer Quell Code Datei mithilfe Visual C++ IDL-Attribute ändern. In vielen Fällen haben Visual C++ IDL-Attribute denselben Namen wie die Mittel l-Attribute. Wenn der Name eines Visual C++ IDL-Attributs und eines Mittelwert Attributs identisch sind, bedeutet dies, dass das Visual C++ Attribut in der Quell Code Datei mit einer IDL-Datei versehen wird, die sein Namespace-Attribut für die mittlere Sprache enthält. Allerdings bietet ein Visual C++ IDL-Attribut möglicherweise nicht die gesamte Funktionalität eines Mittel l-Attributs.

Wenn Sie nicht mit [com-Attributen](com-attributes.md)verwendet werden, können Sie mithilfe von IDL-Attributen Schnittstellen definieren. Beim Kompilieren des Quellcodes werden die Attribute zum Definieren der generierten IDL-Datei verwendet. Bei Verwendung mit COM-Attributen in einem ATL-Projekt bewirken einige IDL-Attribute, wie z `coclass` . b., dass Code in das Projekt eingefügt wird.

Beachten Sie, dass [Idl_quote](idl-quote.md) die Verwendung von mittlerer l-Konstrukten ermöglicht, die in der aktuellen Version von Visual C++ nicht unterstützt werden. Diese und andere Attribute, wie z. b. [importlib](importlib.md) und [Includelib](includelib-cpp.md) , unterstützen Sie dabei, vorhandene IDL-Dateien in Ihrem aktuellen Visual Studio C++-Projekt zu verwenden.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Gibt an, dass ein Steuerelement von einem anderen Steuerelement aggregiert werden kann.|
|[appobject](appobject.md)|Identifiziert die Co-Klasse als Anwendungs Objekt, das einer vollständigen exe-Anwendung zugeordnet ist, und gibt an, dass die Funktionen und Eigenschaften der Co-Klasse in dieser Typbibliothek global verfügbar sind.|
|[async_uuid](async-uuid.md)|Gibt die UUID an, die den mittlerer l-Compiler anweist, sowohl synchrone als auch asynchrone Versionen einer COM-Schnittstelle zu definieren.|
|[bindable](bindable.md)|Gibt an, dass die Eigenschaft die Datenbindung unterstützt.|
|[call_as](call-as.md)|Ermöglicht, dass eine nicht Remote fähige Funktion einer Remote Funktion zugeordnet wird.|
|[case](case-cpp.md)|Wird mit dem [Switch_type](switch-type.md) -Attribut in einer Union verwendet.|
|[coclass](coclass.md)|Platziert die Klassendefinition als Co-Klasse in eine IDL-Datei.|
|[control](control.md)|Gibt an, dass der benutzerdefinierte Typ ein Steuerelement ist.|
|[cpp_quote](cpp-quote.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten Header Datei aus.|
|[defaultbind](defaultbind.md)|Gibt die einzelne, bindbare Eigenschaft an, die das Objekt am besten darstellt.|
|[defaultcollelem](defaultcollelem.md)|Wird zur Optimierung des Visual Basic Codes verwendet.|
|[DefaultValue](defaultvalue.md)|Ermöglicht die Angabe eines Standardwerts für einen eingegebenen optionalen Parameter.|
|[default](default-cpp.md)|Gibt an, dass die benutzerdefinierte Schnittstelle oder Disp-Schnittstelle innerhalb einer Co-Klasse die Standard-Programmierschnittstelle darstellt.|
|[defaultvtable](defaultvtable.md)|Definiert eine Schnittstelle als standardmäßige Vtable-Schnittstelle für ein Steuerelement.|
|[dispinterface](dispinterface.md)|Fügt eine Schnittstelle in die IDL-Datei als Verteilschnittstelle ein.|
|[displaybind](displaybind.md)|Gibt eine Eigenschaft an, die dem Benutzer als Bindable angezeigt werden soll.|
|[dual](dual.md)|Fügt eine Schnittstelle in die IDL-Datei als duale Schnittstelle ein.|
|[ein](entry.md)|Gibt eine exportierte Funktion oder Konstante in einem Modul an, indem der Einstiegspunkt in der DLL identifiziert wird.|
|[first_is](first-is.md)|Gibt den Index des ersten Array Elements an, das übertragen werden soll.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der Hilfedatei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstringcontext](helpstringcontext.md)|Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der dll an, die verwendet werden soll, um die Suche nach Dokument Zeichenfolgen (Lokalisierung) auszuführen.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[verbirgt](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[idl_module](idl-module.md)|Gibt einen Einstiegspunkt in einer DLL an.|
|[idl_quote](idl-quote.md)|Ermöglicht das Verwenden von Attributen oder IDL-Konstrukten, die in der aktuellen Version von Visual C++ nicht unterstützt werden.|
|[id](id.md)|Gibt eine DISPID für eine Element Funktion an (entweder eine Eigenschaft oder eine Methode in einer Schnittstelle oder einer dispinterface).|
|[iid_is](iid-is.md)|Gibt die IID der COM-Schnittstelle an, auf die durch einen Schnittstellen Zeiger gezeigt wird.|
|[immediatebind](immediatebind.md)|Gibt an, dass die Datenbank sofort über alle Änderungen an einer Eigenschaft eines Daten gebundenen Objekts benachrichtigt wird.|
|[importlib](importlib.md)|Stellt Typen, die bereits in einer anderen Typbibliothek kompiliert wurden, der erstellten Typbibliothek zur Verfügung.|
|[import](import.md)|Gibt eine andere IDL-, ODL-oder Header Datei an, die Definitionen enthält, auf die Sie aus der IDL-Hauptdatei verweisen möchten.|
|[darunter](include-cpp.md)|Gibt eine oder mehrere Header Dateien an, die in die generierte IDL-Datei eingeschlossen werden sollen.|
|[Includelib](includelib-cpp.md)|Bewirkt, dass eine IDL-oder h-Datei in der generierten IDL-Datei enthalten ist.|
|[in](in-cpp.md)|Gibt an, dass ein Parameter von der aufrufenden Prozedur an die aufgerufene Prozedur übergeben werden soll.|
|[last_is](last-is.md)|Gibt den Index des letzten Array Elements an, das übertragen werden soll.|
|[lcid](lcid.md)|Ermöglicht es Ihnen, einen Gebiets Schema Bezeichner an eine Funktion zu übergeben.|
|[length_is](length-is.md)|Gibt die Anzahl der zu übertragenden Array Elemente an.|
|[licensed](licensed.md)|Gibt an, dass die Co-Klasse, auf die Sie angewendet wird, lizenziert ist und mithilfe von instanziiert werden muss `IClassFactory2` .|
|[nah](local-cpp.md)|Ermöglicht es Ihnen, den Mittel l-Compiler als Header Generator zu verwenden, wenn er im Schnittstellen Header verwendet wird. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.|
|[max_is](max-is.md)|Legt den maximalen Wert für einen gültigen Array Index fest.|
|[Mond](module-cpp.md)|Definiert den Bibliotheksblock in der IDL-Datei.|
|[ms_union](ms-union.md)|Steuert die Ausrichtung der Netzwerkdaten Darstellung von nicht gekapselten Unions.|
|[no_injected_text](no-injected-text.md)|Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.|
|[nonbrowsable](nonbrowsable.md)|Gibt an, dass ein Schnittstellenmember nicht in einem Eigenschaften Browser angezeigt werden soll.|
|[noncreatable](noncreatable.md)|Definiert ein Objekt, das nicht allein instanziiert werden kann.|
|[nonextensible](nonextensible.md)|Gibt an, dass die `IDispatch` Implementierung nur die Eigenschaften und Methoden enthält, die in der Schnittstellen Beschreibung aufgeführt sind, und kann zur Laufzeit nicht mit zusätzlichen Membern erweitert werden.|
|[object](object-cpp.md)|Identifiziert eine benutzerdefinierte Schnittstelle. Synonym mit benutzerdefiniertem Attribut.|
|[odl](odl.md)|Identifiziert eine Schnittstelle als Object Description Language (ODL)-Schnittstelle.|
|[oleautomation](oleautomation.md)|Gibt an, dass eine Schnittstelle mit Automation kompatibel ist.|
|[optionale](optional-cpp.md)|Gibt einen optionalen Parameter für eine Member-Funktion an.|
|[out](out-cpp.md)|Gibt die Zeigerparameter an, die von der aufgerufenen Prozedur an die aufrufende Prozedur zurückgegeben werden (vom Server an den Client).|
|[pointer_default](pointer-default.md)|Gibt das Standard Zeiger Attribut für alle Zeiger außer auf der obersten Ebene an, die in Parameterlisten angezeigt werden.|
|[pragma](pragma.md)|Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten IDL-Datei aus.|
|[ProgID](progid.md)|Gibt die ProgID für ein COM-Objekt an.|
|[propget](propget.md)|Gibt eine Eigenschaften Accessor (Get)-Funktion an.|
|[propputref](propputref.md)|Gibt eine Eigenschafts Einstellungs Funktion an, die einen Verweis anstelle eines Werts verwendet.|
|[propput](propput.md)|Gibt eine Eigenschaftseinstellungsfunktion an.|
|[ptr](ptr.md)|Legt einen Zeiger als vollständigen Zeiger fest.|
|[öffentlich](public-cpp-attributes.md)|Stellt sicher, dass eine typedef in die Typbibliothek wechselt, auch wenn in der IDL-Datei nicht auf Sie verwiesen wird.|
|[range](range-cpp.md)|Gibt einen Bereich zulässiger Werte für Argumente oder Felder an, deren Werte zur Laufzeit festgelegt werden.|
|[readonly](readonly-cpp.md)|Untersagt die Zuweisung zu einer Variablen.|
|[ref](ref-cpp.md)|Bezeichnet einen Verweis Zeiger.|
|[requestedit](requestedit.md)|Gibt an, dass die Eigenschaft die `OnRequestEdit`-Benachrichtigung unterstützt.|
|[begrenz](restricted.md)|Gibt an, dass eine Bibliothek oder ein Member eines Moduls, einer Schnittstelle oder einer dispinterface nicht willkürlich aufgerufen werden kann.|
|[retval](retval.md)|Gibt den Parameter an, der den Rückgabewert des Members empfängt.|
|[size_is](size-is.md)|Gibt die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger, Größen Zeiger auf Größen Zeiger und einzelne oder mehrdimensionale Arrays an.|
|[source](source-cpp.md)|Gibt an, dass ein Member einer Klasse, Eigenschaft oder Methode eine Quelle von Ereignissen ist.|
|[string](string-cpp.md)|Gibt an, dass das eindimensionale **`char`** , **`wchar_t`** , `byte` oder äquivalente Array oder der Zeiger auf ein solches Array als Zeichenfolge behandelt werden muss.|
|[switch_is](switch-is.md)|Gibt den Ausdruck oder den Bezeichner an, der als uniondiskriminant fungiert, der das Unionmember auswählt.|
|[switch_type](switch-type.md)|Identifiziert den Typ der Variablen, die als uniondiskriminant verwendet wird.|
|[transmit_as](transmit-as.md)|Weist den Compiler an, einen dargestellten Typ, der Client-und Server Anwendungen bearbeitet, mit einem übertragenen Typ zuzuordnen.|
|[uidefault](uidefault.md)|Gibt an, dass der Typinformationsmember der Standard Member für die Anzeige in der Benutzeroberfläche ist.|
|[unique](unique-cpp.md)|Gibt einen eindeutigen Zeiger an.|
|[usesgetlasterror](usesgetlasterror.md)|Teilt dem Aufrufer mit, dass der Aufrufer beim Aufrufen dieser Funktion aufrufen kann, `GetLastError` um den Fehlercode abzurufen.|
|[uuid](uuid-cpp-attributes.md)|Gibt die eindeutige ID für eine Klasse oder Schnittstelle an.|
|[v1_enum](v1-enum.md)|Weist an, dass der angegebene enumerierte Typ als 32-Bit-Entität und nicht als 16-Bit-Standardwert übertragen wird.|
|[vararg](vararg.md)|Gibt an, dass die Funktion eine Variable Anzahl von Argumenten akzeptiert.|
|[vi_progid](vi-progid.md)|Gibt eine Versions unabhängige Form der ProgID an.|
|[wire_marshal](wire-marshal.md)|Gibt einen Datentyp an, der anstelle eines anwendungsspezifischen Datentyps für die Übertragung verwendet wird.|

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Gruppe](attributes-by-group.md)
