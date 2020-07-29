---
title: '#using-Anweisung (C++/CLI)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 0da255957e92a570750da2687bf1444df2e6ab13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219429"
---
# <a name="using-directive-ccli"></a>#using-Direktive (C++/CLI)

Importiert Metadaten in ein Programm, das mit [/CLR](../build/reference/clr-common-language-runtime-compilation.md)kompiliert wurde.

## <a name="syntax"></a>Syntax

> **`#using`***Datei* [ **`as_friend`** ]

### <a name="parameters"></a>Parameter

*Datei*\
Eine MSIL-Datei (Microsoft Intermediate Language) *`.dll`* ,, *`.exe`* *`.netmodule`* oder *`.obj`* . Beispiel:

`#using <MyComponent.dll>`

**`as_friend`**\
Gibt an, dass auf alle Typen in der *Datei* zugegriffen werden kann. Weitere Informationen finden Sie unter Friend-Assemblys [(C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Bemerkungen

bei der *Datei* kann es sich um eine MSIL-Datei (Microsoft Intermediate Language) handeln, die Sie für die verwalteten Daten und verwalteten Konstrukte importieren. Wenn eine DLL ein Assemblymanifest enthält, werden alle DLLs importiert, auf die im Manifest verwiesen wird. In der Assembly, die Sie erstellt haben, wird die *Datei* in den Metadaten als Assemblyverweis aufgelistet.

Möglicherweise enthält die *Datei* keine Assembly (die*Datei* ist ein Modul), und Sie beabsichtigen nicht, Typinformationen aus dem Modul in der aktuellen (assemblyanwendung) zu verwenden. Sie können angeben, dass das Modul Teil der Assembly ist, indem Sie [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)verwenden. Die Typen im Modul wären dann für jede Anwendung verfügbar, die auf die Assembly verweist.

Eine Alternative zur Verwendung von **`#using`** ist die [/Fu](../build/reference/fu-name-forced-hash-using-file.md) -Compileroption.

. exe-Assemblys, die an übergeben **`#using`** werden, sollten mithilfe eines der .net Visual Studio-Compiler (z. b. Visual Basic oder Visual c#) kompiliert werden.  Der Versuch, Metadaten aus einer exe-Assembly zu importieren, die mit kompiliert wurde, **`/clr`** führt zu einer Datei Lade Ausnahme.

> [!NOTE]
> Eine Komponente, auf die mit verwiesen wird **`#using`** , kann mit einer anderen Version der Datei ausgeführt werden, die zur Kompilierzeit importiert wurde, wodurch eine Client Anwendung unerwartete Ergebnisse liefert.

Damit der Compiler einen Typ in einer Assembly (nicht in einem Modul) erkennen kann, muss er gezwungen werden, den Typ aufzulösen. Sie können dies erzwingen, indem Sie z. b. eine Instanz des Typs definieren. Es gibt weitere Möglichkeiten, Typnamen in einer Assembly für den Compiler aufzulösen. Wenn Sie z. b. von einem Typ in einer Assembly erben, wird der Typname dem Compiler bekannt.

Beim Importieren von Metadaten, die aus Quellcode erstellt wurden [`__declspec(thread)`](../cpp/thread.md) , der verwendet wurde, wird die Thread Semantik nicht in den Metadaten beibehalten. Beispielsweise hat eine mit deklarierte Variable **`__declspec(thread)`** , die in einem Programm kompiliert wurde, das für die .NET Framework Common Language Runtime erstellt und dann über importiert wird, **`#using`** keine **`__declspec(thread)`** Semantik für die Variable.

Alle importierten Typen (sowohl verwaltete als auch native) in einer Datei, auf die von verwiesen **`#using`** wird, sind verfügbar, aber der Compiler behandelt systemeigene Typen als Deklarationen, nicht als Definitionen.

Auf mscorlib.dll wird beim Kompilieren mit automatisch verwiesen **`/clr`** .

Die LIBPATH-Umgebungsvariable gibt die Verzeichnisse an, die durchsucht werden sollen, wenn der Compiler Dateinamen auflöst, **`#using`** die an an

Der Compiler sucht nach Verweisen im folgenden Pfad:

- Ein Pfad, der in der-Anweisung angegeben ist **`#using`** .

- Das aktuelle Verzeichnis.

- Das .NET Framework-Systemverzeichnis.

- Mit der-Compileroption hinzugefügte Verzeichnisse [`/AI`](../build/reference/ai-specify-metadata-directories.md) .

- Verzeichnisse der LIBPATH-Umgebungsvariable.

## <a name="example"></a>Beispiel

Sie können eine Assembly erstellen, die auf eine zweite Assembly verweist, die wiederum auf eine dritte Assembly verweist. Sie müssen nur explizit auf die dritte Assembly verweisen, wenn Sie explizit einen ihrer Typen verwenden.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>Beispiel

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel meldet der Compiler keinen Fehler, wenn auf *using_assembly_A.dll*verwiesen wird, da das Programm keinen der in *using_assembly_A. cpp*definierten Typen verwendet.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>Weitere Informationen

[Präprozessoranweisungen](../preprocessor/preprocessor-directives.md)
