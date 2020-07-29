---
title: Friend-Assemblys (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: a42caaf07f6ec0c71f63d6a0df8a79fff6f737e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221444"
---
# <a name="friend-assemblies-c"></a>Friend-Assemblys (C++)

Für anwendbare Laufzeiten stellt die Sprachfunktion *Friend* -Assemblys Typen im Namespace Bereich oder globalen Gültigkeitsbereich einer Assemblykomponente dar, auf die mindestens eine Clientassembly oder netmodule zugreifen kann.

## <a name="all-runtimes"></a>Alle Laufzeiten

**Anmerkungen**

(Diese Sprachfunktion wird nicht in allen Laufzeiten unterstützt.)

## <a name="windows-runtime"></a>Windows-Runtime

**Anmerkungen**

(Dieses Sprachfeature wird in der Windows-Runtime nicht unterstützt.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/ZW**

## <a name="common-language-runtime"></a>Common Language Runtime

**Anmerkungen**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>So machen Sie Typen im Namespace Gültigkeitsbereich oder globalen Gültigkeitsbereich einer Assemblykomponente verfügbar, die für eine Clientassembly oder NETMODULE verfügbar ist

1. Geben Sie in der Komponente ein Assemblyattribut an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> , und übergeben Sie den Namen der Clientassembly oder NETMODULE, die auf Typen im Namespace Bereich oder globalen Gültigkeitsbereich der Komponente zugreift.  Sie können mehrere Clientassemblys oder netmodules angeben, indem Sie zusätzliche Attribute angeben.

1. Wenn Sie in der Clientassembly oder NETMODULE mithilfe von auf die Komponentenassembly verweisen, `#using` übergeben Sie das- **`as_friend`** Attribut.  Wenn Sie das- **`as_friend`** Attribut für eine Assembly angeben, die nicht angibt `InternalsVisibleToAttribute` , wird eine Lauf Zeit Ausnahme ausgelöst, wenn Sie versuchen, auf einen Typ im Namespace-Gültigkeitsbereich oder globalen Gültigkeitsbereich der Komponente zuzugreifen.

Ein Buildfehler wird ausgegeben, wenn die Assembly, die das-Attribut enthält, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> keinen starken Namen hat, sondern die Clientassembly, die das- **`as_friend`** Attribut verwendet.

Obwohl Typen im Namespace Bereich und globalen Gültigkeitsbereich einer Clientassembly oder einem NetModule-Element bekannt sein können, ist der Zugriff auf Member weiterhin wirksam.  Beispielsweise können Sie nicht auf einen privaten Member zugreifen.

Der Zugriff auf alle Typen in einer Assembly muss explizit erteilt werden.  Die Assembly c hat z. b. keinen Zugriff auf alle Typen in Assembly a, wenn Assembly c auf Assembly b verweist und Assembly b Zugriff auf alle Typen in Assembly a hat.

Weitere Informationen zum Signieren von – d. h. zum Zuweisen eines starken Namens für – eine Assembly, die mit dem Microsoft C++-Compiler erstellt wird, finden Sie unter Assemblys mit [starkem Namen (Assemblysignierung) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Als Alternative zur Verwendung der Friend-Assemblys können Sie verwenden, <xref:System.Security.Permissions.StrongNameIdentityPermission> um den Zugriff auf einzelne Typen einzuschränken.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/clr**

### <a name="examples"></a>Beispiele

Im folgenden Codebeispiel wird eine Komponente definiert, die eine Clientassembly angibt, die Zugriff auf die Typen in der Komponente hat.

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Das nächste Codebeispiel greift auf einen privaten Typ in der-Komponente zu.

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

Im nächsten Codebeispiel wird eine Komponente definiert, aber es wird keine Clientassembly angegeben, die Zugriff auf die Typen in der Komponente hat.

Beachten Sie, dass die Komponente mithilfe von **/OPT: NOREF**verknüpft ist. Dadurch wird sichergestellt, dass private Typen in den Metadaten der Komponente ausgegeben werden. Dies ist nicht erforderlich, wenn das `InternalsVisibleTo` Attribut vorhanden ist. Weitere Informationen finden Sie unter [/OPT (Optimierungen)](../build/reference/opt-optimizations.md).

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Im folgenden Codebeispiel wird ein Client definiert, der versucht, auf einen privaten Typ in einer Komponente zuzugreifen, die keinen Zugriff auf seine privaten Typen bietet. Aufgrund des Verhaltens der Laufzeit müssen Sie, wenn Sie die Ausnahme abfangen möchten, versuchen, auf einen privaten Typ in einer Hilfsfunktion zuzugreifen.

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

Im nächsten Codebeispiel wird gezeigt, wie eine Komponente mit starkem Namen erstellt wird, die eine Clientassembly angibt, die Zugriff auf die Typen in der Komponente hat.

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Beachten Sie, dass die Komponente ihren öffentlichen Schlüssel angeben muss. Wir empfehlen, dass Sie die folgenden Befehle nacheinander an der Eingabeaufforderung ausführen, um ein Schlüsselpaar zu erstellen und den öffentlichen Schlüssel zu erhalten:

**SN-d friend_assemblies. snk**

**sn-k friend_assemblies. snk**

**sn-i friend_assemblies. snk friend_assemblies. snk**

**SN-PC friend_assemblies. snk-Schlüssel. PublicKey**

**sn -tp key.publickey**

Im nächsten Codebeispiel wird auf einen privaten Typ in der Komponente mit starkem Namen zugegriffen.

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)
