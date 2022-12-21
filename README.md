# gotor

### Status/Social Links
[![Go](https://github.com/DedSecInside/gotor/actions/workflows/go.yml/badge.svg)](https://github.com/DedSecInside/gotor/actions/workflows/go.yml)
[![Open Source Helpers](https://www.codetriage.com/kingakeem/gotor/badges/users.svg)](https://www.codetriage.com/kingakeem/gotor)
[![](https://img.shields.io/badge/Made%20with-Go-blue.svg?style=flat-square)]()

This is an HTTP REST API and command line program to gather and analyze data using web-crawling via TOR.
The program is meant to be used in tandem with [TorBot](https://github.com/DedSecInside/TorBot), but the API and CLI can be run separately.

### CLI Flags

#### TOR (can also be set from `.env` to retain settings, CLI flags will override environment variables at runtime)
- `-h` SOCKS5 proxy host, defaults to localhost (127.0.0.1)
- `-p` SOCKS5 proxy port, defaults to 9050

#### REST
- `-server` Starts HTTP server that provides a REST API to the crawling mechanisms
- Current crawling mechanisms include: 
	- Building relationship tree of links where children nodes represents links that can be found on a website
	- Getting the IP of the current Tor client
	- Retrieving phone numbers found on websites
	- Retrieving emails found on websites
- e.g. `go run src/cmd/main/main.go -server` <- server will start

#### Additional
- `-d` Searching for children nodes of links, defaults to 1
- `-o` Output destination, supported formats include:
	- `terminal` (tree is printed directly to terminal)
	- `excel` results are saved to `.xlsx` file in current directory
	- `json` results are saved to `.json` file in current directory
- e.g. `go run src/cmd/main/main.go -l https://example.com -d 2 -o excel` <- will create a tree of URLs using https.example.com as the root with a depth of 2 and store the results in an xlsx file.

- TOR can be disabled using the `USE_TOR` flag in `.env`

### How it works
![Crawling drawio](https://user-images.githubusercontent.com/13573860/132710986-954b626d-5b42-4fc3-820a-737419690f35.png)
