---
title: CObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 66d76e0062d13b2bd5a16d9b07f99db9e989805a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753991"
---
# <a name="cobject-class"></a>CObject-Klasse

Die prinzipale Basisklasse für die Microsoft Foundation Class-Bibliothek.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObject::CObject](#cobject)|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|Überprüft die Integrität dieses Objekts.|
|[CObject::Dump](#dump)|Erzeugt ein Diagnose-Dump dieses Objekts.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Gibt `CRuntimeClass` die Struktur zurück, die der Klasse dieses Objekts entspricht.|
|[CObject::IsKindOf](#iskindof)|Testet die Beziehung dieses Objekts zu einer bestimmten Klasse.|
|[CObject::IsSerialisable](#isserializable)|Testet, ob dieses Objekt serialisiert werden kann.|
|[CObject::Serialisieren](#serialize)|Lädt oder speichert ein Objekt aus/in einem Archiv.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObject::operator löschen](#operator_delete)|Spezieller **Löschoperator.**|
|[CObject::operator neu](#operator_new)|Spezieller **neuer** Bediener.|

## <a name="remarks"></a>Bemerkungen

Es dient als Stamm nicht nur `CFile` für `CObList`Bibliotheksklassen wie und , sondern auch für die Klassen, die Sie schreiben. `CObject`grundlegende Dienstleistungen erbringt, einschließlich

- Serialisierungsunterstützung

- Laufzeitklasseninformationen

- Objektdiagnoseausgabe

- Kompatibilität mit Auflistungsklassen

Beachten `CObject` Sie, dass die mehrfache Vererbung nicht unterstützt wird. Ihre abgeleiteten Klassen `CObject` können nur eine `CObject` Basisklasse haben, und diese muss in der Hierarchie am weitesten links sein. Es ist jedoch zulässig, Strukturen und `CObject`nicht abgeleitete Klassen in rechtshändigen Zweigen mit mehrfacher Vererbung zu haben.

Sie werden große `CObject` Vorteile aus der Ableitung ziehen, wenn Sie einige der optionalen Makros in Ihrer Klassenimplementierung und deklarationen verwenden.

Die Makros der ersten Ebene, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) und [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), ermöglichen den Laufzeitzugriff auf den Klassennamen und seine Position in der Hierarchie. Dies wiederum ermöglicht ein sinnvolles diagnostisches Dumping.

Die Makros der zweiten Ebene, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), enthalten alle Funktionen der Makros der ersten Ebene und ermöglichen es, ein Objekt in ein "Archiv" zu und von einem "Archiv" zu "serialisieren".

Informationen zum Ableiten von Microsoft Foundation-Klassen und C++-Klassen im Allgemeinen und verwenden von finden Sie unter `CObject`Verwenden von [CObject](../../mfc/using-cobject.md) und [Serialisierung](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::AssertValid

Überprüft die Integrität dieses Objekts.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

`AssertValid`führt eine Gültigkeitsprüfung für dieses Objekt durch, indem der interne Status überprüft wird. In der Debug-Version `AssertValid` der Bibliothek kann das Programm mit einer Meldung bestätigt und beendet werden, die die Zeilennummer und den Dateinamen auflistet, bei denen die Assertion fehlgeschlagen ist.

Wenn Sie eine eigene Klasse schreiben, `AssertValid` sollten Sie die Funktion überschreiben, um Diagnosedienste für sich selbst und andere Benutzer Ihrer Klasse bereitzustellen. Der überschriebene `AssertValid` `AssertValid` ruft in der Regel die Funktion seiner Basisklasse auf, bevor Datenmember überprüft werden, die für die abgeleitete Klasse eindeutig sind.

Da `AssertValid` es sich um eine **const-Funktion** handelt, ist es Ihnen nicht gestattet, den Objektstatus während des Tests zu ändern. Ihre eigenen `AssertValid` abgeleiteten Klassenfunktionen sollten keine Ausnahmen auslösen, sondern vielmehr bestätigen, ob sie ungültige Objektdaten erkennen.

Die Definition von "Gültigkeit" hängt von der Klasse des Objekts ab. In der Regel sollte die Funktion eine "flache Prüfung" durchführen. Das heißt, wenn ein Objekt Zeiger auf andere Objekte enthält, sollte es überprüfen, ob die Zeiger nicht NULL sind, aber es sollte keine Gültigkeitstests für die Objekte durchführen, auf die die Zeiger verweisen.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Ein weiteres Beispiel finden Sie unter [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject::CObject

Diese Funktionen sind `CObject` die Standardkonstruktoren.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parameter

*objectSrc*<br/>
Ein Verweis auf eine andere`CObject`

### <a name="remarks"></a>Bemerkungen

Die Standardversion wird automatisch vom Konstruktor der abgeleiteten Klasse aufgerufen.

Wenn Ihre Klasse serialisierbar ist (sie enthält das IMPLEMENT_SERIAL Makro), müssen Sie einen Standardkonstruktor (einen Konstruktor ohne Argumente) in Ihrer Klassendeklaration haben. Wenn Sie keinen Standardkonstruktor benötigen, deklarieren Sie einen privaten oder geschützten "leeren" Konstruktor. Weitere Informationen finden Sie unter [Verwenden von CObject](../../mfc/using-cobject.md).

Der Standard-C++-Standardklassenkopierkonstruktor führt eine Member-für-Member-Kopie durch. Das Vorhandensein des `CObject` privaten Kopierkonstruktors garantiert eine Compilerfehlermeldung, wenn der Kopierkonstruktor Ihrer Klasse benötigt, aber nicht verfügbar ist. Sie müssen daher einen Kopierkonstruktor bereitstellen, wenn Ihre Klasse diese Funktion erfordert.

### <a name="example"></a>Beispiel

Eine Auflistung der in den `CAge` `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

Übergibt den Inhalt des Objekts in ein [CDumpContext-Objekt.](../../mfc/reference/cdumpcontext-class.md)

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
Der Diagnose-Dump-Kontext `afxDump`für Dumping, in der Regel .

### <a name="remarks"></a>Bemerkungen

Wenn Sie eine eigene Klasse schreiben, `Dump` sollten Sie die Funktion überschreiben, um Diagnosedienste für sich selbst und andere Benutzer Ihrer Klasse bereitzustellen. Der überschriebene `Dump` `Dump` ruft in der Regel die Funktion seiner Basisklasse auf, bevor Datenmember gedruckt werden, die für die abgeleitete Klasse eindeutig sind. `CObject::Dump`druckt den Klassennamen, `IMPLEMENT_DYNAMIC` wenn Ihre Klasse das oder IMPLEMENT_SERIAL-Makro verwendet.

> [!NOTE]
> Ihre `Dump` Funktion sollte am Ende der Ausgabe kein Zeilenumleinenzeichen drucken.

`Dump`Aufrufe sind nur in der Debugversion der Microsoft Foundation-Klassenbibliothek sinnvoll. Sie sollten Aufrufe, Funktionsdeklarationen und Funktionsimplementierungen mit **#ifdef _DEBUG** /  `#endif` Anweisungen für die bedingte Kompilierung in Klammern klammern.

Da `Dump` es sich um eine **const-Funktion** handelt, ist es Ihnen nicht gestattet, den Objektstatus während des Dumps zu ändern.

Der [CDumpContext-Einfügeoperator (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) ruft auf, `Dump` wenn ein `CObject` Zeiger eingefügt wird.

`Dump`erlaubt nur "azyklisches" Dumping von Gegenständen. Sie können z. B. eine Liste von Objekten ausdumpen, aber wenn eines der Objekte die Liste selbst ist, werden Sie den Stapel schließlich überlaufen.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject::GetRuntimeClass

Gibt `CRuntimeClass` die Struktur zurück, die der Klasse dieses Objekts entspricht.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [CRuntimeClass-Struktur,](../../mfc/reference/cruntimeclass-structure.md) die der Klasse dieses Objekts entspricht. nie **NULL**.

### <a name="remarks"></a>Bemerkungen

Es gibt `CRuntimeClass` eine `CObject`Struktur für jede -abgeleitete Klasse. Die Strukturelemente sind wie folgt:

- **LPCSTR-m_lpszClassName** Eine null-terminierte Zeichenfolge, die den ASCII-Klassennamen enthält.

- **int m_nObjectSize** Die Größe des Objekts in Bytes. Wenn das Objekt über Datenmember verfügt, die auf zugewiesenen Speicher verweisen, ist die Größe dieses Speichers nicht enthalten.

- **UINT-m_wSchema** Die Schemanummer ( - 1 für nicht serialisierbare Klassen). Eine [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) Beschreibung der Schemanummer finden Sie im IMPLEMENT_SERIAL-Makro.

- **CObject\* (\* PASCAL m_pfnCreateObject )( )** Ein Funktionszeiger auf den Standardkonstruktor, der ein Objekt Ihrer Klasse erstellt (gültig nur, wenn die Klasse die dynamische Erstellung unterstützt; andernfalls gibt **NULL**zurück).

- **CRuntimeClass\* (\* PASCAL m_pfn_GetBaseClass )( )** Wenn Ihre Anwendung dynamisch mit der AFXDLL-Version von `CRuntimeClass` MFC verknüpft ist, ein Zeiger auf eine Funktion, die die Struktur der Basisklasse zurückgibt.

- **CRuntimeClass\* m_pBaseClass** Wenn Ihre Anwendung statisch mit MFC verknüpft `CRuntimeClass` ist, ein Zeiger auf die Struktur der Basisklasse.

Diese Funktion erfordert die Verwendung des [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)oder [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) Makros in der Klassenimplementierung. Andernfalls erhalten Sie falsche Ergebnisse.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject::IsKindOf

Testet die Beziehung dieses Objekts zu einer bestimmten Klasse.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parameter

*pKlasse*<br/>
Ein Zeiger auf eine [CRuntimeClass-Struktur,](../../mfc/reference/cruntimeclass-structure.md) die Ihrer `CObject`-derived-Klasse zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt der Klasse entspricht; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion testet *pClass,* um festzustellen, ob (1) es ein Objekt der angegebenen Klasse oder (2) ein Objekt einer Klasse ist, die von der angegebenen Klasse abgeleitet ist. Diese Funktion funktioniert nur für [Klassen,](run-time-object-model-services.md#declare_dynamic)die mit dem Makro DECLARE_DYNAMIC , [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)oder [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) deklariert sind.

Verwenden Sie diese Funktion nicht ausgiebig, da sie die C++-Polymorphiefunktion besiegt. Verwenden Sie stattdessen virtuelle Funktionen.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject::IsSerialisable

Testet, ob dieses Objekt für die Serialisierung in Frage kommt.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn dieses Objekt serialisiert werden kann; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Damit eine Klasse serialisierbar ist, muss ihre Deklaration die [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) Makros enthalten, und die Implementierung muss das [IMPLEMENT_SERIAL-Makros](run-time-object-model-services.md#implement_serial) enthalten.

> [!NOTE]
> Überschreiben Sie diese Funktion nicht.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::operator löschen

Für die Release-Version der Bibliothek gibt der Operator **delete** den vom Operator **new**zugewiesenen Speicher frei.

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Bemerkungen

In der Debugversion nimmt operator **delete** an einem Zuweisungsüberwachungsschema teil, das Speicherverluste erkennen soll.

Wenn Sie die Codezeile verwenden

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

vor einer Ihrer Implementierungen in einem . CPP-Datei, dann wird die dritte Version von **delete** verwendet werden, speichern Sie den Dateinamen und Zeilennummer in der zugewiesenen Block für spätere Berichte. Sie müssen sich keine Sorgen um die Bereitstellung der zusätzlichen Parameter machen; ein Makro kümmert sich um Sie.

Auch wenn Sie DEBUG_NEW im Debug-Modus nicht verwenden, erhalten Sie dennoch eine Leckerkennung, jedoch ohne die oben beschriebene Quelldateizeilennummer..

Wenn Sie Operatoren **neu** überschreiben und **löschen,** verlieren Sie diese Diagnosefunktion.

### <a name="example"></a>Beispiel

Eine Auflistung der in den `CAge` `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::operator neu

Für die Release-Version der Bibliothek führt der Operator **new** `malloc`eine optimale Speicherzuweisung in ähnlicher Weise aus.

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Bemerkungen

In der Debugversion nimmt der Operator **new** an einem Zuweisungsüberwachungsschema teil, das Speicherverluste erkennen soll.

Wenn Sie die Codezeile verwenden

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

vor einer Ihrer Implementierungen in einem . CPP-Datei, dann wird die zweite Version von **new** verwendet werden, speichern Sie den Dateinamen und Zeilennummer in der zugewiesenen Block für spätere Berichte. Sie müssen sich keine Sorgen um die Bereitstellung der zusätzlichen Parameter machen; ein Makro kümmert sich um Sie.

Auch wenn Sie DEBUG_NEW im Debug-Modus nicht verwenden, erhalten Sie dennoch eine Leckerkennung, jedoch ohne die oben beschriebene Quelldateizeilennummer..

> [!NOTE]
> Wenn Sie diesen Operator überschreiben, müssen Sie auch **delete**überschreiben. Verwenden Sie nicht `_new_handler` die Standardbibliotheksfunktion.

### <a name="example"></a>Beispiel

Eine Auflistung der in den `CAge` `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject::Serialisieren

Liest oder schreibt dieses Objekt aus einem oder in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
Ein `CArchive` Objekt, das zu oder von serialisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Sie müssen `Serialize` für jede Klasse überschreiben, die Sie serialisieren möchten. Der überschriebene `Serialize` muss `Serialize` zuerst die Funktion seiner Basisklasse aufrufen.

Sie müssen auch das [DECLARE_SERIAL-Makro](run-time-object-model-services.md#declare_serial) in der Klassendeklaration und das [IMPLEMENT_SERIAL-Makro](run-time-object-model-services.md#implement_serial) in der Implementierung verwenden.

Verwenden Sie [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) oder [CArchive::IsStoring,](../../mfc/reference/carchive-class.md#isstoring) um zu bestimmen, ob das Archiv geladen oder gespeichert wird.

`Serialize`wird von [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) und [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)aufgerufen. Diese Funktionen sind `CArchive` dem Einfügeoperator ( ** < ** **>>**) und dem Extraktionsoperator ( ) zugeordnet.

Beispiele für die Serialisierung finden Sie im Artikel [Serialisierung: Serialisieren eines Objekts](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge` in allen `CObject` Beispielen verwendeten Klasse finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
