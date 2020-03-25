---
title: Module (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: e93073a1728063038ddd4e28dbb313854ee3c8c5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166691"
---
# <a name="module-c"></a>module (C++)

Definiert den Bibliotheksblock in der IDL-Datei.

## <a name="syntax"></a>Syntax

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>Parameter

*type*<br/>
Optionale Kann eines der folgenden sein:

- `dll` fügt Funktionen und Klassen hinzu, mit denen die resultierende DLL als in-Process-COM-Server fungieren kann. Dies ist der Standardwert.

- `exe` fügt Funktionen und Klassen hinzu, mit denen die resultierende ausführbare Datei als out-of-Process-COM-Server fungieren kann.

- `service` fügt Funktionen und Klassen hinzu, mit denen die resultierende ausführbare Datei als NT-Dienst fungieren kann.

- `unspecified` deaktiviert die Injektion von ATL-Code im Zusammenhang mit dem Modul Attribut: der Einschleusung der ATL-Modul Klasse, der globalen Instanz _AtlModule und der Einstiegspunkt Funktionen. Einfügen von ATL-Code aufgrund von anderen Attributen im Projekt wird nicht deaktiviert.

*name*<br/>
Optionale Der Name des Bibliotheks Blocks.

*version*<br/>
Optionale Die Versionsnummer, die Sie dem Bibliotheks Block zuweisen möchten. Der Standardwert ist 1,0.

*uuid*<br/>
Eindeutige ID für die Bibliothek. Wenn Sie diesen Parameter weglassen, wird automatisch eine ID für die Bibliothek generiert. Möglicherweise müssen Sie die *UUID* des Bibliotheks Blocks abrufen. dazu können Sie den Bezeichner **__uuidof (** *Libraryname* **)** verwenden.

*lcid*<br/>
Der Lokalisierungsparameter. Weitere Informationen finden Sie unter [lcid](/windows/win32/Midl/lcid) .

*Steuerelement*<br/>
Optionale Gibt an, dass alle Co-Klassen in der Bibliothek Steuerelemente sind.

*helpstring*<br/>
Gibt die Typbibliothek an.

*helpstringdll*<br/>
Optionale Legt den Namen der DLL-Datei fest, die zum Ausführen einer Dokument Zeichen folgen Suche verwendet werden soll. Weitere Informationen finden Sie unter [helpstringdll](/windows/win32/Midl/helpstringdll) .

*helpfile*<br/>
Optionale Der Name der **Hilfe** Datei für die Typbibliothek.

*helpcontext*<br/>
Optionale Die **Hilfe-ID** für diese Typbibliothek.

*helpstringcontext*<br/>
Optionale Weitere Informationen finden Sie unter [helpstringcontext](helpstringcontext.md) .

*hidden*<br/>
Optionale Verhindert, dass die gesamte Bibliothek angezeigt wird. Dies ist für die Verwendung mit Steuerelementen vorgesehen. Hosts müssen eine neue Typbibliothek erstellen, die das Steuerelement mit erweiterten Eigenschaften umschließt. Weitere Informationen finden Sie unter [hidden](/windows/win32/Midl/hidden) MIDL-Attribut.

*restricted*<br/>
Optionale Member der Bibliothek können nicht willkürlich aufgerufen werden. Weitere Informationen finden Sie unter [restricted](/windows/win32/Midl/restricted) MIDL-Attribut.

*custom*<br/>
Optionale Ein oder mehrere Attribute; Dies ähnelt dem [benutzerdefinierten](custom-cpp.md) Attribut. Der erste Parameter für *Custom* ist die GUID des Attributs. Beispiel:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
Die Zeichenfolgenressource-ID der RGS-Datei, die verwendet wird, um die APP-ID der DLL, ausführbaren Datei oder des Diensts zu registrieren. Wenn das Modul vom Typ Dienst ist, wird dieses Argument auch verwendet, um die ID der Zeichenfolge mit dem Dienstnamen zu erhalten.

> [!NOTE]
> Die RGS-Datei und die Zeichenfolge, die den Namen des Diensts enthält, sollten den gleichen numerischen Wert enthalten.

## <a name="remarks"></a>Bemerkungen

Wenn Sie nicht den Parameter *restricted* auf [emitidl](emitidl.md)setzen, ist **module** in jedem Programm erforderlich, das C++-Attribute verwendet.

Ein Bibliotheksblock wird erstellt, wenn Sie zusätzlich zum **module** -Attribut im Quellcode auch [dispinterface](dispinterface.md), [dual](dual.md), [object](object-cpp.md)oder ein Attribut, das [coclass](coclass.md)impliziert, verwenden.

Pro IDL-Datei ist ein Bibliotheksblock zulässig. Mehrere Modul-Einträge im Quellcode werden zusammengeführt und die neuesten Parameterwerte werden implementiert.

Wenn dieses Attribut in einem Projekt verwendet wird, das ATL verwendet, ändert sich das Verhalten des Attributs. Zusätzlich zum obigen Verhalten fügt das Attribut auch ein globales Objekt (mit dem Namen `_AtlModule`) des richtigen Typs und zusätzlichen Unterstützungs Codes ein. Wenn das Attribut eigenständig ist, wird eine von dem richtigen Modultyp abgeleitete Klasse eingefügt. Wenn das Attribut auf eine Klasse angewendet wird, wird eine Basisklasse des richtigen Modultyps hinzugefügt. Der richtige Typ wird durch den Wert des *Typparameters* bestimmt:

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) dient als Basisklasse und als für einen COM-Server erforderliche Standard-DLL-Einstiegspunkte. Diese Einstiegspunkte sind [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)und [DllGetClassObject](/previous-versions//dd797891\(v=vs.85\)).

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) dient als Basisklasse und ausführbarer Standardeinstiegspunkt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) dient als Basisklasse und ausführbarer Standardeinstiegspunkt [WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

- `type` = **unspecified**

   Deaktiviert die Einfügung von ATL-Code im Zusammenhang mit dem Modulattribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie ein Bibliotheksblock in der generierten IDL-Datei erstellt wird.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

Der folgende Code zeigt, dass Sie Ihre eigene Implementierung einer Funktion angeben können, die in dem Code angezeigt wird, der durch die Verwendung von **module**eingefügt wurde. Weitere Informationen zum Anzeigen von eingefügtem Code finden Sie unter [/Fx](../../build/reference/fx-merge-injected-code.md) . Um eine der Funktionen zu überschreiben, die vom Attribut **module** eingefügt wurden, erstellen Sie eine Klasse, die die Implementierung der Funktion enthält, und wenden Sie das Attribut **module** auf diese Klasse an.

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Überall|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[fern](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)
