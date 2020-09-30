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
ms.openlocfilehash: aa5935332cfa12c02e8084136a311a7593a4f3b9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508587"
---
# <a name="marshal_context-class"></a>marshal_context-Klasse

Mit dieser Klasse werden Daten zwischen nativen und verwalteten Umgebungen konvertiert.

## <a name="syntax"></a>Syntax

```cpp
class marshal_context
```

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die- `marshal_context` Klasse für Datenkonvertierungen, die einen Kontext erfordern. Weitere Informationen dazu, welche Konvertierungen einen Kontext erfordern und welche Marshallingdatei eingeschlossen werden muss, finden Sie unter Übersicht über das Marshalling [in C++](../dotnet/overview-of-marshaling-in-cpp.md). Das Ergebnis des Marshalling bei Verwendung eines Kontexts ist nur gültig, bis das `marshal_context` Objekt zerstört wird. Um das Ergebnis zu erhalten, müssen Sie die Daten kopieren.

Das gleiche `marshal_context` kann für zahlreiche Datenkonvertierungen verwendet werden. Wenn Sie den Kontext auf diese Weise wieder verwenden, wirkt sich dies nicht auf die Ergebnisse früherer Marshallingaufrufe aus.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Erstellt ein- `marshal_context` Objekt, das für die Datenkonvertierung zwischen verwalteten und nativen Datentypen verwendet werden soll.|
|[marshal_context:: ~ marshal_context](#tilde-marshal-context)|Zerstört ein `marshal_context` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Führt das Marshalling für ein bestimmtes Datenobjekt aus, um es zwischen einem verwalteten und einem nativen Datentyp zu konvertieren.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header Datei:** \<msclr\marshal.h> , \<msclr\marshal_windows.h> , \<msclr\marshal_cppstd.h> oder \<msclr\marshal_atl.h>

**Namespace:** msclr:: Interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a> marshal_context:: marshal_context

Erstellt ein- `marshal_context` Objekt, das für die Datenkonvertierung zwischen verwalteten und nativen Datentypen verwendet werden soll.

```cpp
marshal_context();
```

### <a name="remarks"></a>Bemerkungen

Einige Datenkonvertierungen erfordern einen Mars Hall Kontext. Weitere Informationen dazu, welche Übersetzungen einen Kontext erfordern und welche Marshallingdatei Sie in Ihre Anwendung einschließen müssen, finden Sie unter Übersicht über das Marshalling [in C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [marshal_context:: marshal_as](#marshal-as).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a> marshal_context:: ~ marshal_context

Zerstört ein `marshal_context` -Objekt.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Bemerkungen

Einige Datenkonvertierungen erfordern einen Mars Hall Kontext. Unter Übersicht über das Marshalling [in C++](../dotnet/overview-of-marshaling-in-cpp.md) finden Sie weitere Informationen dazu, welche Übersetzungen einen Kontext erfordern und welche Marshallingdatei in Ihre Anwendung eingeschlossen werden muss.

Das Löschen eines- `marshal_context` Objekts führt dazu, dass die von diesem Kontext konvertierten Daten ungültig werden. Wenn Sie Ihre Daten beibehalten möchten, nachdem ein- `marshal_context` Objekt zerstört wurde, müssen Sie die Daten manuell in eine Variable kopieren, die persistent gespeichert wird.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a> marshal_context:: marshal_as

Führt das Marshalling für ein bestimmtes Datenobjekt aus, um es zwischen einem verwalteten und einem nativen Datentyp zu konvertieren.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parameter

*input*<br/>
in Der Wert, der zu einer Variablen gemarshallt werden soll `To_Type` .

### <a name="return-value"></a>Rückgabewert

Eine Variable vom Typ `To_Type` , die den konvertierten Wert von ist `input` .

### <a name="remarks"></a>Bemerkungen

Diese Funktion führt das Marshalling für ein bestimmtes Datenobjekt aus. Verwenden Sie diese Funktion nur mit den Konvertierungen, die in der-Tabelle unter Übersicht über das Marshalling [in C++](../dotnet/overview-of-marshaling-in-cpp.md)angegeben sind.

Wenn Sie versuchen, ein nicht unterstütztes paar von Datentypen zu Mars Hallen, `marshal_as` generiert einen Fehler [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) zur Kompilierzeit. Weitere Informationen zu dem Fehler finden Sie in der zugehörigen Meldung. Der Fehler `C4996` kann auch bei anderen Problemen als veralteten Funktionen generiert werden. Dieser Fehler wird durch zwei Bedingungen verursacht, bei denen versucht wird, ein paar von Datentypen zu Mars Hallen, die nicht unterstützt werden und `marshal_as` für eine Konvertierung zu verwenden sind, die einen Kontext erfordert.

Die Marshallingbibliothek besteht aus mehreren Headerdateien. Für jede Konvertierung ist nur eine Datei erforderlich, Sie können bei Bedarf jedoch zusätzliche Dateien für andere Konvertierungen einbinden. Die-Tabelle in `Marshaling Overview in C++` gibt an, welche marshallingdateien für jede Konvertierung eingeschlossen werden sollen.

### <a name="example"></a>Beispiel

In diesem Beispiel wird ein Kontext für das Marshalling von einem `System::String` zu einem `const char *` Variablentyp erstellt. Die konvertierten Daten sind nach der Zeile, in der der Kontext gelöscht wird, nicht gültig.

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
