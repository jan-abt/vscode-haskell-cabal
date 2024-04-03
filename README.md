# vscode-haskell-cabal
A simple `sh` script to build a basic vs-code workspace suitable for `Haskell` projects using the `cabal` build tool. <br>
It contains a minimal sample app, a little bit of sample code and a few tests.

# usage
```bash
Usage: ./vscode-haskell-cabal.sh "my-project" "My Name" "me@some-domain.com"
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
