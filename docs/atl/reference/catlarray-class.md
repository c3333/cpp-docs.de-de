---
title: Asslarray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423459"
---
# <a name="catlarray-class"></a>Asslarray-Klasse

Diese Klasse implementiert ein Array Objekt.

## <a name="syntax"></a>Syntax

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parameter

*E*<br/>
Der Typ der im Array gespeicherten Daten.

*Echarakteristika*<br/>
Der Code, der zum Kopieren oder Verschieben von Elementen verwendet wird.

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Add](#add)|Mit dieser Methode können Sie dem Array Objekt ein Element hinzufügen.|
|[Append](#append)|Ruft diese Methode auf, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.|
|["AssertValid"](#assertvalid)|Mit dieser Methode können Sie bestätigen, dass das Array Objekt gültig ist.|
|[.](#catlarray)|Der Konstruktor.|
|[~-Größe](#dtor)|Der Destruktor.|
|[Kopieren](#copy)|Ruft diese Methode auf, um die Elemente eines Arrays in ein anderes Array zu kopieren.|
|["Freextra"](#freeextra)|Diese Methode wird aufgerufen, um leere Elemente aus dem Array zu entfernen.|
|[GetAt](#getat)|Rufen Sie diese Methode auf, um ein einzelnes Element aus dem Array Objekt abzurufen.|
|[GetCount](#getcount)|Mit dieser Methode wird die Anzahl der im Array gespeicherten Elemente zurückgegeben.|
|[GetData](#getdata)|Ruft diese Methode auf, um einen Zeiger auf das erste Element im Array zurückzugeben.|
|[Insertarrayat](#insertarrayat)|Ruft diese Methode auf, um ein Array in ein anderes einzufügen.|
|[InsertAt](#insertat)|Mit dieser Methode können Sie ein neues Element (oder mehrere Kopien eines Elements) in das Array Objekt einfügen.|
|[IsEmpty](#isempty)|Mit dieser Methode können Sie überprüfen, ob das Array leer ist.|
|[RemoveAll](#removeall)|Mit dieser Methode können Sie alle Elemente aus dem Array Objekt entfernen.|
|[RemoveAt](#removeat)|Diese Methode wird aufgerufen, um ein oder mehrere Elemente aus dem Array zu entfernen.|
|[SetAt](#setat)|Ruft diese Methode auf, um den Wert eines Elements im Array Objekt festzulegen.|
|["Antatwächst"](#setatgrow)|Ruft diese Methode auf, um den Wert eines Elements im Array Objekt festzulegen und das Array nach Bedarf zu erweitern.|
|[SetCount](#setcount)|Ruft diese Methode auf, um die Größe des Array Objekts festzulegen.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[KOM&#91;&#93;](#operator_at)|Ruft diesen Operator auf, um einen Verweis auf ein Element im Array zurückzugeben.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[Inargtype](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Array verwendet werden soll.|
|[Outargtype](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Array verwendet werden soll.|

## <a name="remarks"></a>Hinweise

`CAtlArray` stellt Methoden zum Erstellen und Verwalten eines Arrays von Elementen eines benutzerdefinierten Typs bereit. Obwohl die Standard-C-Arrays ähnlich sind, kann das `CAtlArray`-Objekt bei Bedarf dynamisch verkleinert und vergrößert werden. Der Array Index beginnt immer an Position 0, und die obere Grenze kann korrigiert oder erweitert werden, wenn neue Elemente hinzugefügt werden.

Für Arrays mit einer kleinen Anzahl von Elementen kann die ATL-Klasse [CSimpleArray](../../atl/reference/csimplearray-class.md) verwendet werden.

`CAtlArray` ist eng mit der `CArray`-Klasse von MFC verknüpft und funktioniert in einem MFC-Projekt, wenn auch ohne Serialisierungsunterstützung.

Weitere Informationen finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="requirements"></a>Voraussetzungen

**Header:** atlcoll. h

##  <a name="add"></a>"Update":: Add

Mit dieser Methode können Sie dem Array Objekt ein Element hinzufügen.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parameter

*gewisses*<br/>
Das Element, das dem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des hinzugefügten Elements zurück.

### <a name="remarks"></a>Hinweise

Das neue Element wird am Ende des Arrays hinzugefügt. Wenn kein-Element bereitgestellt wird, wird ein leeres-Element hinzugefügt. Das heißt, dass das Array so erhöht wird, als ob ein reales Element hinzugefügt wurde. Wenn der Vorgang fehlschlägt, wird " [atlthrow](debugging-and-error-reporting-global-functions.md#atlthrow) " mit dem Argument E_OUTOFMEMORY aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>"": Anfügen

Ruft diese Methode auf, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parameter

*ASRC*<br/>
Das anzufügende Array.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des ersten angefügten Elements zurück.

### <a name="remarks"></a>Hinweise

Die Elemente im angegebenen Array werden am Ende des vorhandenen Arrays hinzugefügt. Bei Bedarf wird der Arbeitsspeicher zugeordnet, um die neuen Elemente zu unterstützen.

Die Arrays müssen denselben Typ aufweisen, und es ist nicht möglich, ein Array an sich selbst anzufügen.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das `CAtlArray`-Argument kein gültiges Array ist oder wenn *ASRC* auf dasselbe Objekt verweist. In Releasebuilds können ungültige Argumente zu unvorhersehbarem Verhalten führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>"": AssertValid "

Mit dieser Methode können Sie bestätigen, dass das Array Objekt gültig ist.

```
void AssertValid() const;
```

### <a name="remarks"></a>Hinweise

Wenn das Array Objekt nicht gültig ist, löst ATLASSERT eine-Assertionen aus. Diese Methode ist nur verfügbar, wenn _DEBUG definiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>"":

Der Konstruktor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Hinweise

Initialisiert das Array Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>"": ""

Der Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Hinweise

Gibt alle Ressourcen frei, die vom Array Objekt verwendet werden.

##  <a name="copy"></a>"": Kopieren

Ruft diese Methode auf, um die Elemente eines Arrays in ein anderes Array zu kopieren.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parameter

*ASRC*<br/>
Die Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Hinweise

Mit dieser Methode können Sie Elemente eines Arrays mit den Elementen eines anderen Arrays überschreiben. Bei Bedarf wird der Arbeitsspeicher zugeordnet, um die neuen Elemente zu unterstützen. Es ist nicht möglich, Elemente eines Arrays in sich selbst zu kopieren.

Wenn der vorhandene Inhalt des Arrays beibehalten werden soll [, verwenden Sie](#append) stattdessen "".

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das vorhandene `CAtlArray` Objekt ungültig ist, oder wenn *ASRC* auf dasselbe Objekt verweist. In Releasebuilds können ungültige Argumente zu unvorhersehbarem Verhalten führen.

> [!NOTE]
> `CAtlArray::Copy` unterstützt keine Arrays, die aus Elementen bestehen, die mit der [cautoptr](../../atl/reference/cautoptr-class.md) -Klasse erstellt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>"Update":: freextra

Diese Methode wird aufgerufen, um leere Elemente aus dem Array zu entfernen.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Hinweise

Alle leeren Elemente werden entfernt, aber die Größe und die obere Grenze des Arrays bleiben unverändert.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das-Objekt nicht gültig ist, oder wenn das Array seine maximale Größe überschreiten würde.

##  <a name="getat"></a>"Update":: GetAt

Rufen Sie diese Methode auf, um ein einzelnes Element aus dem Array Objekt abzurufen.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Indexwert des zurück zugebende Array Elements.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das erforderliche Array Element zurück.

### <a name="remarks"></a>Hinweise

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *IElement* die Anzahl der Elemente im Array überschreitet. In Releasebuilds kann ein ungültiges Argument zu unvorhersehbarem Verhalten führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>"Chanlarray:: GetCount"

Mit dieser Methode wird die Anzahl der im Array gespeicherten Elemente zurückgegeben.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im Array gespeicherten Elemente zurück.

### <a name="remarks"></a>Hinweise

Da sich das erste Element im Array an Position 0 befindet, ist der von `GetCount` zurückgegebene Wert immer 1 größer als der größte Index.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "](#getat)".

##  <a name="getdata"></a>"": GetData

Ruft diese Methode auf, um einen Zeiger auf das erste Element im Array zurückzugeben.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Speicherort zurück, der das erste Element im Array speichert. Wenn keine Elemente verfügbar sind, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>"": Inargtype

Der Datentyp, der zum Hinzufügen von Elementen zum Array verwendet werden soll.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>"": Insertarrayat

Ruft diese Methode auf, um ein Array in ein anderes einzufügen.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parameter

*iStart*<br/>
Der Index, an dem das Array eingefügt werden soll.

*Panew*<br/>
Das Array, das eingefügt werden soll.

### <a name="remarks"></a>Hinweise

Elemente aus dem *arraypanew* werden in das Array Objekt kopiert, beginnend bei Element *iStart*. Die vorhandenen Array Elemente werden verschoben, damit Sie nicht überschrieben werden.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das `CAtlArray` Objekt ungültig ist, oder wenn der *Panew* -Zeiger NULL oder ungültig ist.

> [!NOTE]
> `CAtlArray::InsertArrayAt` unterstützt keine Arrays, die aus Elementen bestehen, die mit der [cautoptr](../../atl/reference/cautoptr-class.md) -Klasse erstellt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>"Update":: InsertAt

Mit dieser Methode können Sie ein neues Element (oder mehrere Kopien eines Elements) in das Array Objekt einfügen.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Index, an dem das Element oder die Elemente eingefügt werden sollen.

*gewisses*<br/>
Der Wert des Elements, das eingefügt werden soll.

*nCount*<br/>
Die Anzahl der hinzu zufügenden Elemente.

### <a name="remarks"></a>Hinweise

Fügt ein oder mehrere Elemente in das Array ein, beginnend bei Index *IElement*. Vorhandene Elemente werden verschoben, damit Sie nicht überschrieben werden.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das `CAtlArray` Objekt ungültig ist, die Anzahl der hinzu zufügenden Elemente 0 (null) ist oder die kombinierte Anzahl von Elementen zu groß ist, um das Array enthalten zu können. In Einzelhandels Builds kann das Übergeben von ungültigen Parametern zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>"": IsEmpty

Mit dieser Methode können Sie überprüfen, ob das Array leer ist.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das Array leer ist, andernfalls false.

### <a name="remarks"></a>Hinweise

Das Array ist leer, wenn es keine Elemente enthält. Daher ist es nicht leer, auch wenn das Array leere Elemente enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>"-Operator":: Operator []

Ruft diesen Operator auf, um einen Verweis auf ein Element im Array zurückzugeben.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Indexwert des zurück zugebende Array Elements.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das erforderliche Array Element zurück.

### <a name="remarks"></a>Hinweise

Führt eine ähnliche Funktion für "" "" "" ["mit"](#getat)". Anders als bei der MFC-Klasse [CArray](../../mfc/reference/carray-class.md)kann dieser Operator nicht als Ersatz für " [asslarray::](#setat)" verwendet werden.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *IElement* die Gesamtzahl der Elemente im Array überschreitet. In Einzelhandels Builds kann ein ungültiger Parameter zu unvorhersehbaren Ergebnissen führen.

##  <a name="outargtype"></a>"Datentypen": outargtype

Der Datentyp, der zum Abrufen von Elementen aus dem Array verwendet werden soll.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>"": RemoveAll

Mit dieser Methode können Sie alle Elemente aus dem Array Objekt entfernen.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Hinweise

Entfernt alle Elemente aus dem Array Objekt.

Diese Methode ruft " [chanlarray:: SetCount](#setcount) " auf, um die Größe des Arrays zu ändern, und gibt anschließend zugeordneten Speicher frei.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "](#isempty)".

##  <a name="removeat"></a>"Update":: RemoveAt

Diese Methode wird aufgerufen, um ein oder mehrere Elemente aus dem Array zu entfernen.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Index des ersten zu entfernenden Elements.

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Hinweise

Entfernt ein oder mehrere Elemente aus dem Array. Alle verbleibenden Elemente werden nach unten verschoben. Die obere Grenze wird verringert, aber der Arbeitsspeicher wird erst freigegeben, wenn ein [calllarray:: freextra](#freeextra) -Befehl durchgeführt wird.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das `CAtlArray` Objekt ungültig ist, oder wenn die kombinierte Gesamtanzahl von *IElement* und *nCount* die Gesamtzahl der Elemente im Array überschreitet. In Einzelhandels Builds können ungültige Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>"":

Ruft diese Methode auf, um den Wert eines Elements im Array Objekt festzulegen.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Index, der auf das festzulegende Array Element verweist.

*gewisses*<br/>
Der neue Wert des angegebenen Elements.

### <a name="remarks"></a>Hinweise

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *IElement* die Anzahl der Elemente im Array überschreitet. In Einzelhandels Builds kann ein ungültiger Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "](#getat)".

##  <a name="setcount"></a>"Chanlarray:: SetCount"

Ruft diese Methode auf, um die Größe des Array Objekts festzulegen.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parameter

*nnewSize*<br/>
Die erforderliche Größe des Arrays.

*ngrowby*<br/>
Ein-Wert, der verwendet wird, um die Größe des Puffers zu bestimmen. Der Wert-1 bewirkt, dass ein intern berechneter Wert verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Größe des Arrays erfolgreich geändert wurde, andernfalls false.

### <a name="remarks"></a>Hinweise

Das Array kann erweitert oder verkleinert werden. Wenn der Wert erhöht wird, werden dem Array zusätzliche leere Elemente hinzugefügt. Wenn die Größe verringert wird, werden die Elemente mit den größten Indizes gelöscht und der Arbeitsspeicher freigegeben.

Verwenden Sie diese Methode, um die Größe des Arrays vor der Verwendung festzulegen. Wenn `SetCount` nicht verwendet wird, werden durch den Prozess des Hinzufügens von Elementen – und der nachfolgenden Speicher Belegung – die Leistung und der fragmentarbeitsspeicher reduziert.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im [Beispiel für "":](#getdata)

##  <a name="setatgrow"></a>"":

Ruft diese Methode auf, um den Wert eines Elements im Array Objekt festzulegen und das Array nach Bedarf zu erweitern.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*IElement*<br/>
Der Index, der auf das festzulegende Array Element verweist.

*gewisses*<br/>
Der neue Wert des angegebenen Elements.

### <a name="remarks"></a>Hinweise

Ersetzt den Wert des Elements, auf das durch den Index verwiesen wird. Wenn *IElement* größer als die aktuelle Größe des Arrays ist, wird das Array automatisch mit einem aufzurufenden [calllarray:: SetCount](#setcount)-Befehl vergrößert. In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das `CAtlArray` Objekt ungültig ist. In Einzelhandels Builds können ungültige Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Siehe auch

[MMXSwarm-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Marquee-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CArray-Klasse](../../mfc/reference/carray-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
