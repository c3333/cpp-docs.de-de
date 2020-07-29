---
title: Co-Klasse (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 0a47f4f503541f9dee67dd8c6cf10297de724a19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232793"
---
# <a name="coclass"></a>coclass

Erstellt ein COM-Objekt, das eine COM-Schnittstelle implementieren kann.

## <a name="syntax"></a>Syntax

```cpp
[coclass]
```

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut **Co-Klasse** platziert ein Co-Klassen Konstrukt in der generierten IDL-Datei.

Wenn Sie eine Co-Klasse definieren, können Sie auch die Attribute [UUID](uuid-cpp-attributes.md), [Version](version-cpp.md), [Threading](threading-cpp.md), [Vi_progid](vi-progid.md)und [ProgID](progid.md) angeben. Wenn eine davon nicht angegeben wird, wird Sie generiert.

Wenn zwei Header Dateien Klassen mit dem **Co-Klasse** -Attribut enthalten und keine GUID angeben, verwendet der Compiler dieselbe GUID für beide Klassen und führt zu einem mittleren Fehler.  Daher sollten Sie das-Attribut verwenden, `uuid` Wenn Sie **Co-Klasse**verwenden.

**ATL-Projekte**

Wenn dieses Attribut einer Klassen-oder Struktur Definition in einem ATL-Projekt vorangestellt ist, gibt es Folgendes:

- Fügt Code oder Daten ein, um die automatische Registrierung für das-Objekt zu unterstützen.

- Fügt Code oder Daten ein, um eine COM-Klassenfactory für das-Objekt zu unterstützen.

- Fügt Code oder Daten ein, um `IUnknown` das Objekt zu implementieren und zu einem com-erstellbar-Objekt zu machen.

Insbesondere werden dem Zielobjekt die folgenden Basisklassen hinzugefügt:

- [CComCoClass-Klasse](../../atl/reference/ccomcoclass-class.md) stellt die Standardklassenfactory und das Aggregations Modell für das-Objekt bereit.

- Die [CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md) verfügt über eine Vorlage, die auf der Threading Modell Klasse basiert, die vom [Threading](threading-cpp.md) -Attribut angegeben wird. Wenn das- `threading` Attribut nicht angegeben wird, ist das Standard Threading Modell "Apartment".

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) wird hinzugefügt, wenn das nicht [erstellbar](noncreatable.md) -Attribut für das Zielobjekt nicht angegeben ist.

Schließlich wird jede duale Schnittstelle, die nicht mit eingebetteter IDL definiert ist, durch die entsprechende [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) -Klasse ersetzt. Wenn die duale Schnittstelle in eingebetteter IDL definiert ist, wird die bestimmte Schnittstelle in der Basisliste nicht geändert.

Das **Co-Klasse** -Attribut macht auch die folgenden Funktionen über injizierten Code verfügbar, oder im Fall von `GetObjectCLSID` als statische Methode in der Basisklasse `CComCoClass` :

- `UpdateRegistry`registriert die Klassenfactorys der Zielklasse.

- `GetObjectCLSID`, der sich auf die Registrierung bezieht, kann auch zum Abrufen der CLSID der Zielklasse verwendet werden.

- `GetObjectFriendlyName`gibt standardmäßig eine Zeichenfolge im Format " \<*target class name*> `Object` " zurück. Wenn diese Funktion bereits vorhanden ist, wird Sie nicht hinzugefügt. Fügen Sie diese Funktion der Zielklasse hinzu, um einen freundlicheren Namen als den automatisch generierten Namen zurückzugeben.

- `GetProgID`, der sich auf die Registrierung bezieht, gibt die mit dem [ProgID](progid.md) -Attribut angegebene Zeichenfolge zurück.

- `GetVersionIndependentProgID`verfügt über die gleiche Funktionalität wie `GetProgID` , gibt jedoch die mit [Vi_progid](vi-progid.md)angegebene Zeichenfolge zurück.

Die folgenden Änderungen, die mit der com-Zuordnung verknüpft sind, werden an der Zielklasse vorgenommen:

- Eine COM-Zuordnung wird mit Einträgen für alle Schnittstellen hinzugefügt, von denen die Zielklasse abgeleitet ist, sowie für alle Einträge, die durch das Einstiegspunkte-Attribut der [com-Schnittstelle](../../mfc/com-interface-entry-points.md) oder durch das [Aggregate](aggregates.md) -Attribut

- Ein [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) -Makro wird in die com-Zuordnung eingefügt.

Der Name der Co-Klasse, die in der IDL-Datei für die Klasse generiert wird, hat denselben Namen wie die Klasse.  Verwenden Sie z. b., und verweisen Sie auf das folgende Beispiel, um auf die Klassen-ID für eine Co `CMyClass` -Klasse in einem Client über die von der mittleren Liste generierte Header Datei zuzugreifen `CLSID_CMyClass` .

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das **Co-Klasse** -Attribut verwendet wird:

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

Im folgenden Beispiel wird gezeigt, wie die Standard Implementierung einer Funktion überschrieben wird, die in dem Code angezeigt wird, der vom **Co-Klasse** -Attribut eingefügt wird. Weitere Informationen zum Anzeigen von eingefügtem Code finden Sie unter [/Fx](../../build/reference/fx-merge-injected-code.md) . Alle Basisklassen oder Schnittstellen, die Sie für eine Klasse verwenden, werden im eingefügten Code angezeigt. Wenn eine Klasse standardmäßig in den eingefügten Code eingeschlossen wird und Sie diese Klasse explizit als Basis für die Co-Klasse angeben, verwendet der Attribut Anbieter das im Code angegebene Formular.

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[IDL-Attribute](idl-attributes.md)<br/>
[COM-Attribute](com-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
