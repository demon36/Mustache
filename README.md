# Mustache

C++11 header-only [Mustache](http://mustache.github.io) templates with no external dependencies.

[![Build Status](https://travis-ci.org/kainjow/Mustache.svg?branch=master)](https://travis-ci.org/kainjow/Mustache)  
[![Build Status](https://ci.appveyor.com/api/projects/status/github/kainjow/Mustache)](https://ci.appveyor.com/project/kainjow/mustache)

## Example 1

````cpp
Mustache::Mustache<std::string> tmpl{"Hello {{what}}!"};
std::cout << tmpl.render({"what", "World"}) << std::endl;
// Hello World!
````

## Example 2

````cpp
using Data = Mustache::Data<std::string>;
Mustache::Mustache<std::string> tmpl{"{{#employees}}{{name}}, {{/employees}}"};
Data employees{Data::List()};
employees << Data{"name", "Steve"} << Data{"name", "Bill"};
tmpl.render({"employees", employees}, std::cout);
// Steve, Bill, 
````

## Example 3

````cpp
Mustache::Mustache<std::string> tmpl("Hello {{what}}!");
std::stringstream ss;
tmpl.render({"what", "World"}, [&ss](const std::string& str) {
    ss << str;
});
// ss.str() == "Hello World!"
````

## Compilers Tested

- Xcode 4.6, 6.3
- GCC 4.8, 4.9
- Clang 3.3, 3.4
- Visual Studio 2013, 2015 CTP

## Run Tests

For *nix:

    make

For OS X:

    make mac

For Visual Studio 2013 (CMake 2.8+ required):

    build.bat

For Visual Studio 2015 (CMake 3.1+ required):

    build.bat 14

## TODO

- Test against [spec](https://github.com/mustache/spec)

## License

    Copyright 2015 Kevin Wojniak
    
    Boost Software License - Version 1.0 - August 17th, 2003
    
    Permission is hereby granted, free of charge, to any person or organization
    obtaining a copy of the software and accompanying documentation covered by
    this license (the "Software") to use, reproduce, display, distribute,
    execute, and transmit the Software, and to prepare derivative works of the
    Software, and to permit third-parties to whom the Software is furnished to
    do so, all subject to the following:
    
    The copyright notices in the Software and this entire statement, including
    the above license grant, this restriction and the following disclaimer,
    must be included in all copies of the Software, in whole or in part, and
    all derivative works of the Software, unless such copies or derivative
    works are solely in the form of machine-executable object code generated by
    a source language processor.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. IN NO EVENT
    SHALL THE COPYRIGHT HOLDERS OR ANYONE DISTRIBUTING THE SOFTWARE BE LIABLE
    FOR ANY DAMAGES OR OTHER LIABILITY, WHETHER IN CONTRACT, TORT OR OTHERWISE,
    ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
    DEALINGS IN THE SOFTWARE.
