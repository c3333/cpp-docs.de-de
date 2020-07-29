---
title: Verweisklassen und Strukturen (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: d128734f8c78c9198f0731b415c1be35b0c58e65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214957"
---
# <a name="ref-classes-and-structs-ccx"></a>Verweisklassen und Strukturen (C++/CX)

C++/CX unterstützt benutzerdefinierte Verweis *Klassen* und Verweis *Strukturen*sowie benutzerdefinierte *Wert Klassen* und *Wert Strukturen*. Diese Datenstrukturen sind die primären Container, mit denen C++/CX das Windows-Runtime Typsystem unterstützt. Ihre Inhalte werden gemäß bestimmten Regeln an Metadaten ausgegeben, sodass Sie zwischen Windows-Runtime-Komponenten und universelle Windows-Plattform-apps, die in C++ oder anderen Sprachen geschrieben sind, übermittelt werden können.

Eine Verweisklasse oder Verweisstruktur hat die folgenden wesentlichen Funktionen:

- Sie muss in einem Namespace und im Umfang des Namespace deklariert werden und darin eine öffentliche oder private Zugreifbarkeit bieten. Nur öffentliche Typen werden an Metadaten ausgegeben. Definitionen der geschachtelten öffentlichen Klasse sind nicht zulässig. Dies schließt geschachtelte öffentliche [enum](../cppcx/enums-c-cx.md) -Klassen ein. Weitere Informationen finden Sie unter [Namespaces und Typsichtbarkeit](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Sie enthält möglicherweise als Member C++/CX einschließlich Verweis Klassen, Wert Klassen, Verweis Strukturen, Wert Strukturen oder auf NULL festleg Bare Wertestrukturen. Sie kann auch skalare Typen wie `float64` , **`bool`** usw. enthalten. Sie kann auch Standard-C++-Typen wie `std::vector` oder eine benutzerdefinierte Klasse enthalten, sofern diese nicht öffentlich sind. C++/CX-Konstrukte haben möglicherweise **`public`** , **`protected`** , **`internal`** , **`private`** oder **`protected private`** Barrierefreiheit. Alle-oder-Member **`public`** **`protected`** werden an Metadaten ausgegeben. Standard-C++-Typen müssen über **`private`** die-,-oder-Barrierefreiheit verfügen **`internal`** **`protected private`** , wodurch verhindert wird, dass Sie an Metadaten ausgegeben werden.

- Sie implementiert möglicherweise eine oder mehrere *Schnittstellenklassen* oder *Schnittstellenstrukturen*.

- Sie kann jedoch von einer Basisklasse erben, und Basisklassen selbst haben weitere Einschränkungen. Vererbung in öffentlichen Verweisklassenhierarchien ist stärker eingeschränkt als Vererbung in privaten Verweisklassen.

- Sie kann nicht als generisch deklariert werden. Wenn sie über eine private Zugreifbarkeit verfügt, ist es möglicherweise eine Vorlage.

- Die Lebensdauer wird durch automatische Verweiszählung verwaltet.

## <a name="declaration"></a>Deklaration

Das folgende Codefragment deklariert die `Person` -Verweisklasse. Beachten Sie, dass der C++ `std::map` -Standardtyp in den privaten Membern verwendet wird und die Windows-Runtime- `IMapView` Schnittstelle in der öffentlichen Schnittstelle verwendet wird. Beachten Sie außerdem, dass das "^" an die Deklaration von Verweistypen angefügt wird.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementierung

Dieses Codebeispiel zeigt eine Implementierung der `Person` -Verweisklasse.

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Verbrauch

Das nächste Codebeispiel zeigt, wie der Clientcode die `Person` -Verweisklasse verwendet.

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

Sie können eine lokale Verweisklassenvariable auch deklarieren, indem Sie Stapelsemantik verwenden. Ein solches Objekt verhält sich wie eine stapelbasierte Variable, auch wenn der Arbeitsspeicher dennoch dynamisch zugeordnet wird. Ein wichtiger Unterschied besteht darin, dass Sie einer mit Stapelsemantik deklarierten Variablen keinen Nachverfolgungsverweis (%) zuweisen können. So wird gewährleistet, dass der Verweiszähler auf Null verringert ist, wenn die Funktion beendet wird. In diesem Beispiel wird eine Basisverweisklasse `Uri`dargestellt sowie eine Funktion, die diese Klasse mit Stapelsemantik verwendet:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Speicherverwaltung

Sie weisen eine Verweis Klasse im dynamischen Arbeitsspeicher zu, indem Sie das- **`ref new`** Schlüsselwort verwenden.

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

Der handle-to-Object-Operator **`^`** wird als *hat* bezeichnet und ist im Grunde ein intelligenter C++-Zeiger. Der Arbeitsspeicher, auf den er zeigt, wird automatisch zerstört, wenn der letzte hat den Gültigkeitsbereich verlässt oder explizit auf festgelegt ist **`nullptr`** .

Definitionsgemäß verfügt eine Verweisklasse über Verweissemantik. Wenn Sie eine Verweisklassenvariable zuweisen, wird das Handle kopiert, nicht das Objekt selbst. Im nächsten Beispiel zeigen `myClass` und `myClass2` nach der Zuweisung beide auf die gleiche Speicheradresse.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Beim Instanziieren einer C++/CX-Verweisklasse wird ihr Speicher mit 0 (Null) initialisiert, bevor der Konstruktor aufgerufen wird. Daher müssen einzelne Member und auch Eigenschaften nicht mit 0 initialisiert werden. Wenn die C++/CX-Klasse von einer WRL-Klasse (Windows Runtime C++ Library) abgeleitet ist, wird nur der abgeleitete C++/CX-Klassenteil mit 0 initialisiert.

### <a name="members"></a>Member

Eine Verweis Klasse kann **`public`** -, **`protected`** -und- **`private`** Funktionsmember enthalten. nur-Member **`public`** und-Member **`protected`** werden in Metadaten ausgegeben. Die Klassen und Verweis Klassen sind zulässig, können jedoch nicht sein **`public`** . Öffentliche Felder sind nicht zulässig; öffentliche Datenmember müssen als Eigenschaften deklariert werden. Private oder geschützte interne Datenmember können Felder sein. Standardmäßig ist in einer Verweis Klasse der Zugriff auf alle Member **`private`** .

Eine Ref-Struktur ist mit einer Verweis Klasse identisch, mit der Ausnahme, dass die Member standardmäßig über **`public`** Barrierefreiheit verfügen.

Eine Verweis **`public`** Klasse oder Verweis Struktur wird in Metadaten ausgegeben, aber um von anderen universelle Windows-Plattform-apps und Windows-Runtime Komponenten verwendet werden zu können, muss Sie über mindestens einen öffentlichen oder geschützten Konstruktor verfügen. Eine öffentliche Verweis Klasse mit einem öffentlichen Konstruktor muss auch als deklariert werden **`sealed`** , um die weitere Ableitung über die Anwendungs Binärdatei Schnittstelle (ABI) zu verhindern.

Öffentliche Member können nicht als deklariert werden, **`const`** da das Windows-Runtime-Typsystem keine Konstanten unterstützt. Sie können eine statische Eigenschaft verwenden, um einen öffentlichen Datenmember mit einem konstanten Wert zu deklarieren.

Wenn Sie eine öffentliche Verweisklasse oder Verweisstruktur definieren, ordnet der Compiler die erforderlichen Attribute für die Klasse zu und speichert diese Informationen in der WINMD-Datei der App. Wenn Sie jedoch eine öffentliche nicht versiegelte Verweis Klasse definieren, wenden Sie das- `Windows::Foundation::Metadata::WebHostHidden` Attribut manuell an, um sicherzustellen, dass die Klasse für universelle Windows-Plattform apps, die in JavaScript geschrieben sind, nicht sichtbar ist.

Eine Verweis Klasse kann über C++-Standardtypen (einschließlich- **`const`** Typen) in beliebiger-,-oder-Member verfügen **`private`** **`internal`** **`protected private`** .

Öffentliche Verweisklassen, die über Typparameter verfügen, sind nicht zulässig. Benutzerdefinierte generische Verweisklassen sind nicht zulässig. Eine private, interne oder private geschützte Verweisklasse ist möglicherweise eine Vorlage.

## <a name="destructors"></a>Destruktoren

In C++/CX **`delete`** ruft der Aufruf von für einen öffentlichen Dekonstruktor den Dekonstruktor unabhängig vom Verweis Zähler des Objekts auf. Durch dieses Verhalten können Sie einen Destruktor definieren, der eine benutzerdefinierte Bereinigung von nicht-RAII-Ressourcen in einer deterministischen Weise ausführt. Allerdings wird auch in diesem Fall das Objekt selbst nicht aus dem Arbeitsspeicher gelöscht. Der Speicher für das Objekt wird nur freigegeben, wenn der Verweiszähler null erreicht.

Ist der Destruktor einer Klasse nicht öffentlich, wird er nur aufgerufen, wenn der Verweiszähler null erreicht. Wenn Sie `delete` für ein Objekt mit einem privaten Dekonstruktor aufzurufen, löst der Compiler die Warnung c4493 aus aus, die besagt, dass DELETE Expression keine Auswirkung hat, da der Dekonstruktor von \<type name> nicht über "Public"-Barrierefreiheit verfügt.

Verweisklassendestruktoren können nur wie folgt deklariert werden:

- öffentlich und virtuell (für versiegelte oder unversiegelte Typen)

- geschützt privat und nicht virtuell (nur für unversiegelte Typen)

- privat und nicht virtuell (nur für versiegelte Typen)

Keine andere Kombination von Zugreifbarkeit, Virtualität und Versiegelung ist zulässig.  Wenn Sie nicht explizit einen Destruktor deklarieren, generiert der Compiler einen öffentlichen virtuellen Destruktor, wenn die Basisklasse des Typs oder ein Member einen öffentlichen Destruktor hat. Andernfalls generiert der Compiler einen geschützten, privaten und nicht virtuellen Destruktor für unversiegelte Typen oder einen privaten, nicht virtuellen Destruktor für versiegelte Typen.

Das Verhalten ist nicht definiert, wenn Sie versuchen, auf die Member einer Klasse zuzugreifen, deren Destruktor bereits ausgeführt wurde. Wahrscheinlich wird das Programm abstürzen. Das Aufrufen von `delete t` für einen Typ, der keinen öffentlichen Destruktor besitzt, hat keine Auswirkungen. Das Aufrufen von `delete this` für einen Typ oder eine Basisklasse, die über einen bekannten **`private`** oder **`protected private`** Dekonstruktor innerhalb der Typhierarchie verfügt, hat ebenfalls keine Auswirkung.

Wenn Sie einen öffentlichen Destruktor deklarieren, generiert der Compiler den Code so, dass die Verweisklasse `Platform::IDisposable` implementiert und der Destruktor die `Dispose` -Methode implementiert. `Platform::IDisposable`ist die C++/CX-Projektion von `Windows::Foundation::IClosable` . Implementieren Sie niemals explizit diese Schnittstellen.

## <a name="inheritance"></a>Vererbung

Platform::Object ist die universelle Basisklasse für alle Verweisklassen. Alle Verweisklassen sind implizit konvertierbar in Platform::Object und können [Object::ToString](../cppcx/platform-object-class.md#tostring)überschreiben. Das Windows-Runtime Vererbungs Modell ist jedoch nicht als allgemeines Vererbungs Modell vorgesehen. in C++/CX bedeutet dies, dass eine benutzerdefinierte öffentliche Verweis Klasse nicht als Basisklasse fungieren kann.

Wenn Sie ein XAML-Benutzersteuerelement erstellen und das Objekt am Abhängigkeitseigenschaftensystem teilnimmt, können Sie `Windows::UI::Xaml::DependencyObject` als Basisklasse verwenden.

Nachdem Sie eine unversiegelte Klasse `MyBase` definiert haben, die von `DependencyObject`erbt, können andere öffentliche oder private Verweisklassen in Ihrer Komponente oder App von `MyBase`erben. Vererbung in öffentlichen Verweisklassen sollte nur vorgenommen werden, um Überschreibungen von Methoden, polymorphe Identität und Kapselung zu unterstützen.

Eine private Basisverweisklasse ist nicht erforderlich, um von einer vorhandenen unversiegelten Klasse abzuleiten. Wenn Sie eine Objekthierarchie benötigen, eine Ihre eigene Programmstruktur zu modellieren oder die Wiederverwendung von Code zu aktivieren, verwenden Sie private oder interne Verweisklassen, oder am besten Standard-C++-Klassen. Sie können die Funktionalität der privaten Objekthierarchie durch einen öffentlichen versiegelten Verweisklassenwrapper verfügbar machen.

Eine Verweis Klasse, die über einen öffentlichen oder geschützten Konstruktor in C++/CX verfügt, muss als versiegelt deklariert werden. Diese Einschränkung bedeutet, dass es keine Möglichkeit gibt, dass Klassen, die in anderen Sprachen wie c# oder Visual Basic geschrieben sind, von Typen erben, die Sie in einer Windows-Runtime Komponente deklarieren, die in C++ geschrieben ist/CX.

Im folgenden sind die grundlegenden Regeln für die Vererbung in C++/CX aufgeführt:

- Verweisklassen können direkt von höchstens einer Basisverweisklasse erben, jedoch können eine beliebige Anzahl von Schnittstellen implementieren.

- Besitzt eine Klasse einen öffentlichen Konstruktor, muss als versiegelt deklariert werden, um eine weitere Ableitung zu verhindern.

- Sie können öffentliche unversiegelte Basisklassen erstellen, die interne oder geschützte private Konstruktoren besitzen, vorausgesetzt, dass sich die Basisklasse direkt oder indirekt von einer vorhandenen unversiegelten Basisklasse wie `Windows::UI::Xaml::DependencyObject`ableitet. Vererbung von benutzerdefinierten Verweisklassen über WINMD-Dateien wird nicht unterstützt. Eine Verweisklasse kann jedoch von einer Schnittstelle erben, die in einer anderen WINMD-Datei definiert ist. Sie können abgeleitete Klassen aus einer benutzerdefinierten Basis Verweis Klasse nur innerhalb derselben Windows-Runtime Komponente oder universelle Windows-Plattform-app erstellen.

- Für Verweisklassen wird nur öffentliche Vererbung unterstützt.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

Das folgende Beispiel zeigt, wie eine öffentliche Verweisklasse, die von anderen Verweisklassen abgeleitet wird, in einer Vererbungshierarchie verfügbar gemacht wird.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Weitere Informationen

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[Wertklassen und Strukturen](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
