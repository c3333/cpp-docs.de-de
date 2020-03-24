---
title: Schnittstellen Attribute (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 81a88ddfd74f20fa57ef615c988ba9786f41c1ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214824"
---
# <a name="interface-attributes"></a>Schnittstellenattribut

Die folgenden Attribute gelten für das-Schlüsselwort der- [Schnittstelle (oder __interface)](../../cpp/interface.md) C++ .

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Gibt die UUID an, die den mittlerer l-Compiler anweist, sowohl synchrone als auch asynchrone Versionen einer COM-Schnittstelle zu definieren.|
|[custom](custom-cpp.md)|Ermöglicht Ihnen, eigene Attribute zu definieren.|
|[dispinterface](dispinterface.md)|Fügt eine Schnittstelle in die IDL-Datei als Verteilschnittstelle ein.|
|[dual](dual.md)|Fügt eine Schnittstelle in die IDL-Datei als duale Schnittstelle ein.|
|[export](export.md)|Bewirkt, dass eine Datenstruktur in der IDL-Datei platziert wird.|
|[helpcontext](helpcontext.md)|Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der Hilfedatei anzeigen kann.|
|[helpfile](helpfile.md)|Legt den Namen der Hilfedatei für eine Typbibliothek fest.|
|[helpstring](helpstring.md)|Gibt eine Zeichenfolge an, die zum Beschreiben des Elements verwendet wird, auf das sie angewendet wird.|
|[helpstringcontext](helpstringcontext.md)|Gibt die ID eines Hilfe Themas in einer. hlp-oder CHM-Datei an.|
|[helpstringdll](helpstringdll.md)|Gibt den Namen der dll an, die verwendet werden soll, um die Suche nach Dokument Zeichenfolgen (Lokalisierung) auszuführen.|
|[hidden](hidden.md)|Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.|
|[library_block](library-block.md)|Platziert ein Konstrukt innerhalb des Bibliotheks Blocks der IDL-Datei.|
|[local](local-cpp.md)|Ermöglicht es Ihnen, den Mittel l-Compiler als Header Generator zu verwenden, wenn er im Schnittstellen Header verwendet wird. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.|
|[nonextensible](nonextensible.md)|Gibt an, dass die `IDispatch` Implementierung nur die Eigenschaften und Methoden enthält, die in der Schnittstellen Beschreibung aufgeführt sind, und kann zur Laufzeit nicht mit zusätzlichen Elementen erweitert werden. Dieses Attribut gilt nur für eine [duale](dual.md) Schnittstelle.|
|[odl](odl.md)|Identifiziert eine Schnittstelle als Object Description Language (ODL)-Schnittstelle.|
|[object](object-cpp.md)|Identifiziert eine benutzerdefinierte-Schnittstelle.|
|[oleautomation](oleautomation.md)|Gibt an, dass eine Schnittstelle mit Automation kompatibel ist.|
|[pointer_default](pointer-default.md)|Gibt das Standard Zeiger Attribut für alle Zeiger außer auf der obersten Ebene an, die in Parameterlisten angezeigt werden.|
|[ptr](ptr.md)|Legt einen Zeiger als vollständigen Zeiger fest.|
|[restricted](restricted.md)|Legt fest, welche Member der Bibliothek nicht willkürlich aufgerufen werden können.|
|[uuid](uuid-cpp-attributes.md)|Stellt die eindeutige ID für die Bibliothek bereit.|

Sie müssen diese Regeln zum Definieren einer Schnittstelle beachten:

- Die Standard Aufruf Konvention ist [__stdcall](../../cpp/stdcall.md).

- Eine GUID wird für Sie bereitgestellt, wenn Sie keine angeben.

- Es sind keine überladenen Methoden zulässig.

Wenn Sie das [UUID](uuid-cpp-attributes.md) -Attribut nicht angeben und denselben Schnittstellennamen in unterschiedlichen Attribut Projekten verwenden, wird dieselbe GUID generiert.

## <a name="see-also"></a>Weitere Informationen

[Attribute nach Verwendung](attributes-by-usage.md)
