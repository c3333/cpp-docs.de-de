---
title: Aggregation und klassenfactorymakros
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
ms.openlocfilehash: 554210ab0a26bc54a716a389a1660c4cbd42a209
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168656"
---
# <a name="aggregation-and-class-factory-macros"></a>Aggregation und klassenfactorymakros

Diese Makros bieten Möglichkeiten zum Steuern der Aggregation und zum Deklarieren von Klassenfactorys.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklariert, dass das-Objekt aggregiert werden kann (Standard).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklariert die Klassenfactory als [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), der ATL-Standardklassenfactory.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklariert das klassenfactoryobjekt als Klassenfactory.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklariert [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) als Klassenfactory.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklariert [ccomclassfactoryautothread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklariert [ccomclassfactorysingleton](../../atl/reference/ccomclassfactorysingleton-class.md) als Klassenfactory.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklariert eine virtuelle `GetControllingUnknown` Funktion.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklariert, dass das Objekt nicht aggregiert werden kann.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklariert, dass das Objekt aggregiert werden muss.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Überprüft den Wert des äußeren unbekannten und deklariert ggf. das Objekt als aggregierbare oder nicht aggregierbare.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Schützt das äußere Objekt vor dem Löschen während der Erstellung eines inneren Objekts.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Gibt die VIEWSTATUS-Flags für den Container an.|

## <a name="requirements"></a>Anforderungen

**Header:** Atlcom. h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Gibt an, dass das Objekt aggregiert werden kann.

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name der Klasse, die Sie als aggregatable definieren.

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält dieses Makro, um das Standard Aggregations Modell anzugeben. Um diese Standardeinstellung zu überschreiben, geben Sie entweder das [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) -oder [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) -Makro in der Klassendefinition an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklariert [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Klassenfactory.

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) verwendet dieses Makro, um die Standardklassenfactory für das Objekt zu deklarieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClassFactory-Klasse

Diese Klasse implementiert die [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) -Schnittstelle.

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Bemerkungen

`CComClassFactory`implementiert die [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) -Schnittstelle, die Methoden zum Erstellen eines Objekts einer bestimmten CLSID enthält, sowie zum Sperren der Klassenfactory im Speicher, sodass neue Objekte schneller erstellt werden können. `IClassFactory`muss für jede Klasse implementiert werden, die Sie in der Systemregistrierung registrieren und denen Sie eine CLSID zuweisen.

ATL-Objekte erhalten normalerweise eine Klassenfactory durch Ableiten von [CComCoClass](../../atl/reference/ccomcoclass-class.md). Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das als `CComClassFactory` Standardklassenfactory deklariert. Um diesen Standardwert zu überschreiben, geben Sie einen der DECLARE_CLASSFACTORY*xxx* -Makros in der Klassendefinition an. Das [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) -Makro verwendet beispielsweise die angegebene Klasse für die Klassenfactory:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Die obige Klassendefinition gibt an `CMyClassFactory` , dass als Standardklassenfactory des Objekts verwendet wird. `CMyClassFactory`muss von `CComClassFactory` abgeleitet und über `CreateInstance`schrieben werden.

ATL bietet drei weitere Makros, die eine Klassenfactory deklarieren:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Verwendet [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), das die Erstellung über eine Lizenz steuert.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Verwendet [ccomclassfactor yautothread](../../atl/reference/ccomclassfactoryautothread-class.md), mit dem Objekte in mehreren Apartments erstellt werden.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Verwendet [ccomclassfactorysingleton](../../atl/reference/ccomclassfactorysingleton-class.md), das ein einzelnes [ccomobjectglobal](../../atl/reference/ccomobjectglobal-class.md) -Objekt erstellt.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Deklariert `cf` als Klassenfactory.

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parameter

*CF*<br/>
in Der Name der Klasse, die das klassenfactoryobjekt implementiert.

### <a name="remarks"></a>Bemerkungen

Der *CF* -Parameter muss von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) abgeleitet werden und `CreateInstance` die-Methode überschreiben.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY](#declare_classfactory) -Makro, das `CComClassFactory` als Standardklassenfactory angibt. Wenn Sie jedoch das DECLARE_CLASSFACTORY_EX-Makro in die Klassendefinition Ihres Objekts einschließen, überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklariert [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) als Klassenfactory.

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parameter

*fröhlich*<br/>
in Eine Klasse, die `VerifyLicenseKey`, `GetLicenseKey`und `IsLicenseValid`implementiert.

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY](#declare_classfactory) -Makro, das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Wenn Sie jedoch das DECLARE_CLASSFACTORY2-Makro in die Klassendefinition Ihres Objekts einschließen, überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>CComClassFactory2-Klasse

Diese Klasse implementiert die [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) -Schnittstelle.

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parameter

*Führer*<br/>
Eine Klasse, die die folgenden statischen Funktionen implementiert:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Bemerkungen

`CComClassFactory2`implementiert die [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) -Schnittstelle, die eine Erweiterung von [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)ist. `IClassFactory2`steuert die Objekt Erstellung über eine Lizenz. Eine Klassenfactory, die auf einem lizenzierten Computer ausgeführt wird, kann einen Laufzeitlizenz Schlüssel bereitstellen. Dieser Lizenzschlüssel ermöglicht es einer Anwendung, Objekte zu instanziieren, wenn keine vollständige Computer Lizenz vorhanden ist.

ATL-Objekte erhalten normalerweise eine Klassenfactory durch Ableiten von [CComCoClass](../../atl/reference/ccomcoclass-class.md). Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um zu `CComClassFactory2`verwenden, geben Sie das [DECLARE_CLASSFACTORY2](#declare_classfactory2) -Makro in der Klassendefinition Ihres Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, der Vorlagen Parameter für `CComClassFactory2`, muss die statischen Funktionen `VerifyLicenseKey` `GetLicenseKey`, und `IsLicenseValid`implementieren. Im folgenden finden Sie ein Beispiel für eine einfache Lizenz Klasse:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`wird sowohl `CComClassFactory2Base` von als auch von der *Lizenz*abgeleitet. `CComClassFactory2Base`wiederum wird von `IClassFactory2` und **\< CComObjectRootEx ccomglobalsthlesemodel >** abgeleitet.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklariert [ccomclassfactoryautothread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory.

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY](#declare_classfactory) -Makro, das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Wenn Sie jedoch das DECLARE_CLASSFACTORY_AUTO_THREAD-Makro in die Klassendefinition Ihres Objekts einschließen, überschreiben Sie diese Standardeinstellung.

Wenn Sie Objekte in mehreren Apartments (in einem Out-of-proc-Server) erstellen, fügen Sie DECLARE_CLASSFACTORY_AUTO_THREAD zu ihrer Klasse hinzu.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Ccomclassfactoryautothread-Klasse

Diese Klasse implementiert die [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) -Schnittstelle und ermöglicht das Erstellen von Objekten in mehreren Apartments.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Bemerkungen

`CComClassFactoryAutoThread`ähnelt [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ermöglicht aber das Erstellen von Objekten in mehreren Apartments. Um diese Unterstützung zu nutzen, leiten Sie das exe-Modul von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)ab.

ATL-Objekte erhalten normalerweise eine Klassenfactory durch Ableiten von [CComCoClass](../../atl/reference/ccomcoclass-class.md). Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um zu `CComClassFactoryAutoThread`verwenden, geben Sie das [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) -Makro in der Klassendefinition Ihres Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklariert [ccomclassfactorysingleton](../../atl/reference/ccomclassfactorysingleton-class.md) als Klassenfactory.

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parameter

*obj*<br/>
in Der Name des Klassen Objekts.

### <a name="remarks"></a>Bemerkungen

[CComCoClass](../../atl/reference/ccomcoclass-class.md) enthält das [DECLARE_CLASSFACTORY](#declare_classfactory) -Makro, das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory angibt. Wenn Sie jedoch das DECLARE_CLASSFACTORY_SINGLETON-Makro in die Klassendefinition Ihres Objekts einschließen, überschreiben Sie diese Standardeinstellung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Ccomclassfactorysingleton-Klasse

Diese Klasse wird von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) abgeleitet und verwendet [ccomobjectglobal](../../atl/reference/ccomobjectglobal-class.md) , um ein einzelnes Objekt zu erstellen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse.

`CComClassFactorySingleton`wird von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) abgeleitet und verwendet [ccomobjectglobal](../../atl/reference/ccomobjectglobal-class.md) , um ein einzelnes Objekt zu erstellen. Jeder Aufrufe der `CreateInstance` -Methode fragt dieses Objekt einfach nach einem Schnittstellen Zeiger ab.

### <a name="remarks"></a>Bemerkungen

ATL-Objekte erhalten normalerweise eine Klassenfactory durch Ableiten von [CComCoClass](../../atl/reference/ccomcoclass-class.md). Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](#declare_classfactory), das als `CComClassFactory` Standardklassenfactory deklariert. Um zu `CComClassFactorySingleton`verwenden, geben Sie das [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) -Makro in der Klassendefinition Ihres Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklariert eine virtuelle Funktion `GetControllingUnknown`.

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Bemerkungen

Fügen Sie dem Objekt dieses Makro hinzu, `GetControllingUnknown` Wenn Sie die nicht definierte Compilerfehlermeldung erhalten (z. `CComAggregateCreator`b. in).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Gibt an, dass das Objekt nicht aggregiert werden kann.

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name des Klassen Objekts, das Sie als nicht aggregierbar definieren.

### <a name="remarks"></a>Bemerkungen

DECLARE_NOT_AGGREGATABLE bewirkt `CreateInstance` , dass einen Fehler (CLASS_E_NOAGGREGATION) zurückgibt, wenn versucht wird, auf das Objekt zu aggregieren.

Standardmäßig enthält [CComCoClass](../../atl/reference/ccomcoclass-class.md) das [DECLARE_AGGREGATABLE](#declare_aggregatable) -Makro, das angibt, dass das Objekt aggregiert werden kann. Um dieses Standardverhalten zu überschreiben, fügen Sie DECLARE_NOT_AGGREGATABLE in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Gibt an, dass das Objekt aggregiert werden muss.

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name des Klassen Objekts, das Sie als nur aggregatable definieren.

### <a name="remarks"></a>Bemerkungen

DECLARE_ONLY_AGGREGATABLE verursacht einen Fehler (E_FAIL), wenn ein Versuch an `CoCreate` Ihrem Objekt als nicht aggregiertes Objekt erfolgt.

Standardmäßig enthält [CComCoClass](../../atl/reference/ccomcoclass-class.md) das [DECLARE_AGGREGATABLE](#declare_aggregatable) -Makro, das angibt, dass das Objekt aggregiert werden kann. Um dieses Standardverhalten zu überschreiben, fügen Sie DECLARE_ONLY_AGGREGATABLE in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Gibt an, dass eine Instanz von **CComPolyObject \< ** *x* **>** erstellt wird, wenn das Objekt erstellt wird.

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name des Klassen Objekts, das Sie als aggregierbare oder nicht aggregierbare definieren.

### <a name="remarks"></a>Bemerkungen

Während der Erstellung wird der Wert des äußeren unbekannten-Werts geprüft. Wenn er NULL ist, `IUnknown` wird für ein nicht aggregiertes Objekt implementiert. Wenn das äußere unbekannte nicht NULL ist, `IUnknown` wird für ein aggregiertes Objekt implementiert.

Der Vorteil der Verwendung von DECLARE_POLY_AGGREGATABLE besteht darin, dass Sie `CComAggObject` sowohl `CComObject` als auch in Ihrem Modul vermeiden müssen, die aggregierten und nicht aggregierten Fälle zu verarbeiten. Ein einzelnes `CComPolyObject` -Objekt behandelt beide Fälle. Dies bedeutet, dass nur eine Kopie der vtable und eine Kopie der Funktionen in Ihrem Modul vorhanden sind. Wenn Ihre Vtable groß ist, kann dies die Modulgröße erheblich verringern. Wenn die Vtable jedoch klein ist, kann die `CComPolyObject` Verwendung von zu einer etwas größeren Modulgröße führen, da Sie nicht für ein aggregiertes oder nicht aggregiertes Objekt wie `CComAggObject` und `CComObject`optimiert ist.

Das DECLARE_POLY_AGGREGATABLE-Makro wird automatisch in Ihrem Objekt deklariert, wenn Sie den ATL-Steuerelement-Assistenten verwenden, um ein vollständiges Steuerelement zu erstellen.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Schützt das Objekt vor dem Löschen, wenn (während [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) das interne aggregierte Objekt den Verweis Zähler Inkremente erhöht und dann die Anzahl auf 0 verringert.

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Platzieren Sie dieses Makro in der Steuerelement Klasse eines ATL-ActiveX-Steuer Elements, um die viewstatusflags für den Container anzugeben.

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parameter

*statusFlags*<br/>
in Die VIEWSTATUS-Flags. Eine Liste der Flags finden Sie unter [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
