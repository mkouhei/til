==================
 Learning Haskell
==================

* filename suffix is ``.hs``
* haskell-mode
* REPL is ``ghci``

Stack
=====

* `haskell-stack <https://www.spock.li/tutorial/>`_

.. code-block:: sh

   $ sudo apt-get install haskell-stack
   $ stack setup

Compile
=======

.. literalinclude:: _static/haskell/hello.hs
   :language: haskell
   :linenos:

.. code-block:: sh

   $ ghc hello.hs
   [1 of 1] Compiling Main             ( hello.hs, hello.o )
   Linking hello ...
   $ ls hello*
   hello  hello.hi  hello.hs hello.o
   $ file hello.hi
   hello.hi: data

strace hello.hi
---------------

.. literalinclude:: _static/haskell/strace-hello-hi.txt

strace hello.o
--------------

.. literalinclude:: _static/haskell/strace-elf-relocatable.txt

.. code-block:: sh

   $ file hello.o
   hello.o: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped
   $ file hello
   hello: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=6b6cf01380d619a867a9df1bc93938cfe6ee71de, not stripped
   $ strings hello | wc -l
   12567
   $ ./hello
   "hello"

runghc
------

.. literalinclude:: _static/haskell/runghc-strace.txt

execute ELF binary
------------------

.. literalinclude:: _static/haskell/hs-elf-executable-strace.txt

LaTeX mode
==========

This is cool!

.. literalinclude:: _static/haskell/hello.lhs
   :language: LaTeX

.. code-block:: sh

   $ runghc hello.lhs
   "hello"

wai
===

.. code-block:: haskell

   {-# LANGUAGE OverloadedStrings #-}

without this sentence

.. code-block:: haskell

   $ stack build
   wai-sample-0.1.0.0: build
   Preprocessing executable 'wai-sample' for wai-sample-0.1.0.0...
   [1 of 1] Compiling Main             ( src/Main.hs, .stack-work/dist/x86_64-linux/Cabal-1.22.5.0/build/wai-sample/wai-sample-tmp/Main.o )
   
   /path/to/wai-sample/src/Main.hs:19:59:
       Couldn't match expected type ‘bytestring-0.10.6.0:Data.ByteString.Lazy.Internal.ByteString’
                   with actual type ‘[Char]’
       In the third argument of ‘responseLBS’, namely ‘"Hello wai"’
       In the second argument of ‘($)’, namely
           ‘responseLBS status200 [] "Hello wai"’
       In the expression: respond $ responseLBS status200 [] "Hello wai"
   
   --  While building package wai-sample-0.1.0.0 using:
         /home/mkouhei/.stack/setup-exe-cache/x86_64-linux/setup-Simple-Cabal-1.22.5.0-ghc-7.10.3 --builddir=.stack-work/dist/x86_64-linux/Cabal-1.22.5.0 build exe:wai-sample --ghc-options " -ddump-hi -ddump-to-file"
       Process exited with code: ExitFailure 1

