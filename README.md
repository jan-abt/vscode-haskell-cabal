# vscode-haskell-cabal
A `sh` script to build a basic vs-code workspace suitable for `Haskell` projects using the `Cabal` build tool. <br>
It contains a minimal sample app, with little bit of code and a few tests.

# usage
```bash
./vscode-haskell-cabal.sh "your-project" "your name" "you@your-domain.com"
```
if permission settings prevent you from executing the script, change them.
```bash
chmod +x vscode-haskell-cabal.sh
```
Once the project has been generated and built and you are finding that you have trouble adding or modifying files, <br>
check your user-id, e.g. `id `, then group affiliations via `groups` <br>
and finally use that info to change the ownership of all files and folders under the root dir over to you, recursively.
```bash
   sudo chown -R <user-name>:<group> .
```
### Cabal File contents:
```cabal
cabal-version:      3.0
name:               sample-project
version:            0.1.0.0
synopsis:           Synopsis of your-project
license:            MIT
license-file:       LICENSE
author:             You
maintainer:         You@your-domain.com
build-type:         Simple
extra-doc-files:    CHANGELOG.md

common common-all
    ghc-options: -Wall -fwarn-tabs
    default-language: GHC2021
    build-depends:    base ^>=4.18.1.0 && < 5,
                      Cabal ^>=3.10.2.1
    
library
    import:           common-all
    exposed-modules:  Lib, Doodles
    hs-source-dirs:   src
    build-depends:    hspec ^>= 2.11.7,
                      QuickCheck ^>= 2.14.3,
                      checkers ^>=0.6.0 
                
executable monad-transformers
    import:           common-all
    main-is:          Main.hs
    other-modules:    Lib, Doodles
    hs-source-dirs:   app, src
    build-depends:    hspec ^>= 2.11.7,
                      QuickCheck ^>= 2.14.3

test-suite test-app
    import:           common-all
    other-modules:    Lib
    type:             exitcode-stdio-1.0
    main-is:          TestSuite.hs
    hs-source-dirs:   src, test
    build-depends:    hspec ^>= 2.11.7,
                      QuickCheck ^>= 2.14.3



```
