---
title: COM-Unterstützung des Compilers
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 9a5961049cbc54c94cec5b444e2d98f013dda932
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233781"
---
# <a name="compiler-com-support"></a>COM-Unterstützung des Compilers

**Microsoft-spezifisch**

Der Microsoft C++-Compiler kann COM-Typbibliotheken (Component Object Model) direkt lesen und den Inhalt in C++-Quellcode übersetzen, der in die Kompilierung aufgenommen werden kann. Spracherweiterungen sind verfügbar, um die COM-Programmierung auf Clientseite für Desktop-Apps zu vereinfachen.

Mithilfe der [#import Präprozessordirektive](../preprocessor/hash-import-directive-cpp.md)kann der Compiler eine Typbibliothek lesen und in eine C++-Header Datei konvertieren, die die COM-Schnittstellen als Klassen beschreibt. Ein Satz von `#import`-Attributen ist für die Benutzersteuerung des Inhalts der resultierenden Typbibliothek-Headerdateien verfügbar.

Sie können das [__declspec](../cpp/declspec.md) Extended-Attribut [UUID](../cpp/uuid-cpp.md) verwenden, um einem COM-Objekt eine Globally Unique Identifier (GUID) zuzuweisen. Das Schlüsselwort [__uuidof](../cpp/uuidof-operator.md) kann zum Extrahieren der einem COM-Objekt zugeordneten GUID verwendet werden. Ein anderes **`__declspec`** Attribut, [Eigenschaft](../cpp/property-cpp.md), kann verwendet werden, um die `get` -Methode und die- `set` Methode für einen Datenmember eines COM-Objekts anzugeben.

Eine Reihe von com-Unterstützung für globale Funktionen und Klassen wird bereitgestellt, um die Typen und zu unterstützen `VARIANT` `BSTR` , intelligente Zeiger zu implementieren und das von ausgelöste Fehler Objekt zu Kapseln `_com_raise_error` :

- [Globale com-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Compiler-com-Unterstützungs Klassen](../cpp/compiler-com-support-classes.md)<br/>
[Globale com-Funktionen des Compilers](../cpp/compiler-com-global-functions.md)
