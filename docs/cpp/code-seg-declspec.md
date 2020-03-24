---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180835"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Microsoft-spezifisch**

Das Attribut **code_seg** Deklaration benennt ein ausführbares Textsegment in der obj-Datei, in dem der Objektcode für die Funktion oder die Klassenmember-Funktionen gespeichert wird.

## <a name="syntax"></a>Syntax

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>Bemerkungen

Das `__declspec(code_seg(...))`-Attribut aktiviert die Platzierung von Code in getrennt benannte Segmente, die einzeln ausgelagert oder im Speicher gesperrt werden können. Sie können dieses Attribut verwenden, um die Platzierung instanziierter Vorlagen und von durch den Compiler generiertem Code zu steuern.

Ein *Segment* ist ein benannter Datenblock in einer OBJ-Datei, der als Einheit in den Arbeitsspeicher geladen wird. Ein *Textsegment* ist ein Segment, das ausführbaren Code enthält. Der Begriff " *Abschnitt* " wird häufig austauschbar mit Segmenten verwendet.

Objektcode, der generiert wird, wenn `declarator` definiert wird, wird in das durch `segname` angegebene Textsegment platziert, das ein Literal mit schmaler Zeichenfolge ist. Der Name `segname` muss nicht in einem [Abschnitts](../preprocessor/section.md) -Pragma angegeben werden, bevor er in einer Deklaration verwendet werden kann. Standardmäßig, wenn kein `code_seg` angegeben wird, wird Objektcode in ein Segment mit dem Namen .text platziert. Ein **code_seg** Attribut überschreibt jede vorhandene [#pragma code_seg](../preprocessor/code-seg.md) Direktive. Ein **code_seg** Attribut, das auf eine Element Funktion angewendet wird, überschreibt alle **code_seg** Attribute, die auf die einschließende Klasse angewendet werden.

Wenn eine Entität über ein **code_seg** Attribut verfügt, müssen alle Deklarationen und Definitionen derselben Entität identische **code_seg** Attribute aufweisen. Wenn eine Basisklasse über ein **code_seg** Attribut verfügt, müssen abgeleitete Klassen über dasselbe Attribut verfügen.

Wenn ein **code_seg** Attribut auf eine Namespace-Scope-Funktion oder eine Member-Funktion angewendet wird, wird der Objektcode für diese Funktion in das angegebene Textsegment eingefügt. Wenn dieses Attribut auf eine Klasse angewendet wird, werden alle Memberfunktionen dieser Klasse und geschachtelter Klassen, was vom Compiler generierte spezielle Memberfunktionen umfasst, in das angegebene Segment platziert. Lokal definierte Klassen – z. b. Klassen, die in einem Member-Funktions Text definiert sind – erben nicht das **code_seg** -Attribut des einschließenden Bereichs.

Wenn ein **code_seg** Attribut auf eine Vorlagen Klasse oder eine Vorlagen Funktion angewendet wird, werden alle impliziten Spezialisierungs Funktionen der Vorlage in das angegebene Segment eingefügt. Explizite oder partielle Spezialisierungs Vererbung erbt nicht das **code_seg** Attribut von der primären Vorlage. Sie können das gleiche oder ein anderes **code_seg** Attribut für die Spezialisierung angeben. Ein **code_seg** Attribut kann nicht auf eine explizite Vorlagen Instanziierung angewendet werden.

Standardmäßig wird vom Compiler generierter Code, wie beispielsweise eine spezielle Memberfunktion, in das Segment .text platziert. Die Direktive `#pragma code_seg` überschreibt diesen Standard nicht. Verwenden Sie das **code_seg** -Attribut für die Klasse, die Klassen Vorlage oder die Funktions Vorlage, um zu steuern, wo der vom Compiler generierte Code eingefügt wird.

Lambdas erben **code_seg** Attribute aus Ihrem einschließenden Gültigkeitsbereich. Um ein Segment für einen Lambda anzugeben, wenden Sie ein **code_seg** -Attribut nach der Parameter-Declaration-Klausel und vor jeder änderbaren oder Ausnahme Spezifikation, allen nachfolgenden Rückgabetyp Spezifikationen und dem Lambda-Text an. Weitere Informationen finden Sie unter [Lambda-Ausdrucks Syntax](../cpp/lambda-expression-syntax.md). In diesem Beispiel wird ein Lambda in einem Segment mit dem Namen PagedMem definiert:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Passen Sie auf, wenn Sie spezifische Memberfunktionen – insbesondere virtuelle Memberfunktionen – in unterschiedliche Segmente platzieren. Wenn Sie eine virtuelle Funktion in einer abgeleiteten Klasse definieren, die sich in einem ausgelagerten Segment befindet, während die Basisklassenmethode sich in einem nicht ausgelagerten Segment befindet, nehmen möglicherweise andere Basisklassenmethoden oder Benutzercode an, dass der Aufruf der virtuellen Methode keinen Seitenfehler auslösen wird.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie ein **code_seg** Attribut die Segment Platzierung steuert, wenn implizite und explizite Vorlagen Spezialisierungen verwendet werden:

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
