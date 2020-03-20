---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 395f1443f4eef16d9eea44c23a6e3288daf03d14
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545468"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Ermöglicht die Verwendung von C++-Schlüsselwörtern als Bezeichner.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="syntax"></a>Syntax

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Hinweise

Die Verwendung des **__identifier**-Schlüsselworts für Bezeichner, die keine Schlüsselwörter sind, ist zulässig, jedoch wird aufgrund stilistischer Aspekte dringend davon abgeraten.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

### <a name="examples"></a>Beispiele

**Beispiel**

Im folgenden Beispiel wird eine Klasse namens **template** in C# erstellt und als DLL verteilt. In dem C++/CLI-Programm, das die **template**-Klasse verwendet, verbirgt das **__identifier**-Schlüsselwort die Tatsache, dass **template** ein standardmäßiges C++-Schlüsselwort ist.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Hinweise

Das **__identifier**-Schlüsselwort ist mit der `/clr`-Compileroption gültig.

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Klasse namens **template** in C# erstellt und als DLL verteilt. In dem C++/CLI-Programm, das die **template**-Klasse verwendet, verbirgt das **__identifier**-Schlüsselwort die Tatsache, dass **template** ein standardmäßiges C++-Schlüsselwort ist.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)<br/>
[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)