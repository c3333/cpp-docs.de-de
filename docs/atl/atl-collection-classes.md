---
title: ATL-Auflistungs Klassen Übersicht
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 039af388a3713540c6ba7d39e8b639cf83d291ff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040859"
---
# <a name="atl-collection-classes"></a>ATL-Auflistungsklassen

ATL stellt viele Klassen zum Speichern und Zugreifen auf Daten bereit. Welche Klasse Sie verwenden möchten, hängt von mehreren Faktoren ab, einschließlich:

- Die zu speichernde Datenmenge

- Effizienz und Leistung beim Zugriff auf die Daten

- Die Möglichkeit, auf die Daten nach Index oder Schlüssel zuzugreifen

- So werden die Daten geordnet

- Persönliche Präferenz

## <a name="small-collection-classes"></a>Kleine Sammlungs Klassen

ATL stellt die folgenden Array Klassen für den Umgang mit einer kleinen Anzahl von Objekten bereit. Diese Klassen sind jedoch eingeschränkt und sind für die interne Verwendung durch ATL konzipiert. Es wird nicht empfohlen, diese in ihren Programmen zu verwenden.

|Klasse|Typ des Datenspeichers|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementiert eine Array Klasse für den Umgang mit einer kleinen Anzahl von Objekten.|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementiert eine Mapping-Klasse für den Umgang mit einer kleinen Anzahl von Objekten.|

## <a name="general-purpose-collection-classes"></a>Universell Auflistungs Klassen

Die folgenden Klassen implementieren Arrays, Listen und Zuordnungen und werden als allgemeine Auflistungs Klassen bereitgestellt:

|Klasse|Typ des Datenspeichers|
|-----------|--------------------------|
|[.](../atl/reference/catlarray-class.md)|Implementiert ein-Array.|
|[Die Kategorie](../atl/reference/catllist-class.md)|Implementiert eine Liste.|
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementiert eine Zuordnungsstruktur, bei der mit einem Schlüssel oder Wert auf Daten verwiesen werden kann.|
|[CRBMap](../atl/reference/crbmap-class.md)|Implementiert eine Mapping-Struktur mit dem Red-Black-Algorithmus.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementiert eine rote schwarze Multimapping-Struktur.|

Diese Klassen fangen viele Programmierfehler auf, wenn Sie in Debugbuilds verwendet werden, aber aus Leistungsgründen werden diese Überprüfungen nicht in Einzelhandels Builds ausgeführt.

## <a name="specialized-collection-classes"></a>Spezialisierte Sammlungs Klassen

Speziellere Sammlungs Klassen werden auch zum Verwalten von Speicher Zeigern und Schnittstellen Zeigern bereitgestellt:

|Klasse|Zweck|
|-----------|-------------|
|[Cautoptrarray](../atl/reference/cautoptrarray-class.md)|Stellt Methoden bereit, die beim Erstellen eines Arrays von intelligenten Zeigern nützlich sind.|
|[Cautoptrlist](../atl/reference/cautoptrlist-class.md)|Stellt Methoden bereit, die beim Erstellen einer Liste von intelligenten Zeigern hilfreich sind.|
|[Ccomunkarray](../atl/reference/ccomunkarray-class.md)|Speichert `IUnknown` Zeiger und ist so konzipiert, dass Sie als Parameter für die [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) -Vorlagen Klasse verwendet wird.|
|[Cheapptrlist](../atl/reference/cheapptrlist-class.md)|Stellt Methoden bereit, die beim Erstellen einer Liste von Heap Zeigern hilfreich sind.|
|[Cinterfakearray](../atl/reference/cinterfacearray-class.md)|Stellt Methoden bereit, die beim Erstellen eines Arrays von COM-Schnittstellen Zeigern hilfreich sind.|
|[Cinterfakelist](../atl/reference/cinterfacelist-class.md)|Stellt Methoden bereit, die beim Erstellen einer Liste von COM-Schnittstellen Zeigern hilfreich sind.|

## <a name="choosing-a-collection-class"></a>Auswählen einer Auflistungs Klasse

Jede der verfügbaren Auflistungs Klassen bietet verschiedene Leistungsmerkmale, wie in der folgenden Tabelle dargestellt.

- In den Spalten 2 und 3 werden die Anordnungs-und Zugriffs Merkmale jeder Klasse beschrieben. In der Tabelle bedeutet der Ausdruck „geordnet“, dass die Reihenfolge, in der Elemente eingefügt und gelöscht werden, deren Reihenfolge in der Auflistung bestimmt. Es bedeutet nicht, dass die Elemente anhand ihres Inhalts sortiert werden. Der Begriff „indiziert“ bedeutet, dass die Elemente in der Auflistung über einen Ganzzahlenindex, ähnlich wie die Elemente in einem normalen Array, abgerufen werden können.

- In den Spalten 4 und 5 wird die Leistung der einzelnen Klassen beschrieben. In Anwendungen, die viele Einfügungen in die Auflistung erfordern, ist möglicherweise die Einfügungsgeschwindigkeit besonders wichtig; für andere Programme könnte die Suchgeschwindigkeit wichtiger sein.

- In Spalte 6 wird beschrieben, ob die einzelnen Formen doppelte Elemente zulassen.

- Die Leistung eines gegebenen Auflistungs Klassen Vorgangs wird in Bezug auf die Beziehung zwischen der zum Abschluss des Vorgangs erforderlichen Zeit und der Anzahl der Elemente in der Auflistung ausgedrückt. Ein Vorgang, der eine gewisse Zeit in Anspruch nimmt, wenn die Anzahl der Elemente zunimmt, wird als O (n)-Algorithmus beschrieben. Im Gegensatz dazu wird ein Vorgang, der einen längeren Zeitraum in Anspruch nimmt, wenn die Anzahl der Elemente zunimmt, als O (log n)-Algorithmus beschrieben. Im Hinblick auf die Leistung übernehmen o (log n)-Algorithmen daher immer mehr und mehr, wenn die Anzahl der Elemente zunimmt.

### <a name="collection-shape-features"></a>Auflistungsformfeatures

|Form|Bestellt|Zierenden|Einfügen eines<br /><br /> element|Suchen nach<br /><br /> bestimmtes Element|Duplizieren<br /><br /> Elemente|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|List|Ja|Nein|Schnell (Konstante Zeit)|Langsame O (n)|Ja|
|Array|Ja|Nach int (Konstante Zeit)|Langsame O (n), außer wenn am Ende eingefügt wird. in diesem Fall ist die Konstante Zeit.|Langsame O (n)|Ja|
|Karte|Nein|Nach Schlüssel (Konstante Zeit)|Schnell (Konstante Zeit)|Schnell (Konstante Zeit)|Nein (Schlüssel) Ja (Werte)|
|Rote schwarze Karte|Ja (nach Schlüssel)|Nach Schlüssel O (log n)|Schnelles O (Protokoll n)|Schnelles O (Protokoll n)|Nein|
|Rote schwarze mehrfach Zuordnung|Ja (nach Schlüssel)|Nach Schlüssel O (log n) (mehrere Werte pro Schlüssel)|Schnelles O (Protokoll n)|Schnelles O (Protokoll n)|Ja (mehrere Werte pro Schlüssel)|

## <a name="using-ctraits-objects"></a>Verwenden von ctrait-Objekten

Da die ATL-Auflistungs Klassen verwendet werden können, um eine breite Palette von benutzerdefinierten Datentypen zu speichern, kann es hilfreich sein, wichtige Funktionen, wie z. b. Vergleiche, zu überschreiben. Dies wird mithilfe der ctrait-Klassen erreicht.

Ctrait-Klassen ähneln, sind jedoch flexibler als die Hilfsfunktionen der MFC-Auflistungs Klasse. Weitere Informationen finden Sie unter Auflistungs [Klassen](../mfc/reference/collection-class-helpers.md) -Hilfsprogramme.

Beim Erstellen der Auflistungs Klasse haben Sie die Möglichkeit, eine ctrait-Klasse anzugeben. Diese Klasse enthält den Code, der Vorgänge wie Vergleiche ausführt, wenn Sie von den anderen Methoden aufgerufen wird, die die Auflistungs Klasse bilden. Wenn das Listen Objekt z. b. ihre eigenen benutzerdefinierten Strukturen enthält, sollten Sie den Gleichheits Test so definieren, dass nur bestimmte Element Variablen verglichen werden. Auf diese Weise wird die Find-Methode des Listen Objekts in einer nützlicheren Weise ausgeführt.

## <a name="example"></a>Beispiel

### <a name="code"></a>Code

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>Kommentare

Eine Liste der ctrait-Klassen finden Sie unter Auflistungs [Klassen](../atl/collection-classes.md).

Das folgende Diagramm zeigt die Klassenhierarchie für die ctrait-Klassen.

![Merkmalhierarchie für Auflistungsklassen](../atl/media/vctraitscollectionclasseshierarchy.gif "Merkmalhierarchie für Auflistungsklassen")

## <a name="collection-classes-samples"></a>Beispiele für Sammlungs Klassen

Die folgenden Beispiele veranschaulichen die Auflistungs Klassen:

- [MMXSwarm-Beispiel](../overview/visual-cpp-samples.md)

- [DynamicConsumer-Beispiel](../overview/visual-cpp-samples.md)

- [UpdatePV-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Marquee-Beispiel](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Weitere Informationen

[Konzepte](../atl/active-template-library-atl-concepts.md)<br/>
[Auflistungs Klassen](../atl/collection-classes.md)
