---
title: 'TN002: Persistentes Objektdatenformat'
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370445"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Persistentes Objektdatenformat

Dieser Hinweis beschreibt die MFC-Routinen, die persistente C++-Objekte unterstützen, und das Format der Objektdaten, wenn sie in einer Datei gespeichert werden. Dies gilt nur für Klassen mit den [DECLARE_SERIAL-](../mfc/reference/run-time-object-model-services.md#declare_serial) und IMPLEMENT_SERIAL-Makros. [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)

## <a name="the-problem"></a>Problemstellung

Die MFC-Implementierung für persistente Daten speichert Daten für viele Objekte in einem einzelnen zusammenhängenden Teil einer Datei. Die Methode `Serialize` des Objekts übersetzt die Daten des Objekts in ein kompaktes Binärformat.

Die Implementierung stellt sicher, dass alle Daten im gleichen Format gespeichert werden, indem die [CArchive-Klasse](../mfc/reference/carchive-class.md)verwendet wird. Es verwendet `CArchive` ein Objekt als Übersetzer. Dieses Objekt bleibt von der Erstellung bis zum Aufrufen von [CArchive::Close](../mfc/reference/carchive-class.md#close)erhalten. Diese Methode kann entweder explizit vom Programmierer oder implizit vom Destruktor aufgerufen werden, wenn das Programm den Bereich verlässt, der die `CArchive`enthält.

Dieser Hinweis beschreibt die `CArchive` Implementierung der Member [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) und [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Sie finden den Code für diese Funktionen in Arcobj.cpp und die Hauptimplementierung für `CArchive` in Arccore.cpp. Benutzercode ruft `ReadObject` nicht `WriteObject` und direkt an. Stattdessen werden diese Objekte von klassenspezifischen typsicheren Einfüge- und Extraktionsoperatoren verwendet, die automatisch von den DECLARE_SERIAL und IMPLEMENT_SERIAL Makros generiert werden. Der folgende Code `WriteObject` `ReadObject` zeigt, wie und wie implizit aufgerufen werden:

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Speichern von Objekten im Store (CArchive::WriteObject)

Die `CArchive::WriteObject` Methode schreibt Headerdaten, die zum Rekonstruieren des Objekts verwendet werden. Diese Daten bestehen aus zwei Teilen: dem Typ des Objekts und dem Status des Objekts. Diese Methode ist auch für die Aufrechterhaltung der Identität des objektgeschriebenen Objekts verantwortlich, sodass nur eine einzelne Kopie gespeichert wird, unabhängig von der Anzahl der Zeiger auf dieses Objekt (einschließlich zirkulärer Zeiger).

Das Speichern (Einfügen) und Wiederherstellen (Extrahieren) von Objekten beruht auf mehreren "Manifestkonstanten". Dies sind Werte, die in Binärdateien gespeichert sind und wichtige Informationen für das Archiv liefern (beachten Sie, dass das Präfix "w" 16-Bit-Mengen angibt):

|Tag|BESCHREIBUNG|
|---------|-----------------|
|wNullTag|Wird für NULL-Objektzeiger (0) verwendet.|
|wNewClassTag|Gibt die Klassenbeschreibung an, die im Folgenden für diesen Archivkontext neu ist (-1).|
|wOldClassTag|Gibt an, dass die Klasse des zu lesenden Objekts in diesem Kontext gesehen wurde (0x8000).|

Beim Speichern von Objekten verwaltet das Archiv einen [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (die *m_pStoreMap*), bei dem es sich um eine Zuordnung von einem gespeicherten Objekt zu einem 32-Bit persistenten Bezeichner (PID) handelt. Jedem eindeutigen Objekt und jedem eindeutigen Klassennamen, der im Kontext des Archivs gespeichert wird, wird eine PID zugewiesen. Diese PIDs werden ab 1 nacheinander verteilt. Diese PIDs haben außerhalb des Archivbereichs keine Bedeutung und sind insbesondere nicht mit Datensatznummern oder anderen Identitätselementen zu verwechseln.

In `CArchive` der Klasse sind PIDs 32-Bit, aber sie werden als 16-Bit geschrieben, es sei denn, sie sind größer als 0x7FFE. Große PIDs werden als 0x7FFF geschrieben, gefolgt von der 32-Bit-PID. Dadurch bleibt die Kompatibilität mit Projekten erhalten, die in früheren Versionen erstellt wurden.

Wenn eine Anforderung zum Speichern eines Objekts in einem Archiv gestellt wird (in der Regel mithilfe des globalen Einfügeoperators), wird ein [NULL-CObject-Zeiger](../mfc/reference/cobject-class.md) überprüft. Wenn der Zeiger NULL ist, wird das *wNullTag* in den Archivstream eingefügt.

Wenn der Zeiger nicht NULL ist und serialisiert `DECLARE_SERIAL` werden kann (die Klasse ist eine Klasse), überprüft der Code die *m_pStoreMap,* ob das Objekt bereits gespeichert wurde. Wenn dies der Zuspruch besteht, fügt der Code die diesem Objekt zugeordnete 32-Bit-PID in den Archivstream ein.

Wenn das Objekt noch nicht gespeichert wurde, gibt es zwei Möglichkeiten zu berücksichtigen: Entweder das Objekt und der genaue Typ (d. h. die Klasse) des Objekts sind neu in diesem Archivkontext, oder das Objekt ist von einem genauen Typ, der bereits gesehen wurde. Um zu bestimmen, ob der Typ angezeigt wurde, fragt der Code `CRuntimeClass` die *m_pStoreMap* nach einem [CRuntimeClass-Objekt](../mfc/reference/cruntimeclass-structure.md) ab, das dem Objekt entspricht, das dem zu speichernden Objekt zugeordnet ist. Wenn eine Übereinstimmung `WriteObject` vorhanden ist, fügt ein Tag `OR` ein, das das Bit-wise von *wOldClassTag* und diesem Index ist. Wenn `CRuntimeClass` der in diesem Archivkontext neu ist, `WriteObject` weist dieser Klasse eine neue PID zu und fügt sie in das Archiv ein, dem der wert *wNewClassTag* vorangestellt ist.

Der Deskriptor für diese Klasse wird dann `CRuntimeClass::Store` mit der Methode in das Archiv eingefügt. `CRuntimeClass::Store`fügt die Schemanummer der Klasse (siehe unten) und den ASCII-Textnamen der Klasse ein. Beachten Sie, dass die Verwendung des ASCII-Textnamens keine Garantie für die eindeutige Eindeutigkeit des Archivs in allen Anwendungen garantiert. Daher sollten Sie Ihre Datendateien markieren, um Beschädigungen zu verhindern. Nach dem Einfügen der Klasseninformationen legt das *m_pStoreMap* Archiv das Objekt `Serialize` in die m_pStoreMap und ruft dann die Methode auf, klassenspezifische Daten einzufügen. Durch das Platzieren *m_pStoreMap* des `Serialize` Objekts in die m_pStoreMap vor dem Aufruf wird verhindert, dass mehrere Kopien des Objekts im Speicher gespeichert werden.

Wenn Sie zum ursprünglichen Aufrufer zurückkehren (in der Regel der Stamm des Objektnetzwerks), müssen Sie [CArchive::Close](../mfc/reference/carchive-class.md#close)aufrufen. Wenn Sie andere [CFile-Vorgänge](../mfc/reference/cfile-class.md)ausführen möchten, müssen Sie die `CArchive` Methode [Flush](../mfc/reference/carchive-class.md#flush) aufrufen, um eine Beschädigung des Archivs zu verhindern.

> [!NOTE]
> Diese Implementierung legt eine harte Grenze von 0x3FFFFFFE-Indizes pro Archivkontext fest. Diese Zahl stellt die maximale Anzahl eindeutiger Objekte und Klassen dar, die in einem einzelnen Archiv gespeichert werden können, aber eine einzelne Datenträgerdatei kann eine unbegrenzte Anzahl von Archivkontexten haben.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Laden von Objekten aus dem Store (CArchive::ReadObject)

Das Laden (Extrahieren) `CArchive::ReadObject` von Objekten verwendet `WriteObject`die Methode und ist die Umgekehrte von . Wie `WriteObject`bei `ReadObject` wird nicht direkt vom Benutzercode aufgerufen. Benutzercode sollte den typsicheren Extraktionsoperator aufrufen, der mit der erwarteten `ReadObject` `CRuntimeClass`aufruft. Dadurch wird die Typintegrität des Extraktvorgangs sichergestellt.

Da `WriteObject` die Implementierung zunehmenden PIDs zugewiesen wurde, beginnend mit 1 `ReadObject` (0 ist als NULL-Objekt vordefiniert), kann die Implementierung ein Array verwenden, um den Status des Archivkontexts beizubehalten. Wenn eine PID aus dem Speicher gelesen wird und die PID *m_pLoadArray*größer `ReadObject` als die aktuelle Obergrenze des m_pLoadArray ist, weiß, dass ein neues Objekt (oder eine Klassenbeschreibung) folgt.

## <a name="schema-numbers"></a>Schemanummern

Die Schemanummer, die der Klasse `IMPLEMENT_SERIAL` zugewiesen wird, wenn die Methode der Klasse gefunden wird, ist die "Version" der Klassenimplementierung. Das Schema bezieht sich auf die Implementierung der Klasse, nicht auf die Häufigkeit, mit der ein bestimmtes Objekt persistent gemacht wurde (in der Regel als Objektversion bezeichnet).

Wenn Sie mehrere verschiedene Implementierungen derselben Klasse im Laufe der Zeit beibehalten möchten, `Serialize` können Sie durch das Erhöhen des Schemas beim Überarbeiten der Methodenimplementierung des Objekts Code schreiben, der objekte laden kann, die mithilfe älterer Versionen der Implementierung gespeichert sind.

Die `CArchive::ReadObject` Methode löst eine [CArchiveException](../mfc/reference/carchiveexception-class.md) aus, wenn sie auf eine Schemanummer im persistenten Speicher trifft, die sich von der Schemanummer der Klassenbeschreibung im Arbeitsspeicher unterscheidet. Es ist nicht einfach, sich von dieser Ausnahme zu erholen.

Sie können `VERSIONABLE_SCHEMA` ihre Schemaversion in Kombination mit (bitweise **oder**) verwenden, um zu verhindern, dass diese Ausnahme ausgelöst wird. Mithilfe `VERSIONABLE_SCHEMA`von kann Der Code die `Serialize` entsprechende Aktion in seiner Funktion ergreifen, indem er den Rückgabewert von [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)überprüft.

## <a name="calling-serialize-directly"></a>Serialisieren Direkt aufrufen

In vielen Fällen ist der Overhead `WriteObject` des `ReadObject` allgemeinen Objektarchivschemas von und ist nicht notwendig. Dies ist der häufige Fall, wenn die Daten in ein [CDocument](../mfc/reference/cdocument-class.md)serialisiert werden. In diesem Fall `Serialize` `CDocument` wird die Methode des direkt aufgerufen, nicht mit den Extrakt- oder Insert-Operatoren. Der Inhalt des Dokuments kann wiederum das allgemeinere Objektarchivschema verwenden.

Das `Serialize` direkte Aufrufen hat folgende Vor- und Nachteile:

- Vor oder nach der Serialisierung des Objekts werden dem Archiv keine zusätzlichen Bytes hinzugefügt. Dadurch werden nicht nur die gespeicherten Daten `Serialize` kleiner, sondern Auch routinen implementiert, die alle Dateiformate verarbeiten können.

- Die MFC ist so `WriteObject` `ReadObject` abgestimmt, dass die Implementierungen und zugehörigen Sammlungen nicht mit Ihrer Anwendung verknüpft werden, es sei denn, Sie benötigen das allgemeinere Objektarchivschema für einen anderen Zweck.

- Der Code muss nicht von alten Schemanummern wiederhergestellt werden. Dadurch ist der Dokumentserialisierungscode für die Codierung von Schemanummern, Dateiformatversionsnummern oder den zu Beginn der Datendateien verwendenden Identifizierenvonnummern verantwortlich.

- Jedes Objekt, das mit einem `Serialize` direkten Aufruf `CArchive::GetObjectSchema` serialisiert wird, darf einen Rückgabewert von (UINT)-1 nicht verwenden oder verarbeiten, was darauf hinweist, dass die Version unbekannt war.

Da `Serialize` das Dokument direkt aufgerufen wird, ist es in der Regel nicht möglich, dass die Unterobjekte des Dokuments Verweise auf das übergeordnete Dokument archivieren. Diese Objekte müssen explizit einen Zeiger auf ihr Containerdokument erhalten, oder Sie müssen `CDocument` die [Funktion CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) verwenden, um den Zeiger einer PID zuzuordnen, bevor diese Hintergrundzeiger archiviert werden.

Wie bereits erwähnt, sollten Sie die Versions- und `Serialize` Klasseninformationen beim direkten Aufruf selbst kodieren, sodass Sie das Format später ändern können, während die Abwärtskompatibilität mit älteren Dateien beibehalten wird. Die `CArchive::SerializeClass` Funktion kann explizit aufgerufen werden, bevor ein Objekt direkt serialisiert wird oder bevor eine Basisklasse aufgerufen wird.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
