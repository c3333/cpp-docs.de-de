---
title: WRL-Integration (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: 3ea0f6aece985a2ee74916e737b9aab1bf0d1d96
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507406"
---
# <a name="wrl-integration-ccx"></a>WRL-Integration (C++/CX)

Sie können den WRL-Code problemlos mit Windows-Runtime dem WRL-Code (C++ Template Library) kombinieren. In derselben Übersetzungseinheit können Sie Objekte verwenden, die mit WRL-Handle-zu-Objekt- `^` Notation () und WRL-intelligenter Zeiger () deklariert wurden `ComPtr<T>` . Sie müssen jedoch manuell Rückgabewerte und WRL HRESULT-Fehlercodes und WRL-Ausnahmen verarbeiten.

## <a name="wrl-development"></a>WRL-Entwicklung

Weitere Informationen zum Erstellen und Verwenden von WRL-Komponenten finden Sie unter [Windows-Runtime C++ Template Library (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Beispiel

Der folgende Code Ausschnitt veranschaulicht die Verwendung von wrl und WRL, um Windows-Runtime Klassen zu nutzen und eine Metadatendatei zu untersuchen.

Das Beispiel stammt aus einem Code Ausschnitt im Forum Building Microsoft Store Apps. Der Autor dieses Codeausschnitts bietet die folgenden Haftungsausschlüsse und Bedingungen an:

1. C++ stellt keine spezifischen APIs bereit, um Windows-Runtime Typen widerzuspiegeln, aber Windows-Metadatendateien (. winmd) für einen Typ sind mit CLR-Metadatendateien vollständig kompatibel. Windows bietet die neuen APIs zur Metadatenermittlung (RoGetMetaDataFile), um zur WINMD-Datei für einen bestimmten Typ zu gelangen. Diese APIs sind für C++-Entwickler jedoch nur von begrenztem Nutzen, da Sie Klassen nicht instanziieren können.

1. Nachdem der Code kompiliert wurde, müssen Sie auch Runtimeobject.lib und Rometadata.lib an den Linker übergeben.

1. Dieser Ausschnitt wird unbearbeitet dargestellt. Auch wenn davon ausgegangen wird, dass er ordnungsgemäß funktioniert, kann er möglicherweise Fehler enthalten.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}
```

## <a name="see-also"></a>Weitere Informationen

[Interoperabilität mit anderen Sprachen](interoperating-with-other-languages-c-cx.md)
