---
title: Einrichten eines statischen Links zum Registrierungscode (nur C++)
description: Es wird erläutert, wie Sie C++-Code statisch mit dem ATL-Registrierungscode verknüpfen.
ms.date: 09/03/2020
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: f08f7d9433ae1344c7a98a5c52502d03bad21e91
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609161"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Einrichten eines statischen Links zum Registrierungscode (nur C++)

C++-Clients können einen statischen Link zum Registrierungscode erstellen. Die statische Verknüpfung des Parsers der Registrierungsstelle fügt ungefähr 5 KB zu einem Releasebuild hinzu.

Die einfachste Methode zum Einrichten statischer Verknüpfungen geht davon aus, dass Sie [`DECLARE_REGISTRY_RESOURCEID`](reference/registry-macros.md#declare_registry_resourceid) in der Deklaration des Objekts angegeben haben. (Dies ist die Standardspezifikation, die von ATL verwendet wird.)

## <a name="to-create-a-static-link-using-declare_registry_resourceid"></a>So erstellen Sie einen statischen Link mithilfe von `DECLARE_REGISTRY_RESOURCEID`

1. Geben Sie **`/D _ATL_STATIC_REGISTRY`** anstelle von **`/D _ATL_DLL`** in der CL-Befehlszeile an. Weitere Informationen finden Sie unter [`/D`](../build/reference/d-preprocessor-definitions.md).

1. RECOMPILE.

## <a name="see-also"></a>Weitere Informationen

[Registrierungs Komponente (Registrierungs Komponente)](../atl/atl-registry-component-registrar.md)
