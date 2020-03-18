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
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447126"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Persistentes Objektdatenformat

In diesem Hinweis werden die MFC-Routinen beschrieben C++ , die persistente Objekte und das Format der Objektdaten unterstützen, wenn Sie in einer Datei gespeichert werden. Dies gilt nur für Klassen mit den [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) -und [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) -Makros.

## <a name="the-problem"></a>Problemstellung

Die MFC-Implementierung für persistente Daten speichert Daten für viele Objekte in einem einzelnen zusammenhängenden Teil einer Datei. Die `Serialize`-Methode des Objekts übersetzt die Daten des Objekts in ein kompaktes binäres Format.

Die-Implementierung gewährleistet, dass alle Daten mit der [CArchive-Klasse](../mfc/reference/carchive-class.md)im gleichen Format gespeichert werden. Es verwendet ein `CArchive` Objekt als Übersetzer. Dieses Objekt wird von dem Erstellungs Zeitpunkt bis zum Aufruf von [CArchive:: Close](../mfc/reference/carchive-class.md#close)beibehalten. Diese Methode kann entweder explizit vom Programmierer oder implizit durch den Dekonstruktor aufgerufen werden, wenn das Programm den Bereich verlässt, der die `CArchive`enthält.

In diesem Hinweis wird die Implementierung der `CArchive` Member [CArchive:: Read Object](../mfc/reference/carchive-class.md#readobject) und [CArchive:: Write Object](../mfc/reference/carchive-class.md#writeobject)beschrieben. Sie finden den Code für diese Funktionen in arcobj. cpp und die Haupt Implementierung für `CArchive` in arccore. cpp. Der Benutzercode ruft `ReadObject` und `WriteObject` nicht direkt auf. Stattdessen werden diese Objekte von klassenspezifischen typsicheren Einfügungs-und Extraktions Operatoren verwendet, die automatisch durch die DECLARE_SERIAL-und IMPLEMENT_SERIAL-Makros generiert werden. Der folgende Code zeigt, wie `WriteObject` und `ReadObject` implizit aufgerufen werden:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Speichern von Objekten im Speicher (CArchive:: Write Object)

Die-Methode `CArchive::WriteObject` schreibt Header Daten, die zum Rekonstruieren des-Objekts verwendet werden. Diese Daten bestehen aus zwei Teilen: dem Objekttyp und dem Status des Objekts. Diese Methode ist auch für die Beibehaltung der Identität des geschriebenen Objekts verantwortlich, sodass nur eine einzige Kopie gespeichert wird, unabhängig von der Anzahl der Zeiger auf das Objekt (einschließlich Zirkel Zeigern).

Das Speichern (einfügen) und das Wiederherstellen (extrahieren) von Objekten basiert auf mehreren "Manifest-Konstanten". Dabei handelt es sich um Werte, die im Binärformat gespeichert werden und wichtige Informationen für das Archiv bereitstellen (Beachten Sie, dass das Präfix "w" aus 16-Bit-Mengen besteht

|Tag|BESCHREIBUNG|
|---------|-----------------|
|wNullTag|Wird für NULL-Objekt Zeiger (0) verwendet.|
|wNewClassTag|Gibt an, dass die folgende Klassen Beschreibung neu in diesem Archiv Kontext ist (-1).|
|wOldClassTag|Gibt an, dass die Klasse des gelesenen Objekts in diesem Kontext (0X8000) angezeigt wird.|

Beim Speichern von Objekten behält das Archiv einen [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (den *m_pStoreMap*) bei, der eine Zuordnung eines gespeicherten Objekts zu einem beständigen 32-Bit-Bezeichner (PID) ist. Jedem eindeutigen Objekt und jedem eindeutigen Klassennamen, der im Kontext des Archivs gespeichert wird, wird eine PID zugewiesen. Diese PIDs werden sequenziell ab 1 ausgegeben. Diese PIDs haben außerhalb des Bereichs des Archivs keine Bedeutung und müssen insbesondere nicht mit Daten Satz Nummern oder anderen Identitäts Elementen verwechselt werden.

In der `CArchive`-Klasse sind PIDs 32-Bit, aber Sie werden als 16-Bit-geschrieben, es sei denn, Sie sind größer als 0x7ffe. Große PIDs werden als 0x7FFF geschrieben, gefolgt von der 32-Bit-PID. Dies gewährleistet die Kompatibilität mit Projekten, die in früheren Versionen erstellt wurden.

Wenn eine Anforderung zum Speichern eines Objekts in einem Archiv erfolgt (in der Regel mit dem globalen einfügeoperator), erfolgt eine Überprüfung für einen NULL- [CObject](../mfc/reference/cobject-class.md) -Zeiger. Wenn der Zeiger NULL ist, wird der *wnulltag* in den Archivdaten Strom eingefügt.

Wenn der Zeiger nicht NULL ist und serialisiert werden kann (die Klasse ist eine `DECLARE_SERIAL` Klasse), überprüft der Code die *m_pStoreMap* , um festzustellen, ob das Objekt bereits gespeichert wurde. Wenn dies der Fall ist, fügt der Code die mit diesem Objekt verknüpfte 32-Bit-PID in den Archivdaten Strom ein.

Wenn das Objekt noch nicht gespeichert wurde, gibt es zwei Möglichkeiten: entweder das-Objekt und der exakte Typ (d. h. die-Klasse) des-Objekts sind neu in diesem Archiv Kontext, oder das Objekt hat einen exakten Typ, der bereits vorhanden ist. Um zu ermitteln, ob der Typ erkannt wurde, fragt der Code die *m_pStoreMap* nach einem [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) -Objekt ab, das mit dem `CRuntimeClass` Objekt übereinstimmt, das dem gespeicherten Objekt zugeordnet ist. Wenn eine Entsprechung vorliegt, fügt `WriteObject` ein Tag ein, das die bitweise `OR` von *woldclasstag* und diesem Index ist. Wenn die `CRuntimeClass` mit diesem Archiv Kontext neu ist, weist `WriteObject` dieser Klasse eine neue PID zu und fügt Sie in das Archiv ein, dem der *wnewclasstag* -Wert vorangestellt ist.

Der Deskriptor für diese Klasse wird dann mithilfe der `CRuntimeClass::Store`-Methode in das Archiv eingefügt. `CRuntimeClass::Store` fügt die Schema Nummer der Klasse (siehe unten) und den ASCII-Textnamen der Klasse ein. Beachten Sie, dass die Verwendung des ASCII-textnamens nicht sicherstellt, dass das Archiv Anwendungs übergreifend eindeutig ist. Daher sollten Sie Ihre Datendateien markieren, um Beschädigungen zu verhindern. Nach dem Einfügen der Klassen Informationen fügt das Archiv das Objekt in die *m_pStoreMap* ein und ruft dann die `Serialize`-Methode auf, um klassenspezifische Daten einzufügen. Wenn das Objekt vor dem Aufrufen `Serialize` in die *m_pStoreMap* platziert wird, wird verhindert, dass mehrere Kopien des Objekts im Speicher gespeichert werden.

Wenn Sie zum ursprünglichen Aufrufer zurückkehren (in der Regel der Stamm des Netzwerks von Objekten), müssen Sie [CArchive:: Close](../mfc/reference/carchive-class.md#close)aufzurufen. Wenn Sie beabsichtigen, andere [CFile](../mfc/reference/cfile-class.md)-Vorgänge auszuführen, müssen Sie die `CArchive`- [Methoden Leerung aufzurufen, um](../mfc/reference/carchive-class.md#flush) eine Beschädigung des Archivs zu verhindern.

> [!NOTE]
>  Diese Implementierung erzwingt ein hartes Limit von 0x3ffffffe-Indizes pro Archiv Kontext. Diese Zahl stellt die maximale Anzahl eindeutiger Objekte und Klassen dar, die in einem einzelnen Archiv gespeichert werden können, aber eine einzelne Datenträger Datei kann eine unbegrenzte Anzahl von Archiv Kontexten aufweisen.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Laden von Objekten aus dem Speicher (CArchive:: Read Object)

Beim Laden (extrahieren) von Objekten wird die `CArchive::ReadObject`-Methode verwendet, und es handelt sich um den umgekehrten `WriteObject`. Wie bei `WriteObject`wird `ReadObject` nicht direkt durch Benutzercode aufgerufen. Benutzercode sollte den typsicheren Extraktions Operator aufrufen, der `ReadObject` mit der erwarteten `CRuntimeClass`aufruft. Dadurch wird die Typintegrität des Extraktions Vorgangs sichergestellt.

Da die `WriteObject` Implementierung, die ansteigende PIDs zugewiesen hat, beginnend mit 1 (0 als NULL-Objekt vordefiniert ist), kann die `ReadObject` Implementierung ein Array verwenden, um den Zustand des Archiv Kontexts beizubehalten. Wenn eine PID aus dem Speicher gelesen wird und die PID größer als die aktuelle obere Grenze der *m_pLoadArray*ist, weiß `ReadObject`, dass ein neues Objekt (oder eine Klassen Beschreibung) folgt.

## <a name="schema-numbers"></a>Schema Nummern

Die Schema Nummer, die der-Klasse zugewiesen wird, wenn die `IMPLEMENT_SERIAL`-Methode der-Klasse gefunden wird, ist die "Version" der Klassen Implementierung. Das Schema bezieht sich auf die Implementierung der-Klasse, nicht auf die Häufigkeit, mit der ein bestimmtes Objekt persistent gemacht wurde (in der Regel als Objekt Version bezeichnet).

Wenn Sie beabsichtigen, mehrere verschiedene Implementierungen derselben Klasse im Lauf der Zeit zu verwalten, können Sie das Schema bei der Überarbeitung der Implementierung des `Serialize`-Methode des Objekts erhöhen, indem Sie Code schreiben, mit dem Objekte geladen werden können, die mit älteren Versionen der Implementierung gespeichert wurden.

Die `CArchive::ReadObject`-Methode löst eine [carchiveexception](../mfc/reference/carchiveexception-class.md) aus, wenn Sie auf eine Schema Nummer im permanenten Speicher trifft, die von der Schema Nummer der Klassen Beschreibung im Arbeitsspeicher abweicht. Die Wiederherstellung nach dieser Ausnahme ist nicht einfach.

Sie können `VERSIONABLE_SCHEMA` in Kombination mit (bitweiser **or**) Ihrer Schema Version verwenden, um zu verhindern, dass diese Ausnahme ausgelöst wird. Wenn Sie `VERSIONABLE_SCHEMA`verwenden, kann der Code die entsprechende Aktion in seiner `Serialize` Funktion durchführen, indem er den Rückgabewert von [CArchive:: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)überprüft.

## <a name="calling-serialize-directly"></a>Direktes Aufrufen von serialisieren

In vielen Fällen ist der Aufwand des allgemeinen Objekt Archiv Schemas von `WriteObject` und `ReadObject` nicht erforderlich. Dies ist der häufige Fall, dass die Daten in ein [CDocument](../mfc/reference/cdocument-class.md)serialisiert werden. In diesem Fall wird die `Serialize`-Methode der `CDocument` direkt aufgerufen, nicht mit den Extrahierungs-oder einfügeoperatoren. Der Inhalt des Dokuments kann wiederum das allgemeinere Objekt Archiv Schema verwenden.

Das direkte Aufrufen von `Serialize` hat die folgenden vor-und Nachteile:

- Vor oder nach der Serialisierung des Objekts werden dem Archiv keine zusätzlichen Bytes hinzugefügt. Dadurch werden die gespeicherten Daten nicht nur kleiner, sondern es können auch `Serialize` Routinen implementiert werden, die beliebige Dateiformate verarbeiten können.

- Der MFC ist optimiert, sodass die `WriteObject`-und `ReadObject` Implementierungen und verwandte Auflistungen nicht mit Ihrer Anwendung verknüpft werden, es sei denn, Sie benötigen das allgemeinere Objekt Archiv Schema für einen anderen Zweck.

- Der Code muss nicht von alten Schema Nummern wieder hergestellt werden. Dadurch ist Ihr dokumentserialisierungscode für das Codieren von Schema Nummern, Dateiformat-Versionsnummern oder alle Identifikationsnummern verantwortlich, die Sie am Anfang der Datendateien verwenden.

- Alle Objekte, die mit einem direkten-`Serialize` serialisiert werden, dürfen `CArchive::GetObjectSchema` nicht verwenden oder einen Rückgabewert von (uint)-1 verarbeiten, der angibt, dass die Version unbekannt war.

Da `Serialize` direkt in Ihrem Dokument aufgerufen wird, ist es in der Regel nicht möglich, dass die untergeordneten Objekte des Dokuments Verweise auf Ihr übergeordnetes Dokument archivieren. Diese Objekte müssen explizit einen Zeiger auf Ihr Container Dokument erhalten, oder Sie müssen die [CArchive:: MapObject](../mfc/reference/carchive-class.md#mapobject) -Funktion verwenden, um den `CDocument` Zeiger einer PID zuzuordnen, bevor diese backzeigern archiviert werden.

Wie bereits erwähnt, sollten Sie die Versions-und Klassen Informationen selbst codieren, wenn Sie `Serialize` direkt aufzurufen, sodass Sie das Format später ändern können, während die Abwärtskompatibilität mit älteren Dateien gewahrt bleibt. Die `CArchive::SerializeClass`-Funktion kann explizit aufgerufen werden, bevor ein Objekt direkt serialisiert oder eine Basisklasse aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
