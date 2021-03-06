---
title: Sobrecarga de operadores (F#)
description: 'Obtenga información acerca de cómo sobrecargar los operadores aritméticos en una clase o tipo de registro y en el nivel global en F #.'
ms.date: 05/16/2016
ms.openlocfilehash: fc9b7311aa746fd758930365972a187ffdfff0d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="operator-overloading"></a>Sobrecarga de operadores

En este tema se describe cómo sobrecargar los operadores aritméticos de un tipo de clase o registro, así como en el nivel global.


## <a name="syntax"></a>Sintaxis

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Comentarios
En la sintaxis anterior, el *símbolo del operador* es uno de los `+`, `-`, `*`, `/`, `=`, y así sucesivamente. El *lista de parámetros* especifica los operandos en el orden que aparecen en la sintaxis habitual para ese operador. El *cuerpo del método* construye el valor resultante.

Las sobrecargas de operador para los operadores deben ser estáticas. Las sobrecargas de operador para los operadores unarios, como `+` y `-`, debe utilizar una tilde (`~`) en el *símbolo del operador* para indicar que el operador es un operador unario y no es un operador binario, tal y como se muestra en el declaración siguiente.

```fsharp
static member (~-) (v : Vector)
```

En el código siguiente se muestra una clase vectorial que solo tiene dos operadores, uno para el unario menos y uno para la multiplicación por un escalar. En el ejemplo, se necesitan dos sobrecargas para la multiplicación escalar porque el operador debe funcionar con independencia del orden en que aparezcan el vector y el escalar.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Crear operadores nuevos
Se pueden sobrecargar todos los operadores estándar, pero también se pueden crear otros nuevos mediante secuencias de determinados caracteres. Permitidos son caracteres de operador `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, y `~`. El carácter `~` tiene el significado especial de convertir en unario un operador y no forma parte de la secuencia de caracteres de operador. Pueden convertir en no todos los operadores unarios.

Según la secuencia de caracteres exacta utilizada, el operador tendrá una prioridad y una asociatividad determinadas. La asociatividad puede ser de izquierda a derecha o de derecha a izquierda, y se utiliza siempre que aparecen en secuencia y sin paréntesis operadores que tienen el mismo nivel de prioridad.

El carácter operador `.` no afecta a la prioridad, de modo que, por ejemplo, para definir una versión propia de multiplicación que tenga la misma prioridad y asociatividad que la multiplicación ordinaria, se pueden crear operadores tales como `.*`.

Solo los operadores `?` y `?<-` puede empezar por `?`.

Se encuentra en una tabla que muestra la prioridad de todos los operadores en F # [Symbol and Operator Reference](symbol-and-operator-reference/index.md).


## <a name="overloaded-operator-names"></a>Nombres de operador sobrecargados
Cuando el compilador de F# compila una expresión de operador, genera un método que tiene un nombre generado por compilador para ese operador. Este es el nombre que aparece en el Lenguaje Intermedio de Microsoft (MSIL) para el método y también en reflexión e IntelliSense. Normalmente, no es necesario utilizar estos nombres en el código de F#.

En la tabla siguiente se muestran los operadores estándar y sus nombres generados correspondientes.



|Operador|Nombre generado|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
Hay otras combinaciones de caracteres de operador que no se muestran en este texto y que se pueden utilizar como operadores; sus nombres se crean a partir de la concatenación de los nombres de los caracteres individuales según la tabla siguiente. Por ejemplo, +! se convierte en `op_PlusBang`.



|Carácter de operador|nombre|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Operadores de prefijo e infijo
*Prefijo* operadores se esperan que se coloquen delante de un operando o los operandos, como una función. *Infijo* operadores se esperan que se coloquen entre los dos operandos.

Solo se pueden usar determinados operadores como operadores de prefijo. Algunos operadores siempre son operadores de prefijo, otros pueden ser de infijo o de prefijo, y el resto son siempre operadores de infijo. Los operadores que comienzan por `!`, excepto `!=`, el operador `~` y las secuencias repetidas de `~`, son siempre operadores de prefijo. Los operadores `+`, `-`, `+.`, `-.`, `&`, `&&`, `%` y `%%` pueden ser operadores de prefijo u operadores de infijo. La versión prefija de estos operadores se distingue de su versión infija agregando `~` al principio de un operador de prefijo cuando se define. `~` no se usa al utilizar el operador, solo al definirlo.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra el uso de la sobrecarga de operadores para implementar un tipo de fracción. Una fracción se representa mediante un numerador y un denominador. La función `hcf` se usa para determinar el factor común, que se utiliza para reducir fracciones.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Salida:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Operadores en el nivel global
También se pueden definir operadores en el nivel global. El código siguiente define un operador `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

La salida del código anterior es `12`.

De esta forma, es posible redefinir los operadores aritméticos normales porque las reglas de ámbito para F# dictan que los operadores recién definidos tienen prioridad respecto de los operadores integrados.

La palabra clave `inline` se suele utilizar con los operadores globales, que a menudo son pequeñas funciones que se integran mejor en el código de llamada. Hacer que las funciones de operador sean inline permite que se puedan usar con los parámetros de tipo que se resuelven estáticamente a fin de generar código genérico resuelto estáticamente. Para obtener más información, consulte [funciones Inline](functions/inline-functions.md) y [resuelto estáticamente los parámetros de tipo](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Vea también
[Miembros](members/index.md)
