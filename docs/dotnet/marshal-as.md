---
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2b2cacb0acf04aa40b3e299bffd7357e04916b16
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544844"
---
# <a name="marshal_as"></a>marshal_as

Bei dieser Methode werden Daten zwischen systemeigenen und verwalteten Umgebungen konvertiert.

## <a name="syntax"></a>Syntax

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parameter

*input*<br/>
in Der Wert, den Sie zu einer `To_Type` Variablen Mars Hallen möchten.

## <a name="return-value"></a>Rückgabewert

Eine Variable vom Typ `To_Type`, bei dem es sich um den konvertierten Wert von `input` handelt.

## <a name="remarks"></a>Hinweise

Diese Methode ist eine vereinfachte Möglichkeit zum Konvertieren von Daten zwischen systemeigenen und verwalteten Typen. Informationen dazu, welche Datentypen unterstützt werden, finden Sie unter Übersicht über das Marshalling [in C++ ](../dotnet/overview-of-marshaling-in-cpp.md). Einige Datenkonvertierungen erfordern einen Kontext. Sie können diese Datentypen mit der marshal_context- [Klasse](../dotnet/marshal-context-class.md)konvertieren.

Wenn Sie versuchen, ein nicht unterstütztes paar von Datentypen zu Mars Hallen, generiert `marshal_as` zum Zeitpunkt der Kompilierung eine [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) -Fehlermeldung. Weitere Informationen zu dem Fehler finden Sie in der zugehörigen Meldung. Der Fehler `C4996` kann auch bei anderen Problemen als veralteten Funktionen generiert werden. Dazu zählt beispielsweise der Versuch, ein Paar von Datentypen zu marshallen, die nicht unterstützt werden.

Die Marshallingbibliothek besteht aus mehreren Headerdateien. Für jede Konvertierung ist nur eine Datei erforderlich, Sie können bei Bedarf jedoch zusätzliche Dateien für andere Konvertierungen einbinden. Informationen darüber, welche Konvertierungen welchen Dateien zugeordnet sind, finden Sie in der Tabelle in `Marshaling Overview`. Unabhängig vom Typ der durchzuführenden Konvertierung ist die Namespaceanforderung immer gültig.

Löst `System::ArgumentNullException(_EXCEPTION_NULLPTR)` aus, wenn der Eingabeparameter NULL ist.

## <a name="example"></a>Beispiel

In diesem Beispiel erfolgt das Marshalling von einem `const char*`- zu einem `System::String`-Variablentyp.

```cpp
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Voraussetzungen

**Header Datei:** \<msclr\marshal.h >, \<msclr \ marshal_windows. h >, \<msclr \ marshal_cppstd. h > oder \<msclr \ marshal_atl. h >

**Namespace:** msclr:: Interop

## <a name="see-also"></a>Siehe auch

[Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context-Klasse](../dotnet/marshal-context-class.md)
