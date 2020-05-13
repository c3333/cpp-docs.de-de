---
title: COM-Schnittstelleneintragsmakros
ms.date: 03/28/2017
f1_keywords:
- atlcom/ATL::COM_INTERFACE_ENTRY
- atlcom/ATL::COM_INTERFACE_ENTRY_IID
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE
- atlcom/ATL::COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_BREAK
- atlcom/ATL::COM_INTERFACE_ENTRY_CACHED_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_TEAR_OFF
- atlcom/ATL::COM_INTERFACE_ENTRY_CHAIN
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC
- atlcom/ATL::COM_INTERFACE_ENTRY_FUNC_BLIND
- atlcom/ATL::COM_INTERFACE_ENTRY_NOINTERFACE
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
ms.openlocfilehash: bb7498f639f463290a4a6593ef7c0fbac09b539b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326675"
---
# <a name="com_interface_entry-macros"></a>COM_INTERFACE_ENTRY Makros

Diese Makros geben die Schnittstellen eines Objekts in seine COM-Zuordnung ein, sodass sie von `QueryInterface`aufgerufen werden können. Die Reihenfolge der Einträge in der COM-Zuordnung ist, dass die `QueryInterface`Auftragsschnittstellen während einer übereinstimmenden IID überprüft werden.

|||
|-|-|
|[Com_interface_entry](#com_interface_entry)|Gibt Schnittstellen in die COM-Schnittstellenzuordnung ein.|
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Verwenden Sie dieses Makro, um zwei Vererbungszweige zu disambiguieren.|
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Verwenden Sie dieses Makro, um die Schnittstelle in die COM-Zuordnung einzugeben und ihre IID anzugeben.|
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Wie [COM_INTERFACE_ENTRY2](#com_interface_entry2), können Sie nur eine andere IID angeben.|
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Wenn die von *iid* identifizierte `COM_INTERFACE_ENTRY_AGGREGATE` Schnittstelle abgefragt wird, wird nach `punk`weiter.|
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Genauso wie [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), mit der Ausnahme, dass die Abfrage nach einer IID dazu führt, dass die Abfrage an *punk*weitergeleitet wird.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Wie [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), außer wenn *Punk* NULL ist, erstellt es automatisch das Aggregat, das von der *clsid*beschrieben wird.|
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Genauso wie [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), mit der Ausnahme, dass die Abfrage nach einer IID dazu führt, dass die Abfrage an *Punk*weitergeleitet wird, und wenn *Punk* NULL ist, wird automatisch das von der *clsid*beschriebene Aggregat erstellt.|
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Bewirkt, dass Ihr Programm [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) aufruft, wenn die angegebene Schnittstelle abgefragt wird.|
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Speichert die schnittstellenspezifischen Daten für jede Instanz.|
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Macht Ihre Abreißschnittstellen verfügbar.|
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Verarbeitet die COM-Zuordnung der Basisklasse, wenn die Verarbeitung diesen Eintrag in der COM-Zuordnung erreicht.|
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Ein allgemeiner Mechanismus zum Einbinden `QueryInterface` in die ATL-Logik.|
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Genauso wie [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), mit der Ausnahme, dass das Abfragen einer IID zu einem Aufruf von *func*führt.|
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Gibt E_NOINTERFACE zurück und beendet die COM-Zuordnungsverarbeitung, wenn die angegebene Schnittstelle abgefragt wird.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="com_interface_entry"></a><a name="com_interface_entry"></a>Com_interface_entry

Gibt Schnittstellen in die COM-Schnittstellenzuordnung ein.

### <a name="syntax"></a>Syntax

```
COM_INTERFACE_ENTRY( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name einer Schnittstelle, von der Ihr Klassenobjekt direkt ableitet.

### <a name="remarks"></a>Bemerkungen

In der Regel ist dies der Eintragstyp, den Sie am häufigsten verwenden.

### <a name="example"></a>Beispiel

```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="com_interface_entry2"></a><a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2

Verwenden Sie dieses Makro, um zwei Vererbungszweige zu disambiguieren.

```
COM_INTERFACE_ENTRY2(x, x2)
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name einer Schnittstelle, die Sie von Ihrem Objekt aus verfügbar machen möchten.

*x2*<br/>
[in] Der Name des Vererbungsverzweigens, von dem *x* verfügbar gemacht wird.

### <a name="remarks"></a>Bemerkungen

Wenn Sie beispielsweise Ihr Klassenobjekt von zwei dualen `IDispatch` Schnittstellen ableiten, machen Sie die Verwendung von COM_INTERFACE_ENTRY2 verfügbar gemacht, da `IDispatch` sie von einer der Schnittstellen abgerufen werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#118](../../atl/codesnippet/cpp/com-map-macros_2.h)]

## <a name="com_interface_entry_iid"></a><a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID

Verwenden Sie dieses Makro, um die Schnittstelle in die COM-Zuordnung einzugeben und ihre IID anzugeben.

```
COM_INTERFACE_ENTRY_IID(iid, x)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der schnittstelle verfügbar gemacht.

*X*<br/>
[in] Der Name der Klasse, deren vtable als Schnittstelle verfügbar gemacht wird, die von *iid*identifiziert wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#117](../../atl/codesnippet/cpp/com-map-macros_3.h)]

## <a name="com_interface_entry2_iid"></a><a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID

Wie [COM_INTERFACE_ENTRY2](#com_interface_entry2), können Sie nur eine andere IID angeben.

```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID, die Sie für die Schnittstelle angeben.

*X*<br/>
[in] Der Name einer Schnittstelle, von der Das Klassenobjekt direkt ableitet.

*x2*<br/>
[in] Der Name einer zweiten Schnittstelle, von der das Klassenobjekt direkt ableitet.

## <a name="com_interface_entry_aggregate"></a><a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE

Wenn die von *iid* identifizierte Schnittstelle abgefragt wird, COM_INTERFACE_ENTRY_AGGREGATE vorwärts zu *Punk*.

```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der abgefragten Schnittstelle.

*Punk*<br/>
[in] Der Name `IUnknown` eines Zeigers.

### <a name="remarks"></a>Bemerkungen

Es wird angenommen, dass der *Punk-Parameter* auf das innere Unbekannte eines Aggregats oder auf NULL hinweist, in diesem Fall wird der Eintrag ignoriert. In der `CoCreate` Regel würden `FinalConstruct`Sie das Aggregat in .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#112](../../atl/codesnippet/cpp/com-map-macros_4.h)]

## <a name="com_interface_entry_aggregate_blind"></a><a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND

Genauso wie [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), mit der Ausnahme, dass die Abfrage nach einer IID dazu führt, dass die Abfrage an *punk*weitergeleitet wird.

```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Der Name `IUnknown` eines Zeigers.

### <a name="remarks"></a>Bemerkungen

Wenn die Schnittstellenabfrage fehlschlägt, wird die Verarbeitung der COM-Zuordnung fortgesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#113](../../atl/codesnippet/cpp/com-map-macros_5.h)]

## <a name="com_interface_entry_autoaggregate"></a><a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE

Wie [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), außer wenn *Punk* NULL ist, erstellt es automatisch das Aggregat, das von der *clsid*beschrieben wird.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der abgefragten Schnittstelle.

*Punk*<br/>
[in] Der Name `IUnknown` eines Zeigers. Muss ein Member der Klasse sein, die die COM-Zuordnung enthält.

*clsid*<br/>
[in] Der Bezeichner des Aggregats, das erstellt wird, wenn *Punk* NULL ist.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#114](../../atl/codesnippet/cpp/com-map-macros_6.h)]

## <a name="com_interface_entry_autoaggregate_blind"></a><a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND

Genauso wie [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), mit der Ausnahme, dass die Abfrage nach einer IID dazu führt, dass die Abfrage an *Punk*weitergeleitet wird, und wenn *Punk* NULL ist, wird automatisch das von der *clsid*beschriebene Aggregat erstellt.

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Der Name `IUnknown` eines Zeigers. Muss ein Member der Klasse sein, die die COM-Zuordnung enthält.

*clsid*<br/>
[in] Der Bezeichner des Aggregats, das erstellt wird, wenn *Punk* NULL ist.

### <a name="remarks"></a>Bemerkungen

Wenn die Schnittstellenabfrage fehlschlägt, wird die Verarbeitung der COM-Zuordnung fortgesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#115](../../atl/codesnippet/cpp/com-map-macros_7.h)]

## <a name="com_interface_entry_break"></a><a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK

Bewirkt, dass Ihr Programm [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) aufruft, wenn die angegebene Schnittstelle abgefragt wird.

```
COM_INTERFACE_ENTRY_BREAK(x)
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Text, der zum Erstellen des Schnittstellenbezeichners verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die Schnittstelle IID wird durch Anfügen von *x* an `IID_`erstellt. Wenn *x* z. `IPersistStorage`B. ist, `IID_IPersistStorage`lautet die IID .

## <a name="com_interface_entry_cached_tear_off"></a><a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF

Speichert die schnittstellenspezifischen Daten für jede Instanz.

```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der Abreißschnittstelle.

*X*<br/>
[in] Der Name der Klasse, die die Schnittstelle implementiert.

*Punk*<br/>
[in] Der Name `IUnknown` eines Zeigers. Muss ein Member der Klasse sein, die die COM-Zuordnung enthält. Sollte im Konstruktor des Klassenobjekts auf NULL initialisiert werden.

### <a name="remarks"></a>Bemerkungen

Wenn die Schnittstelle nicht verwendet wird, verringert dies die Gesamtgröße der Instanz des Objekts.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#54](../../atl/codesnippet/cpp/com-map-macros_8.h)]

## <a name="com_interface_entry_tear_off"></a><a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF

Macht Ihre Abreißschnittstellen verfügbar.

```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der Abreißschnittstelle.

*X*<br/>
[in] Der Name der Klasse, die die Schnittstelle implementiert.

### <a name="remarks"></a>Bemerkungen

Eine Abreißschnittstelle wird als separates Objekt implementiert, das jedes Mal instanziiert wird, wenn die Schnittstelle, die sie darstellt, abgefragt wird. In der Regel erstellen Sie Ihre Schnittstelle als Abreißer, wenn die Schnittstelle selten verwendet wird, da dadurch in jeder Instanz des Hauptobjekts ein vtable-Zeiger spart. Der Abreißer wird gelöscht, wenn die Referenzanzahl Null wird. Die Klasse, die den Abreißer implementiert, sollte von `CComTearOffObjectBase` einer eigenen COM-Karte abgeleitet werden und über eine eigene COM-Karte verfügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="com_interface_entry_chain"></a><a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN

Verarbeitet die COM-Zuordnung der Basisklasse, wenn die Verarbeitung diesen Eintrag in der COM-Zuordnung erreicht.

```
COM_INTERFACE_ENTRY_CHAIN(classname)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
[in] Eine Basisklasse des aktuellen Objekts.

### <a name="remarks"></a>Bemerkungen

Im folgenden Code:

[!code-cpp[NVC_ATL_Windowing#116](../../atl/codesnippet/cpp/com-map-macros_9.h)]

Beachten Sie, dass der erste Eintrag in der COM-Zuordnung eine Schnittstelle für das Objekt sein muss, das die COM-Zuordnung enthält. Daher können Sie Ihre COM-Zuordnungseinträge nicht mit COM_INTERFACE_ENTRY_CHAIN starten, wodurch die COM-Zuordnung eines anderen Objekts an dem Punkt durchsucht wird, an dem **COM_INTERFACE_ENTRY_CHAIN(**`COtherObject`**)** in der COM-Zuordnung Ihres Objekts angezeigt wird. Wenn Sie zuerst die COM-Zuordnung eines anderen Objekts `IUnknown` durchsuchen möchten, fügen Sie der COM-Zuordnung einen Schnittstelleneintrag hinzu, und verketten Sie dann die COM-Zuordnung des anderen Objekts. Beispiel:

[!code-cpp[NVC_ATL_Windowing#111](../../atl/codesnippet/cpp/com-map-macros_10.h)]

## <a name="com_interface_entry_func"></a><a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC

Ein allgemeiner Mechanismus zum Einbinden `QueryInterface` in die ATL-Logik.

```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der schnittstelle verfügbar gemacht.

*dw*<br/>
[in] Ein Parameter, der an den *func*übergeben wird.

*Func*<br/>
[in] Der Funktionszeiger, der *iid*zurückgibt.

### <a name="remarks"></a>Bemerkungen

Wenn *iid* mit der IID der abgefragten Schnittstelle übereinstimmt, wird die von *func* angegebene Funktion aufgerufen. Die Deklaration für die Funktion sollte sein:

`HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`

Wenn Ihre Funktion `pv` aufgerufen wird, zeigt sie auf Ihr Klassenobjekt. Der *riid-Parameter* bezieht sich auf `ppv` die schnittstelle, nach der abgefragt wird, ist der Zeiger auf die Position, an der die Funktion den Zeiger auf die Schnittstelle speichern soll, und *dw* ist der Parameter, den Sie im Eintrag angegeben haben. Die Funktion \* `ppv` sollte auf NULL gesetzt werden und E_NOINTERFACE oder S_FALSE zurückgeben, wenn sie keine Schnittstelle zurückgibt. Mit E_NOINTERFACE wird die COM-Kartenverarbeitung beendet. Mit S_FALSE wird die COM-Kartenverarbeitung fortgesetzt, obwohl kein Schnittstellenzeiger zurückgegeben wurde. Wenn die Funktion einen Schnittstellenzeiger zurückgibt, sollte sie S_OK zurückgeben.

## <a name="com_interface_entry_func_blind"></a><a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND

Genauso wie [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), mit der Ausnahme, dass das Abfragen einer IID zu einem Aufruf von *func*führt.

```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```

### <a name="parameters"></a>Parameter

*dw*<br/>
[in] Ein Parameter, der an den *func*übergeben wird.

*Func*<br/>
[in] Die Funktion, die aufgerufen wird, wenn dieser Eintrag in der COM-Zuordnung verarbeitet wird.

### <a name="remarks"></a>Bemerkungen

Jeder Fehler führt dazu, dass die Verarbeitung auf der COM-Karte fortgesetzt wird. Wenn die Funktion einen Schnittstellenzeiger zurückgibt, sollte sie S_OK zurückgeben.

## <a name="com_interface_entry_nointerface"></a><a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE

Gibt E_NOINTERFACE zurück und beendet die COM-Zuordnungsverarbeitung, wenn die angegebene Schnittstelle abgefragt wird.

```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Text, der zum Erstellen des Schnittstellenbezeichners verwendet wird.

### <a name="remarks"></a>Bemerkungen

Sie können dieses Makro verwenden, um zu verhindern, dass eine Schnittstelle in einem bestimmten Fall verwendet wird. Sie können dieses Makro beispielsweise direkt vor COM_INTERFACE_ENTRY_AGGREGATE_BLIND in Ihre COM-Zuordnung einfügen, um zu verhindern, dass eine Abfrage für die Schnittstelle an das innere Unbekannte des Aggregats weitergeleitet wird.

Die Schnittstelle IID wird durch Anfügen von *x* an `IID_`erstellt. Wenn *x* z. `IPersistStorage`B. ist, `IID_IPersistStorage`lautet die IID .
