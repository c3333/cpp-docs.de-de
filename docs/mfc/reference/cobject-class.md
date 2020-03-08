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
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855294"
---
# <a name="cobject-class"></a>CObject-Klasse

Die prinzipale Basisklasse für die Microsoft Foundation Class-Bibliothek.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CObject:: CObject](#cobject)|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|Überprüft die Integrität dieses Objekts.|
|[CObject::D UMP](#dump)|Erzeugt ein DIAGNOSEDUMP für dieses Objekt.|
|[CObject:: getruntimeclass](#getruntimeclass)|Gibt die `CRuntimeClass`-Struktur zurück, die der-Klasse dieses-Objekts entspricht.|
|[CObject:: IsKindOf](#iskindof)|Testet die Beziehung dieses Objekts mit einer angegebenen Klasse.|
|[CObject:: isserialisierbar](#isserializable)|Testet, ob dieses Objekt serialisiert werden kann.|
|[CObject:: Serialize](#serialize)|Lädt oder speichert ein Objekt aus einem oder in ein Archiv.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CObject:: Operator Delete](#operator_delete)|Spezieller **Delete** -Operator.|
|[CObject:: Operator New](#operator_new)|Spezieller **New** -Operator.|

## <a name="remarks"></a>Hinweise

Es dient nicht nur als Stammverzeichnis für Bibliotheks Klassen wie `CFile` und `CObList`, sondern auch für die Klassen, die Sie schreiben. `CObject` stellt grundlegende Dienste bereit, einschließlich

- Serialisierungsunterstützung

- Lauf Zeit Klassen Informationen

- Objekt Diagnoseausgabe

- Kompatibilität mit Sammlungs Klassen

Beachten Sie, dass `CObject` die mehrfache Vererbung nicht unterstützt. Die abgeleiteten Klassen können nur über eine `CObject` Basisklasse verfügen, und diese `CObject` müssen sich in der Hierarchie ganz links befinden. Es ist jedoch zulässig, Strukturen und nicht `CObject`abgeleitete Klassen in den Verzweigungen mit mehreren Vererbungen in der rechten Hand zu haben.

Sie werden wichtige Vorteile von der `CObject` Ableitung erzielen, wenn Sie einige optionale Makros in der Klassen Implementierung und in Deklarationen verwenden.

Die Makros der ersten Ebene, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) und [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), ermöglichen den Lauf Zeit Zugriff auf den Klassennamen und seine Position in der Hierarchie. Dies wiederum ermöglicht ein sinnvolles Diagnose dumpverfahren.

Die Makros der zweiten Ebene, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), beinhalten die gesamte Funktionalität der Makros der ersten Ebene und ermöglichen es, dass ein Objekt in ein und aus einem "Archiv" serialisiert wird.

Weitere Informationen zum Ableiten von Microsoft Foundation- C++ Klassen und-Klassen im allgemeinen und Verwenden von `CObject`finden [Sie unter Verwenden von CObject](../../mfc/using-cobject.md) und [Serialisierung](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CObject`

## <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="assertvalid"></a>CObject:: AssertValid

Überprüft die Integrität dieses Objekts.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Hinweise

`AssertValid` führt eine Gültigkeits Überprüfung für dieses Objekt durch, indem es den internen Zustand prüft. In der Debugversion der Bibliothek kann `AssertValid` das Programm bestätigen und damit das Programm mit einer Meldung beenden, in der die Zeilennummer und der Dateiname aufgeführt werden, bei denen die Annahme fehlgeschlagen ist

Wenn Sie eine eigene Klasse schreiben, sollten Sie die `AssertValid`-Funktion überschreiben, um Diagnosedienste für sich selbst und andere Benutzer Ihrer Klasse bereitzustellen. Der überschriebene `AssertValid` ruft in der Regel die `AssertValid`-Funktion der Basisklasse auf, bevor die für die abgeleitete Klasse eindeutigen Datenelemente überprüft werden.

Da **`AssertValid` eine Konstante** Funktion ist, ist es nicht zulässig, den Objektzustand während des Tests zu ändern. Ihre eigenen abgeleiteten Klassen `AssertValid` Funktionen sollten keine Ausnahmen auslösen, sondern bestätigen, dass Sie ungültige Objektdaten erkennen.

Die Definition von "Gültigkeit" hängt von der Klasse des Objekts ab. Als Regel sollte die Funktion eine "flache Prüfung" durchführen. Das heißt, wenn ein Objekt Zeiger auf andere Objekte enthält, sollte überprüft werden, ob die Zeiger nicht NULL sind, aber es sollte keine Gültigkeitsprüfung für die Objekte durchgeführt werden, auf die von den Zeigern verwiesen wird.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Ein weiteres Beispiel finden Sie unter [afxdoforzugewiesene bjects](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>CObject:: CObject

Diese Funktionen sind die Standardkonstruktoren `CObject`.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parameter

*objecfs*<br/>
Ein Verweis auf einen anderen `CObject`

### <a name="remarks"></a>Hinweise

Die Standardversion wird automatisch vom Konstruktor ihrer abgeleiteten Klasse aufgerufen.

Wenn Ihre Klasse serialisierbar ist (Sie enthält das IMPLEMENT_SERIAL Makro), benötigen Sie einen Standardkonstruktor (einen Konstruktor ohne Argumente) in der Klassen Deklaration. Wenn Sie keinen Standardkonstruktor benötigen, deklarieren Sie einen privaten oder geschützten "leeren" Konstruktor. Weitere Informationen finden Sie unter [Verwenden von CObject](../../mfc/using-cobject.md).

Der Standardkopierkonstruktor C++ der Standardklasse führt eine Member-by-Member-Kopie aus. Das vorhanden sein des privaten `CObject` Kopierkonstruktors garantiert eine Compilerfehlermeldung, wenn der Kopierkonstruktor der Klasse erforderlich, aber nicht verfügbar ist. Sie müssen daher einen Kopierkonstruktor bereitstellen, wenn Ihre Klasse diese Funktion benötigt.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in den `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>CObject::D UMP

Sichert den Inhalt des-Objekts in ein [CDumpContext](../../mfc/reference/cdumpcontext-class.md) -Objekt.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parameter

*dc*<br/>
Der diagnosedumpkontext für das sichern, normalerweise `afxDump`.

### <a name="remarks"></a>Hinweise

Wenn Sie eine eigene Klasse schreiben, sollten Sie die `Dump`-Funktion überschreiben, um Diagnosedienste für sich selbst und andere Benutzer Ihrer Klasse bereitzustellen. Der überschriebene `Dump` ruft in der Regel die `Dump`-Funktion der Basisklasse auf, bevor Datenelemente gedruckt werden, die für die abgeleitete Klasse eindeutig sind `CObject::Dump` druckt den Klassennamen, wenn die Klasse das `IMPLEMENT_DYNAMIC` oder IMPLEMENT_SERIAL Makro verwendet.

> [!NOTE]
>  Die `Dump` Funktion sollte am Ende der Ausgabe kein Zeilen vorzeitiges Zeichen drucken.

`Dump` Aufrufe sind nur in der Debugversion des Microsoft Foundation Class-Bibliothek sinnvoll. Sie sollten Aufrufe, Funktions Deklarationen und Funktions Implementierungen mit **#ifdef _DEBUG**/ `#endif` Anweisungen für die bedingte Kompilierung anklammern.

Da **`Dump` eine Konstante** Funktion ist, ist es nicht zulässig, den Objektzustand während des Abbilds zu ändern.

Der [CDumpContext-Operator zum Einfügen (< <)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) ruft `Dump` auf, wenn ein `CObject` Zeiger eingefügt wird.

`Dump` gestattet nur das "acyclic"-Dump von Objekten. Sie können z. b. eine Liste von Objekten sichern, aber wenn eines der Objekte die Liste selbst ist, führen Sie letztendlich einen Überlauf des Stapels aus.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>CObject:: getruntimeclass

Gibt die `CRuntimeClass`-Struktur zurück, die der-Klasse dieses-Objekts entspricht.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die der Klasse dieses Objekts entspricht. nie **null**.

### <a name="remarks"></a>Hinweise

Es gibt eine `CRuntimeClass` Struktur für jede `CObject`abgeleitete Klasse. Die Strukturmember lauten wie folgt:

- **LPCSTR m_lpszClassName** Eine mit NULL endenden Zeichenfolge, die den ASCII-Klassennamen enthält.

- **int-m_nObjectSize** Die Größe des-Objekts in Bytes. Wenn das-Objekt über Datenmember verfügt, die auf zugeordneten Arbeitsspeicher zeigen, ist die Größe dieses Speichers nicht inbegriffen.

- **Uint-m_wSchema** Die Schema Nummer (-1 für nicht serialisierbare Klassen). Eine Beschreibung der Schema Nummer finden Sie im [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makro.

- **CObject-\* (Pascal\* m_pfnCreateObject) ()** Ein Funktionszeiger auf den Standardkonstruktor, der ein Objekt der Klasse erstellt (nur gültig, wenn die Klasse die dynamische Erstellung unterstützt), andernfalls wird **null**zurückgegeben.

- **CRuntimeClass-\* (Pascal\* m_pfn_GetBaseClass) ()** Wenn die Anwendung dynamisch mit der AFXDLL-Version von MFC verknüpft ist, ein Zeiger auf eine Funktion, die die `CRuntimeClass` Struktur der Basisklasse zurückgibt.

- **CRuntimeClass-\* m_pBaseClass** Wenn die Anwendung statisch mit MFC verknüpft ist, ein Zeiger auf die `CRuntimeClass` Struktur der Basisklasse.

Diese Funktion erfordert die Verwendung des [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)-, [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)-oder [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makros in der Klassen Implementierung. Andernfalls erhalten Sie falsche Ergebnisse.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>CObject:: IsKindOf

Testet die Beziehung dieses Objekts mit einer angegebenen Klasse.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parameter

*pclass*<br/>
Ein Zeiger auf eine [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die der von `CObject`abgeleiteten Klasse zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das-Objekt der-Klasse entspricht. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion testet *pClass* , um festzustellen, ob es sich um ein Objekt der angegebenen Klasse handelt, oder (2) Es handelt sich um ein Objekt einer Klasse, die von der angegebenen Klasse abgeleitet ist. Diese Funktion funktioniert nur für Klassen, die mit dem [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)-, [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)-oder [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) -Makro deklariert werden.

Verwenden Sie diese Funktion nicht häufig, da Sie die C++ Polymorphie-Funktion verfehlt. Verwenden Sie stattdessen virtuelle Funktionen.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>CObject:: isserialisierbar

Testet, ob dieses Objekt für die Serialisierung geeignet ist.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn dieses Objekt serialisiert werden kann. andernfalls 0.

### <a name="remarks"></a>Hinweise

Damit eine Klasse serialisierbar ist, muss die Deklaration das [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) -Makro enthalten, und die Implementierung muss das [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makro enthalten.

> [!NOTE]
>  Überschreiben Sie diese Funktion nicht.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>CObject:: Operator Delete

Bei der Releaseversion der Bibliothek gibt der Operator **Delete** den von Operator **New**zugewiesenen Arbeitsspeicher frei.

```
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Hinweise

In der Debugversion ist der Operator **Delete** an einem Zuordnungs Überwachungssystem beteiligt, das zum Erkennen von Speicher Verlusten entworfen wurde.

Wenn Sie die Codezeile verwenden

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

vor einer ihrer Implementierungen in einer. Cpp-Datei, anschließend wird die dritte Version von **Delete** verwendet, in der der Dateiname und die Zeilennummer im zugeordneten-Block für die spätere Berichterstellung gespeichert werden. Sie müssen sich keine Gedanken über die Bereitstellung zusätzlicher Parameter machen. ein Makro übernimmt das für Sie.

Auch wenn Sie DEBUG_NEW nicht im Debugmodus verwenden, erhalten Sie immer noch eine Fehlererkennung, aber ohne die oben beschriebene Zeilennummern Berichterstattung der Quelldatei.

Wenn Sie die Operatoren " **New** " und " **Delete**" überschreiben, haben Sie diese Diagnosefunktion nicht mehr

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in den `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>CObject:: Operator New

Bei der Releaseversion der Bibliothek führt Operator **New** eine optimale Speicher Belegung auf ähnliche Weise wie `malloc`aus.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Hinweise

In der Debugversion ist Operator **New** an einem Zuordnungs Überwachungssystem beteiligt, das zum Erkennen von Speicher Verlusten konzipiert ist.

Wenn Sie die Codezeile verwenden

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

vor einer ihrer Implementierungen in einer. Cpp-Datei, anschließend wird die zweite Version von **New** verwendet, in der der Dateiname und die Zeilennummer im zugeordneten-Block für die spätere Berichterstellung gespeichert werden. Sie müssen sich keine Gedanken über die Bereitstellung zusätzlicher Parameter machen. ein Makro übernimmt das für Sie.

Auch wenn Sie DEBUG_NEW nicht im Debugmodus verwenden, erhalten Sie immer noch eine Fehlererkennung, aber ohne die oben beschriebene Zeilennummern Berichterstattung der Quelldatei.

> [!NOTE]
>  Wenn Sie diesen Operator überschreiben, müssen Sie auch **Delete**überschreiben. Verwenden Sie die `_new_handler`-Funktion der Standardbibliothek nicht.

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in den `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>CObject:: Serialize

Liest oder schreibt dieses Objekt aus einem oder in ein Archiv.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*Tempel*<br/>
Ein `CArchive` Objekt, das in oder aus serialisiert werden soll.

### <a name="remarks"></a>Hinweise

Sie müssen `Serialize` für jede Klasse überschreiben, die Sie serialisieren möchten. Die überschriebene `Serialize` muss zuerst die `Serialize`-Funktion ihrer Basisklasse aufzurufen.

Sie müssen auch das [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) -Makro in der Klassen Deklaration verwenden, und Sie müssen das [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makro in der-Implementierung verwenden.

Verwenden Sie " [CArchive:: isload](../../mfc/reference/carchive-class.md#isloading) " oder " [CArchive:: isspeichert](../../mfc/reference/carchive-class.md#isstoring) ", um zu bestimmen, ob das Archiv geladen oder gespeichert wird.

`Serialize` wird von " [CArchive:: Read Object](../../mfc/reference/carchive-class.md#readobject) " und " [CArchive:: schreiteobject](../../mfc/reference/carchive-class.md#writeobject)" aufgerufen. Diese Funktionen sind dem `CArchive` einfügeoperator ( **<\<** ) und dem Extraktions Operator ( **>>** ) zugeordnet.

Beispiele für die Serialisierung finden Sie im Artikel [Serialisierung: Serialisieren eines Objekts](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen `CObject` Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
