---
title: Empfehlungen für die Auswahl einer Sammlungsklasse
ms.date: 11/04/2016
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
ms.openlocfilehash: 53a4eb3e30048d9dc82722d912a026d63a87586d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371749"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Empfehlungen für die Auswahl einer Sammlungsklasse

Dieser Artikel enthält ausführliche Informationen zur Auswahl einer Auflistungsklasse für Ihre besonderen Anwendungsanforderungen.

Ihre Wahl einer Auflistungsklasse hängt von mehreren Faktoren ab, einschließlich:

- Features der Klassenform: Reihenfolge, Indizierung und Leistung, wie in der Tabelle [Auflistungsformfeatures](#_core_collection_shape_features) weiter unten in diesem Thema gezeigt

- ob die Klasse C++-Vorlagen verwendet

- ob die in der Auflistung gespeicherten Elemente serialisiert werden können

- ob die in der Auflistung gespeicherten Elemente zur Diagnose gesichert werden können

- ob die Auflistung typsicher ist

Die folgende Tabelle, [Auflistungsformfeatures](#_core_collection_shape_features), fasst die Merkmale der verfügbaren Auflistungsformen zusammen.

- In Spalten 2 und 3 werden die Anordnungs- und Zugriffsmerkmale jeder Form beschrieben. In der Tabelle bedeutet der Ausdruck „geordnet“, dass die Reihenfolge, in der Elemente eingefügt und gelöscht werden, deren Reihenfolge in der Auflistung bestimmt. Es bedeutet nicht, dass die Elemente anhand ihres Inhalts sortiert werden. Der Begriff „indiziert“ bedeutet, dass die Elemente in der Auflistung über einen Ganzzahlenindex, ähnlich wie die Elemente in einem normalen Array, abgerufen werden können.

- In Spalten 4 und 5 wird die Leistung jeder Form beschrieben. In Anwendungen, die viele Einfügungen in die Auflistung erfordern, ist möglicherweise die Einfügungsgeschwindigkeit besonders wichtig; für andere Programme könnte die Suchgeschwindigkeit wichtiger sein.

- In Spalte 6 wird beschrieben, ob die einzelnen Formen doppelte Elemente zulassen.

### <a name="collection-shape-features"></a><a name="_core_collection_shape_features"></a>Sammlungs-Shape-Features

|Form|Bestellt|Indizierte|Einfügen eines Elements|Suchen nach einem angegebenen Element|Doppelte Elemente|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|List|Ja|Nein|Schnell|Langsam|Ja|
|Array|Ja|Nach Ganzzahl|Langsam|Langsam|Ja|
|Karte|Nein|Nach Schlüssel|Schnell|Schnell|Nein (Schlüssel) Ja (Werte)|

In der folgenden Tabelle, [Merkmale von MFC-Auflistungsklassen](#_core_characteristics_of_mfc_collection_classes), werden weitere wichtige Merkmale bestimmter MFC-Auflistungsklassen als Anleitung zur Auswahl zusammengefasst. Ihre Wahl kann davon abhängen, ob die Klasse auf C++-Vorlagen basiert, ihre Elemente über den MFC-Mechanismus zur [Dokumentserialisierung](../mfc/serialization-in-mfc.md) serialisiert werden können, die Elemente über den MFC-Diagnosesicherungsmechanismus gesichert werden können oder die Klasse typsicher ist – d. h., ob Sie den Typ der Elemente gewährleisten können, die in einer auf der Klasse basierenden Auflistung gespeichert und daraus abgerufen werden.

### <a name="characteristics-of-mfc-collection-classes"></a><a name="_core_characteristics_of_mfc_collection_classes"></a>Eigenschaften von MFC-Sammlungsklassen

|Klasse|Verwendet C++-<br /><br /> Vorlagen|Wird bei Bedarf<br /><br /> serialisiert|Wird bei Bedarf<br /><br /> gesichert|Is<br /><br /> typsicher|
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|
|`CArray`|Ja|Ja 1|Ja 1|Nein|
|`CByteArray`|Nein |Ja|Ja|Ja 3|
|`CDWordArray`|Nein |Ja|Ja|Ja 3|
|`CList`|Ja|Ja 1|Ja 1|Nein |
|`CMap`|Ja|Ja 1|Ja 1|Nein|
|`CMapPtrToPtr`|Nein|Nein |Ja|Nein|
|`CMapPtrToWord`|Nein|Nein |Ja|Nein|
|`CMapStringToOb`|Nein |Ja|Ja|Nein|
|`CMapStringToPtr`|Nein|Nein |Ja|Nein|
|`CMapStringToString`|Nein |Ja|Ja|Ja 3|
|`CMapWordToOb`|Nein |Ja|Ja|Nein|
|`CMapWordToPtr`|Nein|Nein |Ja|Nein|
|`CObArray`|Nein |Ja|Ja|Nein|
|`CObList`|Nein |Ja|Ja|Nein|
|`CPtrArray`|Nein|Nein |Ja|Nein|
|`CPtrList`|Nein|Nein |Ja|Nein|
|`CStringArray`|Nein |Ja|Ja|Ja 3|
|`CStringList`|Nein |Ja|Ja|Ja 3|
|`CTypedPtrArray`|Ja|Je nachdem 2|Ja|Ja|
|`CTypedPtrList`|Ja|Je nachdem 2|Ja|Ja|
|`CTypedPtrMap`|Ja|Je nachdem 2|Ja|Ja|
|`CUIntArray`|Nein|Nein |Ja|Ja 3|
|`CWordArray`|Nein |Ja|Ja|Ja 3|

1. Zum Serialisieren müssen Sie explizit die `Serialize`-Funktion des Auflistungsobjekts aufrufen; zum Sichern müssen Sie explizit seine `Dump`-Funktion aufrufen. Sie können das `ar << collObj` Formular nicht zum `dmp` `<< collObj` Serialisieren oder zum Abladen des Formulars verwenden.

2. Serialisierbarkeit hängt vom zugrunde liegenden Auflistungstyp ab. Wenn z. B. ein typisiertes Zeigerarray auf `CObArray`basiert, ist es serialisierbar; auf `CPtrArray`basierend ist es nicht serialisierbar. Im Allgemeinen können die „Ptr“-Klassen nicht serialisiert werden.

3. Wenn in dieser Spalte „Ja“ markiert ist, ist eine Auflistungsklasse ohne Vorlage typsicher, sofern Sie sie wie vorgesehen verwenden. Wenn Sie z. B. Bytes in einem `CByteArray`speichern, ist das Array typsicher. Aber wenn Sie es zum Speichern von Zeichen verwenden, ist die Typsicherheit nicht so sicher.

## <a name="see-also"></a>Siehe auch

[Sammlungen](../mfc/collections.md)<br/>
[Vorlagenbasierte Klassen](../mfc/template-based-classes.md)<br/>
[Vorgehensweise: Erstellen einer typsicheren Auflistung](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[Zugreifen auf alle Elemente einer Auflistung](../mfc/accessing-all-members-of-a-collection.md)
