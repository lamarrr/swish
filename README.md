# Swish
 ![](assets/icon.png) 
 
## Overview 
Swish is a Modern C++ 17 HTTP client library for Humans

Swish is a simple libcurl wrapper (API) which provides mostly, data structures to make operating with libcurl much easier and pain free as compared to error-prone manual manipulation of sockets.


## Installation
- Install libcurl (7.60.0 or higher)
- clone this repo
- build and install using cmake
For linux users
	
	
		user@pc:~$ cmake .
		user@pc:~$ sudo make install



## Quick Start
	
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



## Building
Swish depends on libcurl, ensure you have an active installation.
Compile with the -lcurl postfix flag e.g in clang :
	
	
	user@pc:~$ clang++ -std=c++17 example.cc -o example.o -lcurl
	user@pc:~$ clang++ -std=c++17 example.cc -o example.o -lcurl
	user@pc:~$ ./example.o
