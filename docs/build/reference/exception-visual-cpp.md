---
title: '&lt;Ausnahme > (C++ Dokumentations Kommentare)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: d56e0ce7c892cfd9fd909b5268043d77929bd43c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439865"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

Mit dem Tag \<exception> können Sie angeben, welche Ausnahmen ausgelöst werden können. Dieses Tag wird auf eine Methodendefinition angewendet.

## <a name="syntax"></a>Syntax

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parameter

*member*<br/>
Ein Verweis auf eine Ausnahme, die von der aktuellen Kompilierungsumgebung verfügbar ist. Der Compiler prüft mithilfe von Regeln für die Namenssuche, ob die angegebene Ausnahme vorhanden ist, und übersetzt in der Ausgabe-XML `member` in den kanonischen Elementnamen.  Der Compiler gibt eine Warnung aus, wenn er `member` nicht findet.

Setzen Sie den Namen in einfache oder doppelte Anführungszeichen.

Weitere Informationen zum Erstellen eines cref-Verweises auf einen generischen Typ finden Sie unter [\<see>](see-visual-cpp.md).

*description*<br/>
Eine Beschreibung

## <a name="remarks"></a>Bemerkungen

Dokumentationskommentare werden zu einer Datei verarbeitet, indem sie mit [/doc](doc-process-documentation-comments-c-cpp.md) kompiliert werden.

Der MSVC-Compiler versucht, die Anmerkungen zu dieser Version in einem Durchlauf durch die Dokumentations Kommentare aufzulösen.  Bei Verwendung der C++-Suchregeln wird deshalb, wenn ein Symbol vom Compiler nicht gefunden wird, der Verweis als nicht aufgelöst markiert. Weitere Informationen finden Sie unter [\<seealso>](seealso-visual-cpp.md).

## <a name="example"></a>Beispiel

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Weitere Informationen

[XML-Dokumentation](xml-documentation-visual-cpp.md)
