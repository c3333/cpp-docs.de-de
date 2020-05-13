---
title: Klasse von "Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168058"
---
# <a name="catlmap-class"></a>Klasse von "Klasse"

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines Map-Objekts bereit.

## <a name="syntax"></a>Syntax

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>Parameter

*Km*<br/>
Der Schlüssel Elementtyp.

*Ramelow*<br/>
Der Wert Elementtyp.

*Kmerkmalen*<br/>
Der Code, der zum Kopieren oder Verschieben von Schlüsselelementen verwendet wird. Weitere Informationen finden Sie unter [celementtrait-Klasse](../../atl/reference/celementtraits-class.md) .

*Vmerkmalen*<br/>
Der Code, der zum Kopieren oder Verschieben von Wert Elementen verwendet wird.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "", "".](#kinargtype)|Typ, der verwendet wird, wenn eine Taste als Eingabe Argument übermittelt wird|
|["", "": Koutargtype](#koutargtype)|Der Typ, der verwendet wird, wenn eine Taste als Ausgabe Argument zurückgegeben wird.|
|["": Vinargtype](#vinargtype)|Der Typ, der verwendet wird, wenn ein Wert als Eingabe Argument übermittelt wird.|
|["": Voutargtype](#voutargtype)|Der Typ, der verwendet wird, wenn ein Wert als Ausgabe Argument ausgegeben wird.|

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|["Klasse": cpair-Klasse](#cpair_class)|Eine-Klasse, die die Schlüssel-und Wert Elemente enthält.|

### <a name="cpair-data-members"></a>Cpair-Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cpair:: m_key](#m_key)|Der Datenmember, der das Schlüsselelement speichert.|
|[Cpair:: m_value](#m_value)|Der Datenmember, der das Value-Element speichert.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["":](#catlmap)|Der Konstruktor.|
|["": ""](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": AssertValid](#assertvalid)|Rufen Sie diese Methode auf, um eine Assert `CAtlMap` -Methode auszulösen, wenn nicht gültig ist.|
|[Ereignis ERMAP::D isableautorehash](#disableautorehash)|Ruft diese Methode auf, um das `CAtlMap` automatische Reaktivieren des Objekts zu deaktivieren.|
|["", "": Enableautorehash](#enableautorehash)|Ruft diese Methode auf, um das `CAtlMap` automatische Reaktivieren des Objekts zu aktivieren.|
|["": GetAt](#getat)|Mit dieser Methode wird das Element an einer angegebenen Position in der Zuordnung zurückgegeben.|
|["Update Map:: GetCount"](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Zuordnung abzurufen.|
|["", "": Gethashtablesize](#gethashtablesize)|Mit dieser Methode können Sie die Anzahl der Container in der Hash Tabelle der Zuordnung bestimmen.|
|["": Getkeyat](#getkeyat)|Rufen Sie diese Methode auf, um den Schlüssel abzurufen, der an der `CAtlMap` angegebenen Position im-Objekt gespeichert ist.|
|["": GetNext](#getnext)|Rufen Sie diese Methode auf, um einen Zeiger auf das nächste Element paar zu `CAtlMap` erhalten, das im-Objekt gespeichert ist.|
|["": GetNextAssoc](#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|["": Getnextkey](#getnextkey)|Rufen Sie diese Methode auf, um den nächsten Schlüssel `CAtlMap` aus dem-Objekt abzurufen.|
|["": Getnextvalue](#getnextvalue)|Mit dieser Methode können Sie den nächsten Wert aus dem `CAtlMap` -Objekt abrufen.|
|["": GetStartPosition](#getstartposition)|Mit dieser Methode wird eine Karten Iterations Methode gestartet.|
|["": Getvalueat](#getvalueat)|Rufen Sie diese Methode auf, um den Wert abzurufen, der an einer `CAtlMap` bestimmten Position im-Objekt gespeichert ist.|
|["": ""](#inithashtable)|Ruft diese Methode auf, um die Hash Tabelle zu initialisieren.|
|["": IsEmpty](#isempty)|Mit dieser Methode können Sie auf ein leeres Map-Objekt testen.|
|["": Lookup](#lookup)|Mit dieser Methode können Sie Schlüssel oder Werte im- `CAtlMap` Objekt suchen.|
|["": ""](#rehash)|Ruft diese Methode auf, um das `CAtlMap` Objekt erneut zu durch drücken.|
|["": Remote Map:: RemoveAll](#removeall)|Mit dieser Methode können Sie alle Elemente aus dem `CAtlMap` -Objekt entfernen.|
|["": Removeatpos](#removeatpos)|Ruft diese Methode auf, um das Element an der angegebenen Position im `CAtlMap` Objekt zu entfernen.|
|["": Removekey](#removekey)|Ruft diese Methode auf, um ein Element aus `CAtlMap` dem-Objekt mit dem angegebenen Schlüssel zu entfernen.|
|["":](#setat)|Mit dieser Methode fügen Sie ein Element Paar in die Zuordnung ein.|
|["": ""](#setoptimalload)|Ruft diese Methode auf, um die optimale Auslastung des `CAtlMap` -Objekts festzulegen.|
|["", "": Setvalueat](#setvalueat)|Ruft diese Methode auf, um den Wert zu ändern, der an einer `CAtlMap` bestimmten Position im-Objekt gespeichert ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Ersetzt oder fügt ein neues Element hinzu `CAtlMap`.|

## <a name="remarks"></a>Bemerkungen

`CAtlMap`bietet Unterstützung für ein Mapping-Array eines beliebigen Typs, wobei ein ungeordnetes Array von Schlüsselelementen und die zugeordneten Werte verwaltet werden. Elemente (bestehend aus einem Schlüssel und einem Wert) werden mit einem Hash Algorithmus gespeichert, sodass eine große Datenmenge effizient gespeichert und abgerufen werden kann.

Bei den Parametern " *ktrait* " und " *vmerkmalen* " handelt es sich um Eigenschaften Klassen, die zusätzlichen Code zum Kopieren oder Verschieben von Elementen enthalten.

Eine Alternative zu `CAtlMap` wird von der [CRBMap](../../atl/reference/crbmap-class.md) -Klasse angeboten. `CRBMap`speichert auch Schlüssel-Wert-Paare, weist jedoch unterschiedliche Leistungsmerkmale auf. Der Zeitaufwand für das Einfügen eines Elements, das Suchen nach einem Schlüssel oder das Löschen eines Schlüssels `CRBMap` aus einem-Objekt ist "Order *Log (n)*", wobei *n* die Anzahl der Elemente ist. Bei `CAtlMap`nehmen alle diese Vorgänge in der Regel eine Konstante Zeit in Anspruch, obwohl die Groß-/Kleinschreibung für Szenarios möglicherweise die Reihenfolge *n*hat. Daher `CAtlMap` ist in einem typischen Fall schneller.

Der andere Unterschied `CRBMap` zwischen `CAtlMap` und wird offensichtlich, wenn die gespeicherten Elemente durchlaufen werden. In einem `CRBMap`werden die Elemente in sortierter Reihenfolge besucht. In einem `CAtlMap`werden die Elemente nicht sortiert, und es kann keine Reihenfolge abgeleitet werden.

Wenn eine kleine Anzahl von Elementen gespeichert werden muss, sollten Sie stattdessen die [CSimpleMap](../../atl/reference/csimplemap-class.md) -Klasse verwenden.

Weitere Informationen finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="requirements"></a>Anforderungen

**Header:** atlcoll. h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>"": AssertValid

Rufen Sie diese Methode auf, um eine Assert `CAtlMap` -Methode auszulösen, wenn das Objekt nicht gültig ist.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

In Debugbuilds führt diese Methode eine Assert-Methode aus `CAtlMap` , wenn das Objekt nicht gültig ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>"":

Der Konstruktor.

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parameter

*nbins*<br/>
Die Anzahl der Container, die Zeiger auf die gespeicherten Elemente bereitstellen. Weitere Informationen zu Containern finden Sie weiter unten in diesem Thema unter "Hinweise".

*"f"*<br/>
Das optimale Last Verhältnis.

*flothreshold*<br/>
Der untere Schwellenwert für das Lasten Verhältnis.

*Wert für "f"*<br/>
Der obere Schwellenwert für das Lasten Verhältnis.

*nblocksize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

`CAtlMap`verweist auf alle zugehörigen gespeicherten Elemente, indem zuerst ein Index mit einem Hash Algorithmus für den Schlüssel erstellt wird. Dieser Index verweist auf einen "bin", der einen Zeiger auf die gespeicherten Elemente enthält. Wenn der bin bereits verwendet wird, wird eine verknüpfte Liste erstellt, um auf die nachfolgenden Elemente zuzugreifen. Das Durchlaufen einer Liste ist langsamer als der direkte Zugriff auf das richtige Element. Daher muss die Karten Struktur die Speicheranforderungen gegen die Leistung ausgleichen. Die Standardparameter wurden in den meisten Fällen dazu ausgewählt, gute Ergebnisse zu liefern.

Das Lasten Verhältnis ist das Verhältnis zwischen der Anzahl von Containern und der Anzahl der im Map-Objekt gespeicherten Elemente. Wenn die Karten Struktur neu berechnet wird, wird der Wert des *foptimzuad* -Parameters verwendet, um die Anzahl der erforderlichen Behälter zu berechnen. Dieser Wert kann [mithilfe der Methode](#setoptimalload) "-Methode (Methode)" von "Methode" geändert werden.

Der *flothreshold* -Parameter ist der niedrigere Wert, den das Lasten Verhältnis erreichen `CAtlMap` kann, bevor die optimale Größe der Karte neu berechnet.

Der Parameter " *shithreshold* " ist der obere Wert, den das Last Verhältnis erreichen `CAtlMap` kann, bevor das Objekt die optimale Größe der Zuordnung neu berechnet.

Dieser neuberechnungs Prozess (wird als Wiederholung bezeichnet) ist standardmäßig aktiviert. Wenn Sie diesen Prozess deaktivieren möchten, wenn Sie vielleicht eine große Anzahl von Daten gleichzeitig eingeben, können Sie die Methode "Methode [::D isableautorehash](#disableautorehash) " aufrufen. Reaktivieren Sie Sie mit [der Methode](#enableautorehash) "" der Methode "Methode".

Der *nblocksize* -Parameter ist ein Maß für den Umfang des Arbeitsspeichers, der zugeordnet wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicher Belegungs Routinen, verwenden jedoch weitere Ressourcen.

Bevor Daten gespeichert werden können, muss die Hash Tabelle mit einem [calllmap:: inithashtable](#inithashtable)-Befehl initialisiert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>"": ""

Der Destruktor.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>"Klasse": cpair-Klasse

Eine-Klasse, die die Schlüssel-und Wert Elemente enthält.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse wird von [den Methoden "](#getnext) ", "", um auf die Schlüssel-und Wert Elemente [zuzugreifen, die](#lookup) in der Zuordnungs Struktur gespeichert sind.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>Ereignis ERMAP::D isableautorehash

Ruft diese Methode auf, um das `CAtlMap` automatische Reaktivieren des Objekts zu deaktivieren.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn die automatische Wiederholung aktiviert ist (standardmäßig), wird die Anzahl der in der Hash Tabelle gespeicherten Behälter automatisch neu berechnet, wenn der Auslastungs Wert (das Verhältnis der Anzahl der Behälter mit der Anzahl der im Array gespeicherten Elemente) den maximalen oder minimalen Wert überschreitet, der zum Zeitpunkt der Erstellung der Zuordnung angegeben wurde.

`DisableAutoRehash`ist besonders nützlich, wenn der Karte gleichzeitig eine große Anzahl von Elementen hinzugefügt wird. Anstatt den Reaktivierungsprozess jedes Mal auszulösen, wenn die Grenzwerte überschritten werden, ist es effizienter `DisableAutoRehash` [, aufzurufen](#enableautorehash), die Elemente hinzuzufügen und schließlich "" "" "" ".

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>"", "": Enableautorehash

Ruft diese Methode auf, um das `CAtlMap` automatische Reaktivieren des Objekts zu aktivieren.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn die automatische Wiederholung aktiviert ist (standardmäßig), wird die Anzahl der in der Hash Tabelle gespeicherten Behälter automatisch neu berechnet, wenn der Auslastungs Wert (das Verhältnis der Anzahl der Behälter zur Anzahl der im Array gespeicherten Elemente) den maximalen oder minimalen Wert überschreitet, der zum Zeitpunkt der Erstellung der Zuordnung angegeben wird.

`EnableAutoRefresh`wird am häufigsten nach einem [calllmap::D isableautorehash](#disableautorehash)verwendet.

## <a name="catlmapgetat"></a><a name="getat"></a>"": GetAt

Mit dieser Methode wird das Element an einer angegebenen Position in der Zuordnung zurückgegeben.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

*key*<br/>
Ein Vorlagen Parameter, der den Typ des Karten Schlüssels angibt.

*value*<br/>
Ein Vorlagen Parameter, der den Typ des Karten Werts angibt.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das aktuelle Paar von Schlüssel-Wert-Elementen zurück, die in der Zuordnung gespeichert sind.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Fehler auf, wenn *POS* gleich NULL ist.

## <a name="catlmapgetcount"></a><a name="getcount"></a>"Update Map:: GetCount"

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Zuordnung abzurufen.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente im Map-Objekt zurück. Ein einzelnes Element ist ein Schlüssel-Wert-Paar.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>"", "": Gethashtablesize

Mit dieser Methode können Sie die Anzahl der Container in der Hash Tabelle der Zuordnung bestimmen.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Container in der Hash Tabelle zurück. Eine [Erläuterung finden Sie](#catlmap) unter "".

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>"": Getkeyat

Rufen Sie diese Methode auf, um den Schlüssel abzurufen, der an der `CAtlMap` angegebenen Position im-Objekt gespeichert ist.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Schlüssel zurück, der an der angegebenen Position `CAtlMap` im-Objekt gespeichert ist.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapgetnext"></a><a name="getnext"></a>"": GetNext

Rufen Sie diese Methode auf, um einen Zeiger auf das nächste Element paar zu `CAtlMap` erhalten, das im-Objekt gespeichert ist.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das nächste Paar von Schlüssel-Wert-Elementen zurück, die in der Zuordnung gespeichert sind. Der *POS* -Positionswert wird nach jedem-Aufrufpunkt aktualisiert. Wenn das abgerufene Element das letzte in der Zuordnung ist, wird *POS* auf NULL festgelegt.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>"": GetNextAssoc

Ruft das nächste Element für die Iteration ab.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

*key*<br/>
Ein Vorlagen Parameter, der den Typ des Karten Schlüssels angibt.

*value*<br/>
Ein Vorlagen Parameter, der den Typ des Karten Werts angibt.

### <a name="remarks"></a>Bemerkungen

Der *POS* -Positionswert wird nach jedem-Aufrufpunkt aktualisiert. Wenn das abgerufene Element das letzte in der Zuordnung ist, wird *POS* auf NULL festgelegt.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>"": Getnextkey

Rufen Sie diese Methode auf, um den nächsten Schlüssel `CAtlMap` aus dem-Objekt abzurufen.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Schlüssel in der Zuordnung zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positions Leistungspunkt ( *POS*). Wenn in der Zuordnung keine weiteren Einträge vorhanden sind, wird der Positions-Counter auf NULL festgelegt.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>"": Getnextvalue

Mit dieser Methode können Sie den nächsten Wert aus dem `CAtlMap` -Objekt abrufen.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Wert in der Zuordnung zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positions Leistungspunkt ( *POS*). Wenn in der Zuordnung keine weiteren Einträge vorhanden sind, wird der Positions-Counter auf NULL festgelegt.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>"": GetStartPosition

Mit dieser Methode wird eine Karten Iterations Methode gestartet.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Startposition zurück, oder NULL wird zurückgegeben, wenn die Zuordnung leer ist.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie eine Karten iterierung starten, indem Sie einen Positionswert zurückgeben, der `GetNextAssoc` an die-Methode übermittelt werden kann.

> [!NOTE]
> Die Iterations Sequenz ist nicht vorhersagbar.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>"": Getvalueat

Rufen Sie diese Methode auf, um den Wert abzurufen, der an einer `CAtlMap` bestimmten Position im-Objekt gespeichert ist.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den-Wert zurück, der an der angegebenen `CAtlMap` Position im-Objekt gespeichert ist.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>"": ""

Ruft diese Methode auf, um die Hash Tabelle zu initialisieren.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parameter

*nbins*<br/>
Die Anzahl von Containern, die von der Hash Tabelle verwendet werden. Eine [Erläuterung finden Sie](#catlmap) unter "".

*ballocnow*<br/>
Ein Kennzeichen, das angibt, wann Speicher zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei erfolgreicher Initialisierung true zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

`InitHashTable`muss aufgerufen werden, bevor Elemente in der Hash Tabelle gespeichert werden.  Wenn diese Methode nicht explizit aufgerufen wird, wird Sie automatisch aufgerufen, wenn ein Element mit der vom- `CAtlMap` Konstruktor angegebenen Anzahl von Klassen zum ersten Mal hinzugefügt wird.  Andernfalls wird die Zuordnung mit der durch den *nbins* -Parameter angegebenen neuen bin-Anzahl initialisiert.

Wenn der Parameter " *ballocnow* " den Wert "false" hat, wird der von der Hash Tabelle benötigte Arbeitsspeicher erst zugewiesen, wenn er zum ersten Mal benötigt wird. Dies kann hilfreich sein, wenn es unsicher ist, ob die Zuordnung verwendet wird.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapisempty"></a><a name="isempty"></a>"": IsEmpty

Mit dieser Methode können Sie auf ein leeres Map-Objekt testen.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Zuordnung leer ist, andernfalls false.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>"", "", "".

Der Typ, der verwendet wird, wenn eine Taste als Eingabe Argument übermittelt wird.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>"", "": Koutargtype

Der Typ, der verwendet wird, wenn eine Taste als Ausgabe Argument zurückgegeben wird.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>"": Lookup

Mit dieser Methode können Sie Schlüssel oder Werte im- `CAtlMap` Objekt suchen.

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Schlüssel an, der das Element identifiziert, das gesucht werden soll.

*value*<br/>
Eine Variable, die den aufsuchten Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Die erste Form der Methode gibt true zurück, wenn der Schlüssel gefunden wurde, andernfalls false. Das zweite und das dritte Formular geben einen Zeiger auf ein [cpair](#cpair_class) zurück, das als Position für Aufrufe von "" für Aufrufe von "" für ["-Aufrufe](#getnext) " verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

`Lookup`verwendet einen Hash Algorithmus, um schnell das MAP-Element zu finden, das einen Schlüssel enthält, der exakt mit dem angegebenen Schlüsselparameter übereinstimmt.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>"-Operator": Operator\[\]

Ersetzt oder fügt ein neues Element hinzu `CAtlMap`.

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel des Elements, das hinzugefügt oder ersetzt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Wert zurück, der dem angegebenen Schlüssel zugeordnet ist.

### <a name="example"></a>Beispiel

Wenn der Schlüssel bereits vorhanden ist, wird das Element ersetzt. Wenn der Schlüssel nicht vorhanden ist, wird ein neues Element hinzugefügt. Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmaprehash"></a><a name="rehash"></a>"": ""

Ruft diese Methode auf, um das `CAtlMap` Objekt erneut zu durch drücken.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parameter

*nbins*<br/>
Die neue Anzahl von Containern, die in der Hash Tabelle verwendet werden sollen. Eine [Erläuterung finden Sie](#catlmap) unter "".

### <a name="remarks"></a>Bemerkungen

Wenn *nbins* den Wert 0 `CAtlMap` hat, berechnet basierend auf der Anzahl der Elemente in der Zuordnung und der optimalen Last Einstellung eine angemessene Zahl. Normalerweise erfolgt der Vorgang für die Wiederherstellung automatisch, aber wenn "" "" "," ", [:D](#disableautorehash) wenn" "" ".

## <a name="catlmapremoveall"></a><a name="removeall"></a>"": Remote Map:: RemoveAll

Mit dieser Methode können Sie alle Elemente aus dem `CAtlMap` -Objekt entfernen.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Löscht das `CAtlMap` -Objekt und gibt den Arbeitsspeicher frei, der zum Speichern der Elemente verwendet wird.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>"": Removeatpos

Ruft diese Methode auf, um das Element an der angegebenen Position im `CAtlMap` Objekt zu entfernen.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

### <a name="remarks"></a>Bemerkungen

Entfernt das Schlüssel-Wert-Paar, das an der angegebenen Position gespeichert ist. Der zum Speichern des Elements verwendete Arbeitsspeicher wird freigegeben. Die Position, auf die von *POS* verwiesen wird, ist ungültig, und während die Position aller anderen Elemente in der Zuordnung gültig bleibt, behalten Sie nicht notwendigerweise dieselbe Reihenfolge bei.

## <a name="catlmapremovekey"></a><a name="removekey"></a>"": Removekey

Ruft diese Methode auf, um ein Element aus `CAtlMap` dem-Objekt mit dem angegebenen Schlüssel zu entfernen.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel, der dem Element paar entspricht, das Sie entfernen möchten.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Schlüssel gefunden und entfernt wurde, false bei einem Fehler.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#catlmap)

## <a name="catlmapsetat"></a><a name="setat"></a>"":

Mit dieser Methode fügen Sie ein Element Paar in die Zuordnung ein.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselwert, der dem `CAtlMap` -Objekt hinzugefügt werden soll.

*value*<br/>
Der Wert, der dem `CAtlMap` -Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Schlüssel-Wert-Element Paars im- `CAtlMap` Objekt zurück.

### <a name="remarks"></a>Bemerkungen

`SetAt`ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird. Wenn der Schlüssel nicht gefunden wird, wird ein neues Schlüssel-Wert-Paar erstellt.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>"": ""

Ruft diese Methode auf, um die optimale Auslastung des `CAtlMap` -Objekts festzulegen.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parameter

*"f"*<br/>
Das optimale Last Verhältnis.

*flothreshold*<br/>
Der untere Schwellenwert für das Lasten Verhältnis.

*Wert für "f"*<br/>
Der obere Schwellenwert für das Lasten Verhältnis.

*brehashnow*<br/>
Flag zum angeben, ob die Hash Tabelle neu berechnet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode definiert den optimalen ladewert für das `CAtlMap` -Objekt neu. Eine Erläuterung der verschiedenen [Parameter finden Sie](#catlmap) unter "". Wenn *brehashnow* den Wert true hat und die Anzahl der Elemente außerhalb der Mindest-und Höchstwerte liegt, wird die Hash Tabelle neu berechnet.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>"", "": Setvalueat

Ruft diese Methode auf, um den Wert zu ändern, der an einer `CAtlMap` bestimmten Position im-Objekt gespeichert ist.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Befehl [von "](#getnextassoc) " für "" von "" für [CAtlMap::GetStartPosition](#getstartposition)"" ("" "" ")"

*value*<br/>
Der Wert, der dem `CAtlMap` -Objekt hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Ändert das Value-Element, das an der angegebenen Position `CAtlMap` im-Objekt gespeichert ist.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>"": Vinargtype

Der Typ, der verwendet wird, wenn ein Wert als Eingabe Argument übermittelt wird.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>"": Voutargtype

Der Typ, der verwendet wird, wenn ein Wert als Ausgabe Argument ausgegeben wird.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>"": Cpair:: m_key

Der Datenmember, der das Schlüsselelement speichert.

```cpp
const K m_key;
```

### <a name="parameters"></a>Parameter

*Km*<br/>
Der Schlüssel Elementtyp.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>"": Cpair:: m_value

Der Datenmember, der das Value-Element speichert.

```cpp
V  m_value;
```

### <a name="parameters"></a>Parameter

*Ramelow*<br/>
Der Wert Elementtyp.

## <a name="see-also"></a>Weitere Informationen:

[Marquee-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
