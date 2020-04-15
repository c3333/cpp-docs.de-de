---
title: Attribute nach Verwendung
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361334"
---
# <a name="attributes-by-usage"></a>Attribute nach Verwendung

In diesem Thema werden Attribute gemäß den C++-Sprachelementen aufgeführt, auf die sie angewendet werden.

Wenn ein Attribut einem Element vorangeht, das sich nicht im Bereich des Attributs befindet, wird der Attributblock als Kommentar behandelt.

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|[Modulattribute](module-attributes.md)|Gilt für das [Modulattribut.](module-cpp.md)|
|[Schnittstellenattribut](interface-attributes.md)|Gilt für das [__interface](../../cpp/interface.md) C++-Schlüsselwort.|
|[Klassenattribute](class-attributes.md)|Gilt für das C++-Schlüsselwort.|
|[Methodenattribute](method-attributes.md)|Gilt für die Methoden in einer Klasse, Coclass oder Schnittstelle.|
|[Parameterattribute](parameter-attributes.md)|Gilt für Parameter einer Methode in einer Klasse oder Schnittstelle.|
|[Datenmemberattribute](data-member-attributes.md)|Gilt für die Datenmember in einer Klasse, Coclass oder Schnittstelle.|
|[Typedef-, Enum-, Union- und Strukturattribute](typedef-enum-union-and-struct-attributes.md)|Gilt für die C++-Schlüsselwörter.|
|[Arrayattribute](array-attributes.md)|Gilt für Arrays oder `SAFEARRAY`s.|
|[Eigenständige Attribute](stand-alone-attributes.md)|Funktioniert eher wie eine Codezeile, funktioniert jedoch nicht mit einem C++-Schlüsselwort. Eigenständige Attributanweisungen erfordern ein Semikolon am Ende der Zeile.|
|[Benutzerdefinierte Attribute](custom-attributes-cpp.md)|Ermöglicht dem Benutzer das Erweitern von Metadaten.|

## <a name="module-attributes"></a>Modulattribute

Das folgende Attribut kann nur auf das [Modulattribut](module-cpp.md) angewendet werden.

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der DLL an, die zum Ausführen der Dokumentzeichenfolgensuche (Lokalisierung) verwendet werden soll.|

## <a name="interface-attributes"></a>Schnittstellenattribut

Die folgenden Attribute gelten für das [C++-Schlüsselwort der Schnittstelle (oder __interface).](../../cpp/interface.md)

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Gibt die UUID an, die den MIDL-Compiler anweist, sowohl synchrone als auch asynchrone Versionen einer COM-Schnittstelle zu definieren.|
|[Benutzerdefinierte](custom-cpp.md)|Hier können Sie eigene Attribute definieren.|
|[Dispatchschnittstelle](dispinterface.md)|Fügt eine Schnittstelle in die IDL-Datei als Verteilschnittstelle ein.|
|[Dual](dual.md)|Platziert eine Schnittstelle in der .idl-Datei als duale Schnittstelle.|
|[Exportieren](export.md)|Bewirkt, dass eine Datenstruktur in der .idl-Datei platziert wird.|
|[Helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzer Informationen zu diesem Element in der Hilfedatei anzeigen kann.|
|[Helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[helpstringcontext](helpstringcontext.md)|Gibt die ID eines Hilfethemas in einer .hlp- oder .chm-Datei an.|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der DLL an, die zum Ausführen der Dokumentzeichenfolgensuche (Lokalisierung) verwendet werden soll.|
|[Versteckte](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[library_block](library-block.md)|Platziert ein Konstrukt innerhalb des Bibliotheksblocks der .idl-Datei.|
|[local](local-cpp.md)|Ermöglicht die Verwendung des MIDL-Compilers als Headergenerator, wenn er im Schnittstellenheader verwendet wird. Bei Verwendung in einer einzelnen Funktion wird eine lokale Prozedur bezeichnet, für die keine Stubs generiert werden.|
|[nonextensible](nonextensible.md)|Gibt an, `IDispatch` dass die Implementierung nur die eigenschaften und methoden enthält, die in der Schnittstellenbeschreibung aufgeführt sind, und kann zur Laufzeit nicht mit zusätzlichen Membern erweitert werden. Dieses Attribut ist nur auf einer [dualen](dual.md) Schnittstelle gültig.|
|[Odl](odl.md)|Identifiziert eine Schnittstelle als ODL-Schnittstelle (Object Description Language).|
|[Objekt](object-cpp.md)|Identifiziert eine benutzerdefinierte Schnittstelle.|
|[oleautomation](oleautomation.md)|Gibt an, dass eine Schnittstelle mit Automation kompatibel ist.|
|[pointer_default](pointer-default.md)|Gibt das Standardzeigerattribut für alle Zeiger mit Ausnahme von Zeigern der obersten Ebene an, die in Parameterlisten angezeigt werden.|
|[Ptr](ptr.md)|Bezeichnet einen Zeiger als vollständigen Zeiger.|
|[Beschränkt](restricted.md)|Legt fest, welche Mitglieder der Bibliothek nicht willkürlich aufgerufen werden können.|
|[uuid](uuid-cpp-attributes.md)|Stellt die eindeutige ID für die Bibliothek bereit|

Sie müssen diese Regeln beachten, um eine Schnittstelle zu definieren:

- Die Standardaufrufkonvention ist [__stdcall](../../cpp/stdcall.md).

- Eine GUID wird für Sie bereitgestellt, wenn Sie keine bereitstellen.

- Es sind keine überladenen Methoden zulässig.

Wenn Sie das [uuid-Attribut](uuid-cpp-attributes.md) nicht angeben und denselben Schnittstellennamen in verschiedenen Attributprojekten verwenden, wird dieselbe GUID generiert.

## <a name="see-also"></a>Siehe auch

[C++-Attribute für COM und .NET](cpp-attributes-com-net.md)<br/>
[Attribute nach Gruppe](attributes-by-group.md)<br/>
[Attribute Alphabetische Referenz](attributes-alphabetical-reference.md)
