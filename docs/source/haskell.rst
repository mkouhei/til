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
