---
title: marshal_context-Klasse
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332015"
---
# <a name="marshal_context-class"></a>marshal_context-Klasse

Diese Klasse konvertiert Daten zwischen systemeigenen und verwalteten Umgebungen.

## <a name="syntax"></a>Syntax

```cpp
class marshal_context
```

## <a name="remarks"></a>Bemerkungen

Verwenden `marshal_context` Sie die Klasse für Datenkonvertierungen, die einen Kontext erfordern. Weitere Informationen darüber, welche Konvertierungen einen Kontext erfordern und welche Marshallingdatei eingeschlossen werden muss, finden Sie unter [Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md). Das Ergebnis des Marshallens bei Verwendung eines `marshal_context` Kontexts ist nur gültig, bis das Objekt zerstört wird. Um das Ergebnis beizubehalten, müssen Sie die Daten kopieren.

Das `marshal_context` gleiche kann für zahlreiche Datenkonvertierungen verwendet werden. Die Wiederverwendung des Kontexts auf diese Weise wirkt sich nicht auf die Ergebnisse früherer Marshallingaufrufe aus.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Erstellt ein `marshal_context` Objekt, das für die Datenkonvertierung zwischen verwalteten und systemeigenen Datentypen verwendet werden soll.|
|[marshal_context::marshal_context](#tilde-marshal-context)|Zerstört ein `marshal_context` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Führt das Marshalling für ein bestimmtes Datenobjekt aus, um es zwischen einem verwalteten und einem systemeigenen Datentyp zu konvertieren.|

## <a name="requirements"></a>Anforderungen

**Headerdatei:** \<msclr-marshal.h \<>, msclr-marshal_windows.h>, \<msclr-marshal_cppstd.h> oder \<msclr-marshal_atl.h>

**Namespace:** msclr::interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context::marshal_context

Erstellt ein `marshal_context` Objekt, das für die Datenkonvertierung zwischen verwalteten und systemeigenen Datentypen verwendet werden soll.

```cpp
marshal_context();
```

### <a name="remarks"></a>Bemerkungen

Einige Datenkonvertierungen erfordern einen Marshallkontext. Weitere Informationen darüber, welche Übersetzungen einen Kontext erfordern und welche Marshallingdatei Sie in Ihre Anwendung aufnehmen müssen, finden Sie unter [Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context::marshal_context

Zerstört ein `marshal_context` -Objekt.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Bemerkungen

Einige Datenkonvertierungen erfordern einen Marshallkontext. Weitere Informationen dazu, welche Übersetzungen einen Kontext erfordern und welche Marshallingdatei in Ihre Anwendung aufgenommen werden muss, finden Sie unter Übersicht über [das Marshalling in C++.](../dotnet/overview-of-marshaling-in-cpp.md)

Durch `marshal_context` das Löschen eines Objekts werden die von diesem Kontext konvertierten Daten ungültig. Wenn Sie Ihre Daten beibehalten `marshal_context` möchten, nachdem ein Objekt zerstört wurde, müssen Sie die Daten manuell in eine Variable kopieren, die beibehalten wird.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context::marshal_as

Führt das Marshalling für ein bestimmtes Datenobjekt aus, um es zwischen einem verwalteten und einem systemeigenen Datentyp zu konvertieren.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parameter

*input*<br/>
[in] Der Wert, den Sie `To_Type` in eine Variable marshallen möchten.

### <a name="return-value"></a>Rückgabewert

Eine Variable `To_Type` des Typs, die `input`den konvertierten Wert von ist.

### <a name="remarks"></a>Bemerkungen

Diese Funktion führt das Marshalling für ein bestimmtes Datenobjekt aus. Verwenden Sie diese Funktion nur mit den Konvertierungen, die durch die Tabelle in [Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md)angegeben sind.

Wenn Sie versuchen, ein Paar von Datentypen zu `marshal_as` marshallen, die nicht unterstützt werden, wird ein Fehler [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) zur Kompilierungszeit generiert. Weitere Informationen zu dem Fehler finden Sie in der zugehörigen Meldung. Der Fehler `C4996` kann auch bei anderen Problemen als veralteten Funktionen generiert werden. Zwei Bedingungen, die diesen Fehler generieren, sind der Versuch, ein Paar `marshal_as` von Datentypen zu marshallen, die nicht unterstützt werden, und versuchen, für eine Konvertierung zu verwenden, die einen Kontext erfordert.

Die Marshallingbibliothek besteht aus mehreren Headerdateien. Für jede Konvertierung ist nur eine Datei erforderlich, Sie können bei Bedarf jedoch zusätzliche Dateien für andere Konvertierungen einbinden. Die Tabelle `Marshaling Overview in C++` in gibt an, welche Marshallingdatei für jede Konvertierung eingeschlossen werden soll.

### <a name="example"></a>Beispiel

In diesem Beispiel wird ein `System::String` Kontext `const char *` zum Marshallen von a zu einem Variablentyp erstellt. Die konvertierten Daten sind nach der Zeile, die den Kontext löscht, nicht mehr gültig.

```cpp
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```
