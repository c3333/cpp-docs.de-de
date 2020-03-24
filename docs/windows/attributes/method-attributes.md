---
title: Methoden Attribute (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: c9823869be96f53a3c4fbc36c7b56e1bea0a1303
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166769"
---
# <a name="method-attributes"></a>Methodenattribut

Die folgenden Attribute gelten für die Methoden in einer Klasse, Co-Klasse oder Schnittstelle.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[bindable](bindable.md)|Gibt an, dass die Eigenschaft die Datenbindung unterstützt.|
|[call_as](call-as.md)|Ermöglicht, dass eine nicht Remote fähige Funktion einer Remote Funktion zugeordnet wird.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen das Definieren eines eigenen Attributs.|
|[db_column](db-column.md)|Bindet eine angegebene Spalte an das Rowset.|
|[db_command](db-command.md)|Erstellt einen OLE DB-Befehl.|
|[db_param](db-param.md)|Ordnet die angegebene Member-Variable einem Eingabe-oder Ausgabeparameter zu und begrenzt die Variable.|
|[db_source](db-source.md)|Erstellt eine Verbindung mit einer Datenquelle.|
|[db_table](db-table.md)|Öffnet eine OLE DB Tabelle.|
|[defaultbind](defaultbind.md)|Gibt die einzelne, bindbare Eigenschaft an, die das Objekt am besten darstellt.|
|[defaultcollelem](defaultcollelem.md)|Wird zur Optimierung des Visual Basic Codes verwendet.|
|[displaybind](displaybind.md)|Gibt eine Eigenschaft an, die dem Benutzer als Bindable angezeigt werden soll.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der **Hilfe** Datei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der **Hilfe** Datei für eine Typbibliothek fest.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[helpstringcontext](helpstringcontext.md)|Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der dll an, die verwendet werden soll, um die Suche nach Dokument Zeichenfolgen (Lokalisierung) auszuführen.|
|[hidden](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[id](id.md)|Gibt eine DISPID für eine Element Funktion an (entweder eine Eigenschaft oder eine Methode in einer Schnittstelle oder einer dispinterface).|
|[immediatebind](immediatebind.md)|Gibt an, dass die Datenbank sofort über alle Änderungen an einer Eigenschaft eines Daten gebundenen Objekts benachrichtigt wird.|
|[in](in-cpp.md)|Gibt an, dass ein Parameter von der aufrufenden Prozedur an die aufgerufene Prozedur übergeben werden soll.|
|[local](local-cpp.md)|Ermöglicht es Ihnen, den Mittel l-Compiler als Header Generator zu verwenden, wenn er im Schnittstellen Header verwendet wird. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.|
|[nonbrowsable](nonbrowsable.md)|Gibt an, dass ein Schnittstellenmember nicht in einem Eigenschaften Browser angezeigt werden soll.|
|[propget](propget.md)|Gibt eine eigenschaftenaccessorfunktion an.|
|[propput](propput.md)|Gibt eine Eigenschafts Einstellungs Funktion an.|
|[propputref](propputref.md)|Gibt eine Eigenschafts Einstellungs Funktion an, die einen Verweis anstelle eines Werts verwendet.|
|[ptr](ptr.md)|Legt einen Zeiger als vollständigen Zeiger fest.|
|[range](range-cpp.md)|Gibt einen Bereich zulässiger Werte für Argumente oder Felder an, deren Werte zur Laufzeit festgelegt werden.|
|[requestedit](requestedit.md)|Gibt an, dass die Eigenschaft die `OnRequestEdit`-Benachrichtigung unterstützt.|
|[restricted](restricted.md)|Gibt an, dass ein Member eines Moduls, einer Schnittstelle oder einer dispinterface nicht willkürlich aufgerufen werden kann.|
|[satype](satype.md)|Gibt den Datentyp der `SAFEARRAY` Struktur an.|
|[Quelle](source-cpp.md)|Gibt die Quell Schnittstellen des Steuer Elements für Verbindungspunkte in einer Klasse an. Bei einer Eigenschaft oder Methode gibt das `source` Attribut an, dass der Member ein Objekt oder eine Variante zurückgibt, das eine Quelle von Ereignissen ist.|
|[synchronize](synchronize.md)|Synchronisiert den Zugriff auf die Ziel Methode.|
|[vararg](vararg.md)|Gibt an, dass die Funktion eine Variable Anzahl von Argumenten akzeptiert.|

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Verwendung](attributes-by-usage.md)
