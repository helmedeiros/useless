useless
=======

A useless library


## Why??

A common use case is to create a reusable library and an application that consumes it, and host both on GitHub. The application called ["uselessd"](https://github.com/helmedeiros/uselessd) will consumes a this trivial library called ["useless"](https://github.com/helmedeiros/useless).


## Code Layout
The app and both libraries live on GitHub, each in its own repository. `$GOPATH` is the root of the project - each of your GitHub repos will be checked out several folders below `$GOPATH`.

Your code layout would look like this:
```
$GOPATH/
    src/
        github.com/
            helmedeiros/
                useless/
                    .git/
                    useless.go
                    useless_test.go
                    README.md
                uselessd/
                    .git/
                    uselessd.go
                    uselessd_test.go
                    README.md
```
Each folder under `src/github.com/helmedeiros/` is the root of a separate git checkout.

## Setup the Workspace
Let's assume we are starting from scratch. Initialize the two new repositories on GitHub, using the "Initialize this repository with a README" option so your repos can be cloned immediately. Then setup the project like this:

```
export GOPATH=~/go # GOPATH = Go workspace
cd $GOPATH
mkdir -p src/github.com/helmedeiros
cd src/github.com/helmedeiros
git clone git@github.com:helmedeiros/useless.git
git clone git@github.com:helmedeiros/uselessd.git
```

## Libraries
Conventionally, the name of the repository is the same as the name of the package it contains. Our `useless` repo contains `useless.go` which defines `package useless`:

```Go
package useless

func Gorillaz() string {
	return "Clint Eastwood!"
}
```
