---
title: Typweiterleitung (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 0803ecc2ffb2da2748b1ef063481aa2571f27f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171930"
---
# <a name="type-forwarding-ccli"></a>Typweiterleitung (C++/CLI)

Mit *Typweiterleitung* können Sie einen Typ aus einer Assembly (Assembly A) in eine andere Assembly (Assembly B) verschieben, sodass es nicht erforderlich ist, Clients, die Assembly A verwenden, neu zu kompilieren.

## <a name="windows-runtime"></a>Windows-Runtime

Dieses Feature wird in der Windows-Runtime nicht unterstützt.

## <a name="common-language-runtime"></a>Common Language Runtime

Im folgenden Codebeispiel wird die Verwendung dieses Typs veranschaulicht.

### <a name="syntax"></a>Syntax

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>Parameter

*Neu*<br/>
Die Assembly, in die Sie die Typdefinition verschieben.

*type*<br/>
Der Typ, dessen Definition Sie in eine andere Assembly verschieben.

### <a name="remarks"></a>Bemerkungen

Wenn eine Komponente (Assembly) geliefert ist und von Clientanwendungen verwendet wird, können Sie mit der Typweiterleitung einen Typ von der Komponente (Assembly) in eine andere Assembly verschieben, die aktualisierte Komponente (und alle zusätzlichen erforderlichen Assemblys) liefern, und die Clientanwendungen sind weiterhin funktionsfähig, ohne erneut kompiliert zu werden.

Typweiterleitung funktioniert nur für Komponenten, auf die vorhandene Anwendungen verweisen. Wenn Sie eine Anwendung neu erstellen, müssen die entsprechenden Assemblyverweise für alle in der Anwendung verwendeten Typen vorhanden sein.

Beim Weiterleiten eines Typs (Typ A) aus einer Assembly müssen Sie das `TypeForwardedTo`-Attribut für diesen Typ sowie einen Assemblyverweis hinzufügen. Die Assembly, auf die Sie verweisen, muss eine der folgenden Alternativen enthalten:

- Die Definition für Typ A.

- Ein `TypeForwardedTo`-Attribut für Typ A sowie einen Assemblyverweis.

Zu den Beispielen für Typen, die weitergeleitet werden können, zählen:

- Verweisklassen

- Wertklassen

- Enumerationen

- Schnittstellen

Sie können die folgenden Typen nicht weiterleiten:

- Generische Typen

- Native Typen

- Geschachtelte Typen (wenn Sie einen geschachtelten Typ weiterleiten möchten, sollten Sie den einschließenden Typ weiterleiten)

Sie können einen Typ zu einer Assembly weiterleiten, die in einer beliebigen, der Common Language Runtime entsprechenden Sprache erstellt wurde.

Wenn also eine Quellcodedatei, die zum Erstellen der Assembly „A.dll“ verwendet wird, eine Typdefinition enthält (`ref class MyClass`), und Sie diese Typdefinition zu Assembly „B.dll“ verschieben möchten, gehen Sie wie folgt vor:

1. Verschieben Sie die `MyClass`-Typdefinition in eine Quellcodedatei, die zum Erstellen von „B.dll“ verwendet wird.

2. Erstellen Sie Assembly „B.dll“.

3. Löschen Sie die `MyClass`-Typdefinition aus dem zum Erstellen von „A.dll“ verwendeten Quellcode, und ersetzen Sie sie durch Folgendes:

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. Erstellen Sie Assembly „A.dll“.

5. Verwenden Sie „A.dll“ ohne erneute Kompilierung von Clientanwendungen.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`
