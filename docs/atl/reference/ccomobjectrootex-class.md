---
title: CComObjectRootEx-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: e8db86f6214f95cd9bb08d3b5f6c6c1a38ca475c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327609"
---
# <a name="ccomobjectrootex-class"></a>CComObjectRootEx-Klasse

Diese Klasse stellt Methoden zum Behandeln der Objektverweisanzahlverwaltung für nicht aggregierte und aggregierte Objekte bereit.

## <a name="syntax"></a>Syntax

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parameter

*ThreadModel*<br/>
Die Klasse, deren Methoden das gewünschte Threadingmodell implementieren. Sie können das Threadingmodell explizit auswählen, indem Sie *ThreadModel* auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)oder [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)festlegen. Sie können das Standardthreadmodell des Servers akzeptieren, indem Sie *ThreadModel* auf [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) oder [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)festlegen.

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Ccomobjectrootex](#ccomobjectrootex)|Konstruktor.|
|[InternAddRef](#internaladdref)|Inkrementiert die Referenzanzahl für ein nicht aggregiertes Objekt.|
|[InternalRelease](#internalrelease)|Dekrementiert die Referenzanzahl für ein nicht aggregiertes Objekt.|
|[Sperre](#lock)|Wenn das Threadmodell multithreaded ist, erhält der Besitz eines kritischen Abschnittsobjekts.|
|[Entsperren](#unlock)|Wenn das Threadmodell multithreaded ist, wird der Besitz eines kritischen Abschnittsobjekts freigegeben.|

### <a name="ccomobjectrootbase-methods"></a>CComObjectRootBase-Methoden

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Überschreiben Sie in Ihrer Klasse, um eine initialisierung durchzuführen, die für Ihr Objekt erforderlich ist.|
|[FinalRelease](#finalrelease)|Überschreiben Sie in Ihrer Klasse, um alle bereinigungen durchzuführen, die für Ihr Objekt erforderlich sind.|
|[OuterAddRef](#outeraddref)|Inkrementiert die Referenzanzahl für ein aggregiertes Objekt.|
|[OuterQueryInterface](#outerqueryinterface)|Delegierte an `IUnknown` das Äußere eines aggregierten Objekts.|
|[OuterRelease](#outerrelease)|Dekrementiert die Referenzanzahl für ein aggregiertes Objekt.|

### <a name="static-functions"></a>Statische Funktionen

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Delegiert `IUnknown` an das eines nicht aggregierten Objekts.|
|[ObjectMain](#objectmain)|Wird während der Modulinitialisierung und -beendigung für abgeleitete Klassen aufgerufen, die in der Objektzuordnung aufgeführt sind.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[m_dwRef](#m_dwref)|Mit `m_pOuterUnknown`, Teil einer Union. Wird verwendet, wenn das Objekt nicht aggregiert `AddRef` `Release`wird, um die Referenzanzahl von und zu enthalten.|
|[m_pOuterUnknown](#m_pouterunknown)|Mit `m_dwRef`, Teil einer Union. Wird verwendet, wenn das Objekt aggregiert wird, um einen Zeiger auf das äußere Unbekannte zu halten.|

## <a name="remarks"></a>Bemerkungen

`CComObjectRootEx`behandelt die Verwaltung der Objektverweisanzahl sowohl für nicht aggregierte als auch für aggregierte Objekte. Sie enthält die Objektverweisanzahl, wenn das Objekt nicht aggregiert wird, und hält den Zeiger auf das äußere Unbekannte, wenn das Objekt aggregiert wird. Bei aggregierten `CComObjectRootEx` Objekten können Methoden verwendet werden, um den Fehler des zu konstruierenden inneren Objekts zu behandeln und das äußere Objekt vor dem Löschen zu schützen, wenn innere Schnittstellen freigegeben oder das innere Objekt gelöscht wird.

Eine Klasse, die einen COM-Server `CComObjectRootEx` implementiert, muss von oder [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)erben.

Wenn Ihre Klassendefinition das [DECLARE_POLY_AGGREGATABLE-Makro](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) spezifiziert, erstellt ATL eine Instanz von `CComPolyObject<CYourClass>` when `IClassFactory::CreateInstance` wird aufgerufen. Während der Erstellung wird der Wert des äußeren Unbekannten überprüft. Wenn es NULL `IUnknown` ist, wird für ein nicht aggregiertes Objekt implementiert. Wenn der äußere Unbekannte `IUnknown` nicht NULL ist, wird für ein aggregiertes Objekt implementiert.

Wenn Ihre Klasse das DECLARE_POLY_AGGREGATABLE-Makro spezifiziert, `CAggComObject<CYourClass>` erstellt ATL eine `CComObject<CYourClass>` Instanz für aggregierte Objekte oder eine Instanz von für nicht aggregierte Objekte.

Der Vorteil `CComPolyObject` der Verwendung besteht `CComAggObject` darin, dass Sie vermeiden, dass sowohl als `CComObject` auch in Ihrem Modul die aggregierten und nicht aggregierten Anfragen behandelt werden. Ein `CComPolyObject` einzelnes Objekt behandelt beide Fälle. Daher sind nur eine Kopie des vtable und eine Kopie der Funktionen in Ihrem Modul vorhanden. Wenn Ihr vtable groß ist, kann dies die Modulgröße erheblich verringern. Wenn Ihr vtable jedoch klein `CComPolyObject` ist, kann die Verwendung zu einer etwas größeren Modulgröße führen, da `CComAggObject` `CComObject`sie nicht für ein aggregiertes oder nicht aggregiertes Objekt optimiert ist, wie es sich in und befindet.

Wenn Ihr Objekt aggregiert ist, wird `CComAggObject` `CComPolyObject` [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) von oder implementiert. Diese Klassen `QueryInterface` `AddRef`delegieren `CComObjectRootEx`, `OuterQueryInterface`und `OuterAddRef` `Release` rufen `OuterRelease` an 's , an und leiten sie an das äußere Unbekannte weiter. In der Regel `CComObjectRootEx::FinalConstruct` überschreiben Sie in Ihrer Klasse, `CComObjectRootEx::FinalRelease` um aggregierte Objekte zu erstellen, und überschreiben, um alle aggregierten Objekte freizugeben.

Wenn Ihr Objekt nicht `IUnknown` aggregiert ist, wird es von `CComObject` oder `CComPolyObject`implementiert. In diesem Fall `QueryInterface`ruft `AddRef`an `Release` , und `CComObjectRootEx`werden `InternalQueryInterface` `InternalAddRef`an `InternalRelease` ' ' , delegiert, und um die eigentlichen Vorgänge auszuführen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomobjectrootexccomobjectrootex"></a><a name="ccomobjectrootex"></a>CComObjectRootex::CComObjectRootex

Der Konstruktor initialisiert die Referenzanzahl auf 0.

```
CComObjectRootEx();
```

## <a name="ccomobjectrootexfinalconstruct"></a><a name="finalconstruct"></a>CComObjectRootEx::FinalConstruct

Sie können diese Methode in der abgeleiteten Klasse überschreiben, um die für Ihr Objekt erforderlichen Initialisierungen durchzuführen.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Rückgabewert

Geben Sie S_OK bei Erfolg oder einem der Standardfehler-HRESULT-Werte zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden `CComObjectRootEx::FinalConstruct` einfach S_OK zurückgegeben.

Die Initialisierung in `FinalConstruct` der Klasse hat Vorteile:

- Sie können keinen Statuscode von einem Konstruktor zurückgeben, aber `FinalConstruct`Sie können ein HRESULT über den Rückgabewert von zurückgeben. Wenn Objekte Ihrer Klasse mit der von ATL bereitgestellten Standardklassenfactory erstellt werden, wird dieser Rückgabewert an den COM-Client zurückgegeben, sodass Sie ihnen detaillierte Fehlerinformationen zur Verfügung stellen können.

- Sie können virtuelle Funktionen nicht über den virtuellen Funktionsmechanismus aus dem Konstruktor einer Klasse aufrufen. Das Aufrufen einer virtuellen Funktion aus dem Konstruktor einer Klasse führt zu einem statisch aufgelösten Aufruf der Funktion, wie sie an diesem Punkt in der Vererbungshierarchie definiert ist. Aufrufe reiner virtueller Funktionen führen zu Linkerfehlern.

   Ihre Klasse ist nicht die am häufigsten abgeleitete Klasse in der Vererbungshierarchie – sie basiert auf einer abgeleiteten Klasse, die von ATL bereitgestellt wird, um einen Teil ihrer Funktionalität bereitzustellen. Es besteht eine gute Wahrscheinlichkeit, dass Ihre Initialisierung die von dieser Klasse bereitgestellten Features verwenden muss (dies trifft sicherlich zu, wenn Objekte Ihrer Klasse andere Objekte aggregieren müssen), aber der Konstruktor in Ihrer Klasse hat keine Möglichkeit, auf diese Features zuzugreifen. Der Konstruktionscode für Ihre Klasse wird ausgeführt, bevor die am meisten abgeleitete Klasse vollständig erstellt wird.

   Wird `FinalConstruct` jedoch sofort aufgerufen, nachdem die am weitesten abgeleitete Klasse vollständig erstellt wurde, sodass Sie virtuelle Funktionen aufrufen und die von ATL bereitgestellte Referenzzählungsimplementierung verwenden können.

### <a name="example"></a>Beispiel

Überschreiben Sie diese Methode in `CComObjectRootEx` der Klasse, von der abgeleitet wird, um aggregierte Objekte zu erstellen. Beispiel:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Wenn die Konstruktion fehlschlägt, können Sie einen Fehler zurückgeben. Sie können auch das Makro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) verwenden, um das äußere Objekt vor dem Löschen zu schützen, wenn das interne aggregierte Objekt während der Erstellung die Referenzanzahl erhöht und dann die Anzahl auf 0 dekrementiert.

Hier ist eine typische Möglichkeit, ein Aggregat zu erstellen:

- Fügen `IUnknown` Sie dem Klassenobjekt einen Zeiger hinzu, und initialisieren Sie es im Konstruktor zu NULL.

- Überschreiben, `FinalConstruct` um das Aggregat zu erstellen.

- Verwenden `IUnknown` Sie den Zeiger, den Sie als Parameter definiert haben, auf das [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) Makro.

- Überschreiben, `FinalRelease` um `IUnknown` den Zeiger freizugeben.

## <a name="ccomobjectrootexfinalrelease"></a><a name="finalrelease"></a>CComObjectRootEx::FinalRelease

Sie können diese Methode in der abgeleiteten Klasse überschreiben, um die für Ihr Objekt erforderlichen Bereinigungen durchzuführen.

```
void FinalRelease();
```

### <a name="remarks"></a>Bemerkungen

Tut standardmäßig `CComObjectRootEx::FinalRelease` nichts.

Das Durchführen `FinalRelease` von Bereinigungen in ist dem Hinzufügen von Code zum Destruktor Ihrer `FinalRelease` Klasse vorzuziehen, da das Objekt an dem Punkt, an dem aufgerufen wird, noch vollständig erstellt ist. Auf diese Weise können Sie sicher auf die Methoden zugreifen, die von der am häufigsten abgeleiteten Klasse bereitgestellt werden. Dies ist besonders wichtig, um alle aggregierten Objekte vor dem Löschen freizugeben.

## <a name="ccomobjectrootexinternaladdref"></a><a name="internaladdref"></a>CComObjectRootEx::InternalAddRef

Erhöht die Referenzanzahl eines nicht aggregierten Objekts um 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen und Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Wenn das Threadmodell Multithread `InterlockedIncrement` ist, wird verwendet, um zu verhindern, dass mehrere Threads gleichzeitig die Referenzanzahl ändern.

## <a name="ccomobjectrootexinternalqueryinterface"></a><a name="internalqueryinterface"></a>CComObjectRootEx::InternalQueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*pThis*<br/>
[in] Ein Zeiger auf das Objekt, das die COM-Zuordnung der Schnittstellen enthält, die für `QueryInterface`verfügbar gemacht werden.

*pEntries*<br/>
[in] Ein Zeiger auf `_ATL_INTMAP_ENTRY` die Struktur, die auf eine Karte verfügbarer Schnittstellen zugreift.

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den in *iid*, oder NULL angegebenen Schnittstellenzeiger, wenn die Schnittstelle nicht gefunden wird.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

`InternalQueryInterface`verarbeitet nur Schnittstellen in der COM-Map-Tabelle. Wenn Ihr Objekt aggregiert `InternalQueryInterface` ist, wird nicht an das äußere Unbekannte delegiert. Sie können Schnittstellen in die COM-Map-Tabelle mit dem Makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) oder einer seiner Varianten eingeben.

## <a name="ccomobjectrootexinternalrelease"></a><a name="internalrelease"></a>CComObjectRootEx::InternalRelease

Dekrementiert die Referenzanzahl eines nicht aggregierten Objekts um 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Rückgabewert

Sowohl in Nicht-Debug- als auch in Debugbuilds gibt diese Funktion einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann. Der genaue zurückgegebene Wert hängt von vielen Faktoren ab, z. B. vom verwendeten Betriebssystem, und kann die Referenzanzahl sein oder auch nicht.

### <a name="remarks"></a>Bemerkungen

Wenn das Threadmodell Multithread `InterlockedDecrement` ist, wird verwendet, um zu verhindern, dass mehrere Threads gleichzeitig die Referenzanzahl ändern.

## <a name="ccomobjectrootexlock"></a><a name="lock"></a>CComObjectRootEx::Sperren

Wenn das Threadmodell Multithread ist, ruft diese Methode die Win32-API-Funktion [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)auf, die wartet, bis der Thread den Besitz des kritischen Abschnittsobjekts übernehmen kann, das über ein privates Datenmember abgerufen wurde.

```
void Lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Ausführung des geschützten Codes `Unlock` abgeschlossen ist, muss der Thread aufrufen, um den Besitz des kritischen Abschnitts freizugeben.

Wenn das Gewindemodell einfädelig ist, führt diese Methode nichts aus.

## <a name="ccomobjectrootexm_dwref"></a><a name="m_dwref"></a>CComObjectRootEx::m_dwRef

Teil einer Union, die auf vier Byte Arbeitsspeicher zugreift.

```
long m_dwRef;
```

### <a name="remarks"></a>Bemerkungen

Mit `m_pOuterUnknown`, Teil einer Union:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Wenn das Objekt nicht aggregiert ist, `AddRef` wird `Release` auf `m_dwRef`die Referenzanzahl zugegriffen, auf die von zugegriffen wird und die in gespeichert wird. Wenn das Objekt aggregiert wird, wird der Zeiger auf das äußere Unbekannte in [m_pOuterUnknown](#m_pouterunknown)gespeichert.

## <a name="ccomobjectrootexm_pouterunknown"></a><a name="m_pouterunknown"></a>CComObjectRootEx::m_pOuterUnknown

Teil einer Union, die auf vier Byte Arbeitsspeicher zugreift.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Bemerkungen

Mit `m_dwRef`, Teil einer Union:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Wenn das Objekt aggregiert wird, wird der Zeiger `m_pOuterUnknown`auf das äußere Unbekannte in gespeichert. Wenn das Objekt nicht aggregiert ist, `AddRef` wird `Release` auf die Referenzanzahl zugegriffen, auf die von m_dwRef zugegriffen wird und in [m_dwRef](#m_dwref)gespeichert wird.

## <a name="ccomobjectrootexobjectmain"></a><a name="objectmain"></a>CComObjectRootEx::ObjectMain

Für jede in der Objektzuordnung aufgeführte Klasse wird diese Funktion einmal aufgerufen, wenn das Modul initialisiert wird, und erneut, wenn sie beendet wird.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parameter

*bStart*<br/>
[out] Der Wert ist TRUE, wenn die Klasse initialisiert wird. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Der Wert des *Parameters bStarting* gibt an, ob das Modul initialisiert oder beendet wird. Die Standardimplementierung `ObjectMain` von tut nichts, aber Sie können diese Funktion in Ihrer Klasse überschreiben, um Ressourcen zu initialisieren oder zu bereinigen, die Sie für die Klasse zuweisen möchten. Hinweis, `ObjectMain` der aufgerufen wird, bevor Instanzen der Klasse angefordert werden.

`ObjectMain`wird vom Einstiegspunkt der DLL aufgerufen, sodass der Typ des Vorgangs, den die Einstiegspunktfunktion ausführen kann, eingeschränkt ist. Weitere Informationen zu diesen Einschränkungen finden Sie unter [DLLs und Visual C++-Laufzeitbibliotheksverhalten](../../build/run-time-library-behavior.md) und [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

## <a name="ccomobjectrootexouteraddref"></a><a name="outeraddref"></a>CComObjectRootex::OuterAddRef

Inkrementiert die Referenzanzahl des äußeren Unbekannten einer Aggregation.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen und Tests nützlich sein kann.

## <a name="ccomobjectrootexouterqueryinterface"></a><a name="outerqueryinterface"></a>CComObjectRootEx::OuterQueryInterface

Ruft einen indirekten Zeiger auf die angeforderte Schnittstelle ab.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den in *iid*oder NULL angegebenen Schnittstellenzeiger, wenn die Aggregation die Schnittstelle nicht unterstützt.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomobjectrootexouterrelease"></a><a name="outerrelease"></a>CComObjectRootEx::OuterRelease

Dekrementiert die Referenzanzahl des äußeren Unbekannten einer Aggregation.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Rückgabewert

Gibt in Nicht-Debug-Builds immer 0 zurück. Gibt in Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann.

## <a name="ccomobjectrootexunlock"></a><a name="unlock"></a>CComObjectRootEx::Entsperren

Wenn das Threadmodell Multithread ist, ruft diese Methode die Win32-API-Funktion [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)auf, die den Besitz des kritischen Abschnittsobjekts freigibt, das über ein privates Datenmember abgerufen wird.

```
void Unlock();
```

### <a name="remarks"></a>Bemerkungen

Um den Besitz zu `Lock`erhalten, muss der Thread aufrufen. Jeder Aufruf `Lock` erfordert einen `Unlock` entsprechenden Aufruf, um den Besitz des kritischen Abschnitts freizugeben.

Wenn das Gewindemodell einfädelig ist, führt diese Methode nichts aus.

## <a name="see-also"></a>Siehe auch

[CComAggObject-Klasse](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject-Klasse](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject-Klasse](../../atl/reference/ccompolyobject-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
