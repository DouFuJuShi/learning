常量 Contants

常量有布尔常量、Rune常量、整型常量、浮点常量、复数常量和字符串常量。Rune常量、整数常量、浮点常量和复数常量统称为数值常量。

常量值由Rune、整数、浮点、虚数或字符串文字、表示常量的标识符、常量表达式、结果为常量的转换或某些内置函数的结果值表示。诸如 min 或 max 之类的函数应用于常量参数，unsafe.Sizeof 应用于某些值，cap 或 len 应用于某些表达式，real 和 imag 应用于复数常量，complex 应用于数值常量。布尔真值由预先声明的常量 true 和 false 表示。预先声明的标识符iota表示整型常量。

一般来说，复常量是常量表达的一种形式，将在该部分讨论。

数字常量表示任意精度的精确值并且不会溢出。因此，没有常量表示 IEEE-754 负零、无穷大和非数字值。

常量可以是类型化([typed](https://go.dev/ref/spec#Types))的，也可以是非类型化的。文字常量、true、false、iota 以及某些仅包含无类型常量操作数的常量表达式是无类型的。

常量可以通过常量声明或转换显式地指定类型，或者在变量声明或赋值语句中使用或作为表达式中的操作数时隐式地指定类型。如果常量值不能表示为相应类型的值，则这是一个错误。如果类型是类型参数，则常量将转换为类型参数的非常量值。

无类型常量具有默认类型</mark>，该类型是常量在需要类型化值的上下文中隐式转换为的类型，例如，在没有显式类型的短变量声明中，例如 i := 0 。无类型常量的默认类型分别为 bool、rune、int、float64、complex128 或 string，具体取决于它是布尔、rune、整数、浮点、复数还是字符串常量。

执行限制： 虽然数字常量在语言中具有任意精度，但编译器可以使用精度有限的内部表示法来实现它们。尽管如此，每个实现都必须

- 表示至少 256 位的整数常量。

- 表示浮点常量，包括复数常量的部分，尾数至少为 256 位，带符号二进制指数至少为 16 位。

- 如果无法精确表示整数常量，则给出错误。

- 如果由于溢出而无法表示浮点或复数常量，则会出现错误。

- 如果由于精度限制而无法表示浮点常数或复数常数，则四舍五入到最接近的可表示常数。

这些要求既适用于字面常量，也适用于常量表达式的求值结果( [constant expressions](https://go.dev/ref/spec#Constant_expressions))。