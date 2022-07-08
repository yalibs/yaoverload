# YA-OVERLOAD
yet another C/C++ `std::variant` overload implementation. Header-only data-structure for use with `std::visit` and `std::variant`

## Usage Notes
`ya::overload` is designed specifically to be used in together with `std::variant` and
`std::visit` as a type-safe switch-like structure.

### Using a Universal Reference
If you don't want to define all of your type cases, you can even use the universal reference, like below. 
Be advised that the universal reference _will overrule_ other overloads defined after it, so make sure to put the universal
reference overload as the last overload. Treat it as the `default` keyword in a regular `switch`.
```c++
std::variant<int,float,bool> example_variant = 3;
std::visit(ya::overload(
        [](auto&& v){ std::cout << v << std::endl; },
       ), example_variant);
```

## Example Usage
```c++
#include <overload> // include the library
std::variant<int,float,bool> example_variant = 3;
std::visit(ya::overload(
        [](const int& i){ std::cout << i << " integer"; },
        [](const float& f){ std::cout << f << " float"; },
        [](const bool& b){ std::cout << std::boolalpha << b << " bool"; }
       ), example_variant);
```
