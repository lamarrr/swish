# Swish
 ![](assets/icon.png) 
 
## Overview 
Swish is a Modern C++ 17 HTTP client library for Humans

Swish is for the most parts, A simple libcurl wrapper which provides, data structures and type safe OOP abstractions to make operating with libcurl much easier and pain free as compared to error-prone manual manipulation of net. sockets.


## Features
- Provides implementations for GET, POST (Multipart and Form Fields), DELETE, HEAD, TRACE etc.
- Fast file download
- Simple and expressive API (type safe OOP)
- Byte type customization
- Almost zero cost abstraction
- supports local file://location
- Custom data structures for ease of use


## Installation
- Install libcurl (7.60.0 or higher)
- clone this repo
- build and install using cmake e.g. For linux users
	
```bash	
user@pc:~$ cmake .
user@pc:~$ sudo make install
```

- *or* copy the *swish* directory to your project's local or global include path


## Quick Start

```cpp
/**
 * @file: example.cc
 *
 */
#include <swish/swish.h>

using namespace swish;

int main() {
  // create a new HTTP client
  auto client = Client();

  // Perform request
  auto [response, status] = client.Get("https://github.com");

  // Check if any errors occured
  if (IsOK(status)) {
    // convert body buffer to std::basic_string<char> aka std::string
    std::cout << response.body.ToString() << "\n";

  } else {
    // Interpret status code to english
    std::cerr << "The following Error occured: " << InterpretStatusCode(status)
              << "\n";
  }

  return EXIT_SUCCESS;
}
```


## Building
Swish depends on libcurl, ensure you have an active installation.
Compile with the -lcurl postfix flag e.g in clang :
	
```bash
user@pc:~$ clang++ -std=c++17 example.cc -o example.o -lcurl
user@pc:~$ clang++ -std=c++17 example.cc -o example.o -lcurl
user@pc:~$ ./example.o
```
