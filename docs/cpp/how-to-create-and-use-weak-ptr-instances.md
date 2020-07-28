---
title: 'Vorgehensweise: Erstellen und Verwenden von weak_ptr-Instanzen'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: d7caea7cfd13b3a41a1cd20f88a9914267cf9677
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187854"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Vorgehensweise: Erstellen und Verwenden von weak_ptr-Instanzen

Manchmal muss ein Objekt eine Möglichkeit speichern, auf das zugrunde liegende Objekt eines [shared_ptr](../standard-library/shared-ptr-class.md) zuzugreifen, ohne dass der Verweis Zähler erhöht wird. Diese Situation tritt in der Regel auf, wenn zyklische Verweise zwischen `shared_ptr`-Instanzen vorliegen.

Der optimale Entwurf ist die Vermeidung von gemeinsamem Zeigerbesitz. Wenn Sie jedoch gemeinsamen Besitz von `shared_ptr`-Instanzen benötigen, vermeiden Sie zyklische Verweise zwischen ihnen. Wenn zyklische Verweise unvermeidlich sind oder aus irgendeinem Grund vorzuziehen sind, verwenden Sie [weak_ptr](../standard-library/weak-ptr-class.md) , um einem oder mehreren Besitzern einen schwachen Verweis auf ein anderes zu übergeben `shared_ptr` . Mit `weak_ptr` können Sie einen `shared_ptr` erstellen, der eine vorhandene Gruppe verwandter Instanzen verknüpft, wobei nur die zugrunde liegende Speicherressource weiterhin gültig ist. Der `weak_ptr` selbst nimmt nicht an der Referenzzählung teil und kann daher nicht verhindern, dass der Referenzzähler den Wert 0 erreicht. Sie können jedoch einen `weak_ptr` verwenden, um zu versuchen, eine neue Kopie des `shared_ptr` zu erhalten, mit der er initialisiert wurde. Wenn der Arbeitsspeicher bereits gelöscht wurde, `weak_ptr` gibt der bool-Operator von den Wert zurück **`false`** . Wenn der Arbeitsspeicher noch gültig ist, erhöht der neue freigegebene Zeiger den Verweiszähler und stellt sicher, dass der Arbeitsspeicher gültig bleibt, solange die `shared_ptr`-Variable im Gültigkeitsbereich liegt.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt einen Fall, in dem `weak_ptr` verwendet wird, um das richtige Löschen von Objekten sicherzustellen, die Ringabhängigkeiten aufweisen. Nehmen Sie für das Beispiel an, dass es erst erstellt wurde, nachdem keine alternativen Lösungen gefunden werden konnten. Die `Controller`-Objekte stellen einige Aspekte eines Computerprozesses dar, und sie funktionieren unabhängig. Jeder Controller muss in der Lage sein, den Status der anderen Controller jederzeit abzufragen, und jeder enthält zu diesem Zweck einen privaten `vector<weak_ptr<Controller>>`. Jeder Vektor enthält einen Zirkelverweis. Daher werden `weak_ptr`-Instanzen anstelle von `shared_ptr` verwendet.

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

Ändern Sie testweise den Vektor `others` in einen `vector<shared_ptr<Controller>>`, und beachten Sie dann in der Ausgabe, dass keine Destruktoren aufgerufen wurden, als `TestRun` zurückkehrte.

## <a name="see-also"></a>Weitere Informationen

[Intelligente Zeiger (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
