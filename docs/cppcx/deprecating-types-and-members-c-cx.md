---
title: Einstufen von Typen und Membern als veraltet (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6d61b00690cc087c3baced6d96d0b6c8d73b5850
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040326"
---
# <a name="deprecating-types-and-members-ccx"></a>Einstufen von Typen und Membern als veraltet (C++/CX)

In C++/CX wird die Veraltung von Windows-Runtime Typen und Membern für Producer und Consumer mithilfe des [veralteten](/uwp/api/windows.foundation.metadata.deprecatedattribute) Attributs unterstützt. Wenn Sie eine API nutzen, für die dieses Attribut gilt, erhalten Sie zur Kompilierzeit eine Warnmeldung, die angibt, dass die API veraltet ist, und auch eine alternative API zur Verwendung empfiehlt. In Ihren eigenen öffentlichen Typen und Methoden können Sie dieses Attribut anwenden und eine eigene benutzerdefinierte Meldung bereitstellen.

> [!CAUTION]
> Das [deprecated](/uwp/api/windows.foundation.metadata.deprecatedattribute) -Attribut ist nur für die Verwendung mit Windows-Runtime Typen vorgesehen. Verwenden Sie für Standard-C++-Klassen und -Member das Attribut [__declspec(deprecated)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie eine eigene öffentliche API – z. B. in einer Windows Runtime-Komponente als veraltet markiert wird. Der zweite Parameter vom Typ [Windows:Foundation::Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) gibt an, ob die API als veraltet markiert oder entfernt wird. Derzeit wird nur der Wert DeprecationType::Deprecated unterstützt. Der dritte Parameter im Attribut gibt die [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) an, auf die das Attribut angewendet wird.

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>Unterstützte Ziele

In der folgenden Tabelle werden die Konstrukte aufgeführt, auf die das veraltete Attribut angewendet werden kann:

:::row:::
   :::column span="":::
      klassi
      Führers
      Enumeration
      Aufzählungs Feld \
      Veranstalter
      interface
   :::column-end:::
   :::column span="":::
      anzuwenden
      parametrisierter Konstruktor \
      property\
      Struktur
      Strukturfeld \
      XAML-Steuerelement
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
