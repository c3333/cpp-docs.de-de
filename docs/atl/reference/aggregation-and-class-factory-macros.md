---
title: Aggregations- und Klassenfactorymakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319339"
---
# <a name="aggregation-and-class-factory-macros"></a>Aggregations- und Klassenfactorymakros

Diese Makros bieten Möglichkeiten zur Steuerung der Aggregation und zum Deklarieren von Klassenfabriken.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklariert, dass Ihr Objekt aggregiert werden kann (Standard).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklariert die Klassenfactory als [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), die ATL-Standardklassenfactory.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklariert Ihr Class Factory-Objekt als Klassenfactory.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklariert [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) als Klassenfactory.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklariert [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklariert [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) als Klassenfactory.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklariert eine `GetControllingUnknown` virtuelle Funktion.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklariert, dass Ihr Objekt nicht aggregiert werden kann.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklariert, dass Ihr Objekt aggregiert werden muss.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Überprüft den Wert des äußeren Unbekannten und deklariert Ihr Objekt für aggregierend oder nicht aggaggierbar.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Schützt das äußere Objekt beim Aufbau eines inneren Objekts vor dem Löschen.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Gibt die VIEWSTATUS-Flags für den Container an.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Gibt an, dass das Objekt aggregiert werden kann.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Klasse, die Sie als aggregatierbar definieren.

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält dieses Makro, um das Standardaggregationsmodell anzugeben. Um diese Standardeinstellung zu überschreiben, geben Sie entweder das [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) oder [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) Makro in der Klassendefinition an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklariert [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Klassenfactory.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) verwendet dieses Makro, um die Standardklassenfactory für Ihr Objekt zu deklarieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClassFactory-Klasse

Diese Klasse implementiert die [IClassFactory-Schnittstelle.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Bemerkungen

`CComClassFactory`implementiert die [IClassFactory-Schnittstelle,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) die Methoden zum Erstellen eines Objekts einer bestimmten CLSID sowie zum Sperren der Klassenfactory im Arbeitsspeicher enthält, damit neue Objekte schneller erstellt werden können. `IClassFactory`muss für jede Klasse implementiert werden, die Sie in der Systemregistrierung registrieren und der Sie eine CLSID zuweisen.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält [DECLARE_CLASSFACTORY](#declare_classfactory)das Makro `CComClassFactory` DECLARE_CLASSFACTORY , das als Standardklassenfactory deklariert wird. Um diese Standardeinstellung zu überschreiben, geben Sie eines der DECLARE_CLASSFACTORY*XXX-Makros* in Ihrer Klassendefinition an. Das [DECLARE_CLASSFACTORY_EX-Makro](#declare_classfactory_ex) verwendet z. B. die angegebene Klasse für die Klassenfactory:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Die obige Klassendefinition `CMyClassFactory` gibt an, dass sie als Standardklassenfactory des Objekts verwendet wird. `CMyClassFactory`muss von `CComClassFactory` ableiten `CreateInstance`und überschreiben .

ATL stellt drei weitere Makros bereit, die eine Klassenfactory deklarieren:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Verwendet [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), das die Erstellung über eine Lizenz steuert.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Verwendet [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), das Objekte in mehreren Apartments erstellt.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Verwendet [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), das ein einzelnes [CComObjectGlobal-Objekt](../../atl/reference/ccomobjectglobal-class.md) erstellt.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Deklariert `cf` als Klassenfabrik.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
[in] Der Name der Klasse, die Ihr Klassenfactoryobjekt implementiert.

### <a name="remarks"></a>Bemerkungen

Der *cf-Parameter* muss von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) `CreateInstance` abstammen und die Methode überschreiben.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY-Makro,](#declare_classfactory) das als Standardklassenfactory angegeben wird. `CComClassFactory` Durch das Einschließen des DECLARE_CLASSFACTORY_EX-Makros in die Klassendefinition des Objekts überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklariert [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) als Klassenfactory.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parameter

*Lic*<br/>
[in] Eine Klasse, `VerifyLicenseKey`die `GetLicenseKey`implementiert `IsLicenseValid`, und .

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY-Makro,](#declare_classfactory) das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Durch das Einschließen des DECLARE_CLASSFACTORY2-Makros in die Klassendefinition des Objekts überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>CComClassFactory2-Klasse

Diese Klasse implementiert die [IClassFactory2-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parameter

*Lizenz*<br/>
Eine Klasse, die die folgenden statischen Funktionen implementiert:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Bemerkungen

`CComClassFactory2`implementiert die [IClassFactory2-Schnittstelle,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) die eine Erweiterung von [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)ist. `IClassFactory2`steuert die Objekterstellung über eine Lizenz. Eine Klassenfactory, die auf einem lizenzierten Computer ausgeführt wird, kann einen Laufzeitlizenzschlüssel bereitstellen. Mit diesem Lizenzschlüssel kann eine Anwendung Objekte instanziieren, wenn keine vollständige Computerlizenz vorhanden ist.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um `CComClassFactory2`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY2](#declare_classfactory2) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`muss `CComClassFactory2`der Vorlagenparameter für , `VerifyLicenseKey`die `GetLicenseKey`statischen Funktionen , und `IsLicenseValid`implementieren. Im Folgenden finden Sie ein Beispiel für eine einfache Lizenzklasse:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`leitet sich von `CComClassFactory2Base` beiden und *Lizenz*. `CComClassFactory2Base`leitet sich wiederum von `IClassFactory2` **cComGlobalsThreadModel\< >von CComObjectRootEx CComGlobalsThreadModel ab. **

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklariert [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY-Makro,](#declare_classfactory) das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Durch das Einschließen des DECLARE_CLASSFACTORY_AUTO_THREAD-Makros in die Klassendefinition des Objekts überschreiben Sie diese Standardeinstellung.

Wenn Sie Objekte in mehreren Apartments (in einem Out-of-Proc-Server) erstellen, fügen Sie ihrer Klasse DECLARE_CLASSFACTORY_AUTO_THREAD hinzu.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>CComClassFactoryAutoThread-Klasse

Diese Klasse implementiert die [IClassFactory-Schnittstelle](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) und ermöglicht das Erstellen von Objekten in mehreren Apartments.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Bemerkungen

`CComClassFactoryAutoThread`[cComClassFactory](../../atl/reference/ccomclassfactory-class.md)ähnelt, ermöglicht jedoch das Erstellen von Objekten in mehreren Apartments. Um diese Unterstützung nutzen zu können, leiten Sie Ihr EXE-Modul von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)ab.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um `CComClassFactoryAutoThread`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklariert [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) als Klassenfactory.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parameter

*obj*<br/>
[in] Der Name des Klassenobjekts.

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY-Makro,](#declare_classfactory) das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Durch das Einschließen des DECLARE_CLASSFACTORY_SINGLETON-Makros in die Klassendefinition des Objekts überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>CComClassFactorySingleton-Klasse

Diese Klasse leitet sich von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ab und verwendet [CComObjectGlobal,](../../atl/reference/ccomobjectglobal-class.md) um ein einzelnes Objekt zu erstellen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse.

`CComClassFactorySingleton`von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ableitet und [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) verwendet, um ein einzelnes Objekt zu erstellen. Jeder Aufruf `CreateInstance` der Methode fragt dieses Objekt einfach nach einem Schnittstellenzeiger ab.

### <a name="remarks"></a>Bemerkungen

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält [DECLARE_CLASSFACTORY](#declare_classfactory)das Makro `CComClassFactory` DECLARE_CLASSFACTORY , das als Standardklassenfactory deklariert wird. Um `CComClassFactorySingleton`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklariert eine `GetControllingUnknown`virtuelle Funktion .

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Bemerkungen

Fügen Sie dieses Makro zu Ihrem Objekt `GetControllingUnknown` hinzu, wenn Sie die `CComAggregateCreator`Fehlermeldung des Compilers erhalten, die nicht definiert ist (z. B. in ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Gibt an, dass das Objekt nicht aggregiert werden kann.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name des Klassenobjekts, das Sie als nicht aggadivierbar definieren.

### <a name="remarks"></a>Bemerkungen

DECLARE_NOT_AGGREGATABLE `CreateInstance` verursacht, dass ein Fehler zurückgegeben wird (CLASS_E_NOAGGREGATION), wenn versucht wird, auf das Objekt zu aggregieren.

Standardmäßig enthält [CComCoClass](../../atl/reference/ccomcoclass-class.md) das [DECLARE_AGGREGATABLE-Makro,](#declare_aggregatable) das angibt, dass das Objekt aggregiert werden kann. Um dieses Standardverhalten zu überschreiben, fügen Sie DECLARE_NOT_AGGREGATABLE in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Gibt an, dass das Objekt aggregiert werden muss.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name des Klassenobjekts, das Sie definieren, ist nur aggregierend.

### <a name="remarks"></a>Bemerkungen

DECLARE_ONLY_AGGREGATABLE verursacht einen Fehler (E_FAIL), wenn `CoCreate` ein Versuch an Ihrem Objekt als nicht aggregiertes Objekt unternommen wird.

Standardmäßig enthält [CComCoClass](../../atl/reference/ccomcoclass-class.md) das [DECLARE_AGGREGATABLE-Makro,](#declare_aggregatable) das angibt, dass das Objekt aggregiert werden kann. Um dieses Standardverhalten zu überschreiben, fügen Sie DECLARE_ONLY_AGGREGATABLE in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Gibt an, dass beim Erstellen des Objekts eine Instanz von **CComPolyObject \< ** *x* **>** erstellt wird.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name des Klassenobjekts, das Sie als aggadivierbar oder nicht aggagierbar definieren.

### <a name="remarks"></a>Bemerkungen

Während der Erstellung wird der Wert des äußeren Unbekannten überprüft. Wenn es NULL `IUnknown` ist, wird für ein nicht aggregiertes Objekt implementiert. Wenn der äußere Unbekannte `IUnknown` nicht NULL ist, wird für ein aggregiertes Objekt implementiert.

Der Vorteil der Verwendung von DECLARE_POLY_AGGREGATABLE `CComAggObject` `CComObject` besteht darin, dass Sie vermeiden, dass sowohl als auch in Ihrem Modul die aggregierten und nicht aggregierten Anfragen behandelt werden. Ein `CComPolyObject` einzelnes Objekt behandelt beide Fälle. Dies bedeutet, dass nur eine Kopie des vtable und eine Kopie der Funktionen in Ihrem Modul vorhanden sind. Wenn Ihr vtable groß ist, kann dies die Modulgröße erheblich verringern. Wenn Ihr vtable jedoch klein `CComPolyObject` ist, kann die Verwendung zu einer etwas größeren Modulgröße führen, da `CComAggObject` `CComObject`sie nicht für ein aggregiertes oder nicht aggregiertes Objekt optimiert ist, wie es sich in und befindet.

Das DECLARE_POLY_AGGREGATABLE Makro wird automatisch in Ihrem Objekt deklariert, wenn Sie den ATL-Steuerelement-Assistenten verwenden, um eine vollständige Steuerung zu erstellen.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Schützt das Objekt vor dem Löschen, wenn das interne aggregierte Objekt (während [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) die Referenzanzahl erhöht und die Anzahl auf 0 dekrementiert.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Platzieren Sie dieses Makro in der Steuerelementklasse eines ATL ActiveX-Steuerelements, um die VIEWSTATUS-Flags für den Container anzugeben.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parameter

*statusFlags*<br/>
[in] Die VIEWSTATUS-Flags. Eine Liste der Flags finden Sie unter [VIEWSTATUS.](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
