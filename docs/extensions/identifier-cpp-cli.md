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
ms.openlocfilehash: 5f95e9fc55acd33705b855c7c4f0ef268d4776a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219689"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Ermöglicht die Verwendung von C++-Schlüsselwörtern als Bezeichner.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="syntax"></a>Syntax

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Bemerkungen

Die Verwendung des **__identifier**-Schlüsselworts für Bezeichner, die keine Schlüsselwörter sind, ist zulässig, jedoch wird aufgrund stilistischer Aspekte dringend davon abgeraten.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

### <a name="examples"></a>Beispiele

**Beispiel**

Im folgenden Beispiel wird eine Klasse mit dem Namen `template` in c# erstellt und als DLL verteilt. Im C++/CLI-Programm, das die- `template` Klasse verwendet, **`__identifier`** verbirgt das Schlüsselwort die Tatsache, dass `template` es sich um ein C++-Schlüsselwort handelt.

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

### <a name="remarks"></a>Bemerkungen

Das **__identifier**-Schlüsselwort ist mit der `/clr`-Compileroption gültig.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Klasse mit dem Namen `template` in c# erstellt und als DLL verteilt. Im C++/CLI-Programm, das die- `template` Klasse verwendet, **`__identifier`** verbirgt das Schlüsselwort die Tatsache, dass `template` es sich um ein C++-Schlüsselwort handelt.

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

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)<br/>
[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
