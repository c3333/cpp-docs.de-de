---
title: '&lt;Ausnahme> (C++-Dokumentations Kommentare)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 7e4b2276ecf5f4f4c4c05b389eb98a0f572f8027
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042107"
---
# <a name="ltexceptiongt-tag"></a>&lt;&gt;ausnahmetag

Mit dem Tag \<exception> können Sie angeben, welche Ausnahmen ausgelöst werden können. Dieses Tag wird auf eine Methodendefinition angewendet.

## <a name="syntax"></a>Syntax

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parameter

*Kollege*<br/>
Ein Verweis auf eine Ausnahme, die von der aktuellen Kompilierungsumgebung verfügbar ist. Der Compiler prüft mithilfe von Regeln für die Namenssuche, ob die angegebene Ausnahme vorhanden ist, und übersetzt in der Ausgabe-XML `member` in den kanonischen Elementnamen.  Der Compiler gibt eine Warnung aus, wenn er `member` nicht findet.

Setzen Sie den Namen in einfache oder doppelte Anführungszeichen.

Weitere Informationen zum Erstellen eines-kref-Verweises auf einen generischen Typ finden Sie unter [\<see>](see-visual-cpp.md) .

*description*<br/>
Eine Beschreibung

## <a name="remarks"></a>Bemerkungen

Kompilieren Sie mit [/doc](doc-process-documentation-comments-c-cpp.md) , um Dokumentations Kommentare in einer Datei zu verarbeiten.

Der MSVC-Compiler versucht, die Anmerkungen zu dieser Version in einem Durchlauf durch die Dokumentations Kommentare aufzulösen.  Bei Verwendung der C++-Suchregeln wird deshalb, wenn ein Symbol vom Compiler nicht gefunden wird, der Verweis als nicht aufgelöst markiert. Weitere Informationen finden Sie unter [\<seealso>](seealso-visual-cpp.md) .

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
