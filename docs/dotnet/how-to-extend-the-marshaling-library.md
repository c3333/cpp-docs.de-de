---
title: 'Gewusst wie: Erweitern der Marshallingbibliothek'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 071ea72a2aa03dcf16eb0f09e121eba4514e5828
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414606"
---
# <a name="how-to-extend-the-marshaling-library"></a>Gewusst wie: Erweitern der Marshallingbibliothek

In diesem Thema wird erläutert, wie Sie die Marshallingbibliothek erweitern, um mehr Konvertierungen zwischen Datentypen bereitzustellen. Benutzer können die Marshallingbibliothek für alle Datenkonvertierungen erweitern, die derzeit nicht von der Bibliothek unterstützt werden.

Die Marshallingbibliothek kann auf eine von zwei Arten erweitert werden: mit oder ohne [Marshal_context-Klasse](../dotnet/marshal-context-class.md). Überprüfen Sie das Thema Übersicht über das Marshalling [in C++](../dotnet/overview-of-marshaling-in-cpp.md) , um zu bestimmen, ob eine neue Konvertierung einen Kontext erfordert.

In beiden Fällen erstellen Sie zuerst eine Datei für neue Marshallingkonvertierungen. Dies geschieht, um die Integrität der standardmäßigen Marshallingbibliotheksdateien beizubehalten. Wenn Sie ein Projekt auf einen anderen Computer oder einen anderen Programmierer portieren möchten, müssen Sie die neue Marshallingdatei mit dem Rest des Projekts kopieren. Auf diese Weise erhält der Benutzer, der das Projekt empfängt, die neuen Konvertierungen und muss keine Bibliotheksdateien ändern.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>So erweitern Sie die Marshallingbibliothek durch eine Konvertierung, die keinen Kontext erfordert

1. Erstellen Sie eine Datei zum Speichern der neuen Marshallingfunktionen, z. b. MyMarshal. h.

1. Fügen Sie eine oder mehrere der Mars Hall Bibliotheksdateien ein:

   - Marshal. h für Basis Typen.

   - marshal_windows. h für Windows-Datentypen.

   - marshal_cppstd. h für die Datentypen der C++-Standard Bibliothek.

   - marshal_atl. h für ATL-Datentypen.

1. Verwenden Sie den Code am Ende dieser Schritte, um die Konvertierungs Funktion zu schreiben. In diesem Code ist für den Typ, in den konvertiert werden soll, von der Typ, aus dem konvertiert werden soll, und `from` ist der zu konvertierende Parameter.

1. Ersetzen Sie den Kommentar zur Konvertierungs Logik durch Code, um den `from` Parameter in ein Objekt von zu konvertieren und das konvertierte Objekt zurückzugeben.

```
namespace msclr {
   namespace interop {
      template<>
      inline TO marshal_as<TO, FROM> (const FROM& from) {
         // Insert conversion logic here, and return a TO parameter.
      }
   }
}
```

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>So erweitern Sie die Marshallingbibliothek durch eine Konvertierung, die einen Kontext erfordert

1. Erstellen Sie eine Datei zum Speichern der neuen Marshallingfunktionen, z. b. MyMarshal. h.

1. Fügen Sie eine oder mehrere der Mars Hall Bibliotheksdateien ein:

   - Marshal. h für Basis Typen.

   - marshal_windows. h für Windows-Datentypen.

   - marshal_cppstd. h für die Datentypen der C++-Standard Bibliothek.

   - marshal_atl. h für ATL-Datentypen.

1. Verwenden Sie den Code am Ende dieser Schritte, um die Konvertierungs Funktion zu schreiben. In diesem Code ist für den Typ, in den konvertiert werden soll, von der Typ, aus dem konvertiert werden soll, `toObject` ein Zeiger, in dem das Ergebnis gespeichert werden soll, und `fromObject` der zu konvertierende Parameter.

1. Ersetzen Sie den Kommentar zur Initialisierung durch Code, um den `toPtr` auf den entsprechenden leeren Wert zu initialisieren. Wenn es sich beispielsweise um einen-Zeiger handelt, legen Sie ihn auf fest `NULL` .

1. Ersetzen Sie den Kommentar zur Konvertierungs Logik durch Code, um den- `from` Parameter in ein Objekt von *zu* konvertieren. Dieses konvertierte Objekt wird in gespeichert `toPtr` .

1. Ersetzen Sie den Kommentar zur Einstellung `toObject` mit Code, der `toObject` auf das konvertierte Objekt festgelegt wird.

1. Ersetzen Sie den Kommentar zum Bereinigen von systemeigenen Ressourcen mit Code, um den von zugeordneten Arbeitsspeicher freizugeben `toPtr` . Wenn `toPtr` Speicher mithilfe von belegt **`new`** wird, verwenden **`delete`** Sie, um den Arbeitsspeicher freizugeben.

```
namespace msclr {
   namespace interop {
      template<>
      ref class context_node<TO, FROM> : public context_node_base
      {
      private:
         TO toPtr;
      public:
         context_node(TO& toObject, FROM fromObject)
         {
            // (Step 4) Initialize toPtr to the appropriate empty value.
            // (Step 5) Insert conversion logic here.
            // (Step 6) Set toObject to the converted parameter.
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // (Step 7) Clean up native resources.
         }
      };
   }
}
```

## <a name="example-extend-marshaling-library"></a>Beispiel: Erweitern der Marshallingbibliothek

Im folgenden Beispiel wird die Marshallingbibliothek durch eine Konvertierung erweitert, die keinen Kontext erfordert. In diesem Beispiel konvertiert der Code die Mitarbeiter Informationen von einem systemeigenen Datentyp in einen verwalteten Datentyp.

```cpp
// MyMarshalNoContext.cpp
// compile with: /clr
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   char* name;
   char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {
         ManagedEmp^ toValue = gcnew ManagedEmp;
         toValue->name = marshal_as<System::String^>(from.name);
         toValue->address = marshal_as<System::String^>(from.address);
         toValue->zipCode = from.zipCode;
         return toValue;
      }
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   NativeEmp employee;

   employee.name = "Jeff Smith";
   employee.address = "123 Main Street";
   employee.zipCode = 98111;

   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);

   Console::WriteLine("Managed name: {0}", result->name);
   Console::WriteLine("Managed address: {0}", result->address);
   Console::WriteLine("Managed zip code: {0}", result->zipCode);

   return 0;
}
```

Im vorherigen Beispiel `marshal_as` gibt die Funktion ein Handle für die konvertierten Daten zurück. Dies wurde durchgeführt, um zu verhindern, dass eine zusätzliche Kopie der Daten erstellt wird. Wenn die Variable direkt zurückgegeben wird, sind unnötige Leistungskosten verbunden.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example-convert-employee-information"></a>Beispiel: Konvertieren von Mitarbeiter Informationen

Im folgenden Beispiel werden die Mitarbeiter Informationen von einem verwalteten Datentyp in einen systemeigenen Datentyp konvertiert. Diese Konvertierung erfordert einen Marshallingkontext.

```cpp
// MyMarshalContext.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   const char* name;
   const char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base
      {
      private:
         NativeEmp* toPtr;
         marshal_context context;
      public:
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)
         {
            // Conversion logic starts here
            toPtr = NULL;

            const char* nativeName;
            const char* nativeAddress;

            // Convert the name from String^ to const char*.
            System::String^ tempValue = fromObject->name;
            nativeName = context.marshal_as<const char*>(tempValue);

            // Convert the address from String^ to const char*.
            tempValue = fromObject->address;
            nativeAddress = context.marshal_as<const char*>(tempValue);

            toPtr = new NativeEmp();
            toPtr->name = nativeName;
            toPtr->address = nativeAddress;
            toPtr->zipCode = fromObject->zipCode;

            toObject = toPtr;
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // When the context is deleted, it will free the memory
            // allocated for toPtr->name and toPtr->address, so toPtr
            // is the only memory that needs to be freed.
            if (toPtr != NULL) {
               delete toPtr;
               toPtr = NULL;
            }
         }
      };
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   ManagedEmp^ employee = gcnew ManagedEmp();

   employee->name = gcnew String("Jeff Smith");
   employee->address = gcnew String("123 Main Street");
   employee->zipCode = 98111;

   marshal_context context;
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);

   if (result != NULL) {
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",
         result->name, result->address, result->zipCode);
   }

   return 0;
}
```

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>Weitere Informationen

[Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md)
